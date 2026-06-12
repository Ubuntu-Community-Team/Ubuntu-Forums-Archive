---
title: "&quot;No %%BoundingBox&quot; error for Samsung ML-1660 printer"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by ParadoxUnknown on 2011-02-04
I have a Samsung ML-1660 Black/White laserjet printer. I finally got the driver installed, relocated a file that was in the wrong directory, but now it's giving me an error that a google search is not finding anything on: 

"Printer State: Idle-N %%BoundingBox:comment in header!"

any ideas? Much appreciated.

---

### Post by ParadoxUnknown on 2011-02-13
Before getting this error it wasn't able to find the "rastertosamsungspl" file, so I looked at another forum and it said to copy that file from my /cdroot/Linux/x86_64/at_root/usr/lib64/cups/filter directory to /usr/lib/cups/filter/ directory... see the problem? it was the i386 version. I realised that but thought that person KNEW what they were doing. And we all know the problem with assumptions. 

after that: 
sudo chown root rastertosamsungspl
and done. it works now!

---

