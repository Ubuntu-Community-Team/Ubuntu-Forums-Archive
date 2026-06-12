---
title: "grub question"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by joClarke on 2005-12-06
Hi everyone, Ive been using Ubuntu on a seperate hard drive to my primary one with XP on it for a while now, and using the grub to alternate between them. I need to reformat the second one and use it as a slave for now, I may reinstall Ubuntu at a later time. Im changing my motherboard and am trying to get it working with just the primary hard drive for the moment.

Anyway my problem is this: I haven't formatted the second hard drive yet but simply removed it from my computer however when I boot the GRUB produces an Error21 and won't go any further. Obviously, as Ive just got the one OS at the moment, I don't need the grub so was wondering how to remove it completely.

Thanks
Jo

---

### Post by bwog on 2005-12-06
In the rescue mode of the windows CD you can use the option fixmbr.

---

### Post by joClarke on 2005-12-06
Wow, all my problems solved with that simple little command.

Thanks very much!
Jo

---

### Post by tomski on 2005-12-06
error 21 is grub saying 'i cant find the files i need'
 by removing the drive containing ubuntu you have remove the files grub uses, which are contained in :
/boot/grub

when you come to use ubuntu again you may want to create a bootable floppy (if you have a floppy drive) by using the following :
grub-install /dev/fd0
reboot and test it if all works then reboot & go straight to the windows recovery console type 'fixmbr' then when ever you want to use linux/ubuntu just shove the floppy in before reboot/startup

---

