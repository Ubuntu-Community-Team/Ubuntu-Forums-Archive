---
title: "RAID install fails"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by Bubba Ho-Tep on 2006-05-02
I'm having difficulty setting up RAID1 on a fresh install of Ubuntu.
I've been following [this](https://wiki.ubuntu.com/Installation/LVMOnRaid) and just doing the RAID part.

I'll describe my setup:

x2 80Gb IDE drives, both master 

I'm installing Ubuntu (Breezy) from scratch

I want to have partitions for root, home, var and swap.

Following the guide above it tells me to create one partion on each of the 80Gigers and mark it as a  RAID volume. So far so good.

So to be clear I have:

IDE master (hda) 80Gb 
	#1 primary 80Gb bootable raid

IDE master (hdc) 80Gb
	#1 primary 80Gb bootable raid

RAID1 device #0 80Gb Software RAID
	#1 80Gb ext3

showing on the install partitioner.

The trouble comes when I try to create partitions inside the RAID device. (I don't know if I'm even meant to be doing this but the guide isn't very clear on this). 

When I create a partition inside the RAID device this seems to work ok but the remaining space is marked unusable. Nothing I've tried from here works.

So I hunted about on the net for other RAID tutorials - and found one (sorry lost the link) that said to create the partitions you want (so in my case a 20Gig /, a 30Gig /home, a 28Gig /var and a 2Gig /swap) on both IDE disks and then create RAID vols for each of those. 

IDE1 master (hda) 80Gb
	#1 primary 20Gb bootable raid
	#2 primary 30Gb    	       raid
	#3 primary 28Gb 	       raid
	#4 primary 2Gb	       raid
IDE2 master (hdc) 80Gb
	#1 primary 20Gb bootable raid
	#2 primary 30Gb    	        raid
	#3 primary 28Gb 	        raid
	#4 primary 2Gb	        raid


This doesn't seem right to me but hey what the hell - ...and it didn't work either

the install partitioner either hangs when trying to create the RAID vols, doesn't detect all the partitions or most frustratingly creates the RAID devices and then when you hit finish partioning and write changes to disk it does nothing.

So umm where am I going wrong? Or can someone please point me to a step by step tutorial to get software RAID going? The one I linked to above skips over lots of steps and (for a newbie like me) is unclear in parts. I've looked everywhere I can think of for info and come up with nowt. If I get this going I'd be more than happy to write a tutorial for the wiki.

BH-T

---

### Post by waster on 2006-05-02
I'd go with Dapper, not Breezy. There is better (although imperfect) support for RAID and LVM.

Since it's all going to be RAID 1, why don't you set up LVM on RAID? Then you don't have to worry about wasted/insuffucient space on your partitions. This is doable from the Dapper installer.

1. Set up 1 RAID1 partition to fill the disk (I would have a SWAP partition on each disk, too)
2. Add it to a new Physical Volume group
3. Create logical volumes for each of your "partitions"
4. Create Reiser filesystems on each logical volume

Reiser can be resized in both directions. Not sure about ext2/3. Several others can't be reduced or even grown.

---

### Post by Bubba Ho-Tep on 2006-05-04
cheers for the suggestion.

I actually got it going (kind of) by initially telling the installer the first partition was 80gigs and then once that was done going back and resizing the partition. 
It kind of makes sense but I've got to say the way the installer presents the info is shithouse. It took me ages to figure out what the hell to do for what should be a simple RAID1 setup. 

Anyways I got it to boot but when I disconnect one drive - it boots from IDE1 but not IDE2. 

Umm my options at mo I see as being 

a) try to work out why one of the RAID array doesn't boot on its own

b) d/l and install Dapper and hope its installer is better

c) go with another distro


a) I'm rapidly getting tired of this so this doesn't appeal much

b) is the Dapper installer better/clearer? why go with Dapper over Breezy - is there a particular reason to?

c) I've never tried another distro (yet). does anyone have any suggestions what might be any good?

---

### Post by lha on 2006-05-04
a) Installer puts grub only on one disk. You have to install grub manually to the other disk. See section 'booting off raid1' from [http://deb.riseup.net/storage/software-raid/]("http://deb.riseup.net/storage/software-raid/")

---

