---
swagger: "2.0"
x-collection-name: Washington Metropolitan Area Transit Authority
x-complete: 0
info:
  title: WMATA Rail Station Information JSON - Station Information
  description: "Description\r\n\r\nReturns station location and address information
    based on a given\r\nStationCode.\r\n\r\nResponse Elements\r\n\r\n\r\n\r\n\r\nElement\r\n\r\nDescription\r\n\r\n\r\n\r\n\r\n\r\nAddress\r\n\r\n\r\nStructure
    describing address information.\r\n\r\n\r\n\r\n\r\nCode\r\n\r\nStation code. Repeated
    from input.\r\n\r\n\r\n\r\nLat\r\n\r\nLatitude.\r\n\r\n\r\n\r\nLineCode1\r\n\r\nTwo-letter
    abbreviation for the line (e.g.: RD, BL, YL, OR, GR,\r\nor SV) served by this
    station.\r\n\r\n\r\n\r\nLineCode2\r\n\r\nAdditional line served by this station.
    This is often the case\r\nwhen stations have multiple platforms (e.g.: Gallery
    Place, Fort\r\nTotten, L'Enfant Plaza, and Metro Center).\r\n\r\n\r\n\r\nLineCode3\r\n\r\nSimilar
    to function as LineCodeX.\r\n\r\n\r\n\r\nLineCode4\r\n\r\nSimilar to function
    as LineCodeX. Currently not in use.\r\n\r\n\r\n\r\nLon\r\n\r\nLongitude.\r\n\r\n\r\n\r\nName\r\n\r\nStation
    name.\r\n\r\n\r\n\r\nStationTogether1\r\n\r\nFor stations with multiple platforms
    (e.g.: Gallery Place, Fort\r\nTotten, L'Enfant Plaza, and Metro Center), the additional\r\nStationCode
    will be listed here.\r\n\r\n\r\n\r\nStationTogether2\r\n\r\nSimilar in function
    to StationTogether2. Currently not in\r\nuse.\r\n\r\n\r\n\r\n\r\n\r\nAddress Elements\r\n\r\n\r\n\r\n\r\n\r\nCity\r\n\r\nCity.\r\n\r\n\r\n\r\nState\r\n\r\nState
    (abbreviated).\r\n\r\n\r\n\r\nStreet\r\n\r\nStreet address (for GPS use).\r\n\r\n\r\n\r\nZip\r\n\r\nZip
    code."
  version: 1.0.0
host: api.wmata.com
basePath: /Rail.svc
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /json/jStationParking:
    get:
      summary: JSON - Parking Information
      description: |-
        Description

        Returns parking information at a station based on a given StationCode. Omit
        the StationCode to return parking information for all stations.

        If a station has no parking, the StationsParking element will contain no
        child elements.

        Response Elements




        Element

        Description





        StationsParking


        Array containing station parking information (StationParking).






        StationParking
        Elements





        Code

        Station code. Useful when returning parking information for all
        stations. Use this value in other rail-related APIs to retrieve
        data about a station.



        Notes

        When not NULL, provides additional parking resources such as
        nearby lots.



        AllDayParking


        Structure describing all-day
        parking options.




        ShortTermParking


        Structure describing short-term
        parking options.






        AllDayParking
        Elements





        TotalCount

        Number of all-day parking spots available at a station.



        RiderCost

        All-day cost per day (weekday) for Metro riders. NULL when no all-day
        spots are available. For most stations, this value is identical to
        the NonRiderCost.

        For cases where the NonRiderCost is different, the lower cost per
        day requires a valid rail trip using a SmarTrip&reg; card
        originating from a station other than the one where the patron
        parked. To receive this lower rate, patrons must pay for their
        parking with the same SmarTrip&reg; card used to enter/exit
        Metrorail, and must exit the parking lot within two hours of
        exiting Metrorail.



        NonRiderCost

        All-day cost per day (weekday) for non-Metro riders. NULL when no all-day
        spots are available.





        ShortTermParking Elements





        SaturdayRiderCost

        Similar to RiderCost, except denoting Saturday prices.



        SaturdayNonRiderCost

        Similar to NonRiderCost, except denoting Saturday prices.



        TotalCount

        Number of short-term parking spots available at a station
        (parking meters).



        Notes

        Misc. information relating to short-term parking. NULL when no
        short-term spots are available.
      operationId: getJsonJstationparking
      x-api-path-slug: jsonjstationparking-get
      parameters:
      - in: query
        name: StationCode
        description: Station code
      responses:
        200:
          description: OK
      tags:
      - Transit
      - Stations
      - Parking
  /json/jStationEntrances:
    get:
      summary: JSON - Station Entrances
      description: "Description\r\n\r\nReturns a list of nearby station entrances
        based on latitude, longitude, and\r\nradius (meters). Omit search parameters
        to return all station entrances.\r\n\r\nResponse Elements\r\n\r\n\r\n\r\n\r\nElement\r\n\r\nDescription\r\n\r\n\r\n\r\n\r\n\r\nEntrances\r\n\r\n\r\nArray
        containing detailed information about station entrances\r\n(StationEntrance).\r\n\r\n\r\n\r\n\r\n\r\n\r\nStationEntrance
        Elements\r\n\r\n\r\n\r\n\r\n\r\nDescription\r\n\r\nAdditional information
        for the entrance, if available.\r\nCurrently available data usually shows
        the same value as the Name\r\nelement.\r\n\r\n\r\n\r\nID\r\n\r\nDeprecated.\r\n\r\n\r\n\r\nLat\r\n\r\nLatitude.\r\n\r\n\r\n\r\nLon\r\n\r\nLongitude.\r\n\r\n\r\n\r\nName\r\n\r\nName
        of the entrance (usually the station name and nearest\r\nintersection).\r\n\r\n\r\n\r\nStationCode1\r\n\r\nThe
        station code associated with this entrance. Use this value\r\nin other rail-related
        APIs to retrieve data about a station.\r\n\r\n\r\n\r\nStationCode2\r\n\r\nFor
        stations containing multiple platforms (e.g.: Gallery\r\nPlace, Fort Totten,
        L'Enfant Plaza, and Metro Center), the other\r\nstation code."
      operationId: getJsonJstationentrances
      x-api-path-slug: jsonjstationentrances-get
      parameters:
      - in: query
        name: Lat
        description: Center point Latitude, required if Longitude and Radius are specified
      - in: query
        name: Lon
        description: Center point Longitude, required if Latitude and Radius are specified
      - in: query
        name: Radius
        description: Radius (meters) to include in the search area, required if Latitude
          and Longitude are specified
      responses:
        200:
          description: OK
      tags:
      - Transit
      - Stations
      - Entrances
  /json/jStationInfo:
    get:
      summary: JSON - Station Information
      description: "Description\r\n\r\nReturns station location and address information
        based on a given\r\nStationCode.\r\n\r\nResponse Elements\r\n\r\n\r\n\r\n\r\nElement\r\n\r\nDescription\r\n\r\n\r\n\r\n\r\n\r\nAddress\r\n\r\n\r\nStructure
        describing address information.\r\n\r\n\r\n\r\n\r\nCode\r\n\r\nStation code.
        Repeated from input.\r\n\r\n\r\n\r\nLat\r\n\r\nLatitude.\r\n\r\n\r\n\r\nLineCode1\r\n\r\nTwo-letter
        abbreviation for the line (e.g.: RD, BL, YL, OR, GR,\r\nor SV) served by this
        station.\r\n\r\n\r\n\r\nLineCode2\r\n\r\nAdditional line served by this station.
        This is often the case\r\nwhen stations have multiple platforms (e.g.: Gallery
        Place, Fort\r\nTotten, L'Enfant Plaza, and Metro Center).\r\n\r\n\r\n\r\nLineCode3\r\n\r\nSimilar
        to function as LineCodeX.\r\n\r\n\r\n\r\nLineCode4\r\n\r\nSimilar to function
        as LineCodeX. Currently not in use.\r\n\r\n\r\n\r\nLon\r\n\r\nLongitude.\r\n\r\n\r\n\r\nName\r\n\r\nStation
        name.\r\n\r\n\r\n\r\nStationTogether1\r\n\r\nFor stations with multiple platforms
        (e.g.: Gallery Place, Fort\r\nTotten, L'Enfant Plaza, and Metro Center), the
        additional\r\nStationCode will be listed here.\r\n\r\n\r\n\r\nStationTogether2\r\n\r\nSimilar
        in function to StationTogether2. Currently not in\r\nuse.\r\n\r\n\r\n\r\n\r\n\r\nAddress
        Elements\r\n\r\n\r\n\r\n\r\n\r\nCity\r\n\r\nCity.\r\n\r\n\r\n\r\nState\r\n\r\nState
        (abbreviated).\r\n\r\n\r\n\r\nStreet\r\n\r\nStreet address (for GPS use).\r\n\r\n\r\n\r\nZip\r\n\r\nZip
        code."
      operationId: getJsonJstationinfo
      x-api-path-slug: jsonjstationinfo-get
      parameters:
      - in: query
        name: StationCode
        description: Station code
      responses:
        200:
          description: OK
      tags:
      - Transit
      - Stations
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---