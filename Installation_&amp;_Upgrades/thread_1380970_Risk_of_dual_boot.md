---
title: "Risk of dual boot?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Biddlesby on 2010-01-14
Hi all. I have a laptop with pre-installed vista and would like to get Ubuntu running along side. Following [a guide](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) I shrunk my windows partition with Vista,  and went into the Ubuntu setup. But the free space was `unusuable'.

The laptop came with the following partitions:

10gb   - EISA Configuration
111gb - NTFS (System, Boot, Page file, Active, Crash Dump, blah blah blah)
107gb - NTFS (Primary Partition) - this has all my media on it
3.5gb  - EISA Configuration

I shrunk the system parition down by 12gb and now that is down as 'unallocated'. Don't really know what the 10gb and 3.5gb partitions are for. I've also got an 80gb external HDD formatted to NTFS.

I have heard that you are only allowed 4 partitions, is this true, and what is the reason?

---

### Post by presence1960 on 2010-01-14
> **Biddlesby said:**
> Hi all. I have a laptop with pre-installed vista and would like to get Ubuntu running along side. Following [a guide](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) I shrunk my windows partition with Vista,  and went into the Ubuntu setup. But the free space was `unusuable'.

The laptop came with the following partitions:

10gb   - EISA Configuration
111gb - NTFS (System, Boot, Page file, Active, Crash Dump, blah blah blah)
107gb - NTFS (Primary Partition) - this has all my media on it
3.5gb  - EISA Configuration

I shrunk the system parition down by 12gb and now that is down as 'unallocated'. Don't really know what the 10gb and 3.5gb partitions are for. I've also got an 80gb external HDD formatted to NTFS.


I have heard that you are only allowed 4 partitions, is this true, and what is the reason?

You are at the limit of 4 partitions. All four are primary. You can get around this by backing up your media partition, then deleting that partition. Then using gparted from the Ubuntu live Cd or [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") create an extended partition from all the unallocated space. You can then create as many logical partitions inside the extended partition that you wish- the only constraint on that is how much space allotted to the extended partition. You can then create a logical partition inside the extended and restore your media to that. Then you can use the rest of the unallocated space to install Ubuntu.

See here for more details about partitions/partitioning: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by darkod on 2010-01-14
I don't know the reason, but yes, you are allowed only 4 partitions. They can either be primary or extended, but a total of 4 is max.

Within an extended partition you can have up to 16 logical ones, which helps to overcome the 4 partitions limitation.

However, if your current 4 partitions are all primary, and it seems they are, you can transform any into extended without removing the data, deleting the partition, creating extended in its place, and then putting the data back.

If your 4 partitions are primary, ubuntu can't do anything with the 12GB unallocated space you created for it.

The 10GB partition sounds like recovery/restore partition and the 3.5GB like some utility partition. Usually you would need the restore partition to restore your windows (although I find them useless) but the utility partition has no big use. But that's up to you if you would consider deleting it.

---

### Post by audiomick on 2010-01-14
Hallo Darko.

> **darkod said:**
>  you can transform any into extended without removing the data, deleting the partition, creating extended in its place, and then putting the data back.

I am pretty sure you mean "you can not transform any...", don't you?

---

### Post by Sef on 2010-01-14
>  Within an extended partition you can have up to 16 logical ones, which helps to overcome the 4 partitions limitation.

Actually it is [64 logical partitions]("https://lists.ubuntu.com/archives/ubuntu-users/2006-April/073303.html"), but sometimes you are limited to 16.

---

### Post by darkod on 2010-01-14
> **audiomick said:**
> Hallo Darko.



I am pretty sure you mean "you can not transform any...", don't you?

Yes, absolutely. Sorry.
You CAN NOT transform.

---

### Post by meierfra. on 2010-01-14
> You CAN NOT transform.

You can use fdisk, or sfdisk, to create an extended partition  and transform  primary partitions to logical partitions without touching any data. Although depending on the current partition table you might have to shrink one of the primary partition by just the tiniest  bit.

---

### Post by Biddlesby on 2010-01-14
Ahh that sounds like too much playing around. Disk Manager won't let me delete the partition, should I load up gparted to do the job?

Incidently, how would I access the system restore partition, if I wanted to?

---

### Post by Biddlesby on 2010-01-14
Aha, have done it using the DiskPart command line.

[http://www.mydigitallife.info/2008/02/29/delete-and-remove-to-unlock-eisa-hidden-recovery-or-diagnostic-partition-in-vista/](http://www.mydigitallife.info/2008/02/29/delete-and-remove-to-unlock-eisa-hidden-recovery-or-diagnostic-partition-in-vista/)

---

### Post by darkod on 2010-01-14
> **Biddlesby said:**
> Ahh that sounds like too much playing around. Disk Manager won't let me delete the partition, should I load up gparted to do the job?

Incidently, how would I access the system restore partition, if I wanted to?

Gparted is much better tool and you can always use it from the ubuntu cd with Try Ubuntu option, or the Gparted LiveCD.
But even windows disk management not allowing you to delete the partition is odd. Maybe because of some utility.

For the restore partition, it depends, but usually you would even have a button you can hit during startup, like F2, F4, what ever, that starts the restore partition.

Depending on the situation grub2 from ubuntu might pick it up too so don't be surprised if you see two windows option in the grub menu, one will be the OS, the other the restore partition.

---

### Post by darkod on 2010-01-14
> **meierfra. said:**
> You can use fdisk, or sfdisk, to create an extended partition  and transform  primary partitions to logical partitions without touching any data. Although depending on the current partition table you might have to shrink one of the primary partition by just the tiniest  bit.

Ooopss.... :oops:

---

### Post by Biddlesby on 2010-01-14
Ah yes, GRUB has picked 'er up.

All installed! Thanks.

One more thing (I'll say this in a whisper...) how do I make Vista the default operating system?

---

### Post by darkod on 2010-01-14
> **Biddlesby said:**
> Ah yes, GRUB has picked 'er up.

All installed! Thanks.

One more thing (I'll say this in a whisper...) how do I make Vista the default operating system?

There is package called startupmanager. In terminal just do:
sudo apt-get install startupmanager

I'm not using it but I think it shows up in System-Administration. With that you can select the timeout for the grub menu and the default OS.

Another option is directly in grub2 config file with:
sudo gedit /etc/default/grub

The value GRUB_DEFAULT needs to be changed to something like "Windows Vista loader on /dev/sda1" but you need to use the exact title as in the grub menu. Exactly!

After the change, save and close the file. In terminal execute sudo update-grub.

---

### Post by Biddlesby on 2010-01-17
Excellent, thanks :)

---

