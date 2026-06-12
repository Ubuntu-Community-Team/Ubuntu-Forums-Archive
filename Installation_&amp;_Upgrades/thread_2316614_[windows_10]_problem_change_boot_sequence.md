---
title: "[windows 10] problem change boot sequence"
date: 2016-03-09
forum: Installation &amp; Upgrades
---

### Post by guido96 on 2016-03-09
hi! I would install lubuntu on my news asus (windows 10 default). i make a partition but when i go to the boot menu (f2) there is only an option: windows boot manager. Someone know how to change the sequence for run my cd with lubuntu?

---

### Post by oldfred on 2016-03-09
It looks like you may have UEFI Secure boot on. For security reasons many UEFI implementations prevent booting from anything else. (also can make it difficult to boot a repair disk.).

Or you may have settings to allow USB boot with Secure boot on. 

Flash drive needs to be a bootable flash drive, for system to see it to allow you to boot. It will show two entries if Secure Boot is off. One is clearly UEFI:name and other is name or BIOS boot where name is name or label of flash drive.

Some other Asus, even though different models, may have similar issues. If newer Ubuntu which is probably required if new system, then may work better.
 Asus M32CD desktop - Skylake several boot parameters required
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

---

