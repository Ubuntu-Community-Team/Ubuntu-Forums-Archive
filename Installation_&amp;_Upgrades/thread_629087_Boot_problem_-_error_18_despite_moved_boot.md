---
title: "Boot problem - error 18 despite moved /boot"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by master_runner on 2007-12-02
So, I discovered that my BIOS does not support booting past a certain cylinder when I installed 7.10 in a dual-boot configuration and GRUB gave me an error 18. I am told tha a solutien is to boot /boot at the beginnig of the drive. 

I was told that a solution was to simply install with /boot in a 500MB area at the beginning of the disk from an old diagnostic partition. So, during the install, I told the partitioner to create a small partition at the beginning of the drive containing with mount point /boot/ and a large partiton about 70GB in with mountpoint / (I also, of course, created a swap partition). Upon booting in to Ubuntu GRUB once again gave me an error 18.

 Have I done something incorrectly?

---

### Post by meierfra on 2007-12-02
Boot from the LiveCD and post the output of 

```
sudo fdisk -l
```

Also try to  find  the  file /boot/grub/menu.lst  on your ubuntu partition and   post its content.
( Look in Computer->Places for your ubuntu partition.  Then File System, boot. grub)

---

