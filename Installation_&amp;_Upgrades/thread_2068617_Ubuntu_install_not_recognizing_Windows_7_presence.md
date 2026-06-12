---
title: "Ubuntu install not recognizing Windows 7 presence"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by rkashby on 2012-10-09
Just bought a Lenovo ultrabook with Windows 7 pre-installed. The "disk" storage is solid state.

Tried to install Ubuntu 12.04 in its own partition, so that I can dual-boot. (installing from a DVD on an external DVD drive.)

Ran into an immediate problem: The installation process did not recognize that Windows 7 was already installed, so it did not ask me what to do. It just went directly to the screen that should show the partitions already there--but it showed NO partitions present.

I cancelled the install and booted back into Windows 7 and got into disk management. It showed two "disks": Disk0 and Disk1.

Disk0 is 8.0 GB and is described as a "Hibernation partition."

Disk1 has four partitions:

1. "SYSTEM_DRV", 200MB, NTFS, "System, Active, Primary Partition"
2. " Windows7_OS (C)", 402GB, NTFS, "Boot, Page File, Crash Dump, Primary Partition"
3. "LENOVO (D)", 25GB, NTFS, "Primary Partition"
4, (unnamed), 19.34GB, "OEM Partition"

As I said, the Ubuntu 12.04 install process doesn't recognized the presence of Windows 7. The above information from Windows 7 disk management is just FYI, in case it is useful information.

Does anyone know why the Ubuntu install does not see Windows 7? And does anyone know what I can do about it?

Thanks very much.

---

### Post by darkod on 2012-10-09
In this type of setup, usually both disks are set up in sort of a raid. I guess that's why it wasn't detected properly.

On top of that, it seems Disk1 already has the maximum 4 primary partitions created, so you can't create any more partitions.

You can create a set of recovery DVDs from the recovery software, after which you don't need partition #4 and can delete it and use that space.

But in any case you need to consider whether you will break the "connection" between the disks or not. From cases reported here, it seems you will not be able to install unless you break them up. But it might be different with your machine.

---

### Post by rkashby on 2012-10-09
Hello Darkod,

I don't really understand the part of your reply about breaking the connection between the disks.

I do remember that when I booted from the installation CD and had to choose where to boot from, the descriptions of the disk included the word "RAID."

Can you explain what you mean by breaking the connection between the disks? I am also concerned about whether I can set up dual boot safely.

Is there something about this laptop that will prevent me from dual-booting Windows and Ubuntu? That would be upsetting. I have been using Ubuntu (only) for four years, but for this new laptop I wanted to set up dual booting because I need MS Office.

---

### Post by darkod on 2012-10-09
I can't be sure, it depends on the machine. I only know what has been said here on the forum.

It seems this kind of setup is something called Intel Rapid Storage Technology, where they use the small SSD as a fast storage/hibernation disk. People with this setup have said that they couldn't manage to install the dual boot until they deactivated IRST in windows first, then in BIOS changed sata mode from RAID to AHCI, and then removed the meta data from the disks using the dmraid commands.

From what has been mentioned, windows will keep on working, the procedure doesn't mess up windows. But the way it works might be little different, not using this fast storage. And on your machine it might create problems, or not. I can't really say 100% so I can't tell you to do this or that.
I only mentioned what I have seen here.

See first if this is IRST on your machine and then do some google research about the dual boot on these machines. If you like what you read, go for it. If not, sorry, it seems you have no options but to return the machine.

Unfortunately these days manufacturers and retailers seem to think you don't deserve to know exactly what you are getting, and any limitations the machine comes with. Of course, they want you to use windows only.

---

### Post by rkashby on 2012-10-09
One further question:

If I do have to return this PC and buy another one, is there something I can look at on the PC in the store BEFORE I buy it and bring it home, to make sure it has the type of disk storage I need in order to be able to dual boot Windows and Ubuntu?

Thanks very much.

---

### Post by darkod on 2012-10-09
I think asking the staff should be enough, they wouldn't/shouldn't lie to you when asked directly. They just don't advertise this setups, but should tell you if you ask directly.

As long as there is only one hdd (or ssd but they cost much and have little capacity), without any hdd/ssd hybrid combination, you should be OK.

Hopefully you won't run into someone willing to help but not knowing what he/she is selling you. :)

---

### Post by rkashby on 2012-10-09
Do you know if this storage configuration would be a problem if I just installed Ubuntu 12.04 in place of Windows 7--wiping out Windows 7--and then used VirtualBox to run Windows 7 virtually?

I guess I would have to buy Windows 7--I don't know if it is possible to make a copy of the pre-installed version and then install it in VirtualBox.

Thanks very much.

---

### Post by darkod on 2012-10-10
You can make a backup using the built-in win7 backup software. Also create a rescue cd which can boot your computer and restore the backup to a partition you select. It can also help with bootloader restoring when you don't have full win7 media.

Making a backup like this is much better than the factory recovery partition since it restores your own backup with your programs and data, and the recovery partition deletes everything and restores the factory image.

You paid for a license and make sure you don't lose windows. Make the backup first, later you can make the computer ubuntu only if you want. You can always restore the backup if you decide to and you have your licensed win7 again.

PS. As for the storage configuration, I don't think it would be a problem for ubuntu only. Just use the alternate cd to install since it handles raid better.

---

