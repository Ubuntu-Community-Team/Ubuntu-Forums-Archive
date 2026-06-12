---
title: "Installing Ubuntu 14.10 with BTRFS RAID-5 - installing GRUB?"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by victorhooi on 2015-02-01
Hi,

I'm trying to install Ubuntu 14.10 Server on a Dell R610 with three 250GB SATA drives.

The Ubuntu installer doesn't seem to support BTRFS RAID modes out of the box, so I had to create these manually using a console in the installer.

Firstly, I created a BTRFS RAID-5 array like so:

```
mkfs.btrfs -d raid5 -m raid5 /dev/sda /dev/sdb /dev/sdc
```

I then issued a:

```
btrfs device scan
```

However, the installer didn't seem to pickup the BTRFS partitions, even with the device scan - it said there was no filesystem on those disks.

I then rebooted the computer, and started the Ubuntu installer again - this time, it did pickup the drives, and I selected to use one of those disks as "/" (which should pickup the whole array), and to not erase those disks and use them as is.

My first question is - is there a way I could have gotten the Ubuntu installer to pickup the BTRFS partition the first time around?

Secondly, the installer complained about the lack of a swap device - what alternate partitioning schemes would you have recommended, in order to also include a swap device whilst still using BTRFS RAID-5?

Should I have created a swap partition on one of the drives? But then how will that work with the drives not being equal sizes now?

Also, apparently BTRFS doesn't support swap files ([https://wiki.archlinux.org/index.php/Btrfs#Swap_file](https://wiki.archlinux.org/index.php/Btrfs#Swap_file)).

Finally, third question - the installer finally failed at the end, with installing the GRUB installer:

```
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the GRUB boot loader on a hard disk
```

I'm guessing this is something to do with my partitioning here? Any ways around this?

Regards,
Victor

---

### Post by grahammechanical on 2015-02-01
Have you read this wiki page?

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

> [COLOR=#333333][FONT=Ubuntu]As of 11.04, it is possible to use only btrfs file systems with the caveat that grub **'MUST NOT**' be installed to the boot sector of the btrfs volume containing /boot. See also [Ubuntu Grub2 Bug 757446]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/757446") and [Ubuntu Grub2 Bug 759772]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/759772"). You must install it to either the parent (sda rather than sda1; MBR/Reserved Sectors) **'OR**' use a dedicated /boot partition as described in the forum post below.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]When installing Ubuntu in one large btrfs-Partition without an extra boot-partition, take care to keep about 1 Mib space free at the beginning of the disk. This is possible using the partition manager in the Ubuntu installer. When there is not this space, the installer fails at the end when trying to install Grub![/FONT][/COLOR]


I experimented a little nit with installing desktop Ubuntu on a btrfs partition and I found that without the 1 MiB unallocated space at the beginning of the hard disk the installation of Grub would fail.

Regards.

---

### Post by victorhooi on 2015-02-02
Aha, so leave 1MB free at the beginning of the drive. Fair enough, I'll try that on the next install.

The heading before the paragraph you quoted says "Fresh Install on 11.04 Natty" - so this is from April 2011. I would have thought a lot changed had changed then, in terms of Ubuntu and BTRFS, and booting? Or not?

---

### Post by MAFoElffen on 2015-02-02
That was on just btrfs as a filesystem. not on btrfs RAID, but:
[https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)
[https://btrfs.wiki.kernel.org/index.php/RAID56](https://btrfs.wiki.kernel.org/index.php/RAID56)

The btrfs project's own wiki says that by the latest status, that btrfs RAID 5/6 is "mostly" working... and their quoted:
> 
Raid 5 and Raid6:
Parity RAID (RAID 5 and RAID 6) are not currently complete, and have significant problems with recovery from the loss of a device. They should not be used for anything other than testing purposes.


---

