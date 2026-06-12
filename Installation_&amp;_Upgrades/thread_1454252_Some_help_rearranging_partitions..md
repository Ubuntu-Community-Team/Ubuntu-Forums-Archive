---
title: "Some help rearranging partitions."
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Totally-Lemonified on 2010-04-14
Hello!  I'm wondering how I can rearrange my partitions into one or two main partitions.  My boot partition is part of an extended partition and I'd much rather it was a separate partition in itself.  All help is really appreciated!  Also, I have gold stars :KS

[IMG]http://imgur.com/pXmlw.png[/IMG]

---

### Post by Objekt on 2010-04-14
Offhand, I don't know of any way to remove a logical partition from its containing extended partition, at least not using gparted.  You could make your boot partition completely occupy the extended partition it is in, but that's not quite what you wanted to do, is it?

---

### Post by Totally-Lemonified on 2010-04-14
Not really but I'd settle for that, as long as I could increase the capacity of the extended partition!

---

### Post by srs5694 on 2010-04-14
Two thoughts:

First, you can increase the size of an extended partition; however, to do so all of its contained logical partitions must be unused. Thus, you'll need to boot an emergency disc to do the job, and you may need to manually disable swap space when you do this.

Second, if you intend to use the disk only for Linux, or perhaps for Linux and certain other non-Windows OSes, you could [convert the disk from Master Boot Record (MBR) form to GUID Partition Table (GPT) form.](http://www.rodsbooks.com/gdisk/mbr2gpt.html) Since GPT does away with the annoying primary/extended/logical distinction, you'll have fewer problems with moving or resizing partitions. If you do this, though, you'll need to re-install your boot loader. If you try it, be sure to create a new [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) (type code EF02 in the [GPT fdisk](http://www.rodsbooks.com/gdisk/) tool you can use for the conversion) of 100KiB-1MiB; this partition holds part of the GRUB 2 boot loader, helping its reliability.

---

### Post by Totally-Lemonified on 2010-04-14
> **srs5694 said:**
> Two thoughts:

First, you can increase the size of an extended partition; however, to do so all of its contained logical partitions must be unused. Thus, you'll need to boot an emergency disc to do the job, and you may need to manually disable swap space when you do this.

Second, if you intend to use the disk only for Linux, or perhaps for Linux and certain other non-Windows OSes, you could [convert the disk from Master Boot Record (MBR) form to GUID Partition Table (GPT) form.](http://www.rodsbooks.com/gdisk/mbr2gpt.html) Since GPT does away with the annoying primary/extended/logical distinction, you'll have fewer problems with moving or resizing partitions. If you do this, though, you'll need to re-install your boot loader. If you try it, be sure to create a new [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) (type code EF02 in the [GPT fdisk](http://www.rodsbooks.com/gdisk/) tool you can use for the conversion) of 100KiB-1MiB; this partition holds part of the GRUB 2 boot loader, helping its reliability.
I like the sound of the second option but it sounds quite complicated and I'm not that experienced.  How long would this take?  Also, would there be any data loss?

---

### Post by srs5694 on 2010-04-14
> **Totally-Lemonified said:**
> I like the sound of the second option but it sounds quite complicated and I'm not that experienced.  How long would this take?  Also, would there be any data loss?

The conversion itself is near-instantaneous; no filesystem data need be touched, and the computations required to convert the MBR data structures to their GPT equivalents are trivial. Most of the time spent on the conversion will be spent just checking the partition table data to be sure it all looks sane.

The entire process is:


[list=1]
[*]Download the GPT fdisk package. (The [Sourceforge downloads page](http://sourceforge.net/projects/gptfdisk/files/) has both x86 and x86-64 [amd64] Debian packages, which should install fine in Ubuntu.) I believe that double-clicking the file will install it. If not, "sudo dpkg -i gdisk_0.6.6-1_amd64.deb" (or i386 rather than amd64, depending on your platform) in a text-mode shell will do the job.
[*]Open a text-mode shell (Konsole, Terminal, xterm, or whatever).
[*](Optional) Type "sudo sfdisk -d /dev/sda > sda-backup.txt" to back up your current partition table in case of trouble.
[*](Optional) Copy sda-backup.txt to a removable USB flash drive, a CD-R disc, or some other disk other than the one you're modifying.
[*]Type "sudo gdisk /dev/sda" to launch the main GPT fdisk program.
[*]Verify that you're working on the correct disk and that the data look sane by typing "p" and examining the results.
[*](Optional) Run a verification by typing "v". The program will report any problems (overlapping partitions, etc.).
[*](Optional) Create new partition(s). If nothing else, I recommend creating a BIOS Boot Partition (type EF02 in GPT fdisk) of 100KiB-1MiB. Note that any partitions you create will not include filesystems, so you'll have to create your filesystems afterward (probably after you reboot) using mkfs. The BIOS Boot Partition doesn't hold a filesystem; GRUB writes to it directly.
[*]Type "w" to save your changes.
[*]Re-install GRUB. Typing "sudo grub-install /dev/sda" should do this.
[*]Reboot to test that everything's fine. If you want to resize or move partitions, you can now use GParted to do the job. (It should detect that the disk now uses GPT and react appropriately.)
[/list]


Whenever you adjust partition tables, there's a risk of data loss; however, the risk when converting from MBR to GPT is probably lower than the risk when resizing a filesystem or moving a partition, since the amount of data that must be changed is much less. Since I wrote GPT fdisk, I've done this hundreds of times myself, and I've only had problems with pre-release development code. IIRC, I've only received one report of data loss from a user, and that person ignored glaring warning messages in the program when converting a disk type that was, at the time, unsupported. (Current versions would work with that hard disk.) You can abort at any time by typing "q"; as with fdisk, this drops you out of the program with your disk untouched. Steps 3 & 4 in the above procedure exist to enable recovery in case you run into problems. You can use the 'z' ("zap") option on the GPT fdisk experts' menu to wipe out the GPT data structures and then use sfdisk to restore the original MBR partition table.

---

