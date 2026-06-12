---
title: "put MBR on GPT disk, bios machine"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by boolewinklegmail. on 2016-06-11
Hello,


Background, I have a 2008 era bios-based machine that I want to upgrade/replace. It has a 500g drive.
I'm hoping to do it in two phases 
1) upgrade the disk, install a 64bit linux on it,
2) move the new disk into a new UEFI box later.


I installed a 4TB drive and installed 64bit 12.04 successfully on it, with one issue, that it still
boots off the 500g drive. The 4TB disk as a 1G /boot partion, and the remainder is a LVM
paritiion, divided into 
- 16g swap encrypted
- 25g root
- 30g to install 16.04 later 
- remainder user data, encrypted
The fstab it generated is below.
It all worked fine, except that the MBR/grub stuff went onto the 500g disk. I.e., it only boots
if the 500g disk is first, otherwise it hangs at boot. I want to be able to boot from the 4TB disk
using the current 2008 bios-based machine, and also later boot from it using a UEFI machine.


My question: is it possible to put a MBR and grub onto the new 4TB disk?
It has a generous 1G /boot partition that could be deleted and divided up
to make room (I read something about grub stage 1.5, but do not understand).


I am a programmer, but not a linux or hardware expert, please keep your reply (if any) on the simple side!


[FONT=courier new]# <file system> <mount point> <type> <options> <dump> <pass>[/FONT]
[FONT=courier new]proc /proc proc nodev,noexec,nosuid 0 0[/FONT]
[FONT=courier new]/dev/mapper/wobblygroup-root / ext4 errors=remount-ro 0 1[/FONT]
[FONT=courier new]/dev/mapper/wobblygroup-rootB /Futurelinux ext4 defaults 0 2[/FONT]
[FONT=courier new]/dev/mapper/wobblygroup-unused /Unused ext4 defaults 0 2[/FONT]
[FONT=courier new]/dev/mapper/wobblygroup-home_crypt /Users/zilla/zilla ext4 defaults 0 2[/FONT]
[FONT=courier new]# /boot was on /dev/sdb1 during installation[/FONT]
[FONT=courier new]UUID=4a096c2f-ff47-449d-b744-b37de1e0ef13 /boot ext4 defaults 0 2[/FONT]
[FONT=courier new]/dev/mapper/wobblygroup-swap_crypt none swap sw [/FONT]

---

### Post by grahammechanical on 2016-06-11
If there are two drives in a machine then LInux will see the first drive as sda (sata drive a) and the second drive as sdb (sata drive b). The Ubuntu installer defaults to installing the boot loader (Grub) onto sda. It does this even if we are installing Ubuntu onto sdb. So, at some point during installation we need to direct the installer to put the boot loader on to sdb. There is usually a panel with a drop down menu offering different locations - drives or partitions to put the boot loader in.

Now if you are sure that the 4 TB drive is sdb, then these two commands will fix things. Run from Ubuntu on the 4 TB drive.

```
sudo grub-install /dev/sdb
sudo update-grub
```

Do not forget to enter the BIOS utility to set the motherboard to boot from the 4 TB drive. Before you move this 4 TB drive into a machine with a UEFI motherboard make sure that Ubuntu is using an open source video driver. You do that in Additional Drivers. Otherwise the proprietary video driver that is being used may be incompatible with the video adapter in the new machine.

Regards.

---

### Post by boolewinklegmail. on 2016-06-11
[FONT=arial](thank you)

Tried this, it gave an error about BIOS boot partition (quoted below).  Currently reading about this.
I suppose the fix is to shrink my /boot partition and add a 1MB Bios boot partition?

[FONT=courier new]sudo grub-install /dev/[/FONT][FONT=courier new]sdb[/FONT][/FONT][FONT=courier new]
/[/FONT][FONT=arial][FONT=courier new]usr[/FONT][FONT=courier new]/[/FONT][FONT=courier new]sbin[/FONT][/FONT][FONT=courier new]/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/[/FONT][FONT=arial][FONT=courier new]usr[/FONT][FONT=courier new]/[/FONT][FONT=courier new]sbin[/FONT][FONT=courier new]/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is [/FONT][FONT=courier new]discouraged..[/FONT][/FONT][FONT=courier new]
/[/FONT][FONT=arial][FONT=courier new]usr[/FONT][FONT=courier new]/[/FONT][FONT=courier new]sbin[/FONT][/FONT][FONT=courier new]/grub-setup: error: will not proceed with blocklists.[/FONT]

---

### Post by oldfred on 2016-06-12
I have not used LVM.

But a few have posted LVM with UEFI and they have the ESP - efi system partition first, then a /boot and then the LVM all on a gpt partitioned drive.
With BIOS installs on gpt drives you must have a bios_grub partition. I started using gpt with my old BIOS only systems in 2010, and soon after planned on an UEFI system so added both the ESP & bios_grub as first two partitions on every drive, even larger flash drives.

With LVM, you would then have / & swap inside the LVM.

 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
        Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by Dennis N on 2016-06-12
> I'm hoping to do it in two phases
1) upgrade the disk, install a 64bit linux on it,
2) move the new disk into a new UEFI box later.

Realize that any OS you install now on the disk you plan to move will not be bootable in UEFI mode in the new UEFI system you plan to get. You would have to continue to boot in the same mode (BIOS) which precludes all the advantages of UEFI, or start over and make a UEFI install. Also, there is no assurance an OS on the disk will work 100% as expected on the other machine with its different hardware.

---

### Post by oldfred on 2016-06-12
While hardware, particularly video and wireless drivers can be an issue with a new system, you can convert a BIOS install to UEFI if on a gpt partitioned drive and you have the correct ESP partition for UEFI or convert to BIOS from UEFI if you have a bios_grub.

You can use Boot-Repair's advanced mode for the full uninstall/reinstall of grub.
It really is uninstalling grub-pc(BIOS) and installing grub-efi-amd64(UEFI) and changing some settings.

But with new drives and/or new systems I am more of a fan of new installs.
You should have good backups of /home which is your user settings, your data which many have in /home, and a dpkg list of installed applications. 
Then you can do a new clean install and restore from backups.

---

### Post by boolewinklegmail. on 2016-06-13
Thanks for the various advice.

In the end I decided to start over with a slightly simpler setup 
(which is also a puzzle, but separate post)

---

