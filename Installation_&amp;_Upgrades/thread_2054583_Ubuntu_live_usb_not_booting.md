---
title: "Ubuntu live usb not booting"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by davidlinn on 2012-09-07
I'm trying to put ubuntu 12.04 from a live usb on a machine that has a  bad hard disk. Ubuntu is not booting and seems stuck in a loop trying to  read from the HD or something. 
I see a " device reported invalid CHS sector 0" line being printed.

How do I get it to boot without touching the hard disk ? I thought it would run completely from the RAM.

---

### Post by mattpatey on 2012-09-07
If your BIOS is capable of booting from USB then you should be able to boot without touching the bad HDD. You need to make sure that the system is booting from the USB stick.

1. You can often get a boot menu with F12 or other key. Using this you may be able to select the USB device. If you can't get a boot menu then make sure that the BIOS boot priority is set up to boot from USB HDD before the main HDD. 

2. Booting from USB HDD can be tricky. I find that some of my USB sticks will do it and others won't. And some PCs are fussier than others. Particularly if it is a desktop with lots of USB ports in different places try another USB port. If possible, try to boot another computer with the USB stick to verify that the USB stick is bootable.

3. If you can't get it to boot from a USB stick then booting from a CD/DVD is generally much more reliable.

---

### Post by davidlinn on 2012-09-07
The USB boots properly on another machine and I did set the BIOS to boot from the USB. During the boot process, it seems to checking the HDD and when it fails, redoing the check. I saw the same set of lines being printed again and again.

---

### Post by critin on 2012-09-07
> **davidlinn said:**
> The USB boots properly on another machine and I did set the BIOS to boot from the USB. During the boot process, it seems to checking the HDD and when it fails, redoing the check. I saw the same set of lines being printed again and again.

Try plugging the usb into other ports.

---

