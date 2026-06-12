---
title: "ubuntu installer has completely hosed my system - help!"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by llcoolbeans on 2007-09-20
Running Windows Vista with RAID 0 system drive.

Installed another extra hard drive intended to be the ubuntu system drive.

Started ubuntu CD, ran installer, had installer install to the new drive.  I specifically didn't want it to mess with my Vista drives.

Restart system, get error message GRUB loading, please wait...
Error 21

Can't even boot back to the ubuntu CD!!!  Totally hosed!

I'm guessing it's having trouble finding the extra drive.

How do I undo this?

I don't understand, why does ubuntu try to take over?  My motherboard knows what drive to boot to.  This Rots!!!  GRUB runs into an error and that's just it.  Game over, no option to boot to another device?

---

### Post by llcoolbeans on 2007-09-20
Got it to boot to the CD again somehow.  What do I need to do to restore original functionality?

Thanks

---

### Post by Herman on 2007-09-20
I don't have Vista myself, and I don't know much about RAID 0 either, but does you Vista installation CD still have the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") like Windows XP has? 
You probably just need to re-install the bootloader's MBR code to make the MBR point to your bootloader in your Vista partition in your Vista hard disk again. With Windows XP, you would run the command FIXMBR to do that, and there are many other ways as well. Try that or whatever the Vista equivalent  of FIXMBR is.

---

### Post by llcoolbeans on 2007-09-20
Oops, my mistake, RAID 1 (mirroring)

I always get those two confused.

---

### Post by llcoolbeans on 2007-09-20
I don't have the Vista CD here with me.  I won't have access to it until tomorrow.

---

### Post by Pumalite on 2007-09-20
* [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
    * [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
    * [http://technet.microsoft.com/en-us/w.../aa905126.aspx](http://technet.microsoft.com/en-us/w.../aa905126.aspx)

---

### Post by llcoolbeans on 2007-09-20
What a relief.

Got it.  Installed yet another spare HD on a regular ATA channel this time.  Intalled ubuntu to it.  GRUB now seems to be working fine.  Can boot to Vista no problem.  Thank the lord!

I was really sweating bullets for a few minutes there.

---

### Post by Herman on 2007-09-20
Oh, good! :)
Well done!

---

