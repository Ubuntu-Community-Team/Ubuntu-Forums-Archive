---
title: "do-release-upgrade 24.04 -&gt; 24.04.1 stuck on specific perl deb file requirement"
date: 2024-08-30
forum: Installation &amp; Upgrades
---

### Post by ricksdunn2 on 2024-08-30
# do-release-upgrade   << procedure upgrade ends on the following error.

Could not download the upgrades 

The upgrade has aborted. Please check  your Internet connection or installation media and try again. 
All files  downloaded so far have been kept. 

Failed to fetch
[http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmodule-depends-perl/libmodule-depends-perl_0.16-5_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmodule-depends-perl/libmodule-depends-perl_0.16-5_all.deb)
Connection failed [IP: 91.189.91.81 80]

***

I verified the link to the file required and it appears when using a browser to :
[http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmodule-depends-perl/](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmodule-depends-perl/)

LINK PRESENTED "http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmodule-depends-perl/libmodule-depends-perl_0.16-5_all.deb"

clicking the link there is no response from the WebServer.. also tried using curl again no response.

---

