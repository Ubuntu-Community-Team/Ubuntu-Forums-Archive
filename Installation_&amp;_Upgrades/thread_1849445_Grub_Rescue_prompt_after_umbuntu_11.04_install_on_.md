---
title: "Grub Rescue prompt after umbuntu 11.04 install on new 3TB disk"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by razor_maze on 2011-09-24
I just don't understand why I can't successfully boot after I install Ubuntu 11.04 on a brand new systems that I put together.  No other OS was ever loaded, everything including the Hitachi 3TB SATA hard drive is brand new.  After I install Ubuntu 11.04 and then restart, the system comes back with:

- error out of disk
- grub rescue

The default Ubuntu installation partitions the 3TB disk like this: [ 1MB BIOS boot partition | linux ext4 | swap ]
I've noticed that /boot/grub is almost empty, containing only 2 files: gfxblacklist.txt and grubenv

On another (older HW) Ubuntu 11.04 system I have the disk is partitioned like this: [ bootable ext4 linux | swap ] and it works just fine.  It's /boot/grub is filled with files.

This has really got me baffled.  I've never had a problem loading Ubuntu on any system before.  Does anyone have advice?

---

### Post by oldfred on 2011-09-24
Since it is 3TB, you have gpt not MBR(msdos) partitioning. Part of grub intalls to the bios_grub partition. But if your /boot/grub is not full of files it seems it did not install correctly.

Is this drive in a new system? If so are you booting with UEFI or BIOS?

With very large drives it is often better to keep system partition small (20-30GB) and let your /home or other data partitions use the rest of the drive.

Post this from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by srs5694 on 2011-09-24
> **oldfred said:**
> Post this from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.


Also, when you boot the live CD, launch a Terminal window and type:

```

dmesg | grep EFI

```

If you get few or no lines of output, your system booted in BIOS mode. If you get dozens of lines of output, mostly referring to memory settings, then you booted in EFI mode. Knowing which mode you used is critical to properly resolving this problem.

---

### Post by razor_maze on 2011-09-24
[FONT=monospace]I didn't get any output from the "dmesg | grep EFI" command so I assume I'm in BIOS mode.

I will test carving up the drive to make the partitions smaller.  I was hoping when i bought the 3TB drive that I wouldn't have to do that though.  I guess another solution might be to put a small drive in the system and use the 3TB drive as a data drive.
[/FONT]

---

### Post by srs5694 on 2011-09-24
There may be a 2 TiB limit in the BIOS or boot loader chain. (I've seen conflicting claims on this, but my limited tests suggests that a 2 TiB limit *does* exist in GRUB 2.) Thus, if your kernel happens reside above the 2 TiB mark on your hard disk, your system wouldn't boot.

I recommend partitioning like this:


[list]
[*]Create a ~200 MiB [EFI System Partition (ESP),](http://en.wikipedia.org/wiki/EFI_System_partition) just in case you need it in the future. If you use GParted to partition, make it FAT32 and give it the "boot flag." Make it the first partition on the disk.
[*]Create a 1 MiB [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) immediately after the ESP. Don't create a filesystem on it, and in GParted, give it a "bios_boot flag."
[*]Create a 200-500 MiB ext2fs partition as a Linux /boot partition. Place this immediately after the BIOS Boot Partition. Splitting off /boot may not be strictly necessary, but I'm advising playing it safe by keeping this partition *very* early on the disk.
[*]Create a 10-25 GiB partition to serve as a Linux root (/) partition. Use whatever Linux filesystem you like on it -- probably ext4fs. Given your disk size, I'd go for a 25 GiB size.
[*]Create a swap partition that's ~1.2x the size of your computer's RAM.
[*]Dedicate the rest of your disk space to a /home partition.
[/list]


Once you've created the partitions, start the Ubuntu installer. When you get to the question about how to partition, select "other." You'll then have to identify how to use each of the partitions. You can ignore the ESP and the BIOS Boot Partition, but you'll have to set mount points for the root (/) and /home partitions. I don't recall if the Ubuntu installer will pick up the swap space automatically or if you'll have to explicitly mark it as swap space at this stage.

Everything should install normally from this point. If not, post back with details about what went wrong.

---

