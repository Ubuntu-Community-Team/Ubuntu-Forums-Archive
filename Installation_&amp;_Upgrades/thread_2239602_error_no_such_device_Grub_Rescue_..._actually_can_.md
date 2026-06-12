---
title: "error: no such device: Grub Rescue ... actually can someone else rescue?"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by dave141 on 2014-08-14
Hi all, firstly I am not a guru, I am a layman.  Had someone install a dual boot onto two separate hdd's one was windows7 the other was ubuntu or kubuntu I do not recall. 
Was using the machine as an ftp server (linux) and windows machine at times however mostly just as the ftp server. One of the two hdd's died. Like does not engage the heads, spins up and does the click click click ... removed from tower. other drive has win 7 installed however will not boot to windows only to the Grub rescue screen.

So, I downloaded a rescue .iso and copied to dvd and boot from cd.. no luck. same error screen?

next I said the heck with it, installed different empty drive, have an official xp pro x64 edition cd, figured install xp on drive and then use windows xp to fix MBR.. nope that one went to blue screen of death. 

The hard disc that "had" ubuntu on it is no longer.  The remaining disc has win7 however cannot load into windows. 

How can I fix the MBR on either win 7 or ... how can I get xp to install ??? it seems like the bios is messed up trying to bootload a version of ubuntu that the hard drive is no longer in the machine and I cannot select windows as the bios only lists the hitachi hd, cdrom, usb, network as boot devices. 

Help... and I will "like" you. 


Thanks!

---

### Post by yancek on 2014-08-14
If the drive on which you had Ubuntu/Kubuntu died, it seems that you had its Grub bootloader installed to the master boot record of the windows drive pointing to the Ubuntu/Kubuntu system where almost all of the Grub files were located.  That would explain what you are experiencing.

> So, I downloaded a rescue .iso and copied to dvd and boot from cd.. no luck. same error screen?


If you want a bootable iso, you need to 'burn as an image' not copy to a cd.  Is that what you did?

> next I said the heck with it, installed different empty drive, have an  official xp pro x64 edition cd, figured install xp on drive and then use  windows xp to fix MBR.. nope that one went to blue screen of death. 

You mean you were't able to install xp?  Windows xp is not going to fix the bootloader for windows 7 as they use different bootloaders and the commands to repair are also different.

> The remaining disc has win7 however cannot load into windows.

The standard method is to use the windows 7 installation medium.  You may be able to use a recovery disk or find some other software for the purpose online.  If you try the latter option, be careful of the site you download from.   If your BIOS doesn't recognize the drive on which you have windows 7, that's another problem.

---

