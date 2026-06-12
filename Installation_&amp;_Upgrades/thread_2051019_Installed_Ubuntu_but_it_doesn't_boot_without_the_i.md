---
title: "Installed Ubuntu but it doesn't boot without the installation source"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by nightfury on 2012-09-01
Hi, I installed Ubuntu 12.04.1 64-bit LTS beside my Win8 which is 64-bit, too from a memory flash drive. The problem is there is no such a list to select one of the installed operating systems. The computer itself runs Win8 automatically. If I want to go through my newly-installed Ubuntu, I HAD TO connect the flash drive to my case and manually select boot options, then select the flash drive to boot. After that GRUB will show up and I can choose one of the operating systems including Ubuntu. The point is, I cannot use my Ubuntu without my flash drive but as I said, I INSTALLED the Ubuntu stuff on my PC. What should I do to normally have a GRUB boot screen and get rid of automatically booting into Win8? Thanks for help :)

---

### Post by darkod on 2012-09-01
Boot your ubuntu once with the usb stick present, then open terminal and see the output of:
```
sudo fdisk -l
```

Usually there will be two devices, /dev/sda and /dev/sdb. Look into their sizes/models and see which is the hdd. Then run:
```
sudo grub-install /dev/sdX
```

using the correct letter instead of X. That will install grub2 to the MBR of the hdd. Restart without the stick and you should have the grub menu.

---

### Post by nightfury on 2012-09-01
> **darkod said:**
> Boot your ubuntu once with the usb stick present, then open terminal and see the output of:
```
sudo fdisk -l
```Usually there will be two devices, /dev/sda and /dev/sdb. Look into their sizes/models and see which is the hdd. Then run:
```
sudo grub-install /dev/sdX
```using the correct letter instead of X. That will install grub2 to the MBR of the hdd. Restart without the stick and you should have the grub menu.

Thanks it worked! :)

---

### Post by dino99 on 2012-09-01
> **nightfury said:**
> Thanks it worked! :)

Good, now set this thread as SOLVED please, using the top right "Thread Tools" menu .

---

