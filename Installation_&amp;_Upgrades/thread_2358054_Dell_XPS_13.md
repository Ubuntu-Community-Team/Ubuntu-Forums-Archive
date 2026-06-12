---
title: "Dell XPS 13"
date: 2017-04-09
forum: Installation &amp; Upgrades
---

### Post by caro.hsg on 2017-04-09
On a new Dell XPS 13, I'm trying to install Ubuntu 16.04.2. The installer says that there's no hard disc space. I tried asking the Geek Squad at Best Buy, but they said that they don't support Linux and can't answer any questions about it. I've installed Ubuntu on 3 other laptops, no problem, but I can't find any way around this. Any help would be much appreciated.
Thanks,

---

### Post by wildmanne39 on 2017-04-09
*Thread moved to **Installation & Upgrades**.*

---

### Post by poltiser2 on 2017-04-09
If I remember well, Dell sells several models with Linux and it should be their best interest to answer your question... ;-)

---

### Post by caro.hsg on 2017-04-09
Dell told me that they don't support Linux unless the computer was purchased with Linux installed by Dell.

---

### Post by oldfred on 2017-04-09
Many threads with successful installs on Dell XPS 13s, but that has many different versions.
Exactly which model do you have?

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
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

### Post by caro.hsg on 2017-04-11
Thank you

---

### Post by mörgæs on 2017-04-11
> **caro.hsg said:**
> The installer says that there's no hard disc space.

Probably there is no free space because Windows is pre-installed. 

Do you want a dual boot or a single boot where Buntu has the entire hard drive?

---

### Post by vanadium on 2017-04-11
See here: [http://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350](http://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350) You may need to change your settings to AHCI for the disk to be recognized. Your windows might also have been pre-installed in IDE mode. You see that that change will require you to reinstall Windows if you still want it.

Eventually disable secure boot. This is not strictly necessary because the Ubuntu installer is signed.

---

