---
title: "ubuntu will only boot from usb"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by andyw0101 on 2015-11-03
Hi, would appreciate some help please. Ubuntu will only boot from usb, otherwise the boot message is "no bootable device". Ubuntu is installed on the HDD and windows was removed. Ive had a look through the BIOS and set the order of the boot (with the HDD first).
Also, ive tried the following commands in the terminal with the following results;

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mn
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mn
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

thanks in advance.

---

### Post by yancek on 2015-11-03
> 
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; 

You are using GPT partitioning on the computer.  You did not create the BIOS Boot Partition mentioned.  You can do that from GParted which is on the Ubuntu installation medium.  I don't use GPT myself but if you do an online search, you should find sites like the one below which explain how to do it.

[http://askubuntu.com/questions/473641/make-boot-partition-using-gparted-in-boot-repair](http://askubuntu.com/questions/473641/make-boot-partition-using-gparted-in-boot-repair)

---

### Post by oldfred on 2015-11-03
Are you wanting to boot in UEFI boot mode or BIOS boot mode.
Ubuntu can boot either way from a gpt partitioned drive if you have correct partitions on drive.
For UEFI you need the ESP - efi system partition formated FAT32 with boot flag if using gparted or code ef00 if using gdisk.
For BIOS you need a bios_grub partition only 1 or 2MB anywhere on drive, unformatted with bios_grub flag or if gdisk code ef02.

Grub-pc is for BIOS and grub-efi-amd64 is for 64 bit UEFI.

How you boot installer is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Often easier to use Boot-Repair, but again UEFI or BIOS?
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by andyw0101 on 2015-11-04
Thank you both for your help! I ran the boot repair and now ubuntu boots without the usb, which is great. However, on boot i get the message "Default Boot Device missing or Boot Failed. Insert recovery media and hit any key. Then select Boot Manager to choose a new boot device or to boot recovery media". I continue without inserting the usb and it goes to the bios and im given the options of "1. unknown device. 2.Windows boot Manager", i press ok as the unknown device (which im assuming is the ununtu grub?) is prioritized and ubuntu boots up. Is there any way of bypassing this or removing the "default windows boot manager"?

Thanks in advance.

---

### Post by oldfred on 2015-11-04
What brand/model.

You can edit UEFI boot entries with efibootmgr.
If only booting Ubuntu, you can change the ubuntu entry in UEFI to a Windows boot but still use grub or shim files to boot.
Details on that in link in my signature. 

Or post link to Boot-Repairs Summary Report if more help needed.

---

