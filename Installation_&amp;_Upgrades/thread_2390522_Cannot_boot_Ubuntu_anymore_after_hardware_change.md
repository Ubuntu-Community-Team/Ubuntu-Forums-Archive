---
title: "Cannot boot Ubuntu anymore after hardware change"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by Anaxagore on 2018-04-29
Hi, After having some forced hardware change (but keeping the disk on which Ubuntu was installed) I have not been able to boot it anymore. When 18.04 came out (I had 16.04.x that worked fine until the hardware change) I took this opportunity to try and install it while keeping the data on my Linux partition.

First attempt at rebooting after installation, and after the Grub menu I get the message that the UUID of my Ubuntu disk does not exist. I booted the live version on USB (same as I used for install) and tried Boot Repair (without luck); I also tried replacing the UUID (which blkid confirmed was the right one) with the /dev/(corresponding device name) in fstab of that drive after mounting it in the Live version. Did not work. I followed the procedure in [https://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](https://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell). Did not work either. I tried adding the boot option (using e on Grub menu and going to the line beginning with linux) "noresume" but it did not work either.

I tried re-installing (again) and got an "error removing initramfs-tools" (sounds like a related problem...) with "installed initramfs-tools package post-installation script subprocess returned error exit status 1".

Any kind of advice to fix the problem?.. Thanks to everybody who can help :)

---

### Post by oldfred on 2018-04-29
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oldos2er on 2018-04-29
Please tell us exactly which hardware changed from what to what--make and model, if possible. I'm guessing it's a hard disk? Difficult to tell from your post.

---

### Post by Anaxagore on 2018-04-29
Dell replaced a Precision 7710 laptop with a 7720 - main changes are graphics (Nvidia M5000M to P5000), CPU (E3-1505M to E3-1545M), wifi (Intel 8260 to 8265), chipset (CM236 to CM238). I moved the SSDs from the old machine to the new one (except for one of them - luckily the empty one on both machines - where they had tightened the screw too much...).

---

