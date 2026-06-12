---
title: "Ubuntu 6.06.1 installer crashed AGAIN"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by atrain on 2007-01-30
Currently I am trying to install Dapper Drake on a Vectra Pentium III with 512 RAM and 80GHD.  After about 20 tries, it finally booted from the CD.  (I know the CD is clean because I tested it on another computer.)  I clicked the installer icon and followed the instructions, but it will not partition the HD. 

THE INSTALLER JUST CRASHED AGAIN!!  I was at 30% installed, and it crashed.  Here is the message:

It says attach the files /var/log/installer/syslog. /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
File "/usr/bin/ubiquity", line 130 in ?
install(sys.argv[1])
File "/usr/bin/ubiquity", line 55, in install 
ret=wizard.run()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264 in run
self.progress_loop()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 553, in progress_loop
raise RuntimeError, ("Install failed with exit code %s; see"
RuntimeError; install failed with exit code - 11; see /var/log/installer/syslog adn /var/log/syslog

Please help

Aaron 
phone 617-417-1818

---

### Post by K.Mandla on 2007-01-30
Those look a lot like corrupted package errors. Have you checked the CD for errors? Did you check the md5sum on the ISO you downloaded?

---

### Post by atrain on 2007-01-31
Thank you for hte suggestions.  I checked the CD and it is good.  I ran it on a different computer so I know that it works.  I think the HD is corrupt.  Right now I cannot get hte CD to run at all and get this error:

Uncompressing Linux
CRC error
system halted_

Can you give me any advice?

Thank you

Aaron

---

