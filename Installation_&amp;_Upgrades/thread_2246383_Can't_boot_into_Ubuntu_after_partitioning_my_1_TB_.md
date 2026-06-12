---
title: "Can't boot into Ubuntu after partitioning my 1 TB HDD"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by josh95 on 2014-09-30
First time posting to the forums, so forgive any mistakes I make.

Note: Ubuntu and my home folder are encrypted.

**My ultimate goal:** To move the /home/[user] folder from my 64 GB SSD (where my encrypted Ubuntu is installed) to my 1 TB HDD where my Windows files and profile is (not the OS, have another 240 GB SSD for the OS).
[LIST=1]
[*]This led me to partition my 1 TB HDD because it only had 1  (NTFS) partition and a 1 MB partition of unallocated space before that 1 partition. I'm new to Linux but I recalled reading (somewhere throughout my process of finishing my ultimate goal) that if I wanted to move my /home directory, I would have to move it to an ext3 partition.
[*]I partition my 1 TB HDD
[LIST=1]
[*]I get Gparted on a Live-CD
[*]Boot on this Live-CD
[*]Change 1 TB HDD by moving/resizing NTFS partition of 900000+ GB into a 750000 GB partition. This took overnight
[LIST=1]
[*]It got rid of the 1 MB unallocated partition that was before it in this process. For some reason, I had to boot from ST1000[bla bla](?) in my BIOS boot sequence in order to run Ubuntu on my 64 GB SSD, in stead of SD640GB (or something like that), which I would assume is the actual boot drive for Ubuntu. Is it possible that the 1MB on the 1 TB held the data to boot into the 64 GB Ubuntu SSD?
[/LIST]

[*]Create a 100 GB ext3 partition in front of the NTFS partition, and leave the rest unallocated.
[/LIST]

[*]Realize I can no longer boot into Ubuntu no matter what drive I select in the BIOS boot sequence.
[*]Read up in the community about Boot-Repair-Disk, get that, and try to repair.
[LIST=1]
[*]Results: [http://paste.ubuntu.com/8466179/](http://paste.ubuntu.com/8466179/)
[*]Still cannot boot into Ubuntu, and that's why I'm here
[/LIST]
[/LIST]

Thankfully, I still have Windows 7 on my computer (that's what I'm using right now) and that has been my primary OS for a while, so nothing really important is on my Ubuntu installation. I really want to try Ubuntu though, because for the few days that I was using it, it seemed really nice. I got it so I could do my class HW on it (class is Linux-based), but all of this trouble to move my /home directory to another drive when Windows 7 was much easier is really leaving a bad taste in my mouth.

Help me tell myself I'm missing something really obvious and reinforce my desire to like Ubuntu.

---

### Post by TheFu on 2014-09-30
HOME doesn't need to be ext3, it just needs to be on a file system that supports UNIX permissions. There must be 20+ viable options - ext4 is the best general purpose file system today when there aren't any specific reasons to use something else.  NTFS is a no-go for HOME, as you know.

Sorry but my FU for encrypted installs is weak - can't help anymore than that.  On systems here with encryption, we have excellent backups - to the point we are willing to wipe HDDs and start over.

---

### Post by yancek on 2014-09-30
> a 1 MB partition of unallocated space

It's either a partition or it's unallocated, not both.

> Is it possible that the 1MB on the 1 TB held the data to boot into the 64 GB Ubuntu SSD?

Pretty likely.  Give the link below a read.  I don't use GPT so don't have any idea what to do but someone else should come along.

[http://en.wikipedia.org/wiki/BIOS_Boot_partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition)

---

### Post by josh95 on 2014-09-30
Ok, thanks I'll look into that link.

EDIT: So, according to the wikipedia link: 

> [COLOR=#252525][FONT=sans-serif]The BIOS Boot partition is typically quite small. It can be as small as about 30 KiB; however, future boot loaders might require more space, so creating a larger BIOS Boot partition is advisable. Due to the [/FONT][/COLOR][1 MiB partition alignment]("http://en.wikipedia.org/wiki/1_MB_partition_alignment")[COLOR=#252525][FONT=sans-serif], policies used by most modern disk partitioning tools to provide optimum performance with [/FONT][/COLOR][Advanced Format]("http://en.wikipedia.org/wiki/Advanced_Format")[COLOR=#252525][FONT=sans-serif] disks, [/FONT][/COLOR][SSD devices]("http://en.wikipedia.org/wiki/Solid-state_drive")[COLOR=#252525][FONT=sans-serif], and some types of [/FONT][/COLOR][RAID]("http://en.wikipedia.org/wiki/RAID")[COLOR=#252525][FONT=sans-serif] configurations, 1 MiB is a logical size for a BIOS Boot partition[/FONT][/COLOR]

So, there is a very good chance that the Boot partition *was* on the 1TB HDD. Now then, the question is, how do I get that boot partition (loader, whatever it's called) back so I can boot into Ubuntu again?

> It's either a partition or it's unallocated, not both

Thanks for that clarification. That makes sense.

---

### Post by oldfred on 2014-09-30
As it says that 1MB was for partition alignment so your drive will work better if a newer 4K drive. If you moved partition all the way to the first sector you may have overwritten entire partition table. And without backup of data & partition table it may be very difficult to repair.

Best to see details. This will not show encrypted partitions correctly including swap a the tools it uses cannot parse it. If from live installer in may ask to unencrypt it or not, do not know about encryption either.

From Ubuntu live installer, install Boot-Repair when in live mode.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

---

### Post by josh95 on 2014-10-02
Everything seems so complex, and I don't really have an idea of how to fix the problem, so should I just reinstall for the 4+th time? Will that fix it and should I be able to boot into Ubuntu with the 1 TB hard drive being partitioned as it is?

Also, did I kind of ruin my 1 TB hard drive by moving the partition to the first sector? Seems fine, but you said the partition table is most likely deleted... is that very bad?

---

### Post by oldfred on 2014-10-02
Lets see where you are at. Post link to the summary report from Boot-repair.

Did you have any important data not backed up on the 1TB drive.
Without partition table it will be difficult if not impossible to read data. But system really should not have let you move it that far. Report should tell us where you are at.

---

### Post by josh95 on 2014-10-04
Sorry it took a while. Here is the summary: [http://paste.ubuntu.com/8492874/](http://paste.ubuntu.com/8492874/)

---

### Post by oldfred on 2014-10-04
Your sda is a new 4K drive, but has the old start sector of 63. That was common with XP and older versions of Linux tools. Windows 7 changed to use sector 2048 and a bit later Linux also converted to start first partition at sector 2048 like your sdb & sdc drives.

If sda1 is just a data partition you may be able to move its start. Not sure of best way, but generally better to use Windows tools for Windows. And you will have to run chkdsk on it afterwards, so make sure your Windows is working or have the Windows repairCD or flash that you make from your Windows install.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Your install in sdb, is encrypted which uses full drive LVM. You cannot use gparted or standard partition tools with LVM, but must use LVM tools.

And it does not look like you installed its grub to the MBR of sdb so you can boot it. I think Boot-Repair may need you to unencrypt your install, so it can correctly install your grub boot loader to the MBR of sdb. Do not let it auto install or put grub in every MBR. And with LVM you have the separate /boot partition and may need to check that also.
      
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by josh95 on 2014-10-04
Ok, thanks. I'll look into all of this later since it looks pretty in-depth and don't have time at the moment to fix it.

---

