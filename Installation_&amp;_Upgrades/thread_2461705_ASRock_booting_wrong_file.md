---
title: "ASRock booting wrong file"
date: 2021-05-05
forum: Installation &amp; Upgrades
---

### Post by flbrent on 2021-05-05
Hi all.  Six years ago I turned off my mining rig.  Now that Dogecoin has hit the roof, I tried to fire up the machine to see how many coins I had.  One problem though.  Each time I turn it on it ask if I want to "try or install Umbuntu".  I can see my original install on the drive but don't know how to make it the primary boot file.  Any help would be greatly appreciated.

---

### Post by yancek on 2021-05-05
It seems your are booting a 'live/install' DVD or USB so if you want to set the boot priority to boot from a hard drive install, you should see a message on screen immediately upon booting tellling you which key to use to access the BIOS firmware to change boot options.  There is no standard key, if you don't see it on boot you will need to do an online search for your specific computer by manufacturer.

---

### Post by grahammechanical on 2021-05-05
Were you running this process from a Ubuntu live session? Is the Ubuntu live/install session on a USB memory stick or on a DVD ROM? If you remove the install media (USB stick - DVD ROM) the machine should boot from the Ubuntu installation on the internal drive. As to selecting which drive to boot from that you can do from the machine's UEFI settings utility. How to do that is information that is supplied by the machine's manufacturer. I do not think that there is a standard menu system that applies to all versions of a UEFI settings utility used by various computer suppliers.

You know the make of your machine. With the model number you could check the manufacturer's web site and may be download a PDF version of the machine's handbook or instruction manual.

Regards

---

### Post by flbrent on 2021-05-05
Thank you for the help.  I didn't remember that one of the usb's was the original installer.
Now showing on the screen is "grub rescue>_"

---

