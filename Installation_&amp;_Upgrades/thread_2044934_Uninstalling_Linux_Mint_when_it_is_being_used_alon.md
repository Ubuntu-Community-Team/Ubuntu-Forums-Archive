---
title: "Uninstalling Linux Mint when it is being used alongside Ubuntu"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by carvaka on 2012-08-20
Hello,

I am currently running an HP laptop with 500 gb harddisk. It has two OSs installed on it on different partitions: Linux mint (~300gb) and Ubuntu (~200gb). I want to get rid of mint entirely and allocate most of the space to Ubuntu, possibly with some left over for smaller "backup" distros. I'd rather not end up loosing all my data, so what would be the best way to go about this? Could I simply uses the Ubuntu partition programme to resize, or would that mess up the bootloader? 

Any advice much appreciated, 

Thanks

---

### Post by Laiquendi on 2012-08-20
About not loosing data - the best way is to backup, thus if you have Ubuntu alongside, simply run it and copy data to Ubuntu partition.

Yes, you can use linux partitioning program, althoug I've been using GParted always and it did the job.

---

### Post by Elfy on 2012-08-20
>  Could I simply uses the Ubuntu partition programme to resize, or would that mess up the bootloader?Depends on order of installation and/or what you did with bootloader.

If you installed Ubuntu last and let it do what it wanted with grub then it's probably ok - if not you'll need to reinstall grub, remove the mint partition and it will fail to find the bootloader.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD](https://help.ubuntu.com/community/Grub2/Installing#Reinstall_from_the_LiveCD)

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by oldfred on 2012-08-20
When you currently boot, which system is first in the menu. That is the one that has the grub2 boot loader in the MBR. If you want Ubuntu in the MBR and it is not, just boot into Ubuntu and run this:

sudo grub-install /dev/sda
or
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I tend to like smaller / (root) partitions (~25GB) and separate data partitions or separate /home. But if you may want to share data with another install then a separate data partition may be better.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

If any partitions are logical in an extended partition, you will need to use gparted from a liveCD as all partitions including swap that you work on need to be unmounted. And any logical partition in the extended mounts the entire  extended partition. LiveCDs usually mount swap, so you have to click on swap and right click swap-off to unmount swap.

---

