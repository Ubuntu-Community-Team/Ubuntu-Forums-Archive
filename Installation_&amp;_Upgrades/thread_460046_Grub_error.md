---
title: "Grub error"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by nicholaskhs on 2007-05-31
I have a D.I.Y computer running Windows XP Professional SP2, Pentium 4 2.80GHz.
I've recently installed Ubuntu 7.04 using the alternate desktop CD, but when I restart, it hangs after this error message,

"Grub Loading stage 1.5.

Grub loading, please wait...
Error 18"

I've tried using the Live CD to reinstall it, but it still hangs. I then used GParted (from the Live CD) to edit partitions (I did not edit the Windows partition), and after restarting, I cannot boot from disc anymore.

I've tried using the Windows XP Pro disc to boot into the recovery console, but I can't even boot from disc! I've already set first boot device to CD-ROM, but still does not work. It does show Boot from CD :, but then it scrolls down and shows that error message. Will I need to wipe out my hard drive? I have valuable data on that drive, and cannot imagine losing it. I suspect it is the corrupted MBR, but as I've mentioned earlier, I cannot boot from disc. MS-DOS floppy disks also fail to boot, that error message appears again.

I want to remove Ubuntu and Grub, and restore my original Windows XP MBR.

EDIT: I set the first, second and third boot devices to CD-ROM, and managed to boot into CD, but when I press <ENTER> on the main interface and then <F8> to agree to the terms and conditions, but then it says <Setup cannot access this disc> where it is supposed to show the partition information. I read this article:
[http://wiki.linuxquestions.org/wiki/GRUB#Error_18]("http://wiki.linuxquestions.org/wiki/GRUB#Error_18")
but it does not have any instructions on how to fix it.

EDIT2: I suspect that me playing with GParted caused this error, but I have no idea on how to fix it.

---

### Post by hellmet on 2007-06-01
It seems like there is some problem with your Cd-Drive also?
In the EDIT 1 case, you've set all boot devices to CDRom, and thats the reason its
not showing your the HDD partitions. Your HDD wasn't booted at all!! ..
If you've a spare CD/DVD drive, try that out.

---

### Post by nicholaskhs on 2007-06-10
Thanks for your help, but I solved it myself. I got myself the GParted Live CD, deleted the Ubuntu partitions, reformatted Windows and everything was back to normal.

---

