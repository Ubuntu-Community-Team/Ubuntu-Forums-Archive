---
title: "why wont my laptop boot my external hdd"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by allsystems on 2010-12-20
So I installed ubuntu onto a usb flash drive. Installation went perfect. I then installed virtualbox and then windows xp.however it dosent finish the installation as the flash drive is too slow. I installed the ubuntu onto the flash drive by disconnecting my desktop computer harddrive and then installing on the usb flash drive and then botting this up in my laptop. 
SO I figured an external harddrive would be faster so I did the same rocedure,used my desktop by disconnecting the harddrive and then connecting the external harddrive using the usb wire and installing ubuntu onto it. EVerything works fine on my desktop,it loads up from the external hard drive when the desktop internal hard drive is disconnected. HOWEVER when i connect this external hard drive to my laptop and boot from hard drive,it dosent boot it and loads windows as normal,what am i doing wrong?i used same procedure for flash drive as for the external hard drive.any help appreciated,thanks

---

### Post by wilee-nilee on 2010-12-20
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

You have a usb boot correct? Run this script with the external plugged in.

---

### Post by allsystems on 2010-12-20
il do this tommorow morning and report back

---

### Post by wilee-nilee on 2010-12-20
> **allsystems said:**
> il do this tommorow morning and report back

Alright, I tend to turn off the auto-email after enough hours pass so if you need my help PM me. ;)

---

### Post by efflandt on 2010-12-20
Some Dell computers go so fast through their BIOS check that a USB hard drive may not have spun up yet and be recognized.  So on a Dell laptop I used to have to boot Windows and then reboot for it to see the USB drive.  But I still had to press F12 in the BIOS splash screen (even with USB before hd in BIOS) to boot from USB.

But now I set BIOS to do a more complete BIOS check, which slows up the boot, but gives the USB drive time to spin up and the F12 boot selection to work.

---

