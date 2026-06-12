---
title: "Linux installation not going well"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by KaitenV on 2007-08-10
Now hear me out. Around a good year ago (maybe 400-500 days) I was running a sad pentium 4 with a slow hard drive and 256mb of ram. Windows XP just used far too many resources and Ubuntu allowed me to code my projects in peice so that I might afford the pc I am using today.

However, this custom rig just does not want to get along with not only Ubuntu, but Debian.

Problems:
[LIST]
[*]Debian (4) installs, however after I get past the GRUB screen it talks to be about some disk read errors.
[*]Now, Ubuntu 6.06 (what was running on the old pc) does not see my 2 PATA hard drives, and can't seem to reconginze the partitions on my 1 SATA hard drive.
[*]So, I gave Wubi a shot, not installer errors, but when i try to boot into Ubuntu I get a huge mess on my screen ending and restarting with *Buffer I/O error on sdb, logical block 4897472*
[/LIST]

Please help me, I'd like to get back to work asap. My system specs are as follows (everything was brought on newegg.com)

EVGA 256-P2-N615-TX GeForce 7600GT 256MB GDDR3 PCI Express x16 Video Card
A-DATA 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)
Intel Core 2 Duo E6300 Conroe 1.86GHz LGA 775
**ASUS P5B Motherboard**
POWER SUPPLY CMAX500W CR-550B BKRT
CASE ANTEC|P180B BLACK RT
SEAGATE 320GB Hard Drive (SATA)
MAXTOR 80GB Hard Drive (PATA)
SAMSUNG 20GB HARD DRIVE (PATA)

---

### Post by dabl on 2007-08-10
That's a nice system -- I have that same black Antec case for mine, with 5 hard drives in it.

OK, first, if you built this yourself, are you pretty confident that you've got everything set in BIOS the way it needs to be?  Hard drives in the desired sequence, boot to CD ROM first, etc.?

Second, are you confident that you did the disk partitioning correctly?  Set no more than 1 "bootable" flag per hard drive, putting Grub on the correct MBR (where it is set "bootable"), etc?

Finally, if you have a choice in the matter, you should install Grub in the first partition of the first PATA drive, i.e. hd0,0.  That's where it "wants" to go, especially if you've got a Windows installation on that disk.  I fought mine for 3 days trying to get it to put Grub on a SATA disk while the PATA disk already had Windows installed, and it's just about impossible.  More guidance is available if you think this might be the problem.

Hope this helps!  :)

---

### Post by KaitenV on 2007-08-11
Thanks, this is actually my first box, and while I do program, I'm not pc guru, so the configuration may not be the best (bios did it). 

Heh, I'll go ahead and try to install Debain, since Ubuntu 6 won't see my drives and the only copy of 7 I have is what wubi downloaded (when I try to boot to what wubi does I get the errors above, and when I try to boot from the cd I made of "ubuntu-7.04-alternate-i386.iso" it locks up.

**My harddrives are installed as follows:**
20GB = hd0
80GB = hd1
320GB = hd2
I've been trying to get everything on hd1, since that's were windows is. Oh, and I let the BIOS configure itself.

MY PARTITIONS: [http://i40.photobucket.com/albums/e243/KaitenV/Untitled-1copy-1.png](http://i40.photobucket.com/albums/e243/KaitenV/Untitled-1copy-1.png)

---

