---
title: "Ubuntu Install On An External Hard Drive"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by s1mp13m4n on 2008-04-19
Hello, I am new to Ubuntu and want to grow beyond the live cd version that I have been using.  I have an older laptop right now that I am using.  Toshiba S501-5105.  It has a 40GB hard drive in it, P4 1.7, 512MB Ram.  I do not want to partition the 40GB drive that way it stays devoted to WinXP for games and such.  What I would li8ke to do is instal Ubuntu on the external hard drive and be able to boot into it if I choose rather than WinXP.  Do I install Ubuntu like "normal" but have it install to the usb drive and then have the boot loader install to the laptops 40GB drive?  I want to make WinXP default for now.  Is there a way to set things up so that when the usb hard drive is connected the bootloader would "see it" and boot to Linux automatically and when it is not connected simply boot into WinXP?  Thank you for the help.  Also once installed, did they ever  get a driver made for my Linksys wireless N laptop card?  The last time I looked months ago there was still not drive thus I could not use the laptop wirelessly in Linux.  Thank you for the help.  Please keep in mind that I am a Linux n00b so please not "deep" replies I can do commandline if it is step by step but do not know what to do if something goes wrong.  Thank you all for the help.

---

### Post by Pumalite on 2008-04-19
This might help:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Sorry, don't know about your card.

---

### Post by s1mp13m4n on 2008-04-19
OK I installed version 7.10 on an external usb hard drive but it would not boot at all.  I got an error 21.  I could not even boot into WinXP, so I have to repair the Windows MBR so I could use the laptop.  What happened and how do I use my new install of Linux?  I do not see where the laptop will boot from USB, but why could I not have a bootloader on the main hard drive that pointed to the usb drive so it will boot?  If this is possible, how do I do it?  Thank you for the help.

---

### Post by Pumalite on 2008-04-19
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
Have of your installation of Grub was left in your external and part in your internal drive.
I'd reinstall and this time disconnect all other drives if that is possible. If not, installing with Live CD, in step 8, press 'Advanced Tab' and change (hd0) for /dev/xxx, where xxx is your USB. You can find out by running sudo fdisk -l

---

### Post by s1mp13m4n on 2008-04-20
OK, now I installed uBuntu again to the usb drive but now it does not boot into Linux but rather WinXP.  When it came to where to boot loader should be installed I chose hda, the default was hd0.  Last time I picked hd0 the laptop would not boot and gave me an error message and I had to restore the Windows MBR.  I must have the install on the usb drive so now how do I get to it so I can boot into it?  The laptop will not boot from a usb drive, the BIOS does not support that.  Is there a way to install Grub from WinXP and set it up manually, and if so how?  Thank you for the help.

---

### Post by Pumalite on 2008-04-20
If your BIOS does not support booting from USB, it makes little sense installing to it.

---

### Post by s1mp13m4n on 2008-04-20
This is true, but could not grub allow me to pick Linux or Winxp and then have a file that points to the usb drive thus booting?  Rather than booting to usb from the bios?  In other words Grub being the "middle man" which points to the Linux install on usb and for lack of a better word a file that boots from usb after the bios has done its "bootup job"?

---

