---
title: "Can't boot encrypted drive. update-initramfs problems."
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by skav2407 on 2014-07-30
I accidentally deleted my kernel when upgrading from 3.13.0-30 to 3.13.0-32.  I have them back thanks to a live CD but now I can't figure out get my system to boot back up.  sda1 is my boot drive (not encrypted) and sda5 (Encrypted) (/dev/mapper/ubuntu--vg-root) is where everything OS is located.  I am trying to run update-initramfs -u -k 3.13.0-32-generic and I get the following:

update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
depmod: WARNING: could not open /tmp/mkinitramfs_JFCF7x/lib/modules/3.13.0-32-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_JFCF7x/lib/modules/3.13.0-32-generic/modules.builtin: No such file or directory

I can't seem to figure out how to get that to go away.


This is my blkid:

root@ubuntu:/etc# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4d88905d-0aa5-4de8-8647-6bd5665a3b2e" TYPE="ext2" 
/dev/sda5: UUID="79523935-cb86-46aa-b8b7-186847a49a7c" TYPE="crypto_LUKS" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
/dev/mapper/luks-79523935-cb86-46aa-b8b7-186847a49a7c: UUID="UXxhKH-3lck-gFi1-RlYN-E7Y5-nzKu-yZQLlY" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="40e30457-31b9-441b-8d0d-44866e9b46c7" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="93174541-dac1-4ebb-9d2b-714f37c95714" TYPE="swap" 

Thanks in advance for the help.

---

