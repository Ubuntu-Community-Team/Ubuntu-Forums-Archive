---
title: "Ubuntu wants to download everything in /boot?"
date: 2016-05-30
forum: Installation &amp; Upgrades
---

### Post by herman-christiani on 2016-05-30
Hi, Installed 16.04 on my main computer already running 16.04 on laptop with no problems.
The install went fine on the main computer after I had to redo because grub would not install the bootloader.
So I made a new /boot partition of 150mb.
Thereafter computer starts fine and runs with no problems, but I can't install software because ubuntu wants to download everything in /boot
which does of course because of the small partition size does not work.
Any pointers how to force to download in / ?
Thanks in advance, Herman

---

### Post by oldfred on 2016-05-30
Are you sure it was a /boot? And now 150MB is not large for a /boot.
And best not to have a separate /boot as it fills up with kernels too quick.
The only software that should be installed in /boot are the boot files, kernels & grub.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by herman-christiani on 2016-05-31
Hi, yes it was /boot, the ssd drive was used before for windows 7, 8 and 10. tried again to install without /boot, 
same again grub would not install and ubuntu install stopped, looks like windows left a hidden partition.
Swapped the ssd for a new one, running ubuntu now without any problems, used the old ssd for /home
Thanks again for the reply

---

