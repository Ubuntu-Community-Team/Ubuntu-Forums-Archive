---
title: "Best way to re-install windows and keep Ubuntu"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by catalytic on 2006-12-16
I currently have an old installation of windows that I would like to remove and re-install. I just installed Ubuntu Breezy again, because of my windows problem. I went to the effort of upgrading it to Edgy, only to have it mess it up, and then I had to start all over again. So this time I have just left it and upgraded some of the Breezy packages.
I would like to know the best way I could go about re-installing windows. The partitiona are already set up as follows:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/hda2            1959        9729    62420557+   f  W95 Ext'd (LBA)
/dev/hda5            1959        8645    53713296    7  HPFS/NTFS
/dev/hda6   *        8646        8696      409626   82  Linux swap / Solaris
/dev/hda7            8697        9729     8297541   83  Linux

Also there is this message when I go to view the partition table

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

What I want to do is install windows again on hda1, I understand I have to format the partition, that's ok as long as it doesn't mess up my other partitions. My concern is the Grub loader, what will happen when I re-install xp? also should I unmount the windows drive and delete the directory in Ubuntu before installing the new windows?

I'm getting used to Ubuntu so I may as well keep it, also I do want to upgrade to Edgy, but last time it worked fine for a day, then suddenly terminal wouldn't run, and I couldn't shut down, then it wouldn't load past the splash screen. Even when I tried loading throught the old Breezy kernel it just stopped at Initialising dev files ro something along those lines. 

In the mean time I have managed to successfuly get my Ati Radeon 9250 card working no problems, and a couple of my needed windows programs, such as PokerStars, I find wine only wants to work with some things, the newer version in Edgy (from the time I had to play with it) seems to work much better with my windows applications. 

Any advice, links etc would be much appreciated, I've found a lot of threads about installing Ubuntu with windows, but I can't find ones about what I'm trying to do.

---

### Post by melancholeric on 2006-12-16
Backup everything. Atleast your home directory.

Install XP.

Then, do a clean install of Edgy. I don't think upgrading from Breezy to Edgy is going to work.

---

### Post by yabbadabbadont on 2006-12-16
A quick search turned up this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It looks to me like it answers some of your questions.  If not, post back and someone will try to help.

---

### Post by catalytic on 2006-12-16
Thanks I think that link will sort out my problem with the Grub loading....
Darn it, I've already installed Ubuntu twice, looks like a third time. At least my isp has the latest Ubuntu iso's as free traffic!

So you suggest when installing windows, format the old windows partition and the linux one, and do a fresh install of both windows and linux Edgy?

---

### Post by melancholeric on 2006-12-16
> **catalytic said:**
> So you suggest when installing windows, format the old windows partition and the linux one, and do a fresh install of both windows and linux Edgy?
If upgrading from breezy to edgy doesn't work, and it doesn't seem to.

You're skipping one version in that upgrade, and considering upgrades to edgy from dapper have been difficult enough I don't think that could work. And I don't think it's recommended either.

---

### Post by catalytic on 2006-12-16
Well I'm downloading both Dapper and Edgy versions, I'm wondering if maybe just sticking to Dapper is a better idea, as I said in OP Edgy for some reason just crapped itself after a day, I worked fine and then nothing would work, this was before I even tried to install the ati driver.
mmm what to do...

---

### Post by catalytic on 2006-12-18
I'm all set now, a friend ended up re-installing xp pro for me, and I've just installed Edgy. I was pleasantly suprised that it took less than half an hour to install, and that my windows drives were automatically mounted, and my screen resolution was perfect, without me having to change a thing. Very nice...I think I might end up doing more work in Ubuntu now that it's all running smoothly.

---

