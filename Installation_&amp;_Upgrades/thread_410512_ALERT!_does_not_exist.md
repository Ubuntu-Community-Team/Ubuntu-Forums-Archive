---
title: "ALERT! does not exist"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by 1ino1eum on 2007-04-15
hi, 
ok I have managed to install feisty on my fakeraid now. everything should work, exectp that not work heh :)

ok the problem is odd :
at the boot, I have "waiting for root filesystem"
then I wait for few minutes. and finely I m on busybox
Now what is strange is that I have this line :
Check root= bootarg cat/proc/cmdline
or missing modules, device : cat /proc/modules ls /dev
ALERT! does not exist. Prompping to shell

ok the odd thing is "ALERT! does not exist"
because usualy, on the "waiting for root filesystem" problem, there is something like
ALERT! /dev/sda does not exist... or whatever
but here, there is NOTHING 
if I do ls /dev/mapper, I have my device raid recognize. 
So , the only problem is that it seams there is no root device that is asked to be mount to continue to boot.
I have no idea to fix that...

---

### Post by a1437053 on 2007-04-23
Same problem!

I tried installing Feisty from liveCD . . . all seemed well . . . until reboot.

REBOOT fails at the same point described.

AND LIVE CD DOES NOT START! I'm left with a blank screen!

José

---

### Post by 1ino1eum on 2007-04-23
I gave up in installed my feisty on a normal sata drive (not raid)

---

### Post by sengoku on 2007-05-14
i'm having this exact problem with a NON raid SATA drive. my system has a SATA hard drive and a non-SATA cd rom drive, and i get

ALERT! does not exist

no mention of the drive name, or uuid or anything. i have changed both /boot/grub/menu.lst and /etc/fstab to use /dev/sda1 (which is my hd) even though the UUID=xxxx they had was the correct UUID number, and that doesn't give any change at all (it doesn't even say ALERT! /dev/sda1 does not exist, still ALERT! does not exist)

any ideas? should i submit a bug report? and if so, which files would be useful to attach?

thanks in advance

---

### Post by tormod on 2007-05-19
[https://bugs.launchpad.net/bugs/106887](https://bugs.launchpad.net/bugs/106887)

---

