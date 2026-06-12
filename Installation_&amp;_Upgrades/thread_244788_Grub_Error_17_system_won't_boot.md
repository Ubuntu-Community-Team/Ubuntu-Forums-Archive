---
title: "Grub Error 17: system won't boot"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by Drenhead on 2006-08-26
I booted to the live CD to try to change one of my partitions using gparted, but my system froze in the middle.  Now, when I forced a reboot, I am getting a grub error.  This is a dual boot XP/Kubuntu machine.

All it tells me is Grub Error:  Error 17.

I am writing this from the Live CD.  What can I do to restore my system?

Thanks in advance.

---

### Post by confused57 on 2006-08-26
I suppose you could try reinstalling grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You'd probably have better luck using the gparted live cd(approx 30 Mb) to partition:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Donnut on 2006-08-27
I just had this error, without reinstalling ubuntu, you can edit the grub file, by changing hitting "e" at the promt, and setting it up manually.  In the live CD, try mounting the linux drive, im betting it is a different /dev than grub tries to boot off of...

[Edit:] P.S. you could also try reinstalling grub with live CD, I tried it and it yeilded the same results...

---

### Post by Drenhead on 2006-08-28
Thanks for the info, but I think i had bigger problems than that.  I booted with the live CD, and the partitions on my drive were all screwed up.  I ended up just reinstalling Kubuntu using the alternate CD and partitioned the drives the way I wanted.  I have everything back working again (except Flash, but that is another story!!).

I appreciate all the help.

---

### Post by mrcbldn on 2007-12-14
I installed XP over my native Vista, obviously the grup installation was covered from Windows bootloader.

Following this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")

I was able to reinstall grup into linux partition (hd0,2); when I rebooted my computer I saw rightly grub menu, if I choosed Windows boot everything was ok but if I choosed Linux Partition appeared:

"Error 17: Cannot mount selected partition"

I choosed 'e' on linux entry into grup menu; the first voice appeared as root (hd0,3) but I saw that the ext2fs partition was into 2!!!
So I changed it into root(hd0,2) with 'e' option.

After the changed it i pressed 'b' (boot); then my linux starded!!!

The changes was not persistant, so after boot, I needed to permanent change the grup configuration.
I went into /boot/grub/menu.lst and I changed the entries for linux into root (hd0,2) (they where to (hd0,3) )

Now everything works well but I still does not understand how my new xp install dropped an existent partition!!
Unlikely I have not the output of previous fdisk command :-(

---

