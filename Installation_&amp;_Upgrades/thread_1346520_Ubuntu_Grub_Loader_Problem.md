---
title: "Ubuntu Grub Loader Problem"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by blastbeast on 2009-12-05
Hello folks,

I installed Ubuntu 8.04 on my desktop a few months ago. After that i installed Windows 7 by resizing the partitions and installing 7 on the new one, and after that Windows XP SP3 (which i think is the problem and there arent any google hits that could direct me to a tutorial of some kind to dual boot XP and Ubuntu after i've installed 2 Windows OS's one after the other).
Now when i boot to Ubuntu using the Live CD, to  reinstate GRUB as the system bootloader, I find the menu.lst file to be empty.
Can someone provide any thoughts as to why this is happening or better a way to dual boot Ubuntu and XP?

Any help would be much appreciated.
Thanks!! :)

---

### Post by darkod on 2009-12-05
Did you install XP over 7 or also next to it? Do you have 2 or 3 OS?

PS. This is how you restore grub1 after windows install:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by phillw on 2009-12-05
> **blastbeast said:**
> Hello folks,

I installed Ubuntu 8.04 on my desktop a few months ago. After that i installed Windows 7 by resizing the partitions and installing 7 on the new one, and after that Windows XP SP3 (which i think is the problem and there arent any google hits that could direct me to a tutorial of some kind to dual boot XP and Ubuntu after i've installed 2 Windows OS's one after the other).
Now when i boot to Ubuntu using the Live CD, to  reinstate GRUB as the system bootloader, I find the menu.lst file to be empty.
Can someone provide any thoughts as to why this is happening or better a way to dual boot Ubuntu and XP?

Any help would be much appreciated.
Thanks!! :)

Hi,

Which version of Ubuntu do you have on your LiveCD ?

Phill.

---

### Post by llawwehttam on 2009-12-05
Well this is the boot-loader I use and Ive never had a problem with it . [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Does this help?

If not its time for ..... superGRUB

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by phillw on 2009-12-05
> **llawwehttam said:**
> Well this is the boot-loader I use and Ive never had a problem with it . [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Does this help?

If not its time for ..... superGRUB

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Hi, there are several howto's within the ubuntu forum. The reason i ask is that grub has been replaced with grub2 & it helps the OP if we ascertain which version of grub they're on. 8.04 should be grub-legacy, but if the live cd is 9.10 then it will be running grub2.

Either way, the method is here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
But, the instructions are different for the two versions of Grub

Phill.

---

### Post by blastbeast on 2009-12-05
> **phillw said:**
> Hi,

Which version of Ubuntu do you have on your LiveCD ?

Phill.


I have Ubuntu 8.04 on the Live CD. I installed the OS from the Live Cd itself.

---

### Post by blastbeast on 2009-12-05
> **darkod said:**
> Did you install XP over 7 or also next to it? Do you have 2 or 3 OS?

PS. This is how you restore grub1 after windows install:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


I installed XP over 7. Counting Ubuntu there must be 2 OS's on my system. (XP and Ubuntu).

---

### Post by phillw on 2009-12-05
> **blastbeast said:**
> I installed XP over 7. Counting Ubuntu there must be 2 OS's on my system. (XP and Ubuntu).

Head to [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)   and use the instructions to restore Grub-legacy  (That's the version of Grub that 8.04 uses) - It'll get you up and running in no time.

Regards,

Phill.

---

### Post by blastbeast on 2009-12-05
> **phillw said:**
> Head to [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)   and use the instructions to restore Grub-legacy  (That's the version of Grub that 8.04 uses) - It'll get you up and running in no time.

Regards,

Phill.


Thanks Phil. I'll try the link.:)

---

