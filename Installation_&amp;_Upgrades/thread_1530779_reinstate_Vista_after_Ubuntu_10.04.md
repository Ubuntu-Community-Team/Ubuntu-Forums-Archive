---
title: "reinstate Vista after Ubuntu 10.04"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by mebomechanicno1 on 2010-07-14
I installed Ubuntu 10.04 on a Sony Vaio following the instructions that came on the cd (obtained from a Linux Magazine bought in the UK) under the misapprehension that i would get a dual boot, (because i specified retaining windows) but instead I got Ubuntu and a Windows recovery partition.  I need to access windows for work related issues, so had to try to recover windows which appeared to go well until I tried to reboot when i got an error message, (to the effect Device not found, Grub not loaded, but since this was about 2.00am last night please excuse me for not writing it down).  I then used my windows recovery discs, (prepared as soon as I got the Vaio for use in an emergency) but the Sony will not now reboot from the cd.  Since by now I had neither windows nor Ubuntu, I then reinstalled Ubuntu (which will install from the cd, although my windows recovery disc will not).  This had the effect of reinstating the windows recovery partition, so i went through the same merrygoround, using the windows recovery partition to "recover" windows, which would not boot because of a grub error; then tried to reinstall Ubuntu which now will not reinstall, but prompts me to manually partition the hard drive which is when i gave up and came to work instead!  When I now try to boot with no Ubuntu cd in the drive i get a message reading along the lines "Grub recovery: error 22", which is the message i get whether there is nothing in the cd drive or the windows recovery disc in the cd drive.

---

### Post by skarme on 2010-07-14
Well I belive you should get rid of GRUB and boot into Windows first!
For this you can fix the boot record using the Vista CD. GRUB will disappear and you would boot into Widows. Check this link for help:
[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)
Once this is done, you can create a partition via Windows and the install Ubuntu.

---

### Post by mebomechanicno1 on 2010-07-14
Thanks, I will try it when I get home, but as I said, it is not booting from anything but an Ubuntu CD.

---

### Post by phillw on 2010-07-14
If your Win disk cannot boot your system, chances are that it is not a boot disk. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) has full details on putting with Win boot loader back on, along with where to get a boot image for Vista or Win7 (If you need XP then PM me and I'll sort a link out for you).

Regards,

Phill.

---

### Post by mebomechanicno1 on 2010-07-14
It is a system recovery disc I made when I got the Vaio, and I have used it one time previously to recover the system from scratch, but I have now downloaded and made up a Windows boot disk, ready to return to the fray tonight, thanks for the help and support.

---

### Post by mebomechanicno1 on 2010-07-14
The tutorial at  [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1014708[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1014708") did the trick.  Do not be tempted to ignore the command line quoted.  That is what does the trick.  Good old DOS!
 
Thanks you two guys, I much appreciate the time you took.  All I need to do now is get the Ubuntu to dual boot (or get up into the attic room and find my first ever Vaio and load that with Ubuntu and nothing else).

---

