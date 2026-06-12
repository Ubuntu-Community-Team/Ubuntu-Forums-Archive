---
title: "Created 6 primary partitions"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by wonko on 2011-02-07
I seem to have created 6 primary partitions (see gparted screenshot) - is this possible or am I misreading gparted? Should I repartition - am I in danger of damaging my harddrive?

About my setup: I run Kubuntu 10.10, the hd is a Western Digital Caviar Green 2TB. The first 5 partitions were created during installation, while the last one I just created with gparted. Now it seems I can't create any extended/logical partitions, but any number of primary partitions.

---

### Post by oldfred on 2011-02-07
Did you select gpt not MBR(msdos)? gpt only uses primary partitions.

I installed gpt on a small drive just to test it and it works just fine (now). I orginally had issues with booting another drive that was msdos but that has been fixed by grub2.

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

---

### Post by srs5694 on 2011-02-07
I agree with oldfred; you've almost certainly got a GPT disk there. You can tell what you've got by downloading the latest version of GPT fdisk (gdisk) from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) (get the .deb file for your architecture -- probably i386 or amd64), installing it by double-clicking the file, opening a Terminal, and typing:

```

sudo gdisk -l /dev/sda

```

The result will include something like the following:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

This particular pattern indicates a normal GPT disk. If the "MBR" line reads "MBR only", then you've got a Master Boot Record (MBR) disk, and a mystery. Other patterns could indicate other things. For instance, if the "APM" line reads "present," it means you've got an Apple Partition Map (APM) disk. This is most likely if you're using a PowerPC Mac. Post those lines if you need help interpreting them.

I also concur with oldfred that you should create a BIOS Boot Partition. I'd put it at the very end of the disk to keep it out of the way, then re-install grub ("sudo grub-install /dev/sda"). This will reduce the odds of your having boot problems in the future.

One other comment, unrelated to the partition table type: Many recent Western Digital disks use Advanced Format technology, which means the disks use 4096-byte sectors but lie to the computer and claim to use 512-byte sectors. This lie helps work around certain problems, but it creates others. In particular, you have to be very careful about how your partitions are aligned; they must be aligned on 4096-byte (8-sector) multiples. Most modern partitioning tools align to 1-MiB (2048-sector) multiples, which is fine for this; but there's a chance your disk is partitioned improperly. You can check this with the gdisk output; just check that all the partition start points are on multiples of 8. For instance:

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40             439   200.0 KiB   EF02  BIOS boot partition
   2             440          410039   200.0 MiB   EF00  EFI System
   3          410040          819639   200.0 MiB   0700  Linux /boot (unused)
   4          819640         1229239   200.0 MiB   0700  Linux /boot (unused)
   5         1229240      1953525134   930.9 GiB   8E00  Linux LVM

```

That's taken from one of my systems. Note that all the partitions have values under the "Start (sector)" column that are multiples of 8. If your disk *isn't* properly aligned, it might be OK if your disk happens to not use Advanced Format technology. You'll have to check the exact model number on WD's Web site to find out what you've got, or look at the drive physically (they've got notices on them about this issue).

---

### Post by wonko on 2011-02-07
Thanks a lot guys! Gdisk indicates I'm using normal GPT, and luckily all partitions are also 8-sector-aligned :) I'm guessing the Kubuntu installer chose this because I have a 2TB disk. I wish it'd informed me better though - I was just about to reformat my drive...

---

### Post by srs5694 on 2011-02-07
GPT isn't really necessary for 2 TB disks (2 TiB is the cutoff point, and 2 TiB = ~2.2 TB). The cutoff is simple binary problem; it's not like performance degrades as you approach the limit. Thus, I'm not sure what the reasoning would be to go to GPT on disks smaller than when it's necessary, but it's certainly possible that the installer did so. If your system is booting, there's absolutely no reason to switch to MBR; GPT offers a number of minor advantages, the most important of these being the lack of the primary/extended/logical distinction. There are probably three or four posts a week on this site alone relating to problems caused by that 20-year-old hack. You won't have such problems on your new disk, so that's a plus!

---

