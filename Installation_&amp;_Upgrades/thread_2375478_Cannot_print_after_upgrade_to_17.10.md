---
title: "Cannot print after upgrade to 17.10"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by peabrane on 2017-10-24
I have a dual boot computer with Windows 10 and Ubuntu-mate 17.10. Since upgrading to 17.10, I cannot print to an HP C5280 printer scanner connected via USB cable. In the queue, the job is listed as pending. Looking under CUPS on Firefox, the printer is listed as Paused - "Unplugged or turned off". This cannot be correct as I can use the scanner without any problem.
From windows 10, I have no problems printing. Neither did I have a problem printing from 17.04. Something has changed as a result of upgrading to 17.10.

---

### Post by drs305 on 2017-10-24
I did a dist-upgrade to 17.10 and my HP printer failed to work initially even though the system saw it. Even though the scanner portion works, you might try re-running hp-setup (or whatever you used to install the printer initially). That's what got my printer working again.

---

### Post by peabrane on 2017-10-25
Many thanks for replying.

I have had the printer so long I can't remember how I installed it.
Tried hp-setup -i it came back with 
error: No device selected/specified or that supports this functionality.

I checked system>administration>printers and it was specified there. So I deleted it and via New> reinstalled it. I now have a working printer. I have been using ubuntu for at least 6 years and installed every new version. I have never had this problem before.

---

