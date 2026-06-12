---
title: "Installation problems"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by the_crabe on 2005-10-13
Hello, I have a problem when trying to install this distribution ...
I have 3 HDD's, one of which is on a separate RAID card (I don't use RAID, the drive is alone on the card). I would like to install Ubuntu on this drive.
During the install from CD, the drive is recognized as hda and no problem
When rebooting, it seems the drive is hda no more, and computer refuses to boot (seems to be hde) ...
Is this problem coming from the fact that the drive is on a RAID card ? How to avoid such problems ?
If someone could help me with this one ...

Thanks in advance !

---

### Post by the_crabe on 2005-10-14
Well, still don't know why it happened, but now at least I got it to work thanks to this thread : [http://www.ubuntuforums.org/showthread.php?t=75829](http://www.ubuntuforums.org/showthread.php?t=75829)
I just modified grub at boot time to give it the right hard disk and then modified my fstab accordingly ...

now I have everything working !
I hope someone will find the cause of this for the next release, as it is quite annoying :-s

---

