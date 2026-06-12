---
title: "Installation goes strange after partitioner"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Chris Mounce on 2005-06-22
I am having trouble installing Ubuntu 5.04. The computer is a Pentium 2 that was originally running Windows 98. The hard drive data was badly corrupted, but we are pretty sure that the drive itself is sound. I decided to make Ubuntu the new operating system. I went with the default installation, and everything went fine until it hit the partitioner.

I selected the option to erase and completely repartition the hard drive, which set up a 6.3 GB ext3 partition and a roughly 200 MB swap partition. I then told it to write changes to disk; it began to do so, but odd things started happening. The progress bar made it to 6%, stopped for some time, then jumped to 33%. After another delay, the box containing the progress bar disappeared, leaving only the blue background. More time passed, and the screen turned black, with only a blinking cursor in the corner.

I have a bootable CD with Knoppix, which I have been using in an attempt to format the drive by hand with fdisk and mkfs. So far, I have had no luck. I would appreciate any help that anyone can give me.

---

### Post by joelito on 2005-06-22
Reading that reminded me of a problem I had with my mom's Dell (Pentium 3 intel chipset 10gb HDD), and I think your problem in on a hardware level.

Did you tried to set up linux on another Disk??

---

### Post by mingus on 2005-06-22
with the Knoppix CD, what does fdisk tell you?  have you tried cfdisk?  or QTParted?

---

### Post by Chris Mounce on 2005-06-23
Joelito, this is my first time actually installing a Linux system, if that's what you're asking. However, I have used Linux- and Unix-based computers before.

Alright, I booted from Knoppix, using the parameters knoppix 2 lang=us. I don't know if this is important, but the following text appeared right after the penguin logo:

```

ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ldm_validate_partition_table(): Disk read failed.
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ide-scsi: hdd: unsupported command in request que (0)
ldm_validate_partition_table(): Disk read failed.

```

The following is the record of running fdisk:

```

fdisk /dev/hda

Command (m for help): p

Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device     Boot     Start     End     Blocks      Id     System
/dev/hda1     *        1         761     6112701     83     Linux
/dev/hda2              762       784     184747+     5      Extended
/dev/hda5              762       784     184716      82     Linux swap

Command (m for help): v

124 unallocated sectors

Command (m for help): q

```

The last time I tried repartitioning the disk with fdisk, it didn't complain at all; it just wrote out the data to disk (at least, so it told me) and exited. I have looked at cfdisk, but I haven't done much with it. I haven't tried QTParted yet.

I tried formatting the partitions with mkfs yesterday, but I don't remember what it said and I didn't write it down. It was able to create an ext2 filesystem, but it had some problems with creating an ext3 filesystem; it just went into a loop of error messages. With the ext2 filesystem already in place, I got past the partitioner, but it complained a bit, and the installation was going fairly slowly; how much time does an Ubuntu install normally take? The base installation failed at around 28%; I don't remember the exact error, but it was probably I/O related.

I ran fsck this morning and got the following:

```

fsck /dev/hda

fsck 1.34-WIP (21-May-2003)
e2fsck 1.34-WIP (21-May-2003)
Couldn't find ext2 superblock, trying backup blocks...
hda: irq timeout: status=0xd0 { Busy }

ide0: reset: success
hda: irq timeout: status=0xd0 { Busy }

ide0: reset: success
hda: read_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: read_intr: error=0x40 { UncorrectableError }, LBAsect=65537, sector=65537
end_request: I/O error, dev 03:00 (hda), sector 65537
hda: irq timeout: status = 0xd0 { Busy }

ide0: reset: success
hda: irq timeout: status=0xd0 { Busy }

ide0: reset: success
hda: irq timeout: status=0xd0 { Busy }

end_request: I/O error, dev 03:00 (hda), sector 65544
hda: irq timeout: status = 0xd0 { Busy }

hda: drive not ready for command
ide0: reset: success
/dev/hda was not cleanly unmounted, check forced.

Pass 1: Checking inodes, blocks, and sizes
Deleted inode 133 has zero dtime. Fix<y>? yes

```

After this point, there are numerous error messages concerning dtimes, set dtime flags, set imagic flags, compression flags set on filesystems without compression support, set INDEX_FL flags, prompts to Clear HTree index, and references to bad values for i_blocks and i_size. I said "yes" to all of them. At one point there was a long pause, and I left the computer; when I came back, the screen was flooded with more "DriveReady SeekComplete DataRequest" errors.

I hope there's something useful in all of this, and thank you for your help so far!

---

### Post by mingus on 2005-06-23
You indicated at the start that the drive's data was badly corrupted.  Did you check the drive for bad sectors?

---

### Post by Chris Mounce on 2005-06-23
What's the best way to go about checking for bad sectors?

---

### Post by mingus on 2005-06-23
[QUOTE=Chris Mounce]What's the best way to go about checking for bad sectors?[/QUOTE]

I use Spinrite, which is commercial.  I'm not familiar with the Linux tools.  

MS's tool was chkdsk/scandisk/chkdsk - it's changed over the years.  It could "mark" bad sectors which would be moved to a "don't use" section of the disk, and would re-write the data in those sectors (if it could) to good clusters.

Modern disks have built-in technology which self-detects and quarantines bad sectors (at least that's how it's supposed to work).  But not in a disk as old as yours.  There may be a tool by the manufacturer of your drive that can do this; I've used such tools from WD, Maxtor, and IBM/Hitachi.

fsck checks the filesystem.  If it encounters pointers in bad sectors, it will report errors, but only the broken chain, not the source of the problem.  Bad sectors are literally bad spots on the disk media.  They cannot be repaired, only quarantined.  If they are not, data will be corrupted and ultimately the filesystem will fail, or the disk itself.

---

### Post by Chris Mounce on 2005-06-24
I tried running badblocks, which is supposed to scan for bad sectors as well as, I assume, bad blocks. It did seem to be doing something, but these familiar-looking errors kept on repeating:

```

ide0: reset: success
hda: irq timeout: status=0xd0 { Busy }

ide0: reset: success
hda: read_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: read_intr: error=0x40 { UncorrectableError }, LBAsect=23944, sector=23944
end_request: I/O error, dev 03:00 (hda), sector 23944
hda: irq timeout: status = 0xd0 { Busy }

```

---

### Post by mingus on 2005-06-25
Chris, pls take a look at $man badblocks and $man e2fsck -

backblocks standalone looks for bad blocks, but does not correct them.  It may need to be given a block size, and the man indicates it cannot do a read/write (which you need done) if the drive is mounted.

so run it this way:  $sudo e2fsck -c

this way it supposedly will quarantine any bad blocks it finds.  You may need to run it as "-c -c" 

but read the man page first

---

