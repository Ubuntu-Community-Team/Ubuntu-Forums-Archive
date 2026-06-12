---
title: "BitDefender antivirus"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by barath on 2007-04-05
I installed bitdefender anti virus.I got the notification saying that the installation was successfull.But when i typed 

           bdc --update


    BDC/Linux-Console v7.0 (build 2492) (i386) (Dec 11 2003 13:24:00)
Copyright (C) 1996-2003 SOFTWIN SRL. All rights reserved.

Error: can't find update dll

I got this error. How can i start the antivirus.

I am beginner in linux

---

### Post by tkjacobsen on 2007-04-05
Try

sudo bdc --update



Actually you don't need antivirus on linux... But if you really like you should use clamav which can be installed via synaptic.  This is supported by the ubuntu community -- this is better than thirt party software.

See [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by shareMenaPeace on 2007-04-12
Hi i have clamav installed and just re-installed it. Still when i try to run it from 
Applications --> System Tools --> AntiVirus 
With the latest kernel 11,17  nothing happens.
What is the command to run clamav?

I want to check a fresh downloaded file fro a possible trojan (windoze).

Thanks

---

### Post by shareMenaPeace on 2007-04-12
I found this informative thread about clamav, but there is something wrong with something else i guess. I even tried uninstall clamav and reinstall. no matter if i use a script, from terminal or from menu nothing happens.
[http://ubuntuforums.org/showthread.php?t=400440&highlight=command+antivirus](http://ubuntuforums.org/showthread.php?t=400440&highlight=command+antivirus)

Hmmm, any ideas?

---

### Post by shareMenaPeace on 2007-04-12
bump...

---

