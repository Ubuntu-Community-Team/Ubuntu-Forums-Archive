---
title: "[SOLVED] Intrepid Ibex - Grub Error."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2008-11-01
I did a new installation ( as the upgrade from Hardy didn't go well, anyways ) and the installation was smooth - no problem, except that there wasn't a smooth reboot, the PC just went silent - had to 'reset' to get back.

Please find attached my disk layout. 

[LIST]
[*]Linux's home is **/dev/sdb11**
[*]**750GB HDD ( /dev/sda ) is a SATA drive, that I fixed later( under Hardy )**
[*][B]/dev/sdb is the home for Windoze & Linux
[/B]
[/LIST]

When I reboot, got Grub Error 17. I booted from the installation CD and went on to recover grub...

ubuntu@ubuntu:~$ sudo grub
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd1,10)
grub> root (hd1,10)
root (hd1,10)
grub> setup (hd1,10)
setup (hd1,10)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,10)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,10)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,10) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> 

What's this error ?! I still get Error 17, please advice as how I can get back on.

---

### Post by shankariyer on 2008-11-01
I fixed this problem, but have a new one.

On my fix, I should have given setup(hd1) NOT setup(hd1,10).

That said, I can't login to my windows partition now.

It reports
> Error 12: Invalid device requested.

My grub entry ( now that I'm in Ibex, for windoze is
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Should I recover grub again ?! Please advice.

---

### Post by meierfra. on 2008-11-01
Try:

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1

---

### Post by shankariyer on 2008-11-02
Yup, that did the trick. Wonder what those 'map' thingy was...

---

### Post by meierfra. on 2008-11-02
> Wonder what those 'map' thingy was... 
> root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 


This is the correct entry for XP if XP is not on the boot drive.
XP assumes  that the boot  files (ntldr, ntdetect and boot.ini) are on the boot drive.  The map line virtually swap the two drives (hd0) and (hd1), making sure that XP can find the boot files.


But in your case,  XP actually is on the boot drive. So  the map lines are unnecessary.

---

