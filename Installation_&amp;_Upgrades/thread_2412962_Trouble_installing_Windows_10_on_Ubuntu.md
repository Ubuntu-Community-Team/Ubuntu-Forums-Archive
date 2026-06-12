---
title: "Trouble installing Windows 10 on Ubuntu"
date: 2019-02-19
forum: Installation &amp; Upgrades
---

### Post by derfey on 2019-02-19
This is my first post on Ubuntu forums and my last if this doesn't get fixed.

I tried ubuntu, for a whole week, and I enjoyed it, but it wasn't for me.
So I figured: "Well I bet it will be easy to just go back to Windows!" How wrong I was.
I followed every tutorial, article, commands and everything else. Nothing worked at all.
Win/woeUSB didn't work.
I tried using Gparted to format my USBStick and used Grub, never worked.
And when I was so close... An error popped up on my windows installation: "install.win does not exist!"
PLEASEPLEASEPLEASEPLEASE HELP ME!

---

### Post by Frogs Hair on 2019-02-19
Did you use the entire disk for Ubuntu or dual boot ? If your computer had preinstalled Windows was/is there a recovery partition for factory reset?

---

### Post by derfey on 2019-02-19
I was dumb to think that most porgrams would work and... Yeah.... WIndows was already in the computer before I installed, and I was so freaking dumb that I selected "Delete Everything" in the ubuntu installation, yeah, I had some backups saved on my windows installation.

---

### Post by oldfred on 2019-02-19
Is this a newer UEFI system. Microsoft converted to UEFI with release of Windows 8 in 2012.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key) 

But if older Windows 7 system, and you totally erased system, you now have to purchase a new product key.

If you then have a valid prouct key, you can install Windows from scratch. Its just if using the standard Microsoft offical copy, it still will not include any unique drivers your system may require. You then have to go to your vendors side & download drivers assuming your Windows works well enough to do that.

Windows is actually a lot more difficult to install than Linux, especially if older copy. And not particularly easy even if newer copy.
 I hate the number of reboots & time it takes.

---

### Post by Frogs Hair on 2019-02-19
> **derfey said:**
> I was dumb to think that most porgrams would work and... Yeah.... WIndows was already in the computer before I installed, and I was so freaking dumb that I selected "Delete Everything" in the ubuntu installation, yeah, I had some backups saved on my windows installation.

If you can get Windows 10 installed your device info should still be  listed on Microsoft servers and the OS _may_ activate without a problem.

---

### Post by koshamo on 2019-02-19
If you wiped your entire disk and installed Ubuntu then your data is obviously... well, gone. Download an official iso from Microsoft and use woeusb to create a bootable usb drive. There should be some instructional videos on YouTube that will tell you *exactly *what to do. 

I am sorry for your loss :-({|=

---

