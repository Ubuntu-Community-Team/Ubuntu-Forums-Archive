---
title: "Cannot access Ubuntu - after upgrading Vista to Windows 7"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by subhankarvirgoan on 2010-01-12
Hi.I had partitioned my dell inspiron 1525 to have Windows Vista and Ubuntu 9.04. I upgraded Vista to Windows 7. Now whenever I start the computer it goes directly to Windows 7. Is the Grub been deleted?  How do I get to my Ubuntu. I have the Ubuntu Live CD with me.
I would be grateful if anybody could help me out.
Thanks!!!

---

### Post by darkod on 2010-01-12
Yes, grub was overwritten by windows bootloader. If you are using 9.04 then you had grub1, not grub2 that comes with 9.10.
Using your 9.04 cd, restore grub as per the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Be careful to use the instructions for 9.04 and not 9.10.

---

### Post by raymondh on 2010-01-12
> **subhankarvirgoan said:**
> Hi.I had partitioned my dell inspiron 1525 to have Windows Vista and Ubuntu 9.04. I upgraded Vista to Windows 7. Now whenever I start the computer it goes directly to Windows 7. Is the Grub been deleted?  How do I get to my Ubuntu. I have the Ubuntu Live CD with me.
I would be grateful if anybody could help me out.
Thanks!!!

I hope this is not a wubi-installed ubuntu.

If ubuntu is in it's own partition, just re-install GRUB.  You see, when you upgraded, win7 may have overwritten the MBR with its' own bootloader.

Instructions to re-install GRUB here

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to GRUB for 9.04 or earlier ... 

Raymond

---

