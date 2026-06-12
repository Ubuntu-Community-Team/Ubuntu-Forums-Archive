---
title: "GRUB install with encrypted /boot in a full encrpyted drive"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by palma95 on 2016-02-03
I'm trying to setup a full encrypted disk with a separate /boot partition and I'm having some troubles.
  I'll write down the procedure I've been following: 
(On a Ubuntu 15.04 Live DVD session) 

- fill the disk with 'random data'
  ```
sudo dd if=/dev/urandom of=/dev/sda1 bs=4096

```  
- create the partitions (using gparted)
  ```
1) Create Partition Table - gpt
2) /dev/sda1 ext2 1.5GB #boot
   /dev/sda2 linux-swap 4GB #swap
   /dev/sda3 ext4 15 GB #root
   /dev/sda4 ext4 FREESPACE #home

```  
- encrypt volumes
  ```
cryptsetup luksFormat --cipher twofish-xts-plain64 --key-size 512
                      --hash sha512 --iter-time 3000 /dev/sda1
cryptsetup luksFormat --cipher twofish-xts-plain64 --key-size 512
                      --hash sha512 --iter-time 3000 /dev/sda2
cryptsetup luksFormat --cipher twofish-xts-plain64 --key-size 512
                      --hash sha512 --iter-time 3000 /dev/sda3
cryptsetup luksFormat --cipher twofish-xts-plain64 --key-size 512
                      --hash sha512 --iter-time 5000 /dev/sda4

```  
- open cryptovolume
  ```
cryptsetup luksOpen /dev/sda1 boot
cryptsetup luksOpen /dev/sda2 swap
cryptsetup luksOpen /dev/sda3 root
cryptsetup luksOpen /dev/sda4 home

```  
- format
  ```
mkfs.ext2 /dev/mapper/boot
mkswap /dev/mapper/swap
mkfs.ext4 /dev/mapper/root
mkfs.ext2 /dev/mapper/home

```  
- install (using ubiquity)
  ```
boot loader on /dev/sda
/dev/sda1 - use as ext2 - mount point /boot
/dev/sda2 - use as ext2 - mount point /boot
/dev/sda3 - use as ext2 - mount point /boot
/dev/sda4 - use as ext2 - mount point /boot

```  
At the end the installer warns that grub-install failed (because  the boot volume is encrypted), so choose 'continue without bootloader'.
  
- clean boot volume
  ```
mkfs.ext2 /dev/mapper/boot

```  
- mount volume
  ```
mkdir /mnt/root
mount /dev/mapper/root /mnt/root
mount /dev/mapper/boot /mnt/root/boot

```  
- update fstab and crypttab

  ```
sudo blkid

[/dev/sr0: UUID="2015-10-21-16-17-40-00" LABEL="Ubuntu 15.10 amd64"
           TYPE="iso9660" PTUUID="429817b4" PTTYPE="dos"
/dev/sda1: UUID="...#1" TYPE="crypto_LUKS" PARTUUID="..."
/dev/sda2: UUID="...#2" TYPE="crypto_LUKS" PARTUUID="..."
/dev/sda3: UUID="...#3" TYPE="crypto_LUKS" PARTUUID="..."
/dev/sda4: UUID="...#4" TYPE="crypto_LUKS" PARTUUID="..."
/dev/mapper/boot: UUID="..." TYPE="ext2"
/dev/mapper/swap: UUID="..." TYPE="swap"
/dev/mapper/root: UUID="..." TYPE="ext4"
/dev/mapper/home: UUID="..." TYPE="ext4"]

```  -@@@@ fstab
  ```
#<file system>   <mount point>   <type>   <options>           <dump>   <pass>
UUID=#1          /boot           ext2     defaults            0        2
UUID=#2          none            swap     sw                  0        0
UUID=#3          /               ext4     errors=remount-ro   0        1
UUID=#4          /home           ext4     defaults            0        2

```  -@@@@ crypttab
  ```
 boot   UUID=#1   luks,cipher=twofish-xts-plain64,size=512,
                  hash=whirlpool, time=3000
 swap   UUID=#2   luks,swap,cipher=twofish-xts-plain64,size=512,
                  hash=whirlpool,time=3000
 root   UUID=#3   luks,cipher=twofish-xts-plain64,size=512,
                  hash=whirlpool,time=3000
 home   UUID=#4   luks,cipher=twofish-xts-plain64,size=512,
                  hash=whirlpool,time=5000

```  
- update initramfs image
  ```
cd /mnt
sudo chroot root
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
update-initramfs -u                

```  
- configure bootloader (/etc/default/grub)
  ```
GRUB_ENABLE_CRYPTODISK=y
GRUB_PRELOAD_MODULES="luks cryptodisk"
GRUB_CMDLINE_LINUX="cryptdevice=UUID#3:root root=/dev/mapper/root resume=/dev/mapper/swap 
                    crypto=whirlpool:twofish-xts-plain64:512:0:"

```  
- create config file
  ```
grub-mkconfig -o /boot/grub/grub.cfg

[/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/mapper/root'.]

```  -@@@@ try outside
  ```
exit
grub-mkconfig -o /boot/grub/grub.cfg

[/usr/sbin/grub-probe: error: failed to get canonical path of `/cow']


```
  
Did I make any mistake before this? 
How can I continue to configure and install grub correctly?

  
Thanks for your help!

---

### Post by oldfred on 2016-02-03
I do not know LVM nor encryption.
But the default full drive with encryption is one partition for /boot unencrypted and not in the LVM and the one partition for the entire rest of the drive that is the LVM and has two default partitions / & swap. If manually creating you can have whatever logical partitions you want, but should only have the one physical partition. But LVM can span more than one physical partition, but that is normally ot use more than one drive.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061)

---

### Post by palma95 on 2016-02-03
Pavel Kogan posted a [guide]("http://www.pavelkogan.com/2014/05/23/luks-full-disk-encryption/") for full disk encryption with /boot...
Do you mean an external /boot volume can't be setup?

---

### Post by oldfred on 2016-02-04
Those instructions looks reasonable.
But the difference is that he has all his Linux partitions in the LVM in one physical partition sda1.
That makes it a bit easier.

---

### Post by palma95 on 2016-02-04
Yeah and I've tried it, but it didn't worked exactly as it's written there...  
Ubiquity failed grub-install and terminal grub-mkconfig failed as I wrote in the post, so I manage to do it with boot-repair, changing /etc/default/grub and obviously, using mkinitramfs instead of mkinitcpio.
  After you type the master password in the preload and lunch ubuntu it doesn't load some libs, so maybe Ubiquity didn't manage to install correctly the system or the guide is not perfect.  

It's really nice that users share their own experience, the fact is there are 8000 different guides with different procedures and the most are for Arch... Damn, how is it possible the ubuntu community can't provide an official safe and complete guide for full disk encryption in all modalities, including plain mode for deniable encryption?

---

