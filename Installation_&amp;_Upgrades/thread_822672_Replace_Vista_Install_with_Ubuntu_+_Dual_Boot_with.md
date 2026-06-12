---
title: "Replace Vista Install with Ubuntu + Dual Boot with XP"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by simonjp on 2008-06-08
I have two partitions on my laptop - 40GB drive in half with Vista on the first partition (Drive C) and XP on the second (Drive D).

I'd like to replace the installation of Vista with Ubuntu but keep and boot into the XP partition.

Currently the boot order is Vista first then XP second in the Vista bootloader.

My initial thought was to boot into XP, format the Vista partition, start Ubuntu install from CD and point it to the first partition where Vista used to be.  By doing this though will the Ubuntu set-up still be able to detect and add an entry in the grub loader to the XP partition?  Or will I have to add entries manually after Ubuntu has finished installing?

Any takers......please?

---

### Post by Pumalite on 2008-06-08
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Herman on 2008-06-08
It will probably be a troublesome venture.

You should stop and check to see if your Windows XP is in a primary partition and make sure if has ntldr, ntdetect.com and boot,ini files.

If ntldr, ntdetect.com and boot.ini are all safe and sound in your Windows XP partition and it's a primary partition, you won't have any trouble, but I will be surprised if that is the case.

If those files are in your Vista partition, or do not exist at all and you delete Vista, Windows XP will be unbootable. 

If 'D:' drive is a logical partition (partition number greater than 4), then you should look for your Windows XP boot loader files in the root of your Vista partition and copy them into Windows XP using your Ubuntu Hardy Heron LiveCD before you delete Vista.
Then, if Windows XP is in a logical partition, you should copy the whole partition with Gnome partition editor in your Ubuntu Hardy Heron LiveCD and paste it into the empty space where Vista was, so it will be in a primary partition.
You might need to edit boot.ini to make it bootable, but you'll end up with a bootable system. 
There's another workaround, but it's messy.

Regards, Herman :)

---

### Post by simonjp on 2008-06-08
Thanks Herman.  I had a feeling that I'd still need the 3 Windows boot files.

The Vista partition was created initially by upgrading an installation of XP in it i.e. I had two partitions with XP.  So, I think you're right in that it (Vista) is the primary partition.

Looking at the link Pumalite provided (thanks bud), a dual boot install all points to XP being the first OS in the Primary partition, then Ubuntu can be anywhere else.

So in summary you're suggesting:

1. Copy the 3 Windows boot files to the D: drive (XP).
2. Boot with the LiveCD and format the Vista partition.
3. With the Gnome partition editor copy the D: drive into the first partition.
4. Edit the boot.ini so the partition(2) line reads partition(1) redirecting the XP boot to the 1st partition.

Does that sound about right?

---

### Post by Herman on 2008-06-08
> Looking at the link Pumalite provided (thanks bud), a dual boot install all points to XP being the first OS in the Primary partition, then Ubuntu can be anywhere else.Well, in my computers Windows can be moved to any location on the hard disk, it didn't matter in the tests and experiments I've done, as long as the partition number isn't changed.
If the partition number is changed, then as long as Windows is in a primary partition, it's simple enough to edit boot.ini and Windows will boot in any (primary) partition.
If you copy Windows XP to a logical partion, then you can't boot it in the normal way, but if you use a partition editor to place a boot flag on the logical partition you can still get it to boot.
The simpler you can keep things, the easier it will be for yourself, and anyone else who may have to work on your computer, so for most people it's just easier to leave Windows at the beginning of the hard disk. In you case, the reason for copying it and pasting it is only so that it will be in a primary partition.  :)
> So in summary you're suggesting:

1. Copy the 3 Windows boot files to the D: drive (XP).
2. Boot with the LiveCD and format the Vista partition.
3. With the Gnome partition editor copy the D: drive into the first partition.
4. Edit the boot.ini so the partition(2) line reads partition(1) redirecting the XP boot to the 1st partition.

Does that sound about right?     1. Definitely make sure you copy the 3 Windows boot files into your D: drive!
2. Yes, or delete it.
3. Yes, but you don't have to if 'D: drive' is a primary partition, but I'm guessing it's a logical partition, so I think you should copy and paste it for the purpose of making sure it's in a primary partition. 
If you can post the partition numbers then I'll know for sure, drive letters are meaningless.
Make sure you back up your files first, of course.
4. Yes. That sounds right.

---

### Post by simonjp on 2008-06-12
The partition details are:

/dev/sd1 - ntfs @ 20GB - Flag set to: boot
/dev/sda2 - extended - Flag set to: lba
/dev/sda5 - ntfs @ 20GB

When looking at the Information for the disks there is a note that it's reporting 30 bad clusters.  It suggests running ntfsclone --rescue, but you need an output file and yet I've run out of disk space to create this!  I've run Windows chkdsk over the partition yet this doesn't find any errors.

I'm worried that if I copy the partition into the free space that it won't copy correctly because of these bad clusters.  What is the command to run a chkdsk under ubuntu?

---

### Post by Pumalite on 2008-06-12
sudo fsck /dev/???
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)
You can check your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Herman on 2008-06-12
:) fsck works for NTFS partitions too now? 

I thought we still had to install ntfsprogs and run ntfsfix, but maybe I'm not keeping up to date with the latest developments well enough. 
:popcorn:

I would have said ```
sudo apt-get install ntfsprogs
``` and ```
sudo ntfsfix /dev/sda5
``` but Pumalite's way will be simpler.

---

### Post by meierfra. on 2008-06-12
man fsck: 

 fsck - check and repair a Linux file system


man   ntfsfix:

DESCRIPTION
       ntfsfix  is  a  utility  that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies,  resets  the  NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

---

