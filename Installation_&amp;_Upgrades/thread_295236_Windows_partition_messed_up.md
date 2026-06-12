---
title: "Windows partition messed up"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Thisper on 2006-11-07
Well I planned on dual booting ubuntu and windows so I booted up to ubuntu and then clicked install on the desktop and when it came to the partitions part I resized the existing partition to have enough space to make a new 20gb partition but when i went to the next step and seleted the new partition as the one to install ubuntu on it said it was too small and I went back and checked and the new one was 0mb and my windows partiton was a unrecognized filesystem, so I shut down and tried booting normally but it didn't work so i booted back to ubuntu and checked my drive in gparted [IMG]http://www.mikey.panscomenterprises.com/Screenshot2.png[/IMG]
so I can't access any of the data on it...if there is any way to be able to fix it or be able to atleast get my data off please let me know

Thanks for you help

---

### Post by sethmahoney on 2006-11-07
In a terminal in Ubuntu, try:

```
sudo mkdir /windows
sudo mount /dev/hdc1 /windows -t ntfs
```

It probably wont work, but its worth a shot.

(Edited: /dev/hd1 to /dev/hdc1)

---

### Post by Thisper on 2006-11-07
Thanks for your quick reply, I already tried that though, should have mentioned it


```
ubuntu@ubuntu:/$ sudo mount /dev/hdc1 /media/windows -t ntfs
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/$

```

---

### Post by Thisper on 2006-11-07
I ran dmesg after trying to mount the drive and heres some of what it gave me

```
[17180335.348000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180335.348000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180335.348000] NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.
[17180399.392000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180399.392000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180399.392000] NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.
[17180473.908000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180473.908000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180473.908000] NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.
[17181257.584000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17181257.584000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17181257.584000] NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.
```

I don't know if that helps at all, even if i won't be able to fix it theres some important stuff on it i'd atleast try to recover

---

### Post by frank ross on 2006-11-07
Your error messages reveal that Ubuntu has incorrectly overwritten the MBR/partition table of your drive- hopefully it hasn't damaged the files themselves.
If you are SURE that your Windows drive was formatted as FAT32 you can boot with a Win98 startup disk- type in fdisk /mbr after it boots and this will probably restore the boot sector.
If the partition was NTFS, start the computer with your WinXP install disk. There is an option to repair your Windows installation with command line tools. Try the commands CHKDSK,FIXMBR and FIXBOOT-with luck this may recover your drive.
I may have dodged a bullet here-on my last post I wrote that I aborted installing Ubuntu because Gparted didn't properly recognize partitions. I am a bit worried that Ubuntu's default install is designed to wipe everything off the drive.

frank

---

