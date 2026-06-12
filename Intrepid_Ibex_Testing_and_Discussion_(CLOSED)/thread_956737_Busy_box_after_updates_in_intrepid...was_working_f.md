---
title: "Busy box after updates in intrepid...was working fine from hardy upgrade"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rodrickjaynes on 2008-10-23
somewhat newb here...

i upgraded to intrepid last week from hardy.  every thing was going smooth...but then i just updated i now get a busybox when i try to boot

this is preceded by a warning that it wasn't loading vesafb like this

/scripts/init-top/brltty: 19: grep: not found
WARNING: Not loading blacklisted module vesafb

it sits there for quite a while then says

Gave up waiting for root device.  Common problems:
    - Boot args (cat /proc/cmdline)
        - Check rootdelay= (did the system wait long enough?)
        - Check root= (did the system wait for the right device?)
    - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist. Dropping to a sheel!
(initramfs)

things i've tried. 1. dpkging the kernel 2.6.27-7-generic by booting with another kernel (which freezes at the graphical login and i have to alt+F1 to do anything).  2. adjusting the root location right before the boot in the grub menu and in the fstab list and in the /boot/grub/menu.lst

after i repackaged the kernel it switched from trying to find the thing by UUID to the normal /dev/sdx format but still returned the error.  also when i adjusted the UUID or the /dev/sdx which i asked the computer for, it read back the correct info and still told me it didn't exist---liars.

searched and searched haven't really come up with anything.  growing impatient but resisting a reinstall.

:popcorn:

---

### Post by GordonTGopher on 2008-10-25
Having just upgraded from Hardy to Intrepid RC I have the same error but the alert is for /dev/disk/by-uuid/69f3e(long UUID string!)

I'm even more of a newb and have not tried to do anything yet, but am wiling to be guided if I can help track the bug before I re-install

Results of a little bit of investigation;
If I choose Kernel 2.6.24.21 from the GRUB menu everything boots OK, if I choose 2.6.27.7 I have problems.

Should I file a bug with this small amount of info or can someone point me in the direction of what information I should try and capture?

Gordon

---

### Post by homerhomer on 2008-10-25
I'm in the same boat!

Yikes, this needs to be fixed

---

### Post by neverone99 on 2008-10-26
I'm having the same issue with Busybox after an upgrade from 8.04 server to 8.10 server.  After booting in to the 2.6.27 kernel I get dropped to a Busybox prompt and the error message is that it can't mount the UUID that is listed.  I verified that the UUID in the 2.6.27 boot item in GRUB was the same as the boot item for 2.6.24 kernel version which boots fine.

Here is a bug that I believe fits the description:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262588](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262588)

---

### Post by GordonTGopher on 2008-10-29
I've followed the advice in this bug report [https://bugs.launchpad.net/ubuntu/intrepid/+source/busybox/+bug/290153](https://bugs.launchpad.net/ubuntu/intrepid/+source/busybox/+bug/290153) Adding the root delay solved the problem for me, hope it helps others reading this thread.


Gordon

---

