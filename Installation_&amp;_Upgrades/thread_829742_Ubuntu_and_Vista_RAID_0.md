---
title: "Ubuntu and Vista RAID 0"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by Tkolini on 2008-06-15
Ive spent the last few dayas trawling through the internet trying to find a solution to my problem to no avail. I have 2 250gb drives which holds vista in one partition and general storage in another. I also have a 500gb drive which i want to install Ubuntu 8.04 to.

During the ubuntu installation i have tried setting the bootloader installation to various paritions but it never seems to work, it either breaks the bootloader or does nothing at all. I tried using EasyBCD from within vista to try and manipulate the bootloader to recognise linux but i get grub errors when i select ubuntu in the boot menu after the fiddling.

I have also tried disconnecting the RAID 0 array and then installing ubuntu on its own on the 500gb, with the MBR on that drive. This works happily until i plug the RAID array back in again which causes it to go back to square one. Ive seen suggestions about changing the boot order of the drives but for some reason i am unable to do this in my motherboards bios (Abit AB9 Pro).

However i have managed to flukily get the vista bootloader to go to the grub bootloader when i select ubuntu, but when i get into that and select ubuntu again i get a grub error 26. I played around with the grub menu.lst via the livecd to change the drives to which it booted. Originally it was set to hd2 but i changed it to hd3 or sd3 (all the drives are SATA). But this too did not work.

All in all im a tad annoyed, and any help would be greatly appreciated:)

---

### Post by Pumalite on 2008-06-15
This might help:
[http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)
See if you can incorporate Ubuntu to this boot.ini

---

### Post by Tkolini on 2008-06-15
Thanks for the prompt reply. Unfortunately that doesnt seem to help me that much, ive already tried to install ubuntus mbr on its own drive and then mess with vista bootloader...

---

### Post by Pumalite on 2008-06-15
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

---

### Post by Pumalite on 2008-06-15
[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

---

