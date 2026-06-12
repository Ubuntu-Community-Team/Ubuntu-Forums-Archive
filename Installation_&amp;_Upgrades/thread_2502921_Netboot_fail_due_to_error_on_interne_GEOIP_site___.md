---
title: "Netboot fail due to error on interne GEOIP site  : https://geoip.ubuntu.com/lookup"
date: 2024-12-05
forum: Installation &amp; Upgrades
---

### Post by pnomblot2 on 2024-12-05
Hello, 

we cannot anymore install Ubuntu 20.04 / 22.04 due to subiquity crash which is, I think,  caused by a service outage on [https://geoip.ubuntu.com/lookup](https://geoip.ubuntu.com/lookup)  (error 500 ) 


Subiquity crash : 
 2024-12-05 13:05:07,612 ERROR subiquity.common.geoip:119 geoip lookup failed
 Traceback (most recent call last):
   File "/snap/subiquity/3119/lib/python3.8/site-packages/subiquity/server/geoip.py", line 82, in get_response
     response.raise_for_status()
   File "/snap/subiquity/3119/usr/lib/python3/dist-packages/aiohttp/client_reqrep.py", line 941, in raise_for_status
     raise ClientResponseError(
 aiohttp.client_exceptions.ClientResponseError: 500, message='Internal Server Error', url=URL('https://geoip.ubuntu.com/lookup')


 The above exception was the direct cause of the following exception:


 Traceback (most recent call last):
   File "/snap/subiquity/3119/lib/python3.8/site-packages/subiquity/server/geoip.py", line 117, in _lookup
     self.response_text = await self.strategy.get_response()
   File "/snap/subiquity/3119/lib/python3.8/site-packages/subiquity/server/geoip.py", line 85, in get_response
     raise LookupError from e
 subiquity.server.geoip.LookupError



 GEOP internet service  return an error 500 , see  [https://geoip.ubuntu.com/lookup](https://geoip.ubuntu.com/lookup)



this happen despite the fact we disable GEOIP in APT section of cloud config 

  apt:
    geoip: false
anyone else get this error using Ubuntu auto install ?

---

