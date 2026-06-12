---
title: "[OT] Anybody played with apt-file?"
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-30
Hi all, 
 Another OT question. Has anybody played with apt-file update. 

 ran apt-file update the first time. It did the whole thing apart from finding stuff from ddebs which I guess is fine
 shirish@shirish-desktop:~$ sudo apt-file update
Can't get [http://ddebs.ubuntu.com/dists/intrepid/Contents-i386.gz](http://ddebs.ubuntu.com/dists/intrepid/Contents-i386.gz)
Can't get [http://ddebs.ubuntu.com/dists/intrepid-updates/Contents-i386.gz](http://ddebs.ubuntu.com/dists/intrepid-updates/Contents-i386.gz)
Can't get [http://ddebs.ubuntu.com/dists/intrepid-proposed/Contents-i386.gz](http://ddebs.ubuntu.com/dists/intrepid-proposed/Contents-i386.gz)
Can't get [http://ddebs.ubuntu.com/dists/intrepid-security/Contents-i386.gz](http://ddebs.ubuntu.com/dists/intrepid-security/Contents-i386.gz)

 Now I'm updating the cache again and still finding its taking quite some time.
 
I have wget as well as curl but haven't done 
any modifications in  /etc/apt/apt-file.conf

Any ideas anybody?

---

