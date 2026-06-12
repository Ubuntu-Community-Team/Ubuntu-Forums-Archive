---
title: "PC boots straight to windows after 11.04 Install"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Monkadelicd on 2011-05-08
I am fairly inexperienced with Linux. I'm good with windows and PCs in general.
I've been wanting to setup a Linux environment for teaching myself some programming so I downloaded Ubuntu 11.04 to install on my main Windows desktop.

I have two internal HDDs and an external HDD. Each of the internals is 160GB and the external is 1TB.

I have Windows on the drive in SATA0. I split the drive in SATA1 into 3 partitions. 

[LIST]
[*]I Windows Disk Management to shrink the NTFS partition to 100GB for storage.
[*]I used gParted to create a 2GB swap partition
[*]the rest is a ext4 partition
[/LIST]
So sda1 is NTFS, sdb1 is swap, sdb2 is ext4, and sdb3 is NTFS, and sdc1 is NTFS

I mounted sdb2 as root and installed Ubuntu there. I chose the manual option for the installation as the install alongside Windows option only showed my external HDD (sdc).

I wasn't sure where to place the boot loader so I tried to overwrite the Windows boot loader on sda but that failed with an error about no file system available or compatible. I figured Grub2 doesn't work on NTFS

I did some reading and to my understanding Grub2 is to be installed on the partition with Ubuntu. I tried the installation again and selected sdb2 as the location for the boot loader. 

The installation finished with no errors and instructed me to restart. I did this and the PC booted straight into Windows without ever displaying a boot loader screen, Windows or Grub2.

How can I get the Grub2 screen to show up? Did I put it in the wrong place?

Thanks ahead for any help offered.

---

### Post by kansasnoob on 2011-05-08
Please post the output of:

```
sudo parted -l
```

---

### Post by oldfred on 2011-05-08
No you do not install the grub2 boot loader to a partition. Grub itself is in the /boot/grub folder of the root partition ( and setting in other places). Windows has its boot loader in the MBR (master boot record or first sector of hard drive), also has code in the partition boot sector (PBR) and its boot files in its boot/recovery partition or main install partition.

Since you did not install grub2's boot loader to a drive's MBR, it is still using windows.

Since you have two Hard drives I would keep windows boot loader in the sda drive, install grub2's boot loader in the MBR of sdb and set BIOS to boot sdb as grub will also let you boot windows.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb2 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb2 if not correct:
sudo fdisk -l
#confirm that linux is sdb2
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

If you did get grub to install or partially install to the windows partition you may have trouble booting windows.

---

### Post by Monkadelicd on 2011-05-08
> **oldfred said:**
> No you do not install the grub2 boot loader to a partition. Grub itself is in the /boot/grub folder of the root partition ( and setting in other places). Windows has its boot loader in the MBR (master boot record or first sector of hard drive), also has code in the partition boot sector (PBR) and its boot files in its boot/recovery partition or main install partition.

Since you did not install grub2's boot loader to a drive's MBR, it is still using windows.

Since you have two Hard drives I would keep windows boot loader in the sda drive, install grub2's boot loader in the MBR of sdb and set BIOS to boot sdb as grub will also let you boot windows.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb2 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb2 if not correct:
sudo fdisk -l
#confirm that linux is sdb2
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

If you did get grub to install or partially install to the windows partition you may have trouble booting windows.

I followed these instructions and I still have the same result. It just boots straight to windows. I don't have the option in BIOS to boot from sdb first. I'm on a Dell OptiPlex GX620. Should I just switch sdb to the SATA0 port and put sda on SATA1?

I guess I'll try to switch the drives and see what happens.

---

### Post by oldfred on 2011-05-08
I think all BIOS with SATA have an option on which drive to boot first. Only old IDE only BIOS only booted primary master, which was set by jumpers on the hard drive and which cable was used.

 Some have it as anther line somewhere in BIOS, and some have it as you select which device (hd, Cd, etc) and then under HD you have another selection.

You also should have a one time boot key, usually BIOS tells you on the instial BIOS screen. Mine is f12, but it varies by system.

---

### Post by Monkadelicd on 2011-05-08
> **oldfred said:**
> You also should have a one time boot key, usually BIOS tells you on the instial BIOS screen. Mine is f12, but it varies by system.

There is a prompt for F12 that enters boot menu. I'll try that. 

But as for setting a specific HDD for booting, I don't know. I tried to get to an option for which HDD but I can only enable or disable the option for booting from an internal HDD. There is nothing to select options I can see. I'll look in other areas but I've not seen anything as of yet.

---

