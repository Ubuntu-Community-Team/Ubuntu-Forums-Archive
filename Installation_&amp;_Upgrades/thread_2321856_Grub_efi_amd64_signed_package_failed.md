---
title: "Grub efi amd64 signed package failed"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by koaung2 on 2016-04-24
Dear sir,
When i install ubuntu 16.04,show error message "Grub-efi-amd64-signed package-failed to install into /target/.Without the GRUB boot loader , the installed system will not boot.
And i boot usb live and install bootrepair and type followed command

sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda6" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda6" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*

but show following error 
shin-signed
grub-efi-amd64 signed error

---

### Post by oldfred on 2016-04-24
Do you have an ESP - efi system partition which is the FAT32 formated partition with boot flag on drive sda?

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by koaung2 on 2016-04-26
Thank your sir,
Now boot ubuntu. But window boot partition is lose.How should i do?

---

### Post by oldfred on 2016-04-26
See post #2, need details to know what issue may be.

---

### Post by koaung2 on 2016-05-09
now i can solve with esp partition 

Thank for all

---

