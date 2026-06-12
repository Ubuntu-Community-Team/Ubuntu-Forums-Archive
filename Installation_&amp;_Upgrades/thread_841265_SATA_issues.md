---
title: "SATA issues?"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by allanlewis on 2008-06-26
I'm planning on building a new PC with an SATA HDD and I recall people having problems installing various versions of Ubuntu on SATA drives. I searched the forums and it seems that different people are different problems, but I'm not clear if these problems are entirely due to the SATA or if it's specific SATA controllers/chipsets/motherboards playing up. (Such posts include #788856 and #822859.)

So, can someone post a quick summary of issues that can occur when installing Ubuntu (primarily Hardy) onto SATA drives? (Some of the problems seem to be with multiple hard drives, especially a mixture of SATA and IDE/PATA, which isn't my situation.)

Also, is anyone aware of any problems arising from installing Ubuntu from an SATA DVD drive (to any type of hard drive)?

---

### Post by PmDematagoda on 2008-06-26
I have two SATA drives and Ubuntu works very well with both of them, so them problem must be down to specific SATA controllers that may not play that well with Linux, but usually(in my opinion), SATA works well with Linux so the install should go well for you unless you are really unlucky.

---

### Post by suri.mahendra on 2008-07-10
Hi,

My SATA HD is a Seagate.  Dumped Hardy on it and booted no problem.  I am having some difficulty locating a SATA DVD burner that will work with Hardy.  So far steer clear of LG.

---

### Post by charonred on 2008-07-10
and my 2 cents 2;

My preference these days is to install other OSs to seperate drives rather than partitioning a drive for different OSs - otherwise, if/when things go wrong, you can mess up healthy OSs in the process of fixing broken ones.

My experience with multiple sata drives (and 1 pata/ide) is that GRUB seems to drop the bootloader on the first drive, regardless of which drive you are installing Ubuntu - and I think this is what it is supposed to do.

So if you have XP or Vista on your first drive, your bootloader gets replaced with the GRUB one, and it may or may not provide a 'working' boot option for existing OSs, especially if they are on other drives.

I have my pata, and 2 sata, in removable bays so I can swap in other drives when needed (storage etc.), with 2 other sata fixed inside PC - if I swapped out the pata, which had the bootloader on, then I couldn't boot anything.

My solution, not a favoured one, but effective, was to disconnect all other drives not having Ubuntu installed on, then reconnect them after install is complete. 

Most modern boards offer a 'boot choice' when starting - with Gigabyte m/boards this is the F12 whilst booting PC. 

With this feature you no longer need to have a bootloader to manage different OS installs if they are on different drives.

However, you still need a multi OS bootloader (GRUB or other) if you are partitioning drives for multi OS installs.

If you also have other physical drives, then I would still unplug them till the install is done - just to make sure the bootloader goes on the multi OS disk, and not another drive.

---

### Post by allanlewis on 2008-07-11
Thanks for all the replies.

Has anyone found an SATA DVD writer that works reliably with Hardy? I'm looking at the [Samsung S203P]("http://www.novatech.co.uk/novatech/specpage.html?SAM-S203P") at the moment.

---

### Post by mc4man on 2008-07-12
> Has anyone found an SATA DVD writer that works reliably with Hardy
I'm going to do the same as you next month. My inclination is to get a sata dvd drive based on the quality and performance of the drive. While there are certainly a number of posts concerning sata dvd drives not being recognized, I can't believe it's solely due to the make and model of the drive. And that is the only issue, once it's recognized you can get it to work one way or the other.

I have to think it's more a matter of hardware configuration, in general and at time of install, with a very slight possibility that the hardware chosen will have an issue no matter what.

What I'm thinking is to have a couple of sata hdd's, a sata dvd drive and an ide dvd drive. The ide dvd drive will be what I install the Os from. (set in bios as the boot capable cdrom). Probably will start by booting to the live cd and see if the sata drive is detected, if so great, copy the contents of a couple of files for reference and do the install. If not then time to get creative.

---

