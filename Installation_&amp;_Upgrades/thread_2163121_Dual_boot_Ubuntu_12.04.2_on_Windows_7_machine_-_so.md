---
title: "Dual boot Ubuntu 12.04.2 on Windows 7 machine - some issues"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by tapasray on 2013-07-17
After botching an Ubuntu install on my laptop in 2009, I waited until now to try it again. This time it's a Sony VAIO laptop running Windows 7 Starter Edition, and I have sort of succeeded, but with some issues.

1. The hard drive (320 GB) originally (in Win 7) was NTFS and had no partition - it was just 'C'. While installing Ubuntu from a pen drive, it was split up into two large  partitions and two or three smaller ones ('swap', etc). Now, when I have Win 7 open, I can see only one of the large partitions and when Ubuntu is open, I see only see the other one. Saved documents, thankfully, are visible in both, but in Ubuntu accessing them means clicking through several directory levels. This is what I want to do for optimal use of disk space, as well as convenience: 

Place Windows in a smallish partition of its own, say 20 GB, Ubuntu in another partition of about 20 GB, and my data in a third partition of about 270 GB. I have installed Gparted in Ubuntu, but don't know how to go about it and am afraid of wiping out data. 

2. Instead of the Windows/Ubuntu dual boot screen, the first black screen I get has 7 options. I have to click on one of the Windows options there to get the dual-boot screen. How can I eliminate the first (7-option) screen/step?

Will much appreciate some help here!

---

### Post by oldfred on 2013-07-17
Is this a full partitioned install, not wubi? As if you get grub first it should give a choice for either Ubuntu or Winows. If wubi you get the Windows BCD menu, then you get a grub menu.

You should be able to shrink Windows from inside Windows with it disk tools and reboot so it can run chkdsk. Just do not make too small as NTFS partitions need about 30% free space to work well. At 10% free they just about stop working and that is a main reason users complain Windows is slow.

I typically install Ubuntu in 25GB / (root) partition but have all data in other drives and both NTFS and Linux formatted data partitions.

Post these:

# to see all partitions
sudo parted -l
#mount the Windows NTFS partition as this command only shows mounted partitions
df -h

---

### Post by tapasray on 2013-07-20
Thanks, oldfred. I went into Windows and shrank my C drive as you suggested, then created a new drive with the "unallocated space" freed up that way. But when I try to restart to complete the process, the machine refuses to boot. I get a black terminal screen with two lines - 'error: unknown filesystem' and 'grub rescue>'. What should I do now?

---

### Post by oldfred on 2013-07-20
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

