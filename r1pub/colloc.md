# Collar tracking data app README + DEV Log

20190614 dfgchiang

## Objective

Parse animal collar data from a REST API call to URL provided with a
collar ID and key from the manufacturer [VECTRONIC](https://www.vectronic-aerospace.com/wp-content/uploads/2018/11/VECTRONIC-Aerospace-HTTP-Wildlife-API-2.pdf) to obtain
the most recent location (latitude, longitude) by date time of an animal
tracked and place a proximate hexagon location on a map for CDFW Northern
Region (R1) stakeholders.

## Development Progress

1. Created a new HTTP request test page based on Esri JS API sample
[Request data from a remote server](https://developers.arcgis.com/javascript/latest/sample-code/request/index.html) and the sample collar ID (18461) and collar key provided by
[Ken Morefield](mailto:ken.morefield@wildlife.ca.gov)
2. Add the new test page under new repo folder
[../r1pub/collarmap.html](./r1pub/collarmap.html)
3. Push the new commit to origin master repo on GitHub page hosted as
[r9gis.github.io/r1pub/collarmap.html](https://r9gis.github.io/r1pub/collarmap.html)
4. Test new web page - FAILED.

## Issues

1. Sample URL call to
https://wombat.vectronic-wildlife.com:9443/v2/collar/18461/gps?collarkey=68C9B8A4BAD4EC91BA2E6582DFC6E5B5D2EFEAF18DA697AD6ED87DA8CD6179B36F420223714105432FD39CC11EF71511EA486D1669B2E7DF3398A2B30850E619AECA40B1A8C614CED47B66F8DEF6DC324816DE62F06F46114CF66B9D857F2801D3A12AF37E157ACB60D9C5E4868A1D0E8304AFDA39D64FD9DB24A156852BEDDBE27782091E3973B4D59F6D79E2B0F0471038D2C45C763A50454FCD4F664CB6F44F2D8BA71BA9FEF2BF182ECF8E57623B4F4CA019BBA813924474F6423C481E6A791AE37C43C36E920FDEC90B3F65CDCB647BC92A0476081846141E3F155C87970B04DF4E83060CB9D98840EA50C3D42BF1B51769E72F163ED89FA055B302C24E
cannot be viewed in a browser from inside CDFW internal network.
```
wombat.vectronic-wildlife.com:9443/v2/collar/18461/gps?collarkey=...:1 Failed to load resource: net::ERR_TUNNEL_CONNECTION_FAILED
```
2. Outside the CDFW internal network, the URL result can be view in a web page
in a browser, but using Esri JS API Request object in new test page
[./collarmap.html](./collarmap.html) to request the data failed due to
Access-control-allow-origin error.
3. Inside the CDFW internal network, making the URL request resulted in error
```
dojo.js:152 GET https://wombat.vectronic-wildlife.com:9443/v2/collar/18461/gps?collarkey=xxx net::ERR_TUNNEL_CONNECTION_FAILED
a @ dojo.js:152
a.<computed> @ dojo.js:148
x @ dojo.js:517
e @ dojo.js:517
w @ dojo.js:523
(anonymous) @ dojo.js:528
a @ dojo.js:136
then.f.then @ dojo.js:139
C @ dojo.js:528
getcollar @ collarmap.html:119
onclick @ collarmap.html:159
```
4. Try to test a fix in Chrome by going to
Settings/Advanced settings/Open proxy settings failed due to feature locked
down by system Administrator.

//
