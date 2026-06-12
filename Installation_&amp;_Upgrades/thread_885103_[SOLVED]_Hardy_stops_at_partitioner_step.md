---
title: "[SOLVED] Hardy stops at partitioner step"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by steve.knoblock on 2008-08-09
Everything goes okay in the Hardy desktop install CD until I get to the partition step. It shows the progress bar right away up to 46% and then stays there. I can see the partitioner dialog with grayed out buttons, but the progress bar goes away and never completes.

I let XP create two partitions, one for XP and an 8GB one for linux (I was going to install damn small linux, but it has some trouble with my wireless keyboard).

I can run the live desktop but gParted also says no drives detected.

Any ideas?

My system

E8400
ASUS P5Q
4GB Corsair
nVidia 9600GT
250GB WD SATA

---

### Post by spiderbatdad on 2008-08-09
Just saw another post with a similar problem. Did you defrag xp prior to attmepting to install, regardless or whether xp says it doesnt need to be defragged. Also you might try the gparted live cd to create partitions.

---

### Post by steve.knoblock on 2008-08-10
I just completed defrag of XP and booted into the Hardy desktop install screen. It gets to partitioner and goes to 46% and says scanning disks. After a while the display closes and the partitioner screen remains empty of any partitions and buttons grayed out.

Given it stops at about 50% and I have two drives in the system, one SATA HD and one IDE CDROM, it may see the CDROM but not the HD.

I may try connecting a HD to the IDE cable.

Edit: Out of curiosity, I decided to plug in a 16MB USB thumbdrive I had laying around while the installer was open. It detected it immediately and advanced to the screen asking me how to setup a partition. I do not think it is seeing the SATA drive. Maybe it only sees ATA drives?

---

### Post by Evolution-42 on 2008-08-10
I'm having the exact same problem. Partition check stops at 46%, and no drives are recognized. I have one SATA drive. I am trying to set up a dual boot system. I've done this once before with Hardy on a system with IDE drives and had no problems.

After building a new system (Asus m3n78 pro MB, AMD 4850e CPU, 250 GB SATA HDD, 4 GB DDR2 800 RAM, NVIDIA 6800 video card) I installed Win XP. Did some minor overclocking of ~7%...rock steady for 24 hours. Note, Express Gate is configured and works seamlessly. Then I defragged the HDD.

Loaded a live CD of Hardy and tried to install from the desktop as I had done on the other system, but It couldn't seem to find the SATA drive. As I stated above, Gparted scanned the system up to "46%", then grayed out all options and I could go no further.

I repeated the process with a Mint 5 live CD and had the same results.

I fired up a Parted Magic Live(3.0) CD and was able to find the SATA HDD. I was able to partition the drive (NTFS 78GB, ext3 10GB, swap 2GB, ext3 143GB). I wanted to make the ext3 partitions into the "/", and"/home" but was unable to find the options to do this using the included GParted. 

I then went back to the Hardy Live CD (and the Mint 5 CD) and tried both installing from the Live environment desktop install, and the direct install (on Hardy only) without going to the Live desktop. In all three attempts (and another three after that) I stalled at the same point where the partition manager (GParted) could not seem to find the drive.

I also tried a GParted Live 0.3.7-7 CD to see if I could get the partition process to go any further...or just to see if I could figure something out...but it couldn't find the drive at all. 

My best guess is that this is a compatibility problem between Hardy or GParted, and SATA drives, the ASUS MB in general, or maybe the presence of EXPRESS GATE in the ASUS MB bios. I'm a Linux noob however, and I really have no idea what I'm talking about.

---

### Post by Evolution-42 on 2008-08-10
Additional info to my post above:

I ran testdisk which identified all four partitions as above, no errors.

Also, the bios is set for SATA OPERATION MODE:IDE, AHCI is off, no RAID.

---

### Post by steve.knoblock on 2008-08-10
My solution (from a user in another thread) was to add 

```
all_generic_ide
```

to the boot options. I did this by pressing F6 at the option screen (where it asks if you want to Install) and adding it to the end of the string past the -- part. My BIOS reports all Sata drives in IDE configuration. See this thread [http://ubuntuforums.org/showthread.php?t=818167]("http://ubuntuforums.org/showthread.php?t=818167")

It recognized my 250GB Sata drive with XP and one free space partition. I was able to partition free space and install. I could not see a way to resize the XP partition non-destructively to gain more space. The original partition was intended for damn small linux so it was 8GB, but I was able to squeeze Ubuntu onto it. A good start.

BTW I wondered how to specify a swap partition, until I noticed you select this from the _file type_ option menu.

---

### Post by spiderbatdad on 2008-08-10
nice post. I forgot about that option.
Also there is a "Thread Tools" menu at the top of this window to mark your thread as solved. Thanks for telling us how you did it.

---

### Post by Evolution-42 on 2008-08-10
Excellent!

That did the trick.

Thanks.

---

