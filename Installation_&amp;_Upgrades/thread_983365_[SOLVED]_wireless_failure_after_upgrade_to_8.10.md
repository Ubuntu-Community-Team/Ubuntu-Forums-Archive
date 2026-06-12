---
title: "[SOLVED] wireless failure after upgrade to 8.10"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by dldeskins on 2008-11-15
I put off upgrading until I had time to mess with the wireless.  I was using MadWifi on my Toshiba Satellite U305-S7448, and every time that the kernel was updated, I had to rebuild MadWifi for that kernel.

I finally backed up my files and upgraded overnight, and have been trying to get the wireless going since then.  I have tried the built in drivers, one at a time... rebooting on each activation.  Then I tried deactivating them both, and building MadWifi and trying to get it work.  Everything has failed.

Please help, if you have any ideas.

Thanks,

Don

---

### Post by alwayshere on 2008-11-15
[http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)


have a look at this site

---

### Post by dldeskins on 2008-11-15
> **alwayshere said:**
> [http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://linuxwireless.org/en/users/Download#DownloadlatestLinuxwirelessdrivers)


have a look at this site

I guess i asked for help too soon.  I went to the site that you suggested and downloaded the file.  I was right in the middle of the make, and i decided to try the built-in drivers again.  I activated the first one (for the 5000 series) and it recognized my network.  I put the passphrase in and it connected up.

thank you much, though.  Looks like that I should have been a bit more persistent. :)

---

### Post by dldeskins on 2008-11-15
OK, I thought I had it solved and it is so partially.

The right driver is the first one for 5000 series LAN cards.  But if I restart/start, I have no network connection.  I go into System > Administration > Hardware drivers and the first is activated "but not in use".  I deactivate it and then activate it, then it connects up to the wireless network.

Any suggestions to get this connection on start up?

---

### Post by dldeskins on 2008-11-17
bump

---

### Post by dldeskins on 2008-11-24
I found the answer.  I was looking through /etc/modprobe.d/ and found a madwifi module.  I figured this was interferring with the other driver (I was using madwifi with 8.04).  I looked around and uninstalled all madwifi tools/modules.  This solved the problem

---

