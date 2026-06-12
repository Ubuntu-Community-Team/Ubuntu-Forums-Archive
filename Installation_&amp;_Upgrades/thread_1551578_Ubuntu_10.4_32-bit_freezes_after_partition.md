---
title: "Ubuntu 10.4 32-bit freezes after partition"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by HobbDogg on 2010-08-12
I have been trying to install Ubuntu for about 2 days now. First I downloaded and burnt to a Disc Ubuntu 10.4 32-bit i386, the process of booting into the Live CD would freeze the computer. So....I downloaded the alternate install of the same Distro/etc. I have deleted all of the partitions to create the Free space on the hard drive then use the "guided" option for installation. Ubuntu partitions the ext4 and the swap space, but freezes at a blue screen right after and does not proceed with the installation.

I read somewhere that it is possible if there was ever a RAID configuration that there is possibly some META data left over on the Hard drive that needs to be erased. If this is the case I believe I have the command that will do so....BUT I do not know how to get to a terminal from the alternate install CD....is it possible? If so how do I get there?

If there is anything else that I can provide or if there is any other recommendations please let me know. Thanks in advance

---

### Post by dabl on 2010-08-12
> **HobbDogg said:**
> I have been trying to install Ubuntu for about 2 days now.



Congratulations -- you are building "character".  :D

I have a couple of notions that may or may not help -- kinda depends on some things I don't know about your system and intentions.

1. I find it helpful/stress-reducing to do partitioning in advance of installing, and using a tool made for the purpose.  There's a Gparted Live CD, but my favorite is [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://partedmagic.com/), mainly because of the other tools on the CD (or USB stick, as I use it).

2. In your BIOS, you need to review the SATA settings, and make sure any built-in "RAID" capability is disabled.  Also, on some motherboards, the *buntu installer gags on "AHCI" mode for the SATA bus, so you might need to change it to "Legacy IDE" or whatever the alternative is.  After installation, you can set it back to AHCI and it should be fine.

3. If there is no data or partitioning on the hard drive, at all, you can "zeroize" it with the "dd" command.  From a booted Live CD, open a terminal and issue (as root, or with "sudo"):

```
dd if=/dev/zero of=/dev/sd_x_ bs=512 count=1
```

where "x" is the device letter of the drive that you plan to partition and install on

NOTE: -- Be careful! -- Don't do this if there is any doubt whatsoever about the ID of your target disk/device -- it will nuke the partition table (and all data) on the device!

Then, after you have "dd" it, you can boot your Parted Magic CD or USB stick, set the partition table type to "MS-DOS", and proceed with partitioning, and formatting the filesystems.  Then as the last step, you can boot your Alternate Install CD, and install Ubuntu.

p.s. "Frozen" installation routines are often indicative of a defective CD, and defective CDs are often indicative of a user who did not set the burn speed to the lowest speed available when burning the ISO image.  ;-)

---

