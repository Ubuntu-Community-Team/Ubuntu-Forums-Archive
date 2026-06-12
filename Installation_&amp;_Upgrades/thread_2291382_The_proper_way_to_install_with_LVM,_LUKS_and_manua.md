---
title: "The proper way to install with LVM, LUKS and manual partitioning"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by gbbloanf on 2015-08-19
I am trying to install Xubuntu 15.04 with LVM and LUKS, manually partitioning in order to have a separate **/home** partition.

So far I have booted the Xubuntu live CD and went through these steps:

[LIST=1]
[*]Used gparted to create three partitions:
[LIST]
[*]**200 MB fat32 **with** boot **flag as** /dev/sda1** - EFI System Partition. 
[*]**300 MB ext2 **as** /dev/sda2** - Will be used for /boot. 
[*]**400 GB unformatted **as** /dev/sda3** - Will be the encrypted volume. 
[/LIST]
  
[*]Created and opened the encrypted volume:
[LIST]
[*][I]cryptsetup luksFormat --cipher aes-xts-plain64 --key-size 512 --hash sha512 /dev/sda3
[/I] 
[*]*cryptsetup luksOpen /dev/sda3 crypt* 
[/LIST]
  
[*]Set up the logical volumes on the encrypted volume:
[LIST]
[*][I]pvcreate /dev/mapper/crypt
[/I] 
[*]*vgcreate vgcrypt /dev/mapper/crypt* 
[*]*lvcreate -n lvcryptroot -L 30G vgcrypt* 
[*][I]lvcreate -n lvcryptswap -L 10G vgcrypt
[/I] 
[*]*lvcreate -n lvcrypthome -l 100%FREE vgcrypt* 
[/LIST]
  
[*]Set up the filesystem on the logical volumes:
[LIST]
[*][I]mkfs.ext4 /dev/vgcrypt/lvcryptroot
[/I] 
[*]*mkfs.ext4 /dev/vgcrypt/lvcrypthome* 
[*]*mkswap /dev/vgcrypt/lvcryptswap* 
[/LIST]
  
[*]Ran the installer, selected the appropriate options and started the installation.
[LIST]
[*]Set **/dev/mapper/vgcrypt-lvcryptroot** to mount point **/** 
[*]Set **/dev/mapper/vgcrypt-lvcrypthome** to mount point **/home** 
[*]Set **/dev/sda2** to mount point **/boot** 
[*]Set **/dev/sda** as the device for boot loader installation. 
[/LIST]
  
[*]When the installer finished, I chroot into the new system:
[LIST]
[*][I]cd /mnt
[/I] 
[*][I]mkdir root
[/I] 
[*][I]mount /dev/mapper/vgcrypt-lvcryptroot root
[/I] 
[*][I]mount /dev/sda2 root/boot
[/I] 
[*]*chroot root* 
[*]mount -t proc proc /proc 
[*]mount -t sysfs sys /sys 
[/LIST]
  
[*]Created **/etc/crypttab** and added an entry for **/dev/sda3** to it:
[LIST]
[*]*vi /etc/crypttab* 
[*]Inserted the line: **crypt UUID=*<uuid_here>* none luks** 
[*]*update-initramfs -u* 
[*]*exit* 
[*]*reboot  * 
[/LIST]
   
[/LIST]
 
Upon attempting to boot into the newly installed system, I am not asked for a password to decrypt the encrypted volume. I am thrown into the initramfs prompt without any errors. What did I miss?

---

### Post by TheFu on 2015-08-19
Don't know. I tried to do it the same way and failed. After a few days screwing around with it, I just needed a working solution.

I let the installer handle it, but made certain to NOT use the entire encrypted VG for LVs. 

Then after the first reboot, I manually created a LV for home and moved everything over to it, fixed the fstab, removed the old files, then did a mount -a. Logout/login - all was good.  

Then I doubled the swap from 2G for 4G.

---

