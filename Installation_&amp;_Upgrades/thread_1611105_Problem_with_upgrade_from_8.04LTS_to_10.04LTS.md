---
title: "Problem with upgrade from 8.04LTS to 10.04LTS"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by mcmlvii on 2010-11-01
I initiated the on-line upgrade from 8.04 LTS to 10.04 LTS. When the upgrade finished and restarted the computer, I got the following messages:
ALERT! /dev/disk/by-uuid/32a1eb0a-c9a4-4867-ac4d-5fbb2acafa76 does not exist. opping to a shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1 ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) 
 
It leaves me at that initramfs prompt. Any suggestions for a remedy will be greatly appreciated.

---

### Post by mörgæs on 2010-11-02
Hi, welcome to the forum.

I would not waste much time on an upgrade which went astray. A reinstall often is a faster and better solution.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by oldfred on 2010-11-02
mörgæs is probably correct. We often spend days fixing things when you can reinstall and be up and running in about an hour. But we still like to try to fix things.:)

I saved this but it is older now.

 SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

---

