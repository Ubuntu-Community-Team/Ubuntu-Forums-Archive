---
title: "settings for software RAID on dual disk?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by BakCompat on 2010-11-05
Ok, most of my servers run CentOS on hardware RAID5, but I've got an Ubuntu and Mint box doing some other stuff. 

I've got an Intel Atom D510 mobo on the way and will be loading it up with 2 of the newer WD20EARS hard drives to make a file server. I had planned on loading it up with FreeNAS and letting it do ZFS in software RAID1 but I'm not a big fan of BSD and am perfectly content to not add another OS to my servers so I can keep more commonality and maintenance easier.

So, I'd much rather load up my incoming file server with a linux distro. Here's the situation: the Atom motherboard does not support RAID - it's just plain ole IDE/AHCI sata ports, and only two of them. For an $80 mobo and cpu, I'm not complaining.. it does what it does... efficient with power.

So, I have this board with 2 sata ports that will connect 2 hard drives, each 2TB in size. I have an external usb dvd drive to install from, so no problems there I hope. 

Should I install the OS directly to the drives themselves and let them be parted out to multiple parts? Or should I install a 4 gig usb thumbdrive internally and install linux on it, thereby allowing the 2x2 hard drives to be a single data partition each?

As I am looking to use this as a file server, and not a daily desktop use machine, system resources are not too particular, and the Atom is more than enough, with my planning on it replacing my current ftp server only - a p3-550 w/ 128 ram and 3 diff drives in an LVM totalling 280 gigs. BTW, proftpd on that box consumes about 200 MHz during xfer over a FA310TX nic (couldn't find any 3Com 905b or c's laying around)..

The box will be on a gig-E lan with some PowerEdges for file xfer back and forth, and I might end up doing a gui install so I can NX into it, but haven't decided. Webmin might suffice.

So to reiterate the original question: Install OS directly to the hard drives in software RAID config, or install to a usb thumbdrive and use the two disks as single partition data drives in software RAID?

Expected uses will be FTP, Samba, and maybe NX if I go gui. Aw hell, bittorrent also! Might as well make it a seedbox. :)

---

### Post by BakCompat on 2010-11-09
4 days, 80 views, and no replies... OK, guess I'll have to try this one my own and see how it goes.

---

### Post by bsmith1051 on 2010-11-09
Install from the Ubuntu Alternate CD, then setup both drives with matching 'raid' partitions, then choose Setup Software RAID, combine each matching pair and use ext4 (the new default, btw).

In other words, just run everything off the 2 drives!  No need to introduce a separate USB drive for /.  You don't even need to mirror / if you don't want to.

P.S. I don't know why there isn't an all-in-one install option for this in Ubuntu.  I've heard that there is in Debian and/or Fedora?

---

### Post by roddersg on 2010-11-09
>> the Atom motherboard does not support RAID - it's just plain ole IDE/AHCI sata ports, and only two of them.

Says who?
I have the same board and coupled with a plain SATA3114 (4-port SATA interface) have a NAS running with 6x1T drives using software Raid 5.  Remember that the atom is much faster than an old hardware raid card.

Use software raid 0,1 or 5.  Doesn't matter, it will run.  If the board dies, just replace the motherboard.  The data is intact, unlike using a dedicated hardware raid card where you have to pray that you can get an exact replacement.

You can use the alternate install CD or boot from the desktop version and then apt-get install mdadm or alternatively, use the server disk.

Just a short note that if your drives create a volume > 2GB, then you will need to partition them using GPT instead of FDisk.

---

### Post by bsmith1051 on 2010-11-09
> **roddersg said:**
> >> the Atom motherboard does not support RAID - it's just plain ole IDE/AHCI sata ports, and only two of them.

Says who?
He's probably thinking of the so-called 'Fake RAID' that a lot of after-market motherboards offer.  I think a lot of people have shown that pure sw-raid works better than Fake RAID, so hopefully no Linux users are bothering to use it anymore?

---

### Post by BakCompat on 2010-11-13
> **roddersg said:**
> >> the Atom motherboard does not support RAID - it's just plain ole IDE/AHCI sata ports, and only two of them.

Says who?
I have the same board and coupled with a plain SATA3114 (4-port SATA interface) have a NAS running with 6x1T drives using software Raid 5.  Remember that the atom is much faster than an old hardware raid card.

Use software raid 0,1 or 5.  Doesn't matter, it will run.  If the board dies, just replace the motherboard.  The data is intact, unlike using a dedicated hardware raid card where you have to pray that you can get an exact replacement.

You can use the alternate install CD or boot from the desktop version and then apt-get install mdadm or alternatively, use the server disk.

Just a short note that if your drives create a volume > 2GB, then you will need to partition them using GPT instead of FDisk.

The motherboard says so. It's IDE or AHCI only, which is why I *intend* to use software RAID, specifically because the cpu is capable of doing so... Though, I only have 2 of these disks so I'll be using them in RAID1 instead of RAID5, which I would much prefer....

And speaking of the SiL3114, I had thought of purchasing one of them and sticking it in another box with a bunch of old drives and setting them up as a JBOD array with LVM.. They're all irregular sizes, so doing useful RAID5 on them isn't feasible. That box would probably be 7 hard drvies from 80 gigs to 320 gigs each, combines just for a simple ftp server.

> He's probably thinking of the so-called 'Fake RAID' that a lot of after-market motherboards offer. I think a lot of people have shown that pure sw-raid works better than Fake RAID, so hopefully no Linux users are bothering to use it anymore?

yeah, pretty much. I'd like it if there were more options, but since I didn't pay for this hardware, I'm not going to shell out any cash to upgrade it. ;) I'll just be administering it...

---

### Post by i.r.id10t on 2010-11-13
First, fdisk each of the disks and make 'em one big primary partition

Then create the raid array
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

Then format it
mkfs.ext3 /dev/md0

I seem to need to do a scheduled check at very inopportune times... 

tune2fs -c 0 /dev/md0
tune2fs -i 0 /dev/md0

Get the blkid if your new file system

blkid /dev/md0

Add an entry to your mdadm.conf file

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b3630382:c0bcd82b:10179dc3:e8fd0b62

Bring it up, mount it, etc.

mdadm --assemble md0
mount /dev/md0 /raid

---

