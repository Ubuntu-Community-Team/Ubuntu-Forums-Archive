---
title: "Xymon (hobbit) system monitor Install."
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by MasterGamerJK on 2012-03-20
Software: [http://www.xymon.com/](http://www.xymon.com/)

Does anyone know of a GOOD tutorial that is designed around Ubuntu. I have searched for two days now and can only seem to find guides for Solaris and centOS etc. So far this is the best that I have found: 

[http://www.kaltura.org/kaltura-ce-v30-installing-xymon-monitoring-package-ubuntu-1004-0](http://www.kaltura.org/kaltura-ce-v30-installing-xymon-monitoring-package-ubuntu-1004-0)

I have not had a chance to try it yet, but I did spend several hours last night doing an install from scratch.

Problem: When running "./configure-server" I get an error for rrdtools. I have installed them (also from source) and ran the example (which appears to be working) but during the configuration it says that it found the rrdtools, but ran into an error when compiling them.  Any thoughts?

Message: "ERROR: RRDtool include files found in /usr/local, but compile fails."

---

### Post by MasterGamerJK on 2012-03-21
Soo...  Apparently you can 

"apt-get install apach2"
"apt-get install xymon"  <--- gives you an older version, but still good.
Browse to [http://127.0.0.1/hobbit](http://127.0.0.1/hobbit)

I would imagine it would be easy to upgrade from there.

---

