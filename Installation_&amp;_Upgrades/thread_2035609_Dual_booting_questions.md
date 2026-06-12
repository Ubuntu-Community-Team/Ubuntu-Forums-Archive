---
title: "Dual booting questions"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by srharri9 on 2012-07-30
I'm a Ubuntu novice. I'd like to dual boot Windows 7 and Ubuntu. However, I like my current Ubuntu system the way it is. Is there a way to partition my hard drive and install Windows without messing up my current Ubuntu installation?

---

### Post by levlaz on 2012-07-30
> **srharri9 said:**
> I'm a Ubuntu novice. I'd like to dual boot Windows 7 and Ubuntu. However, I like my current Ubuntu system the way it is. Is there a way to partition my hard drive and install Windows without messing up my current Ubuntu installation?

This is an [excellent guide]("https://help.ubuntu.com/community/WindowsDualBoot") that will help you do exactly what you are asking for.

---

### Post by QIII on 2012-07-30
Do backups.

Do backups.

Do backups.

---

### Post by darkod on 2012-07-31
So, you have only ubuntu right now?

If the ubuntu partitions are taking up the whole disk, there is no way to install windows without shrinking some of the linux partitions to make unallocated space.

Depending on the disk layout, you need to decide what partition to shrink, and you will probably have to do that from live mode because you can't shrink a running root partition.

After that is done, create ntfs partition from the unallocated space, primary. Set the boot flag on it, just in case. Do that from ubuntu rather then letting the win7 installer do it because it will try creating two partitions.

Then install win7 onto the created ntfs partition. It will delete the grub2 bootloader from the MBR so you will have to reinstall it after the win7 install is done.

---

### Post by srharri9 on 2012-07-31
I will take a look at that guide later today. It looks very helpful at first glance. I'm at work now, and all I want to do is work on my computer :(
 
All of my important files are backed up--I just don't want to have to start over on ubuntu.
 
I have only one partition on my hard drive and it has Ubuntu installed on it.  What should I use to shrink the partition and make a new one within Ubuntu?  When you say to shrink the partition from live mode, you mean to do it while using a live cd?  How can I go about reinstalling the grub2 bootloader?
 
Thanks for all your help!

---

### Post by oldfred on 2012-07-31
You can use liveCD and gparted to shrink the Ubuntu partition. You probably have to click on swap and rightclick swapoff. LIveCDs usually mount swap to speed things up.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Mostly on expanding
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
Lots of detail on resizing:
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

If dual booting you may want two NTFS partitions. One for the system and another for shared data. Always best not to write a lot of info from Ubuntu into a Windows partition. Best just to mount the Windows system as read-only and use a shared NTFS data partition for any data you want to share. I have my Firefox & Thunderbird profiles in a shared NTFS partition so I have same bookmarks and email in both. But now I do not boot XP any more.

A few have said they had to reformat the NTFS partition again in the Windows 7 installer, others seem to have had it work. But boot flag on the primary NTFS partition is important as that is how Windows boots, know where to install or what to repair.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you prefer a gui you can use this from the Ubuntu liveCD/USB or download as a liveCD.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

