---
title: "Ugrade to Win 7 destroyed grub loader"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by kbgluxford on 2014-02-05
I installed Ubuntu 13.10. The other OS was win xp. Everything worked OK.  Then upgraded win xp to win 7 and have lost grub boot loader.  Can I restore grub boot loader without re-installing the whole of 13.10?
Thanks
Kevington

---

### Post by Bucky Ball on 2014-02-06
Welcome. Boot from the Ubuntu install media>'Try Ubuntu>When at the desktop, open a terminal and:

sudo grub-install /dev/sda

... if that is where you want to put it. Usually the place. Once done, restart and you should have a grub with both entries on.

You are positive 13.10 is still on the disk? Might be silly question, but better to ask ...

---

### Post by kbgluxford on 2014-02-06
Thanks for helpful reply.  13.10 installation disk reports a 13.10 installation present in the partitions where originally placed, so am pretty sure win 7 installation did not zot 13.10.

Will try your suggestion and let you know the outcome.

Thanks again,

Kevington

---

### Post by kbgluxford on 2014-02-06
Well that did not work.  got:
 ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
ubuntu@ubuntu:~$ 

It appears that the installation CDROM has no knowledge of the hard drives and their partitions attached to the system.  That information appears to be deduced at system partitioning time during the installation process.

However, many thanks for the suggestion and prompt response.

Cheers

Kevington

---

### Post by Bucky Ball on 2014-02-06
Well, you could try Boot Repair if its going to be stubborn with us:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can boot to a live desktop and install it if you can get online. Should do the trick. If you wanted to get out the toolkit, this is the correct way to do it from a live desktop:

[http://www.noobslab.com/2012/10/installrecover-grub-from-linux-live-cd.html](http://www.noobslab.com/2012/10/installrecover-grub-from-linux-live-cd.html)

Sorry, my mistake. That command I gave you doesn't work from a live boot, only from a real install (for reinstalling grub or installing it on another partition). #-o ;)

---

