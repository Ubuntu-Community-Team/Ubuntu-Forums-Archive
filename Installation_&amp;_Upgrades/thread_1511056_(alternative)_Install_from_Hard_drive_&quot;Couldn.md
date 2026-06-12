---
title: "(alternative) Install from Hard drive: &quot;Couldn't mount CD-ROM&quot;"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Ananth on 2010-06-16
Trying to install Ubuntu Studio 10.04 from the Alternate installation ISO image copied to Hard drive. Installation begins. After detecting Keyboard etc, I get this message

 = = Detect and Mount CD-ROM ==
Your Installation CD-ROM couldn't be mounted.  .... Try again to mount the CD-ROM?


I'm following this guide:  [https://help.ubuntu.com/community/Installation/FromLinux#Procedure%201](https://help.ubuntu.com/community/Installation/FromLinux#Procedure%201)

1. Running an existing Ubuntu 10.04. Copied these files to the present ext4 partition. 

[LIST]
[*]Alternate ISO image (to /)
[*]vmlinuz, initrd.gz (from the ISO image to /studio/)
[/LIST]
2. Edited Grub -

```

menuentry "INSTALL ubuntu studio(iso on /dev/sda4)" {
    insmod ext2
    set root='(hd0,4)'
    linux /studio/vmlinuz root=/dev/ram ramdisk_size=1048576 rw
    initrd /studio/initrd.gz
}

```Basically copy-pasted grub entry for the existing installation and modified. ISO etc for new install is on the same drive, so I hope the hd0,4 numbers are correct. (besides, installation does begin.)

Tried with/without "root=/dev/ram ramdisk_size=1048576 rw" in 'linux /stu...' line. 

Still, "Your Installation CD-ROM couldn't be mounted".  Any help is greatly appreciated. 

ps: I have 2 ubuntu installs: 9.10, 10.04. LVM and Non-lvm partitions. Couldn't burn a DVD or create usb startup disk.

--
Ananth

---

