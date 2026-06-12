---
title: "Software patch can't find file"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by JBD88 on 2010-05-22
Hi,
Haven't booted to my linux in a while.  Just did.  Many updates.  I'm betting this error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010g~repack-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010g~repack-0ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.30 80]


Anyone help?  Seems to be working fine.

Joe

---

### Post by kiryl viarenich on 2010-08-18
I took it from [here ]("http://launchpadlibrarian.net/42409076/tzdata_2010g%7Erepack-0ubuntu0.8.04_all.deb")
Then copied it to /var/cache/apt/archives and made update using Synaptic. I also had to download some other packages wich are no longer at the repositoory and it worked fine.

---

