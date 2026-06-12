---
title: "Dual booting windows 7 with ubuntu"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-06-05
I am trying to dual boot windows 7 with ubuntu 12.04 and thought this would be straight forward so must be doing something wrong. 

I have cut CD's 32 and 64 bit and tried to install both in separate installs to see if the result would be any different but get this error 'Unable to find a medium containing a live file system'. Please advise.

---

### Post by Basher101 on 2012-06-05
does your computer support USB boot? Reboot and take a look in your BIOS to see if you can boot from a USB drive. You can then proceed to making a Live USB (instead of a live cd) and try to boot that.

---

### Post by bencouve on 2012-06-05
These appear to be the boot options
Internal CD/DVD Rom Drive
Notebook Hard Drive
!USB Floppy
USB Diskette on key/USB Hard disk
USB CD/DVD Rom Drive
!Network Adapter

I have tried 'USB CD/DVD' Rom Drive but got the same error message,  will now try 'USB Diskett on key/USB Hard Disk'  and see what happens

---

### Post by Varad Vyapari on 2012-06-05
probably when u have a bootable usb device plugged into ur system, the boot options would change and the name of the bootable device would be displayed there. try doing so

---

### Post by Basher101 on 2012-06-05
> **bencouve said:**
> These appear to be the boot options
Internal CD/DVD Rom Drive
Notebook Hard Drive
!USB Floppy
USB Diskette on key/USB Hard disk
USB CD/DVD Rom Drive
!Network Adapter

I have tried 'USB CD/DVD' Rom Drive but got the same error message,  will now try 'USB Diskett on key/USB Hard Disk'  and see what happens

i am sorry i lost track of your thread...

anways here comes the (a bit late) explanation on how to proceed:

your PC does support usb boot, so thats good.
Usb CD/DVD means an external CD/DVD drive, which you would connect using USB (which, ofcourse, you do not have so ignore this)

First you will need to prepare a USB to make it bootable. To do so go here [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) and download the universal USB installer. Plug a USB drive into your PC and run the program. Choose the 12.04 iso and follow the steps onward to make the USB bootable (do not choose persistance, you wont need this!). 
After you are done, reboot and go into the BIOS.

You will set USB hard disk as the first option and let it boot. From here on you should somehow get a live session running, if not write another post explaining what happend.

regards

---

### Post by bencouve on 2012-06-06
Just like to thank [Basher101]("http://ubuntuforums.org/member.php?u=1377584") for his help. I am typing this message from my new Ubuntu install. Though am running the OS from the USB device. Have not done an install onto the hard drive yet. Am concerned about overwriting the Windows 7 OS.

For anyone reading this and wanting to improve on the documentation found on the internet relating to a Ubuntu install then please include the part about making the usb bootable, as am pretty sure it will help.

---

