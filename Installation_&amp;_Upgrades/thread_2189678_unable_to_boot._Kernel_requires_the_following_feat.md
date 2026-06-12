---
title: "unable to boot. Kernel requires the following features not present: pae"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by claytonbagwell on 2013-11-23
I attempted to install live cd ubuntu 11.10 64 BIT by mistake. My system is 32 bit. Now when I try to boot A 32 BIT LIVE CD OF 12.04.1, I get the following message:
"the kernel requires the following features not present on the CPU: pae     Unable to boot - please use a kernel appropriate for your CPU.

Does the 32 bit live cd think I have a 64 bit system? What happened? Is there a cache I can clear?

---

### Post by Bashing-om on 2013-11-23
claytonbagwell; Hi !

Hard to tell, what are your hardware specs ?

Maybe these links will shed some light on the subject:

Old hardware/installs: See if these are relevant:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Means and woes:
[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

and some options:
[https://bugs.launchpad.net/ubuntu/+s...x/+bug/1072311](https://bugs.launchpad.net/ubuntu/+s...x/+bug/1072311)

So we need to find something that will boot.. say Lubuntu ?

just try'n to help

---

### Post by ptrakk on 2013-11-23
the CD's bootloader may be trying to boot to the harddrive..
during the boot menu use the 'e' edit or 'c' command prompt to make sure it is being linked to the cd instead of the harddrive

---

