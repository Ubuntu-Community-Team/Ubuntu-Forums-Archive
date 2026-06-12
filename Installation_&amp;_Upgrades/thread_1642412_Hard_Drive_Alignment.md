---
title: "Hard Drive Alignment"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by dpilot83 on 2010-12-10
I am installing a triple boot of Windows XP Pro, Windows 7 Pro and Ubuntu 10.10. I am using the Ubuntu Live CD for my partitioning needs. This is on a new 500 GB Western Digital Black (7200 RPM) hard drive. As far as I'm aware this drive is not one of the new drives that has to use the MiB alignment. I see that the partitioning tool defaults to MiB alignment. I thought this might be a problem for Windows XP Pro so for the partition that I intend to install that on I chose cylinder alignment. For the remainder of the partitions I allowed it to use the default MiB alignment. Is having two different types of alignment on the same hard drive going to cause problems? Will I be able to access data off of other NTFS partitions on the drive from Windows XP if the other NTFS partitions are aligned to MiB? Any help would be appreciated. Thanks.

---

### Post by oldfred on 2010-12-10
Do not know enough about alignment issues to help. Cannot believe it is an issue as you can install XP in any primary partition which means higher numbers. With LBA the old CHS is not really used.

But if installing 2 windows, be aware it will combine the boot into the first windows that has the boot flag (active partition). So you will be booting win7 anyway. If you install win7 second and then uninstall XP, you will break  it, as all its boot files were in the XP partition. You can only then repair win7 if it also is in a primary partition. Default installs of win7 create a separate boot/recovery partition so you can encrypt the main partition. If you create NTFS partition in advance then it will install into one partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Herman on 2010-12-10
I have Windows XP Home Edition in one of my computers and after checking to see that it did begin on the old traditional cylinder alignment, (in case I might have already tried this experiment and forgotten about it), I resized it with Maverick Meerkat's GParted.

I can confirm that Windows XP boots just as happily with a starting  sector of 2048 as it did when the partition started in sector 63, or at least mine does. 
I would need to use Windows and try it out like that for a long time to make sure there are no programs that could be affected, but I can't imagine any just off-hand. I'm not primarily a Windows user, (or at least I don't use it in my home computers), so we'll have to wait for somebody to report a problem before we'll know if any problems or issues can arise from that in long-term use.

EDIT: I also tried Windows 98 SE for booting from sector 2048 and it seems to be fine too. 
After moving the Windows 98 partition from sector 63 to start at sector 2048 instead, I ran fdisk /mbr and sys c: to get it to boot. Probably only the sys c: command would have been important though. (runs SYS.COM which will write a new boot sector and also refresh the important files in the root of drive C: that are needed for booting, which are: IO.SYS, MSDOS.SYS and COMMAND.COM).  :D

---

### Post by srs5694 on 2010-12-11
In theory, there should be no problems mixing alignment. Unfortunately, libparted-based tools (which is most Linux partitioning tools) sometimes get confused when doing resizes or creating new partitions on such disks; you can get a "can't satisfy all constraints" error when trying to create or move a partition too close to an existing boundary. Given that XP is fine with MiB alignment, I recommend sticking to that for everything. This will also guarantee no performance issues if you're mistaken about the drive using 4096-byte sectors (it's cheap insurance).

---

### Post by efflandt on 2010-12-11
I believe that partition alignment is only an issue of the BIOS of some computers for boot partitions.  I have such an HP computer from 2004 with Asus motherboard.  It will not boot to a default partition created from 10.04 or newer unless I use partman/alignment=cylinder kernel boot parameter for install, or first create partitions with gparted set to align partitions to cylinders.

Although, once an OS is running on the PC, no OS has any trouble accessing partitions with any alignment.  So it is just a BIOS boot partition issue for some older computers.

The only thing you may run across with mixed alignment is small unallocated gaps between partitions.

---

### Post by dpilot83 on 2010-12-11
Thanks for all the advice everyone. The XP Pro partition that I created by using cylinder alignment with gparted was the first partition I created on the drive and it was a primary partition. Based on this thread I went back in and resized it so that I could re-align it to MiB alignment. When I looked at the information it said that it still started at 63 though so I'm not sure if it did it right. I tried several times and was unable to get it to show anything else under alignment so I just left it that way.

I'm not really sure why, but I installed Ubuntu at that point instead of installing XP first. I usually don't do it that way but I had a reason last night, just can't remember it now. Anyways, I installed XP next which worked fine and then installed 7. Then I re-installed and updated grub and now I can boot to any of the three I choose. I haven't used XP much yet as I still need to hook up to my old hard drive with an external enclosure so I can get the drivers off of one of the partitions on that drive but it seemed to be working fine. Thanks for the help all. I'll label this thread as solved.

---

### Post by srs5694 on 2010-12-12
> **efflandt said:**
> I believe that partition alignment is only an issue of the BIOS of some computers for boot partitions.

This may be true of some very old BIOSes; there are so many that I wouldn't want to say that it's never a problem. Today, though, the issue is alignment to avoid performance problems with some types of RAID arrays and, more importantly, disks with 4096-byte physical sectors. See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for details.

> Although, once an OS is running on the PC, no OS has any trouble accessing partitions with any alignment.  So it is just a BIOS boot partition issue for some older computers.

I've never tested this, but my understanding is that some very old versions of DOS require cylinder-aligned partitions.

[quote=dpilot83]Based on this thread I went back in and resized it so that I could  re-align it to MiB alignment. When I looked at the information it said  that it still started at 63 though so I'm not sure if it did it right. I  tried several times and was unable to get it to show anything else  under alignment so I just left it that way.[/quote]

You could go to WD's Web site and download the alignment tools for Advanced Format drives. They should correctly detect whether your disk is an Advanced Format model and, if it is, realign the XP partition(s).

---

