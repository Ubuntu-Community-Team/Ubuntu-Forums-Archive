---
title: "Installing Ubuntu LTS on an HP Pavilion 23 all in one desktop- boot issues"
date: 2023-02-28
forum: Installation &amp; Upgrades
---

### Post by jlouisll on 2023-02-28
I am using a .iso image on a USB stick, it will try out and run just fine, but when I install ubuntu (not wanting to dual boot simply wiped hard drive and installing ubuntu only) it gives me the following error message "The attempt to mount a file system with type vfat in SCSI 1 (0,0,0) partition #1 (sda) at /boot/efi failed. You may resume partitioning from the partitioning menu.". I ran boot repair and it references this address:

 [https://paste.ubuntu.com/p/yssfrkMPfq/](https://paste.ubuntu.com/p/yssfrkMPfq/)    

Can someone with more experience help me out? I read the boot-repair text file and it seems there is a problem with the partition size or the NTFS formatting... I'm out of my depth. Any suggestions?

---

### Post by jlouisll on 2023-02-28
solved the issue. I erased and reformatted the windows partition into fat file system and reran the installation, and it mounted the drive without a problem this time. Installation is proceeding normally so far...

---

