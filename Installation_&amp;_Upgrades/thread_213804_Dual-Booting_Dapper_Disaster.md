---
title: "Dual-Booting Dapper Disaster"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by AdamP on 2006-07-11
I've been having an impossible time getting Ubuntu to dual-boot with XP and Vista on my paritioned drive.

Here are the steps I've taken:

XP was installed first.
Then Vista.
XP and Vista dual-boot just fine w/Vista's boot loader.

When I install Ubuntu, I'm not so lucky.  First I tried installing via the LiveCD.  When GRUB didn't show up on restart (in fact, nothing did - just got a blinking cursor), I decided to start from scratch, so I deleted the Ubuntu partition and swap partition, fixed my MBR, and started again at square one.

This time I installed Ubuntu via the text installer.  I partitioned my drives the same way (added two primary partitions, one swap of 512MB, one ext3 of 25GB), the installer said specificially this time that it was installing GRUB, but on restart... no GRUB to be found - just want straight to the Vista bootloader.

Next I tried [this method for fixing GRBU]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot"), and finally I actually *saw* GRUB for the first time, but then I got an error message (Error message 22) telling me that the Ubuntu install can't boot!

So, umm... anyone have any idea where I can go from here/what I've been doing wrong?  I'd really love to get Ubuntu up and running, as I'm all set to proselytize its glory to the world, but - well, so far the experience hasn't been all that glorious. :(

Help me! :)

(Oh, and thanks...)

---

### Post by AdamP on 2006-07-11
Btw - I just checked again, and GRUB Error Message 22 is "No such partition."

The thing is, using the method I linked to above, shouldn't it be a sure thing that the partition exists???

---

### Post by Herman on 2006-07-12
So Grub isn't automatically booting Ubuntu from the new Grub Menu? Would you be interested in trying out Grub's Command Line Interface and see if you can boot with Grub that way?
You should be able to find your partition and boot anything on it that is bootable with Grub's Command Line. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to see how.
As you boot up with Grub's Command Line, take note of what commands you use that are successful, because once Ubuntu boots up you can edit your /boot/grub/menu.lst with the very same commands, likely it's a mistake in your menu.lst that's causing your problem.
I hope that works for you, good luck,  Regards, Herman :D

---

