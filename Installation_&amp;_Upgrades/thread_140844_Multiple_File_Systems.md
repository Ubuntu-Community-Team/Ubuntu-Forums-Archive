---
title: "Multiple File Systems"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2006-03-07
I have a homebuilt AMD 64 system with two hard drives on it, a 40G and a 160G.  Yesterday I wiped an existing SuSE 9.3 system and replaced it with Kubuntu 5.10.

All of the data I needed to save got backed up -- the really critical stuff onto external storage, and general-purpose stuff onto the 160G drive.

The 40G drive user partition is hdc1, and the second drive is hdd2.  The problem is that while Kubuntu 5.10 generated its partitions as ext3, the 160G second drive is in ext2 format.  When I try to mount hdd2, I get an error.

Can I read or open files on the ext2 disk through KDE?  I don't want to have to reformat that big drive unless I have to.

---

### Post by soonindallas on 2006-03-07
Do you see your disk hdd2 in /media ?

if you do, does your /etc/fstab show "ext2" for this disk ?  change this if necessary.

if you don't, what happens if you type.

```
sudo mkdir /mnt/hdd2
sudo mount -t ext2 /dev/hdd2 /mnt/hdd2
```

in the terminal ?

can you browse /mnt/hdd2 ?

---

### Post by llanitedave on 2006-03-07
It's working -- I don't know if it's going to be stable.  Rather than create a new directory in /mnt, I created /media/hdd2.  However, it didn't become mountable until I changed the file system to "Automatic" in the KDE system settings utility.

I don't know if it's going to have issues this way down the road or not...

---

### Post by soonindallas on 2006-03-07
there's no reason why you should have issues really.

ext2 lacks journalling but you can live without it.

search for more info, maybe you can migrate from ext2 to ext3.

[https://wiki.ubuntu.com/LinuxFilesystemsExplained](https://wiki.ubuntu.com/LinuxFilesystemsExplained)

---

### Post by llanitedave on 2006-03-07
Thanks, soonindallas.  Got to study up on this!

---

