---
title: "Boot ARM .img installer in QEMU?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by Michael Crawford on 2010-02-08
The Karmic installers for ARM CPUs are .img files that are meant to be written directly to Flash media, rather than .iso files that are meant to be burned to CD.

I'd like to run the ARM port of Karmic under the QEMU hardware emulator.  This should be possible, because the .img files are sector-for-sector images of a hard disk drive.

But when I try, I get a panic because the kernel can't mount the root filesystem.

I think the problem is that hard drives are provided by QEMU by emulating an IDE controller, whereas the ARM .image files are meant to be run from a USB stick.  Those are accessed via SCSI rather than IDE.

Perhaps my problem is that the kernel I'm using with QEMU doesn't contain an IDE controller.

It appears that QEMU doesn't provide a SCSI emulation, just IDE.

An alternative would be to convert the .img installer file to a *bootable* CD-ROM image.  Is there a way I can do that?

Here is my command line:

```
$ qemu-system-arm -M versatilepb -kernel ~/Documents/Kernels/ARM/vmlinuz-2.6.28-versatile -hda ubuntu-9.10-desktop-armel+dove.img -m 256M -append "root=/dev/sda1 rw"
```It doesn't work to say "root=/dev/hda1 rw" - it still can't find the root filesystem.

Thanks for any insight you can give me. -- Mike

---

### Post by Michael Crawford on 2010-02-08
nrg2iso will convert .img files to .iso files.  I was able to boot off the resulting iso, but still cannot mount root.

I just now noticed this message, just before my panic:

[quote]VFS: Cannot open root device "hda1" or unknown-block(2,0)
Please append a correct "root=" boot option; here are the available partitions:
0800 665140 sda driver: sd[quote]

I'm pretty sure the ARM kernel doesn't contain an IDE driver.

That "665140" in the available partitions line looks suspiciously close to the size of the iso file, which suggests that the kernel is seeing it through the SCSI driver, but I'm not able to mount it.  Using "root=/dev/sda1" doesn't work.

---

### Post by Michael Crawford on 2010-02-08
I wasn't quite right about the .img format.  It is indeed a sector copy of a physical drive, but not a Linux drive.

There is a Master Boot Record boot block and partition map, then a FAT filesystem.  On the FAT filesystem is a single file containing the Linux image, and the SYSLINUX software.

What SYSLINUX does is boot Linux out of a file on a FAT volume.

This is similar to the ISOLINUX that is used to make bootable Linux CD-ROMs.

I have had no luck getting QEMU to boot the .img directly.  I think it might work if I could get that Linux filesystem image off of the FAT volume, then construct a bootable disk image out of it.

---

### Post by Michael Crawford on 2010-02-08
... or something like that...

I managed to get the files off the image, but still having no luck at mounting root no matter what I do.

I'll have to come back to this later.

---

### Post by MrUmunhum on 2010-11-06
> **Michael Crawford said:**
> ... or something like that...

I managed to get the files off the image, but still having no luck at mounting root no matter what I do.

I'll have to come back to this later.

Have you made any progress??

---

