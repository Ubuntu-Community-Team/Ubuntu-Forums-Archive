---
title: "invalid signatures in packages?"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by Linux_junkie on 2011-03-07
Hi guys, I've just been trying to download latest updates to Xubuntu 10.10 and with after downloading about 180MB with 22MB to complete it the update manager tells me theres a problem with my internet connection.  

I have also Ubyntu 10.04 LTS on a laptop and performede an update to it with no problems whatsoever. Using the exact same connection method for the two computers.

Does anyone know if there is a problem with the signatures for the remaining packages still to download?

---

### Post by Linux_junkie on 2011-03-07
Update on problem...
Received the following error whilst trying to update system.

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.2-0ubuntu1_all.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.2-0ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]

---

### Post by Sean Moran on 2011-03-07
> **Linux_junkie said:**
> Update on problem...
Received the following error whilst trying to update system.

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.2-0ubuntu1_all.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.2-0ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1_i386.deb) 404  Not Found [IP: 91.189.92.167 80]

Perhaps try changing Software Sources to the Main Server, because the 404 error usually means that your computer and the repository server are not talking, just like the 404 errors on web pages.

If that doesn't work, and two different servers give you the same errors, then it is most likely your own Internet connection.  Keep reloading the web pages in the browser every few minutes, because apt-get doesn't always make the right noises when ISP connections timeout.  

I got the same problems today with apt-get, and one answer (if all else is good with the connection) is to open a browser and scoot through a few usual sites to wake up the connection that the ISP thinks has fallen asleep because apt-get doesn't yawn the way web browsers do when they wake up.

---

