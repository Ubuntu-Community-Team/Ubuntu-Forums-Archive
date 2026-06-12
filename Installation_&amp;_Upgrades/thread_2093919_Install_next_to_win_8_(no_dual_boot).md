---
title: "Install next to win 8 (no dual boot)"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by tboheeren on 2012-12-12
Hey all,

Currently I'm running the following setup:
SSD one partition: windows 8 up & running
HDD 3 partitions. All ntfs and for media
HDD 2 partitions. One for media (NTFS) the other unallocated.

I would like to install ubuntu on the unallocated space, but I dont want to have a dual boot screen. I just want to hit F12 at startup and then boot from the 3rd disk if I want to run ubuntu. So by default win8 would startup.

I've read that I should disconnect all other drives and just install ubuntu from the bootable cd on the 3rd dsik, but is this really necessary (certain warranties will end if I do this, i know its stupid but it is what it is).
Next to that, I read that I should disable the prober in /etc/grub.d. But I have no idea how to do this.

Any suggestions?

---

### Post by sudodus on 2012-12-12
Welcome to the Ubuntu Forums :-)

What computer is it? If it is a desktop or workstation, it is straightforward to unplug an internal disk drive, and it really makes things easier during the installation.

But it is possible to install without removing the other drives. You must install grub into that drive, not to the drive with Windows! And you must be sure to identify the drives correctly, which is sometimes difficult. This is why it is good to remove the other drives during the operation.

You could even install Ubuntu when the drive is connected to another computer as long as you don't install any proprietary drivers (and they do not install automatically). Then move the drive into your computer with the other two drives, use F12, install proprietary drivers if necessary, and that's it.

You disable the prober when you remove execute permissions:
```
sudo chmod ugo-x /etc/grub.d/30_os-prober
```
and enable the prober again when you add execute permissions:
```
sudo chmod ugo+x /etc/grub.d/30_os-prober
```

ps/ I have a workstation with several drives installed (and other drives available via eSATA). I use the grub menu to select among the operating systems, which I prefer to using F12 (or the corresponding hotkey). /ds

---

### Post by tboheeren on 2012-12-12
Super reply! Thanks a lot. 
It is indeed a desktop machine so removing drives is easily.
I indeed saw in the installer that the drives were not super easy to identify (sha, shc, etc).
I will proceed as you described by removing the other drives!

---

### Post by sudodus on 2012-12-12
Good luck :-)

---

### Post by mastablasta on 2012-12-12
> **tboheeren said:**
> Super reply! Thanks a lot. 
It is indeed a desktop machine so removing drives is easily.
I indeed saw in the installer that the drives were not super easy to identify (sha, shc, etc).
I will proceed as you described by removing the other drives!
 
you can identify them in installer by their size. in manual partitioning you should be able to set where the GRUB goes.
 
 
 
hda1 - hard disk a, first parittion
hda2 - hard disk a, second parittion
hdb1 - hard disk b, first partition
 
i think h is replaced by s for sata drives. so sata drive a partition 1 is sda1

---

### Post by Mark Phelps on 2012-12-12
+1 on removing the other drives ...

I have a multi-drive machine and ALWAYS remove the other drives when installing a new version of Ubuntu.  This prevents having GRUB accidentally written to the wrong drive -- and corrupting any existing boot loader on that drive.

---

### Post by oldfred on 2012-12-12
If you do not unplug drives you have to use manual install or something else. That is the only choice that gives the option on which drive to install the grub2 boot loader into. All other choices default to sda. And even that has issues with a few computers as the flash drive used to install is sometimes promoted to sda. Normally the first internal drive is sda.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    
If your Windows 8 is pre-installed and using UEFI, you should also install Ubuntu in UEFI. But drive then needs to be gpt partitioned.
Ubuntu's os-prober has a bug and does not create a correct chain load entry to UEFI Windows 8 installs. Boot-Repair can fix that.

       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

