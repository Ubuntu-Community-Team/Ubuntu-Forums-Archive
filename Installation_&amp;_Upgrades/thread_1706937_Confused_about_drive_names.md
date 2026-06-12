---
title: "Confused about drive names"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by XEtedBear on 2011-03-14
I'm trying to solve a boot issue on my system. After reading a lot of forum threads - especially about rebuilding Grub - I am totally confused by drive device names. Could I get some clarification please?

For example, the Grub rebuild guide tells me that my first drive is 'sda' - but what does 'first' mean? Who is doing the counting?

On my hardware I have 2 IDE channels. Is the 'first' drive that which is connectd to the Primary channel?

But wait, in my BIOS I can set the hard disk order (this is NOT the boot priority), so now for example I can set the disk on my secondary IDE channel as disk number 1. Is this now the first disk? Or is disk 0 the first disk?

It get even more confusing: If I use the command 'ls' when in the Command line option of the Grub menu, or use Gparted, my disks have names like HD0 and HD1 or HDA and HDC - what happened to HDB? But elsewhere the disks have names like SDA and SDB - how do these map to the HDxy names?

But we're not finished yet: about partitions: the Grub guidance tells me that the first partition on my disk will be hda1, the second will be hda2 - but are these the primary, extended or logical partitions? How do I do the counting? On one of my disks (I can't tell if it's the first or the second - even ignoring where the origin for counting is, zero or one) there are unallocated spaces between my partitions (according to Gparted). Are these spaces to be included in the partition count?

When it comes to fstab, I don't know if I should be setting my root disk as hda1 or hdc1 or sda3 or sdc5. There is insufficiently complete and unambiguous guidance. For somebody who is not fluent in Geek it is an unecessary source of stress in trying to make a Linux system work.

---

### Post by oldfred on 2011-03-14
In windows they confuse drives & partitions, everything is a drive, but then you do not know which is a hard drive or a partition.

There used to be a difference between hda & sda as sda was SCSI. But they changed to a unified driver a few years ago and all  hard drives are sda, sdb, sdc etc.

Partitions are the numbers after the drive so sda1 is the first partition. sdc3 is the third partition on the third drive.

BIOS may control drive order. Old IDE drives had primary and secondary channels (two cables) and master & slave (two hard drives). With IDE and old BIOS' only primary master was bootable. With SATA you can choose to boot any drive.

Grub numbers drive like hd0, hd1 where hd0 is the first drive. That may not be sda in Linux as normally the boot drive is hd0. New grub2 and grub legacy also changed partition numbering, just to add to the confusion.

```
        grub    grub2
sda1    hd0,0    hd0,1
sda2    hd0,1    hd0,2

sdb1    hd1,0    hd1,1

```Primary partitions are the original 4 partitions, But then they realized that was not enough and let you make one primary an extended. The extended is just a container for all the logical partitions. Primary will always be sda1 thru sda4 and logical will always start at sda5 even if you make sda2 the extended and do not use sda2 & sda4.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by oldfred on 2011-03-14
If you want to know what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

