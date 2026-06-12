---
title: "Two OS on two hard drives vs. partition of one drive"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by blauendonau on 2011-06-03
Is there any performance degradation or complications that arise from having Linux installed on a separate, physical hard disk from Windows in a dual-boot setup?

I have a computer that I'd like to dual-boot Ubuntu and Windows but the current hard drive is quite fragmented and the Windows partitioner won't allow me to make a partition large enough to comfortably run Linux+several gigabytes of media that need to be stored. The rig, however, may have room for another internal drive, so I thought that having a separate physical disk reserved completely to Linux would be an easy solution. The tech guy at the local computer store suggested there might be difficulties with this configuration because one drive needs to be the "master" and the other a "slave", resulting in boot complications. Can anyone advise?

Thanks!

---

### Post by ddnev45 on 2011-06-03
I set up my dual boot on two separate drives so the OS's do not mingle - Win7 and Debian Testing in my case. Win7 on the primary master and debian on the secondary master.

No performance degradation that I can notice.

As for booting, grub can handle it; I always put grub on the second harddrive with Debian and let grub find Windows 7; then change the boot order in the BIOS.

There are some good HowTwo threads for dual booting in the Tips and Tutorials forum - recommend you read them first.

---

### Post by oldfred on 2011-06-03
How old is system? Master/Slave is IDE/PATA drives with older BIOS. Then, only jumpers on drive controlled boot from primary master. Cable select then is a newer version that boot is controlled by location on cable. Jumpers on drive had to be set for cable select.

My newer SATA calls the boot drive Master, but boot is totally controlled by software/BIOS. Many newer BIOS that support both IDE & SATA will let you choose boot drive in BIOS.

If BIOS supports it you keep each totally separate and have each boot loader on each drive and each drive could work on its own. If BIOS only boots primary master then you install grub2's boot loader to the primary master and boot either drive. If you removed the windows drive, you would have to reinstall a windows boot loader to the MBR which is easy to do.

I recommend two drives.

More info:
with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by blauendonau on 2011-06-03
Thanks to both of you for your replies.

The computer is (comparatively) new, from around early '08. I'm pretty confident it uses SATA; I can check.

I know how to do an install of Linux on a partitioned computer - done it several times - but never on a two-drive machine. I assume that assigning partitions in the installer would work similarly to a single-drive install? (N.B.: I always use the manual/advanced option in the installer.) Except that instead of writing Linux to 'sda2', it'd be 'sdb1'? (Assuming that sda contains Windows.)

In my experience, the Ubuntu installer doesn't automatically recognise any drives other than the main one (e.g. on this rig the Windows backup/recovery drives weren't present in the installer), so I don't know how to tell it to use another physical disk.

---

### Post by oldfred on 2011-06-03
I always partition in advance and use manual install to format and choose / & /home partitions. You have to use manual install so you can choose to install grub2's boot loader to sdb, which you want to do. Then change BIOS to boot sdb.

Herman has one of the few installs with screenshots on a second drive. Lots of detail, not as complex as it may seem, just because of the detail.

Installing Ubuntu in Hard Disk Two (or more) internal or external Maverick screens shown, only minor screen differences with other versions.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by blauendonau on 2011-06-04
Follow-up: Managed to get the Windows drive defragmented with the help of some heavy-duty third-party partitioning tools. Thanks to Microsoft for providing a useless default defragmenter. ](*,) Almost as if they're trying to prevent you from partitioning your machine to dual boot :grin:

Anyways, I got both OS installed on one drive, it was the most convenient thing to do. Turns out there might not have been room for a third internal HD, plus I didn't want to go through the expense of buying another drive. One more computer running Ubuntu!

---

