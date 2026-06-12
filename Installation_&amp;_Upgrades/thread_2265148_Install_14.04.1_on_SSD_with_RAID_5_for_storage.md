---
title: "Install 14.04.1 on SSD with RAID 5 for storage"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by Travis_Williams on 2015-02-12
I'm looking to install 14.04.1 on an SSD in my desktop PC. No dual-boot or other fanciness. I would then like to use 3-1TB HDD's in a RAID5 configuration for file storage. I'm having a hard time finding guidance on if I can do this, and how I can do this. 

Here's the specs on my PC Build

[TABLE]
[TR]
[TD="class: vbmenu_control"]**Motherboard**[/TD]
[TD="class: vbmenu_option1"]ASRock 970 Extreme4[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Motherboard BIOS version**[/TD]
[TD="class: vbmenu_option1"]UEFI 2.60[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Processor**[/TD]
[TD="class: vbmenu_option1"]AMD FX 4130[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Video Card #1**[/TD]
[TD="class: vbmenu_option1"]EVGA GEForce GT610[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Hard Drive #1**[/TD]
[TD="class: vbmenu_option1"]Kingston 128GB SSD[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Hard Drive #2**[/TD]
[TD="class: vbmenu_option1"]WD Blue 1TB[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Hard Drive #3**[/TD]
[TD="class: vbmenu_option1"]WD Blue 1TB[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Hard Drive #4**[/TD]
[TD="class: vbmenu_option1"]WD Blue 1TB[/TD]
[/TR]
[TR]
[TD="class: vbmenu_control"]**Power Supply**[/TD]
[TD="class: vbmenu_option1"]EVGA Supernova NEX750B[/TD]
[/TR]
[/TABLE]

Thanks in advance for any assistance.

---

### Post by TheFu on 2015-02-13
Install to the SSD as normal. Ignore the 3 other drives.  Get things installed and patched. Be happy for 30 minutes.

Then look up the mdadm how-to and follow that for RAID5 steps for the 3 disks.  google found it here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) Mount md0 wherever you like ... /home, /mnt and /media are probably NOT the best locations.  I like /D ... for data. Set the file/directory permissions on /D to allow the users/groups you want with access as desired. Be happy for a few years - assuming you are running 14.04 LTS.

---

### Post by MAFoElffen on 2015-02-13
Or you... it is easier to do it while installing. The partitioner is intuative and you don't have to know any commands.

Basically, you will be installing as normal. on the SSD, but choose "other" (manual). This is just a suggested guideline recipe...

As you partition, you would partition the SSD as 
sda1 512mb bios_grub (unformatted)
sda2 512MB EFI fat32 boot
sda3 etx4 /
sda4 linux_swap

Your 3 other drives, do extt4, the same size as each other. After you partition them, a new option will appear in the partitioner, at the top, for RAID mdadm. It will ask you to create RAID? md0 as default first, select the RAID, type, select the 3 disks as members, select the default settings. 

After you finish, you will see the RAID, at the top, above the didsks. Select the unformatted and create a partition in md0, using ext4... tell it the mount point as /home.... Continue installing. Done.

Even if you do it that way, learn to use mdadm and it's commands. Just get comfortable using it and keep your references handy. I'm the project manager for mdadm-gui and I have to admit, mdadm has so many different option and variations to options, that no one person could possibly remember them all. That is why I wanted to build something a bit more user friendly, to step through that... but because of all those otpions, that's also why been  why it's been so hard to do so.

Remember that RAID is not a substitute for a backup. A backup will get you back up sooner that a resync/reassemble. If you are doing this for redundancy and a promise of uptime (server), you are on the right track and should think of later going to RAID6 down the road... If you are doing this to learn, you are on the right track...

If you are doing that just to extend disk and if you are not a production environment, LVM is easier and less overhead. And with backups, you could do LVM snapshots. As with mdadm, there a lot of CLI utilities with many options. Keep a cheat sheet handy and learn to use them. Get comfortable with whatever you use.

Some people may join in with opinions, but even free has a cost in what you put into it, the security of and what it takes to get back up. Is that enough info to answer your question?

---

### Post by Travis_Williams on 2015-02-16
Wow, thanks for the excellent and helpful responses TheFu and MAFoElffen! Can you tell me more about LVM? I'm just having fun with a home PC build but expect that my family will be storing lots of pictures and videos on it and would like to keep those safe with local backups. RAID5 made sense to me, but The little I just read about LVM and snapshots may be easier to manage. I'll have online backups as well, but those could take even longer to restore than rebuilding a RAID.

---

### Post by MAFoElffen on 2015-02-17
LVM stands for Logical Volume Manager. Been around for years in Linux. Windows 8.x heralds it as new to them and refers to it as "Storage Spaces"

With Linux, you can boot into a Linux LVM volume. (Windows hasn't figured that out yet.)

Basically, it's sort of like Linux Software Raid... where you have some LVM commandline utilities to learn. You have a PV (Physical Volume). You create a physical volume from extents, which means from partitions. You can add extands to a PV. That is the outer container. The extents do not need to be the same size as eaxh other, as with RAID. Inside of the PV, you have smaller divisions called an VG (Volume Group) and LV (Logical Volume). These can span physical disks. You add your filesystems inside the LV's. You can shrink or grow your filesystems... as well as your logical containers.

You can even create LVM mirrored volumes. Some might refer to that as RAID1, but it is not. That would just P off purests, but is mirrored, so in practice... Is like.

So to grow... You partition a new disk, add to the PV. Extend your LV. Extend your filesystem.

Inside the LV's, you can partition and create your file systems. You can create a snapshot with creates a ive copy of the filsystem, and can tack the changes to it. You do that by creating it onto an empty extent. Since it tracks the original, then changes from that original, they take less shape than full backups. It cn also be done live, without having to bring down the machine. (other backups with other filesystems, sometimes have problems with open files.)

What I can say about it, is that it is very flexible. Not as peace of mind or foregiving as RAID, but very fast and easy. I'm been testing on it for over a year here and am very happy with it. Have servers here on mdadm and lvm... some just on LVM. Works great for me in what I do... mdadm and LVM treat some things similarly, as logical containers.

That's a basic summary of... Any more detail, and I would suggest looking at the LVM Wiki. (Good info there).

---

### Post by TheFu on 2015-02-17
I'd only add that LVM can be most complex and it is possible to have huge data loss due to 1 drive failing if the PV has been extended across multiple partitions.  I lost data on 3 drives when 1 failed over a decade ago. Have good, simple, backups, that you know how to restore. Best to get backup religion (which you already have) BEFORE any failure or mistyped commands occur.

I use LVM on my physical servers, but only because the flexibility is required. It also provides a way to have encrypted partitions, if that it important for your portable devices. 

RAID1 has a place here too - mainly as storage for running virtual machines where any failure would "be bad." In the old days, I used RAID5 for media storage. I didn't know better.  These days, media isn't on RAID here.

---

