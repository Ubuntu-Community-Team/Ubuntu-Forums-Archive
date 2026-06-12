---
title: "mdadm not installing to /boot on new 13.04 install"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by jeff-harmonydrive on 2013-09-15
I'm trying to install 13.04 on a system with several raid arrays.  I'm ignoring the raid array for /home and will add that in later, but the root partition is a raid-1 array.  Therefore, I need to have mdadm available at boot time so the raid array can be mounted.  However, I'm getting the error

```
ALERT!  /md1 does not exist. Dropping to a shell!
```

Unfortunately, when I go to run mdadm at the initramfs command line, I get the error:

```
/bin/sh: mdadm: not found
```

Which, of course, tells me that the installer didn't include the minimum mdadm files in the /boot partition.

My question is, In 12.04 there was an Alternate Install CD which was intended to be used in cases, for example, where a RAID file system was desired.  In 13.04 there does not appear to be one, and there was not one in 12.10 either.  My old system was 12.04, but was damaged, so I figured I'd bump up to 13.04 on my reinstall.  I installed by going to the 'try Ubuntu' screen, installing mdadm with apt-get, assembling the arrays, and starting them up.

My / root partition is raid-1.
My /boot partition is ext3.  (In the past I've used raid-1 for this, too, but because I was having problems with 13.04 I pulled it off of raid, which is what allowed me to even get to initramfs at all.)
I'm not using EFI.

Do I have to install 12.04 and migrate up to 13.04?  Or is there something I can do in the 13.04 installer process to get it to include mdadm in /boot?

---

### Post by jeff-harmonydrive on 2013-09-15
Solved my own problem by installing mdadm, doing mdadm -As, installing Ubuntu 13.04, and then before allowing it to reboot, apt-get and execute [boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair").

---

