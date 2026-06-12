---
title: "Help needed for Vista partiton table destroyed"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Houchy on 2010-05-02
Hello,

I made a big mistake yesterday.

While trying to partition my USB memory stick to be able to run Ununtu 10.4 in persistent mode I instead re-partitionned my hard drive. So I destroyed my Vista installation!

Is there any way to repair my Vista? Please help ...

Initially I had 1 main partition on my hard drive for Vista, and maybe another small one (1 or 2 MB) at the beginning of the hard drive.

Now, when I use testdisk to analyze my hardrive, the Quick Search show only one partition:
ext3  casper-rw

Then the deepter search find 2 partitions on 70GB and 250GB.

Initially me Vista was 320GB.

Is there a way to retrieve my old partition table and write it in the MBR?

Thank you in advance for your help.
:confused:

---

### Post by Houchy on 2010-05-02
Here is what testdisk finds:

```

Partition             Start        End    Size in sectors

D Linux             0  32 33 38913  37 36  625137664 [casper-rw)
D HPFT - NTFS    1147 118 60  8575  21 22  119324672
D HPFT - NTFS    8575  21 23 38913  48 31  487381680 [DATA]

```

It seems like my partition could have been starting at 1147 and finish at 38913.

Is there anyway to recreate this partition?

Any help will be greatly appreciated ...

---

### Post by srs5694 on 2010-05-02
If you're sure of those start and end points (1147 and 38913), you could try using fdisk to re-create the partition. If you do this, I recommend trying a *read-only* mount of the partition to verify that it's correct. Check that the files seem sensible, and do a "df -h" to verify the size of the filesystem (vs. the size of the partition; they should be quite similar, give or take a bit of slop for various reasons). If it seems OK, you could try running a CHKDSK on it in Windows. You could then try to recover your second partition.

Note that recent versions of Windows (including pre-installations on new computers) like to consume two partitions (or sometimes three or even four on some new computers). Windows might not boot without the second partition, so you may need to recover this second partition before you can try booting Windows. Your first partition most probably starts at either sector 63 or sector 2048, depending on what utility created it; however, other values are possible.

Finally, for best safety you should do a byte-for-byte backup of the whole disk to another disk of the same or greater capacity before you start messing with the disk. In Linux, you can do this with dd:

```

sudo dd if=/dev/sda of=/dev/sdc

```

This copies /dev/sda to /dev/sdc. Be sure to get the if= and of= parameters right, or you could end up irrecoverably trashing your disk rather than backing it up! Also, note that drives of the same nominal capacity ("500GB", say) may not be *exactly* the same size, so if you need to buy a disk to make this backup, it's best to buy one that's a bit larger than the original.

In future, you can back up your partition table so you've got an easy recovery method. See the "Final Conversion Thoughts" section of [this Web page](file:///home/rodsmith/homepage/gdisk/mbr2gpt.html) for details on how to do this. (The process is quite painless and quick.) Store your backups on a floppy disk, USB flash drive, CD-R, network share, or anything else that's easily accessed from an emergency system.

---

### Post by Houchy on 2010-05-27
Thank you for your answer, I tried it and it's not working.

I still have the same message "Operating System Missing" ...

---

