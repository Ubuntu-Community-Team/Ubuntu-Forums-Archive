---
title: "Third-party partition manager that I could burn to CD?!?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by DeaconBlues on 2008-05-24
I've been using ubuntu since Gutsy and I think it's a fantastic, erm "thing". One thing that's always annoyed me is the text-based partition manager when you first install though.

It's fine if you only have 1 hard drive, as I installed it on a mates laptop without a problem, but if you're trying to configure RAID it's horrible.

One of the main things I'd hoped the developers would improve would be to update the partitioner with Gutsy: it seems that it's exactly the same one.

I've had Hardy Heron working from install with the following setup:

100Gb root : 2 x 50Gb RAID0 partitions
200Gb home : 2 x 100Gb RAID0 partitions

300Gb spare drive used for music and TV shows - older SATA 1 drive.

I've been messing about with dual-booting recently and I thought I'd start from scratch but I couldn't get the partition utility to get me back to how I used to have my drives.

Every time I rebooted to wipe my RAID drives (leaving my media drive intact, of course) Linux would remember the partition setup I had aborted during the previous installation!

So I thought "sod this, I WILL reset my hard-drives, Linux!": I turned on Hardware RAID on my motherboard and configured an array using my BIOS, which should theoretically wipe both hard drives (?).

Then I got an old, cracked, copy of Windows XP out which I've had for aeons and used to work fine. It picked up my hardware RAID array fine and asked me if I wanted to wipe the drives. I said "yeah" and started to install XP...

I waited until the blue XP installation screen started rapidly copying over the O/S files, thinking "get in! My master boot record/partition tables/file allocation table are surely overwritten now!" and cut the power to my PC half-way through the XP installation.

When I restarted I went back into BIOS and diabled hardware RAID, since I used to have Ubuntu working fine on my old software RAID setup, and then rebooted with the ubuntu alternate install CD in my drive.

I thought after a part install that Ubuntu would see a corrupt file system, start from scratch, and reformat the drives that I wanted to use as an array.

But no! It still saw my old RAID array!! How is this possible? I deliberately buggered my FAT and partition information on my drives and then restarted from CD!

Is there a partition table that Linux uses that Windows doesn't overwrite or something?

Specs:

Motherboard: Gigabyte GA-965P-DS3P (flashed to beta BIOS to accommodate my new CPU)

CPU: Intel Core 2 Quad Q9300

RAM: 2 Gb of 667Mhz, dual channel

GPU: eVGA 8600GT

Drives:

2 x Western Digital 250Gb SATA II, which I use for RAID, identical drives -plugged into SATA ports 1 & 2 on mobo.

1 x Maxtor 300Gb SATA I for music/videos -plugged into SATA 4, I think, on mobo.

---

### Post by Mark_in_Hollywood on 2008-05-24
I can't respond to the entire set of issues, I can suggest using GParted LiveCD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

download, check integrity and re-boot. GParted will load and you can find all your devices, drives, memory sticks (usb or jump drives), anything that can be formatted or partitioned.

Good luck.

---

### Post by imhdd on 2008-05-24
I dual boot Windows 98SE 4 partitions, and Ubuntu 6.06 3 partitions plus swap. I tried to install Ubuntu 8.04 - the partitioner insisted on using the entire disk - again and again - on two computers - using both the Live CD and downloaded ISO. 

I've always had trouble with the Ubuntu partitioner. I always try it to see if it's improved - then I boot up with the old Mandrake 9.1 installation CD. It shows me graphically exactly what my partitions are and all needed info about them.

Using Mandrake, I leave my Windows partitions as is. I wipe out the three old Ubuntu partitions and make one large ext3 partition out of them, mark the new large partition as / and format. 

As Mandrake begins to install programs, I hit my stop button, remove the Mandrake CD and insert the Ubuntu 8.04 CD, boot up, and let it install. When it reaches the Ubuntu partitioner it now gives me the opportunity to manually set up my 3 Ubuntu partitions. Then I finish the install. Why Ubuntu does this, I have no idea. Maybe it's my computers? It doesn't happen to everyone obviously.

I'm not a novice with computers - but I'm somewhat of a novice with Linux. 
I have 2 computers, more than enough memory, 5, 80Gb hard drives which are all cloned with my Windows and Ubuntu 6.06 and I'm retired - so I can experiment all I wish. After 4 days of trying to get gparted to work in Ubuntu I gave up and returned to the Mandrake partitioner which is simple and it always works.

I suppose then, any good third party partitioner should accomplish the same.

Good luck.

---

### Post by DeaconBlues on 2008-05-24
> **imhdd said:**
> I'm not a novice with computers - but I'm somewhat of a novice with Linux. 
I have 2 computers, more than enough memory, 5, 80Gb hard drives which are all cloned with my Windows and Ubuntu 6.06 and I'm retired - so I can experiment all I wish. After 4 days of trying to get gparted to work in Ubuntu I gave up and returned to the Mandrake partitioner which is simple and it always works.

I suppose then, any good third party partitioner should accomplish the same.

Good luck.

Heh, I totally agree with you. I myself come from an electronics background (I'm a tank engineer in the British Army). It's quite infuriating when Canonical have such an awesome, configurable product, but don't cater for us geeks that like to set up RAID parts!

I like frittering about with electronics and swapping boards and so forth, it's partly a hobby. But it's annoying when a piece of software doesn't do what you tell it to do!

I'll stay with Ubuntu because it's a fantastic distro for people like me, who are just getting into Linux. I'm going to download Mandrake purely to use as a partition program.

A re-instatement: the text partitioner that comes with Ubuntu sucks!

If I have success tomorrow I'll post back to this thread. I'm no good for installing O/S at them moment. 1 bottle of wine too many.

---

### Post by DeaconBlues on 2008-05-25
> **imhdd said:**
> As Mandrake begins to install programs, I hit my stop button, remove the Mandrake CD and insert the Ubuntu 8.04 CD, boot up, and let it install. When it reaches the Ubuntu partitioner it now gives me the opportunity to manually set up my 3 Ubuntu partitions. Then I finish the install. Why Ubuntu does this, I have no idea. Maybe it's my computers? It doesn't happen to everyone obviously.

Brilliant advice. I downloaded the Mandriva install CD this morning and used that to reset the partitions on my drives. I still couldn't format RAID working though, because Mandriva insisted on installing mdadm, even though there was nowhere to install it to! So I set up my partitions as I wanted them, let Mandriva format them and then swapped disks back to my Ubuntu when it restarted my computer.

I'd advise any Ubuntu user to use this method. It only took me 30 minutes to download and install the Mandriva CD,

---

### Post by Pumalite on 2008-05-25
The Gparted Live CD is the best partitioner around.

---

