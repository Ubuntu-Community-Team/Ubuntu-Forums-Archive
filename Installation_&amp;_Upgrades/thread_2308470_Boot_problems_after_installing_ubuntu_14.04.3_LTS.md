---
title: "Boot problems after installing ubuntu 14.04.3 LTS"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by geert4 on 2016-01-03
Hi there,

After some days of trying all proposals I could find in the support, I still did not get it to boot from my hard disk. Here are the results of boot-repair: [http://paste.ubuntu.com/14389520/](http://paste.ubuntu.com/14389520/)

At present the disk is not even shown at startup as a device at all. At some former installations it was visible there, but then got the error No bootable device...

Hope someone out there can help me.

Best, Geert

---

### Post by oldfred on 2016-01-03
Is this an older system with newer large drive?
Some very old BIOS would not boot from partitions over 137GB, and some slightly newer BIOS then had same issue if set to IDE compatibility. Make sure you have drives set to AHCI in BIOS if you have that setting.
Often better just to have a 25GB / (root) and then the rest of the drive as /home and/or data partitions.
If a newer user easier to install with /home. But if thinking of multiple installs of Ubuntu or other Linux then a data partition that can be shared may also be better.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

