---
title: "No such device [UUID device number]. Grub rescue&gt;"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by Selman555 on 2011-09-19
Hey, I'm a newbie here, but not to the scene ;)

I have seen many threads about this error (title), but have never been able to come to a conclusion.
Every time I try to install ubuntu 11.04 (with updates) I get this error after restarting.
Altough, ubuntu was succcesfully installed and working before (same version/no further updates). and after a while I still get this error when rebooting.

I have a dualboot set up between ubuntu (64bit) and windows 7 (64bit) (windows installed first). I installed ubuntu to a usb-harddrive (500gb)
I manually set up the partitions on the usb:
/ 1gb
swap 4gb
/boot 10gb
/home 35gb
I've tried installing grub to my harddisk (where windows is installed) and to my usb-harddisk. I have a liveCD of 11.04 and a windows 7 DVD available to troubleshoot, but i'm out of ideas :o

Is there a solution to this problem? I'm sorry to say, but for now I've been very disappointed about ubuntu (or grub).

---

### Post by oldfred on 2011-09-19
Welcome to the forums.

I hope you posted your / & /boot backwords. / has to be just over 4GB to install and I often suggest 10 to 20-GB for root. I do not recommend /boot except very old systems or servers with RAID or LMV or the few desktops that use those setups.

With manual install just be sure to install the grub2 boot loader to the MBR of the external drive.

More info:
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

