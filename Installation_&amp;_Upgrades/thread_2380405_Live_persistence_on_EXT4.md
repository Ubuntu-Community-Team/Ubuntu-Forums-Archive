---
title: "Live persistence on EXT4"
date: 2017-12-17
forum: Installation &amp; Upgrades
---

### Post by virgosun on 2017-12-17
Hi all, 
I make a Live persistence on a hdd partition.
It is actually Raw on FAT32 for Live part and EXT4 for persistence data part.
I think convert from FAT32 to EXT4 for Live part would make it run faster
EXT4 is faster than FAT32 right, although most of the base system is actually on squashfs?
So I convert  Live FAT32 to EXT4.
Now system not boot at all, only to Grub rescue, where it can not recognize EXT4 partition.
I digging the google, also come across this thread with no help [URL="https://ubuntuforums.org/showthread.php?t=1380886&p=8666605#post8666605"]https://ubuntuforums.org/showthread.php?t=1380886&p=8666605#post8666605
[/URL]I digging the Grub rescue prompt and discover that bootx64.efi not load ext4 driver.
I try to patch the bootx64.efi and lead to these step to the success:

1. Recreate memdisk and config file
```

$mkdir memdisk

$nano memdisk/boot/grub/grub.cfg
            search --file --set=root /.disk/info
            set prefix=($root)/boot/grub
            source $prefix/x86_64-efi/grub.cfg

$tar cvf memdisk.tar memdisk/*

```
2. Recreate bootx64.efi with EXT4 support
```

$nano embeded.cfg
             insmod normal
             set root=(memdisk)
             set prefix=($root)/boot/grub
             source $prefix/grub.cfg

$grub-mkimage  -o bootx64.efi -O x86_64-efi  fat  iso9660 part_gpt part_msdos  \
             normal boot linux configfile loopback chain  efifwsetup efi_gop efi_uga \
             ls search search_label search_fs_uuid search_fs_file  gfxterm gfxterm_background \
             gfxterm_menu test all_video loadenv memdisk ext2 tar  -m memdisk.tar -c embeded.cfg

```
3. copy the bootx64.efi to your /efi/boot   folder
Voila your EXT4 Live partition now boot as if a RAW iso image
Regards

---

### Post by sudodus on 2017-12-17
I think it will be difficult to make your persistent live system work after you converted the FAT32 file system to ext4.

I would recommend

1. **Backup** all your personal data files to another drive, because it is risky to install an operating system.

2. Decide what kind of operating system(s) you want in your drive.

Are there operating systems, that you want to preserve in your drive (other than this faulty one)?

You can select between an new version of a persistent live system and an installed system (like a usual installed system in an internal drive). See this link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

3. Ask questions until you know what you want, and you are rather sure that you will get what you want.

4. Go ahead :-)

---

### Post by virgosun on 2017-12-18
Thanks.
This, I just want to share a method to make LiveUSB/CD on ext4 bootable
I attach here the ext4 supported bootx64.efi
Just copy it to ESP/EFI and it will boot any distro LiveUSB/CD on ext4
[ATTACH]277871[/ATTACH]

---

