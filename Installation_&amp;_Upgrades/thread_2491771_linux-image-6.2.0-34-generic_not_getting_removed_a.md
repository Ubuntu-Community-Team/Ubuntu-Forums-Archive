---
title: "linux-image-6.2.0-34-generic not getting removed after upgrade to Ubuntu 23.10"
date: 2023-10-19
forum: Installation &amp; Upgrades
---

### Post by sanjayminni on 2023-10-19
after upgrading to Ubuntu 23.10 mantic
every time I try to install any package or run apt upgrade or apt update

 it says
...
The following packages will be REMOVED
  linux-image-6.2.0-34-generic
...
and then it ends with the following error
...
(Reading database ... 234913 files and directories currently installed.)
Removing linux-image-6.2.0-34-generic (6.2.0-34.34) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.2.0-34-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-9-generic
Found initrd image: /boot/initrd.img-6.5.0-9-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda5@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
Adding boot menu entry for UEFI Firmware Settings ...
/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.2.0-34-generic (--remove):
 installed linux-image-6.2.0-34-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-6.2.0-34-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
...

how to resolve

---

### Post by jezzaw007 on 2023-10-27
I too got this error, but I recall noting the error messages when upgrading as it failed to update one of the scripts in /etc/grub.d
in my case 10_linux, I made a backup of this script and replaced it from the 23.10 ISO and reran 
sudo apt install initramfs-tools
sudo apt update && apt upgrade
sudo update-grub

This resolved issue with update manager but doesnt seem to update grub properly, now boots to a screen asking for username with no grub menu so cant boot.  So how to fix so it loads a 6.5 kernel instead of 6.2.35 image?

Im in process of checking all scripts in the grub.d folder

---

### Post by jezzaw007 on 2023-11-08
UPDATE - Just to confirm my issues now resolved. I was able to purge the linux-image-6.2.0-34-generic using live cd boot, 
updated the /etc/grub.d/10_linux file
then proceeded with 
apt update
apt upgrade
apt autoremove
This fixed the remaining issues with missing packages and it now boots with the 6.5.0-10 image

---

### Post by MAFoElffen on 2023-11-09
Happy to hear all is working now!

Since fixed-- Please go to the upper right of the page, to the "Thread Tools" link to mark your thread as Solved, that will help other user find what worked for you to Solve their similar problems.

---

