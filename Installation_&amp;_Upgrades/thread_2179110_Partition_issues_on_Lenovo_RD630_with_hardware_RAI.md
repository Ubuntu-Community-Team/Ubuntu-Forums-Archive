---
title: "Partition issues on Lenovo RD630 with hardware RAID"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by jackpark on 2013-10-06
Doing install of 64-bit 12.04.3 on an RD630 with 4 1tb disks. RAID5 was preconfigured in the hardware with the RD630 configuration program. I am operating on the theory that simply building a simple linux partition during "expert" installation would leave the system handled by the hardware RAID. I get this screen option in partitioning:
[FONT=arial]SCSI1 (2.0.0) (sda) - 3.0 TB LSI MR9260-8i[/FONT]
[FONT=arial]        1.0 MB   Free space[/FONT]
[FONT=arial] #1   1.0 MB   K biosgrub[/FONT]
[FONT=arial] #2    2.9TB        ext4[/FONT]
[FONT=arial] #3    1.0 GB   F  swap        swap[/FONT]
[FONT=arial]         67.7GB  Free space

Where I downgraded swap to 1.0 GB. When I save to continue, I get the famous "No Root System Selected". I return and select #2, which is premarked "do not use".  I have many options from which to choose. I chose "use as physical volume for RAID". Still no root system selected.  I note at this time that neither #1 (biosgrub) nor #2 (now "raid") is "bootable".

Are there links to explain the details of my particular situation, or good suggestions of how to solve this one?

Many thanks
Jack
[/FONT]

---

### Post by oldfred on 2013-10-08
The bios_grub is not a boot partition, but just some unformatted space in a gpt partitioned drive for grub to put core.img.
While gpt has a protective MBR, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

Did you install with a Desktop version or a sever version? Desktop does not have the RAID drivers you need to install grub2's boot loader into the RAID root.

You need a desktop or live version if you did use server version which is not a live version.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

