---
title: "Dell XPS 15 not seeing thumbdrive, can't install kubuntu.  Rufus the problem?"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by MechaMechanism on 2017-05-04
When creating a Kubuntu thumb drive in Windows 10 using Rufus and a 256GB drive I can not get the XPS to show the drive as a boot option.  I also used an 4GB drive and that drive would not show up in the boot menu.  Also Rufus did not work also with an 16GB and 256GB SD card.

Dell XPS 15 9560, bought at the end of April 2017
Latest Windows 10
I did not install the latest bios update as I only install those kinds of updates if I have a problem as bios updates are inherently risky
Thumb drives work just fine otherwise
Kubuntu 17.04

So what am I doing wrong.  The thumb drives are in good working order as is the XPS.

P.S.  When creating the Kubuntu thumb drive in Ubuntu and then booting into System76 Wild Dog Pro from December 2015 it works.

---

### Post by oldfred on 2017-05-04
Are you using the 64 bit version and booting in UEFI mode?
Have you change drive to AHCI mode. Common with most new Dell.

 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)

---

### Post by MechaMechanism on 2017-05-05
Solved by updating BIOS to 1.2.4.  After that the XPS could see my thumb drive.

---

