---
title: "[SOLVED] Ubuntu 8.04 install from pen"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by alberto ferreira on 2008-10-27
I have an old laptop (Compaq 1200) and it's cdrom drive is broken.
I had 7.10 installed and working perfectly but now I've tried to install 8.04 and thanks to the malfunctioning drive setup crashed in midst of the installation and because the drive is broken there's no way I can install from cd.


So i need to install from a pen.

The architecture is i686


How do I install Ubuntu 8.04 for i686 architecture from a pen?


I need help desesperately as I need the laptop for school tomorrow, any help is greatly appreciated. Help!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by hcaleman on 2008-10-27
can you do a network install (pxe boot)?  That's the way I went with my portege that has no cd-drives.

---

### Post by alberto ferreira on 2008-10-27
No, my only alternative is a pen installation :s

---

### Post by hcaleman on 2008-10-27
Your laptop is a bit older than mine, about a year or two.  I tried to go the USB stick install route, the problem was the bios didn't support that and my system has no FDD or CD drive, so that idea was killed for me.  

I needed a floppy drive to run some minimal boot disks that from there may have *possibly* let me mount the pendrive and go from there.  I was reading through some of the links from this thread though for initial ideas: 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4160191](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4160191)

[http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by issih on 2008-10-27
Easy enough to do...

Use this guide if you are preparing the usb stick from a linux pc:

[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

and this one if you are using a windows pc:

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

Same basic procedure in both cases...copy stuff to usb stick, make stick bootable, install syslinux and change a few files.

I know its doable, as I installed my last pc using the same method.

Hope that helps

---

### Post by alberto ferreira on 2008-10-27
I see, I must boot GRUB from a floppy and then select my pen to boot from it.

Now, how do I put Ubuntu 8.04 "installer" in the pen? Can I convert Ubuntu 8.04 cd's .iso or must I download a .img file? Also, since my pc ran ubuntu 7.10 installed with the regular Live CD, I don't need to download a i686 specific .img right?

I'd like to follow a solution that expends the less bandwith possible or else I'll have to pay more money to my ISP

Thanks


EDIT: in the first link that issih gave to me they talk about downloading vmzlinux but they only discuss AMD64 version or i386. Should I download i386 being my architecture i686?

---

### Post by issih on 2008-10-27
This guide tells you various ways to get the installation media onto the usb stick, some easier than others.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

All of them will be about the same download size as the big download is going to be the ubuntu iso (700 odd meg)

This guide tells you what to do if your computer can't natively boot from usb.

[https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD](https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD)

its a bit complicated, but is doable, I've had it working on my macbook (mac's are very bad at usb booting)

---

### Post by alberto ferreira on 2008-10-27
Ok, I've created a bootable pen with this:
[http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/)

Now how do I boot it using GRUB through a pen? My pc does't support booting from USB directly so I need to boot from a GRUB floppy.

I have already made that bootable floppy with GRUB but I don't know how to configure GRUB parameters (kernel, root, etc.).

My laptop has :
1 hard-drive, 1 cd-rom drive, 1 floppy drive, 2 USB ports

Doubts:
1-How do I configure GRUB?
2-Can I create another folder in that pen to take some word documents to school tomorrow? - I have more than 1 GB free.

I've been trying for the last 2 hours to configure GRUB and I went to command-line mode, there when I type root the only options I have are fd0(floppy) and hd0(hard-drive), so it's not detecting the pen!!!??? Wasn't it supposed to work?

---

### Post by alberto ferreira on 2008-10-28
Ok, the pen didn't work so I tried installing from the disc once again and after the 5th try it worked!

---

