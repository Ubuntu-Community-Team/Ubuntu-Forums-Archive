---
title: "Someone please tell me how to install Ubuntu and keep WinXP"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2007-03-31
I have WinXP installed and working fine on a partition that only takes up a fraction of the total space on my HD.  I want to install Ubuntu and dual boot both OSes on the same HD.  I *DO NOT* want Ubuntu to kill my windows XP install.  Can someone please tell me how to install Ubuntu such that it takes up the unallocated space on my hard drive and gives me some option of selecting which OS to boot at startup?  This really should be easy.

---

### Post by Majorix on 2007-03-31
Do you have a separate partition? Or is the whole disk one single partition?

If your disk is made of one partition only, then there is no way you can install Linux. Well there is, there are some partitioning tools on Windows, but to mine and my friend's experience they don't work or can even make your pc non-bootable. So stay away from them.

If you do have a second partition then it's easy. Just make sure there are no files in the second partition, insert the Ubuntu LiveCD in your drive, and reboot if the comp is open. After you press the install icon and answer a few questions the partitioner will come up. There you have to choose "Use the largest continuous free space". Then Ubuntu will use the second partition and your Windows partition will remain untouched.

If you have problems with the installation, feel free to come back here and ask away :)

---

### Post by bollix47 on 2007-03-31
Have a look [_here_]("http://www.psychocats.net/ubuntu/index") for some useful information.

---

### Post by benerivo on 2007-03-31
By the sound of it you have a hard drive, with only a small fraction of it taken up with a XP partition, and the rest as non-partitioned / unallocated space. If this is the case then you should be in the ideal position for a linux installation. Simply load the ubuntu cd from the pc boot up, and choose the install option from the Ubuntu desktop when it has loaded. One of the first few options in the installation is the partitioning. It should be straightforward (ie. i can't remember!), but do not delete the xp partition. Instead create a root partition and a swap partition for Ubuntu in the empty space. The Ubuntu installer will create a boot selector automatically (known as grub) that will include your xp as an option. It has worked every time i have installed a linux distro, but there are no guarantees so be prepared for the worst. Before doing this i would back up as much as possible and also create a ntfs partition from xp, so that when you have installed ubuntu, it may be used by the two os's for personal files - such as music, pics, docs, etc..

---

### Post by bollix47 on 2007-03-31
".... and also create a ntfs partition from xp...."

That should probably say Fat32 partition, not ntfs.

---

### Post by benerivo on 2007-03-31
".... and also create a ntfs partition from xp...."
 
 That should probably say Fat32 partition, not ntfs.

Either is okay. Ubuntu can read / write to both. The classic linux example, states FAT32 for a shared partition, but I think the read/write ntfs driver (the ntfs-3g package) is now stable (?). At least, i have used it for several months with no side effects.

---

### Post by SNYP40A1 on 2007-03-31
> **benerivo said:**
> By the sound of it you have a hard drive, with only a small fraction of it taken up with a XP partition, and the rest as non-partitioned / unallocated space. If this is the case then you should be in the ideal position for a linux installation. Simply load the ubuntu cd from the pc boot up, and choose the install option from the Ubuntu desktop when it has loaded. One of the first few options in the installation is the partitioning. It should be straightforward (ie. i can't remember!), but do not delete the xp partition. Instead create a root partition and a swap partition for Ubuntu in the empty space. The Ubuntu installer will create a boot selector automatically (known as grub) that will include your xp as an option. It has worked every time i have installed a linux distro, but there are no guarantees so be prepared for the worst. Before doing this i would back up as much as possible and also create a ntfs partition from xp, so that when you have installed ubuntu, it may be used by the two os's for personal files - such as music, pics, docs, etc..

Yes, I actually have two hard drives, but one is a sacred backup drive that I do not want to touch.  In fact, I will unplug it while installing.  The other drive has my WinXP installed on the NTFS partition which takes up about 80% of the disk space, leaving the rest as unallocated space.  So I will try to install on the unallocated space.  I am a little paranoid because when I tried this last night, I ended up corrupting the boot loader such that I got the no operating systems installed error.  I could boot into Ubuntu and see all files in both XP and ubuntu install, but I figured I messed up the boot loader.  Anyway, I will try installing again.  Thanks for the help!!

---

