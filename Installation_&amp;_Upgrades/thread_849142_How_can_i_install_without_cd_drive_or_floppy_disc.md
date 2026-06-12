---
title: "How can i install without cd drive or floppy disc"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2008-07-04
Hello i have a computer without a cd drive ( well it works but does not auto run at startup and does not have del to enter setup) and no floppy disk drive. But usb ports and network card and 2 other ubuntu computers on the network.
How can i install ubuntu on this?

---

### Post by anubhavrocks on 2008-07-04
You can try installing using USB drive,provided your BIOS supports it.

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb)

---

### Post by DavidTangye on 2008-07-04
If you have another PC, download the alternative CD iso to it, set it up as a netboot bootp, and nfs or ftp server, and netboot into it from the one you want to install ubuntu onto. See [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet) for details. Use the alternative CD iso as I am currently having trouble using the desktop iso, and am working on resolving it.

---

### Post by Partyboi2 on 2008-07-04
Another good one is [[COLOR=Blue]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html")

---

### Post by VMC on 2008-07-04
> **CameronCalver said:**
> Hello i have a computer without a cd drive ( well it works but does not auto run at startup and does not have del to enter setup) and no floppy disk drive. But usb ports and network card and 2 other ubuntu computers on the network.
How can i install ubuntu on this?

How do you want to install this. You have several examples posted. If you want to install using the ISO itself, that's called the loop-back method. Here is one example:

[http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html](http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html)

---

### Post by Rhubarb on 2008-07-04
You can pull out the hard drive and put it into a PC that has an optical drive, install Ubuntu on that, then put the hard drive back.
This method works quite well, but you may have to reconfigure a few things, like video driver.  (Perhaps not even video driver, as the newer X.org in Ubuntu 8.04 is very good).

---

### Post by CameronCalver on 2008-07-04
well im not sure which one would be the easyest this computer isnt old around 2 years probably but im not sure which one would work because i dotn no if the bios has usb booting or network booting the motherboard is a GA-7VRX or a GA - 7VRXP

---

