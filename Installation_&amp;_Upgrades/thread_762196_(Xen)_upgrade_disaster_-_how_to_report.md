---
title: "(Xen) upgrade disaster - how to report?"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by guenthert on 2008-04-21
After (eventually) successfully upgrading a few machines at home and my laptop at work from Ubuntu 7.10 (and one from 6.04) to 8.04 (beta), I dared to attempt to upgrade the desktop at work too. Unfortunately, I forgot that this particular machine is running Xen and I was running the update-manager within Dom0. 

All seemed to go quite well, until common-lisp-controller 6.12 was being configured. It seemed sbcl was recompiling some tools, which took an eternity (OK, on a Athlon 64 X2, 6+ minutes CPU time are an eternity). I decided that was enough and attempted to kill the process in order to move on and to take care of this later, but without success: I found the process in 'D' state (uninteruptible sleep in kernel - which one shouldn't see, certainly not for any extended period of time). I rebooted the machine (it hung during reboot then, but nothing the big red button couldn't solve).

Then, however the real problems started ;-/
Some tool had modified the fstab (I'm sure, there is a good reason for that, but right now, none comes to my mind) and marked the filesystems to be found by UUID. Alas the initramfs had apparently not been updated yet and didn't had any of this (there was no /dev/disk/by-uuid). So, beside the root FS no file systems could be mounted (consequently sudo didn't work, as it happens to be placed in /usr/bin). Since I grew accustomed to using sudo, I never bothered to set the root password on this box, so I didn't get anywhere until I rebooted, now in single user mode (recovery mode). Fortunately Ubuntu's security is rather lax in this respect and didn't ask for a root password on boot.

After restoring the /etc/fstab (oh, can we please have a vi in the root fs? Nano makes me cringe and ed is just a bit too tough), now using special files in the first field again, I was able to boot regularly and running `dpkg --configure -a` (a few times to resolve apparent dependency issues), I got the system back into a sane state, with now new and improved packages.

Yay to dpkg!

In short: do not attempt to upgrade from Ubuntu 7.10 to 8.04 (rc) on a Athlon 64 box within Dom0! Instead boot first into the native Linux. Not sure, how to report this other than posting my experience here.

hth
    GuentherT

---

### Post by ezek1el on 2008-10-30
***Hola! All done well, ends well! :)***

---

