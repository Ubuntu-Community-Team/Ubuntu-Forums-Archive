---
title: "Partitioning and Kubuntu woes"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by hexwolf on 2008-02-18
After partitioning my hard drive such that it has one NTFS volume and a logical volume split into three EXT3 partitions and a swap partition, I've installed Windows Vista in the NTFS partition and it works flawlessly, the first logical volume is occupied with Kubuntu 7.10, which is also where I get the version of GRUB that I use for my bootloader. I then usually install Dream Linux and Sabayon in the remaining two EXT3 partitions.

The problem I'm having is getting GRUB to pick up Sabayon. I can't find the kernel information to add it manually (I'm using Sabayon 3.4f) and upon trying to boot into Kubuntu after installing an OS in one of the other two EXT3 partitions, it usually refuses to boot. If anyone has any input upon my partitioning scheme, the GRUB configuration and/or the Kubuntu refusing to boot after installing distros, it'd be much appreciated.

Thanks for your time!

---

### Post by Pumalite on 2008-02-18
Reinstall Grub with your Kubuntu Live CD: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Then boot into Kubuntu, mount your Sabayon partition. Look in boot. Edit your Kubuntu menu.lst to include Sabayon. You can get the information you need from the partition you mounted.

---

