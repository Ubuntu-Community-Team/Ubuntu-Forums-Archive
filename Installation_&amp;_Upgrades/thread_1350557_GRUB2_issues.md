---
title: "GRUB2 issues"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Noob37S on 2009-12-09
Hey guys,
 
I am new to linux and all so please bear with me on this issue I've been having.
 
I have 2 set of HDs, 1 set RAIDed and 1 SATA 100GB. The RAIDed one, I am using it for XP and 7 while the SATA one is for Ubuntu 9.10 by itself.
 
 
 
The problem I am having is that when the machine boot up, I got this instead of it booting into the OS: 
 
[ Minimal BASH-like editing is supported. For the first world, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
 
sh:grub>_
 
 
 
What happend? What should I do? 
 
Thanks in advance

---

### Post by darkod on 2009-12-09
Did you install wubi or ubuntu? It's NOT the same.
If you installed wubi read post #10 here:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

Depending on what partition is wubi, you might need to use something different instead of /dev/sda1.

PS. And I would consider installing a proper side-by-side dual boot ubuntu.

---

### Post by Noob37S on 2009-12-09
I installed Ubuntu not Wubi....
That's what I am afraid you would say, installing it side by side with Windows 7. Is there anyway around it?

When I installed Ubuntu with the CD, at the final stage it gave me an message of FATAL ERROR GRUB NOT INSTALL.

---

### Post by darkod on 2009-12-10
> **Noob37S said:**
> I installed Ubuntu not Wubi....
That's what I am afraid you would say, installing it side by side with Windows 7. Is there anyway around it?

When I installed Ubuntu with the CD, at the final stage it gave me an message of FATAL ERROR GRUB NOT INSTALL.

You don't need a way around it, it's the preferred way to use it. Side-by-side doesn't mean literary, you can have them on two separate HDDs. I'm slightly confused, you said two sets of HDDs, RAID and SATA. Does that mean at least two drives in RAID and one separate SATA? Minimum of three HDDs?
Depending of the setup grub2 might have tried to install itself on the raid set and I don't think it can do that. First, set the sata drive as first choice in boot order in BIOS. Then, boot with the ubuntu cd, select Try Ubuntu, and open terminal. Check you partition on the sata drive with:
sudo fdisk -l

Probably you will have one large root partition and smaller swap partition. If your root partition is for example /dev/sda1 theh drive is /dev/sda, use the following to install grub2 on it's MBR:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Change /dev/sda1 and /dev/sda depending on the results fdisk gives. Or post the fdisk results here if you have questioons.

After those commands grub2 should be installed on your sata, reboot, and see how it goes.

---

### Post by Noob37S on 2009-12-10
my bad, I should have made it clearer.  I have 3 HDs total, 2 are RAID together and the other is a SATA standalone.

I tried the code you've given me and the results are posted below.  However I still get the black screen with the command line and unable to boot into OS.  Am I missing something?

```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffff of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x466defa2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60801   385985722+   f  W95 Ext'd (LBA)
/dev/sda5   ?      280098      547447  2147483647+  ff  BBT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22ee8501

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c844c83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       11687    93875796   83  Linux
/dev/sdc2           11688       12188     4024282+   5  Extended
/dev/sdc5           11688       12188     4024251   82  Linux swap / Solaris

Disk /dev/sdd: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f5d06e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4111    33021576    7  HPFS/NTFS
/dev/sdd2            4112       36481   260012025    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdc
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

```

---

### Post by darkod on 2009-12-11
> **Noob37S said:**
> my bad, I should have made it clearer.  I have 3 HDs total, 2 are RAID together and the other is a SATA standalone.

I tried the code you've given me and the results are posted below.  However I still get the black screen with the command line and unable to boot into OS.  Am I missing something?

```
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xffff of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x466defa2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60801   385985722+   f  W95 Ext'd (LBA)
/dev/sda5   ?      280098      547447  2147483647+  ff  BBT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22ee8501

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c844c83

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       11687    93875796   83  Linux
/dev/sdc2           11688       12188     4024282+   5  Extended
/dev/sdc5           11688       12188     4024251   82  Linux swap / Solaris

Disk /dev/sdd: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f5d06e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4111    33021576    7  HPFS/NTFS
/dev/sdd2            4112       36481   260012025    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdc
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

```

It looks fine. You need to make sure the /dev/sdc, the 100GB disk is first option in boot order in BIOS. You just installed grub2 there and that's where BIOS should check first for a bootloader.
If that doesn't help I'm out of ideas... :(

---

### Post by Noob37S on 2009-12-11
do you it has anything to do with the fact that SDC is not set to bootable? It does not have an asterisk on any of the partitions on SDC. Thanks for your help though....

---

### Post by darkod on 2009-12-11
> **Noob37S said:**
> do you it has anything to do with the fact that SDC is not set to bootable? It does not have an asterisk on any of the partitions on SDC. Thanks for your help though....

In general linux doesn't need the boot flag, only windows. But I'm not sure if it can confuse the BIOS. You can add boot flag on any partition with Gparted.

---

### Post by Noob37S on 2009-12-11
> **darkod said:**
> In general linux doesn't need the boot flag, only windows. But I'm not sure if it can confuse the BIOS. You can add boot flag on any partition with Gparted.
 
 
how do you do that? Worth a try since nothing seems to work right now.

---

### Post by Noob37S on 2009-12-11
> **darkod said:**
> In general linux doesn't need the boot flag, only windows. But I'm not sure if it can confuse the BIOS. You can add boot flag on any partition with Gparted.
 
How do I add in a boot flag in Linux? Worth a try I guess since nothing seems to work right now....

---

### Post by darkod on 2009-12-11
> **Noob37S said:**
> How do I add in a boot flag in Linux? Worth a try I guess since nothing seems to work right now....

I'm not sure if you can do it within ubuntu because / is mounted. If you boot with the cd in Try Ubuntu, open Gparted (in System-Administration) and right click the / partition, there should be Flags in the menu. In Flags check the boot flag.
You will probably need to click the big green tick mark button in Gparted to execute the operation. That's it.

---

### Post by Noob37S on 2009-12-13
Darkod, I figured out what I did wrong...thanks for all your help. Got it to work now

---

