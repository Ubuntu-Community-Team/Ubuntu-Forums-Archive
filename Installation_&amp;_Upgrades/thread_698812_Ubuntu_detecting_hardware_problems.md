---
title: "Ubuntu detecting hardware problems"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by fwish on 2008-02-16
Hi guys, i'm having a bit of a problem installing via PXE onto a laptop after having major problems with windows - the installer has connected via dhcp, got all the files via proxy but is stuck on 1% on Detecting disks and all other hardware during the setup process...

Has anyone got any ideas to move it on? I've restarted several times but it always gets stuck on this screen. And don't say install via a cd because the cd drive is knackered! :)

Cheers!

---

### Post by fwish on 2008-02-16
By the way I'm a bit new to all of this after having 2 xp machines and a mac, I thought I'd delve in. But any help you can give would be appreciated!!:)

---

### Post by mrsteveman1 on 2008-02-16
Which installer are you using? Where are the PXE images coming from?

Does this laptop lack a CD drive? Does it have the ability to boot from USB? you can make a liveusb for ubuntu out of the livecd pretty easily to test things.

---

### Post by fwish on 2008-02-16
> **mrsteveman1 said:**
> Which installer are you using? Where are the PXE images coming from?

Does this laptop lack a CD drive? Does it have the ability to boot from USB? you can make a liveusb for ubuntu out of the livecd pretty easily to test things.

okay im using the edgy pxe install from [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com)
pxe images files are coming from gb.archive.ubuntu.com

ive tried the boot from usb option before but after various tests and different usb devices this is the most viable method of actually getting stuff on the laptop as the usb often screws it up - the bios sees the usb device but doesn't really want to boot from it even though its got the bootable sectors on it. i really dont know why but thats a different story.... :D

---

### Post by fwish on 2008-02-16
oh never mind - i think ive found out what the problem is, its not detecting the hard drive. thanks for your help anyway!!

---

