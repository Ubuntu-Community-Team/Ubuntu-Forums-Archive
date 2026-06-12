---
title: "Making the switch"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by Steve Danahey on 2010-03-11
Tomorrow I am getting a 100 stack of DVDR's to back up all my stuff and a new 1tb hard drive to install ubuntu on. I plan on using my older 250gig hard drive to run XP Pro or Vista strictly for gaming and a separate 10gig hard drive for ubuntu recovery disk. I just have a few questions but before I ask i will list system specs so you can see what i am working with.

Dell 32bit OS Vista Home Premium
AMD Athlon 64 X2 Dual Core Processor 4600+ 2.40GHz
2 gigs ram
NVIDA GEFORCE 7300 LE

For my 1tb hard drive I plan on having a 4gig SWAP ,10 gig OS, but for all my audio/pictures/movies should I create a separate partition for that or just make a large os partition? Since no windows application will be on this hard drive I understand it is best to create all Ext4 partitions am I correct on this? Also being that both OS will be on separate drives does it matter if I install ubuntu first? All my drives are SATA drives so I assume the order in which I connect them does not matter or should I make the master drive the first connected, then ubuntu recovery, then windows drive? Also is my system capable of installing the 64bit ubuntu or should I stick with the 32bit? I will be mostly ripping music /movies, watching hq movies  and sharing through P2P the most, no animation or any other crazy stuff.Thanks for any help..Cant wait to make the switch..:D:D

---

### Post by Ginsu543 on 2010-03-11
I would create a separate data partition in NTFS for all your audio/pictures/movies. That way, you will be able to access those files both in Ubuntu and in Vista. This is how I would partition that 1 TB drive:

1) 20 GB / partition in Ext4
2) 76 GB /home partition in Ext4
3) 4 GB swap partition
4) 900 GB data partition in NTFS

You should have no problems installing 64-bit Ubuntu, so I would go with that. The order in which you install the physical hard drives shouldn't matter, since you can use grub to set up a dual-boot system (to do this you need to set your 1 TB drive with Ubuntu on it as the first drive to boot from in BIOS) or you can just use the BIOS to choose which hard drive to boot from.

---

### Post by underquark on 2010-03-11
You could install Windows on the 250Gb drive using, say, 150Gb.  That would leave room for all the files that Windows games need to install.  Windows likes to be installed first on a disk.

Then create a Live CD (I'd go for 64-bit) and install ubuntu on the rest of that drive (choose to install alongside Windows) with separate OS, Home, swap partitions.  You could keep your non-multi-media documents here.

Leave the 1Tb drive purely as a data bucket.  Format it as NTFS if it will contain photo's, movies etc. that you must access from Windows (say if you have a favourite Windows video editor).  Format it as Ext4 if you have no need to access the data on it from Windows.

There are many ways to things but I think that you already have grasped the main point which is to back up all data first.

---

