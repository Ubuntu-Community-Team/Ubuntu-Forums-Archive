---
title: "Help with GRUB for booting UBUNTU off an external hard disk"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by pranav on 2007-04-08
My status:

I intend to boot the PC off an external USB harddisk (seagate 250GB; thru an ide to usb casing) 

(K)Ubunbtu (edgy) is installed on the external hdd (sdb5) and the GRUB is installed on the MBR of the internal hdd; it boots successfully. This is what happened by default.

i have formatted the MBR of the internal device to let it boot the proprietary OS by default (its a corporate environment and hence the limitation to keep the internal hdd untouched)

Also i cant keep the USB drive plugged in always... After installing GRUB on the MBR of the external hdd the BIOS refuses to let the external  hdd boot, (shortcoming of the motherboard... in spite of setting it to boot from "USB device")

There is no floppy disk on the machine. Hence the only option is a CD boot. 

So what i really want is a live CD of some kind such that it will boot and then let me choose what hard disk to boot from... windows on the internal or ubuntu on the external.

Please suggest what should i do ?

---

### Post by confused57 on 2007-04-08
You could try using the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by pranav on 2007-04-09
The Super Grub Disk Worked... Thank you so much...

UbuntuForums are the best...


I cant express my gratitude to you for your suggestion...

Thank you so much... I love you

---

