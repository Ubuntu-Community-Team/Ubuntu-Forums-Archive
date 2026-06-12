---
title: "Installing Ubuntu on a USB drive"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by kspanks04 on 2009-12-24
I'm a bit new to using Ubuntu portably, i.e. on a usb drive. I successfully installed 9.10 on my 8gb usb drive with a 4gb casper. I booted Ubuntu from the usb drive and was under the impression I had 4 gb of space to install additional software. I've concluded that Ubuntu Live uses the casper only to save common settings with default applications. 

Ok, so I'm wondering if I can just install Ubuntu to the USB drive and use it as a fully functional Ubuntu 9.10 OS portably without altering any settings on the host machines I boot from. 

TLDR? I want to boot Ubuntu 9.10 from my jump drive with the ability to install additional software that will be retained on a system restart. 

Thanks in advanced.

---

### Post by 5BallJuggler on 2009-12-24
Have a read of this, it will help
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

Phil

---

### Post by kspanks04 on 2009-12-24
Hmm, thanks for the link, that thread was semi-helpful, it was a bit outdated. My main wish is to install software via the software center under a live session. That issue wasn't really addressed in that thread. Perhaps I will just have to try some things out myself.

---

### Post by howefield on 2009-12-24
> **kspanks04 said:**
> TLDR? I want to boot Ubuntu 9.10 from my jump drive with the ability to install additional software that will be retained on a system restart.

The option System > Administration > USB Startup Disk Creator will do that.

---

### Post by theozzlives on 2009-12-24
What I did was setup 2 partitions (sdb1=fat32, sdb2=ext4) and did a regular install on sdb2 (I disconnected my HD for the install). Windows only sees the fat32 partition, while I can boot with a full install of Ubuntu.

---

### Post by kspanks04 on 2009-12-24
I used the USB-Installer for Ubuntu via [pendrivelinux]("http://www.pendrivelinux.com/downloads/u910/USB-Installer-for-Ubuntu-v0.2.exe"). I cannot install software via the Software Center but I did install Chrome for Linux and when I rebooted it was still installed, so it appears that it will work after all. 

Another alternative, that would probably enable the Software Center, is to install Wubi to a flash drive and use a bootloader to boot from the USB...you can then uninstall Wubi from the host machine. Here's the tutorial: [Move Wubi to a USB...]("http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/")

Thanks for the replies.

---

