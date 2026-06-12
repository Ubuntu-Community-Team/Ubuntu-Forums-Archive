---
title: "Installed Ubuntu on 2nd hard drive, but no grub on reboot"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Rorscharch on 2007-09-22
Hi there,

I used to run Windows XP on a 250gb SATA hard drive, which was fine. I added a 40gb IDE hard drive and installed ubuntu 7.04 on it, using the automatic partitioning of just that drive.

When I rebooted after the install, XP loaded without showing me a grub interface asking which OS I wanted to load.

What have I missed out/done wrong? I went to boot menu, but all I can choose is to boot from hard drive (which is daft since i want to choose between 2 hard drives). I loaded the live ubuntu cd and typed "sudo grub" and then "find /boot/grub/stage1" which returned "hd0,0". I followed the advice here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to no avail.

I take it that grub hasn't installed on my mbr, but where is it? On my SATA drive? I don't know what to do, can someone help?

Sorry if I sound pretty clueless!

---

### Post by Pumalite on 2007-09-22
Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Rorscharch on 2007-09-22
The super grub disk page doesn't actually give instructions for creating the disk in Windows. It just says "Information will be added here". And I visited the first link, did everything it asked, but nothing changed..

ADDITIONAL INFO:

If it makes any difference, I have an AMD 64 machine and installed the 64bit version of Ubuntu.

---

### Post by logos34 on 2007-09-22
go back into your Bios and look for the hard disk boot priority submenu.  You're just seeing the *device* boot order--i.e. removable drives, cdrom. hard drive, etc.  Set the 40gb ide first.  That's where grub must be--or else it didn't install for some reason.

---

### Post by Rorscharch on 2007-09-22
Thanks logos! That was the only problem. I'm now writing this on Ubuntu.

Thanks again, I owe you one!

---

### Post by logos34 on 2007-09-22
ok, glad to hear it's working.  Enjoy your ubuntu!

---

