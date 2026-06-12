---
title: "Can't reinstall Windows XP after Ubuntu install"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by zerubbabel on 2012-11-26
I've been trying to help a friend reinstall Windows XP after she decided she wasn't ready for Ubuntu, but when I boot her Lenovo T61p from the Windows XP install disk, it complains that there is no hard drive. But the hard drive is fine, and will still boot Ubuntu. I even booted Ubuntu from the Ubuntu install CD and used the partition manager to remove the Ubuntu partitions, and then retried running the Windows XP install, but still it claims there is no hard drive. Then I put the Ubuntu install CD back in and had no trouble reinstalling Ubuntu on the supposedly "nonexistent" hard drive. What is going on? How can I get around this?

---

### Post by uRock on 2012-11-26
Use the partition manager within the ubuntu live CD to create an NTFS partition. The Windows XP installer is unable to see the EXT partitions used by ubuntu.

---

### Post by westie457 on 2012-11-26
Did you only delete the partitions or did you rewrite the partition table to wipe the drive? AFAIK XP was fussy about any drive that was not either completely empty or formatted to something it can work with (FAT32 or NTFS). Later versions of Windows usually know the drive is there and tell you to format it.

---

### Post by zerubbabel on 2012-11-26
Tried that. Nothing on the drive except a brand new NFTS partition. XP install still doesn't see the hard disk.

---

### Post by oldfred on 2012-11-26
Did you put boot flag on it? That makes Windows see it as the active partition and then it will install to it.

---

### Post by zerubbabel on 2012-11-26
> **oldfred said:**
> Did you put boot flag on it? That makes Windows see it as the active partition and then it will install to it.

Ok, thanks, I'll give that a try...

Well, still no go. I made the NTFS disk bootable, but the XP install still doesn't recognize the drive.

---

### Post by oldfred on 2012-11-26
From Ubuntu liveCD terminal post this:

sudo fdisk -lu

---

### Post by arpanaut on 2012-11-27
If this is a XP install disk without SP1 or maybe SP2 and it is a sata drive system the installer will not recognise the drive.  The sata driver had to be installed at the beginning of the installation process. I remember having to, at the start of install, hit F6 then inserting the media with the sata driver then following the prompts and then continuing the install.

Could that be your problem?

---

### Post by efflandt on 2012-11-27
Assuming it is the first or only drive in the computer, I imagine if you boot an Ubuntu live/install system from CD or USB, the following should make the drive appear to be empty and fresh to XP:

dd if=/dev/zero of=/dev/sda bs=1K count=1

That basically writes zeros to the beginning of the drive overwriting the mbr including the partition table which is all in the first 512 bytes.  I don't know if it is necessary to write any more to it for XP install to see it as an empty drive and automatically format it.

---

### Post by zerubbabel on 2012-11-27
kubuntu@kubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077f25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234436544   117218241    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095050

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    31696244    15848091    b  W95 FAT32
kubuntu@kubuntu:~$ 


Yes, it's a SATA drive, and yes, my XP install disk is an old one (pre-SP1 and 2), but it's the only licensed copy I have. So I suppose that is the problem. How can I get around that during the XP install?

---

### Post by darkod on 2012-11-27
XP can't see SATA disks. You have two options:
1. If the computer has a floppy disk, put the SATA drivers for that machine on a floppy, and immediately after booting the XP CD press F6 when it asks you to add additional drivers. Use the floppy to add the SATA driver.

2. If the above can't work or you don't want to bother, go into BIOS and find the SATA mode option. Change it from AHCI to IDE and then the XP CD can read the hdd. It will work little bit slower in IDE mode compared to SATA, but it will be readable without the need for a driver.

---

### Post by zerubbabel on 2012-11-27
I don't have a floppy drive, but I have an external USB CD/DVD drive, so I guess I could load the SATA driver from that.

---

### Post by darkod on 2012-11-27
> **zerubbabel said:**
> I don't have a floppy drive, but I have an external USB CD/DVD drive, so I guess I could load the SATA driver from that.

Nope, the XP installer is very limited, it asks the driver to be on a floppy only, you can't load it from CD or USB stick. As far as I know, there is no way without floppy.

One option is to slipstream the driver into the XP CD and create a new XP CD that includes the needed driver, but it might be too much bother. If you are interested, search on google about slipstreaming xp with nlite.

Check if you can change the sata mode to IDE and that should work.

---

### Post by zerubbabel on 2012-11-27
I tried the slipstream route, getting the exact driver from the Lenovo site for this specific Thinkpad, but it still doesn't work. It complains that the driver is corrupted (can't remember the exact wording). I tried the same procedure three times, burning three different .iso images, and they all fail the same way. Guess I'm out of luck.

---

### Post by varunendra on 2012-11-29
> **zerubbabel said:**
> I tried the same procedure three times, burning three different .iso images, and they all fail the same way. Guess I'm out of luck.
Why are you going into unnecessary complications ? Did you check the BIOS for the SATA 'modes' like darko suggested above? I have used xp for years on SATA drives in IDE mode without issues.

As far as the speed limitation is concerned, I doubt if it really matters for a laptop drive. I believe it should work @ 133MB/s in [IDE mode]("https://en.wikipedia.org/wiki/Parallel_ATA"), which is much more than the practical read/write speeds of a typical laptop drive (and I am aware that [yours may be a 7200 rpm drive]("http://www.notebookreview.com/default.asp?newsID=3889"), but still, a laptop drive nonetheless).

So I'd say, don't bother with SATA drivers, just change to IDE mode and you should be all set.

.

---

### Post by zerubbabel on 2012-12-06
Yes, I considered that, but we found a copy of Windows 7 we could install, so we went with that. The whole experience makes me appreciate Linux more...

---

