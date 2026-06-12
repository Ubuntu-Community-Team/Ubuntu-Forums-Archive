---
title: "LBA out of range, partition manager"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by cecida on 2007-07-30
Folks,

Trying to install Ubuntu 7.03 in a dual-boot configuration with XP. Loading the live CD desktop, and running the partition manager. Want to resize the XP partition, and create a partition with the free space created as a result. I can get to the confirm screen, but when I continue, I get the message "LBA out of range". I then ran Cute partition manager from a bootable CD, tried to edit the same partition, and got the error message "LBA out of range". 

I have ran a SMART test, and some diagnostics on the disk, and no errors were found, no bad sectors. The thing is, this is a work laptop, it has symantec client security installed, a locked down policy, and general restrictions. I also notice an unnamed 8MB partition on the disk. I was just throwing it out, that it may be some type of low level encryption utility? Nothing in the BIOS to indicate any low level protection, and I am not asked for any password apart from the usual XP login screen.

Finally I notice, that when running Disk Management in XP, I cannot delete the primary partition, make the partition active and so forth. Now once again, this is probably a policy setting, but I'm pretty clueless as to what could be causing the issue. Can anyone shed any light?

---

### Post by Pumalite on 2007-07-30
Your 'small partition' is probably a 'rescue partition'. First defrag XP several times,erase all temp files. Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Resize your windows partition and install. Be careful with the 'small partition'. Best thing would be to get OEM XP disk. You can use your old key.

---

### Post by cecida on 2007-07-30
Hi,

I doubt its a rescue partition, we ghost and image over the network so no need for a rescue disk. I can't see how defragmenting XP will make any difference. Gparted would work on the disk level, not the OS, so the state of the OS, or its position on disk would not make any difference. Its like the MBR is beyond a certain range or something, or else the disk is being 'protected'

---

### Post by Pumalite on 2007-07-30
[http://ubuntuforums.org/showthread.php?t=480484](http://ubuntuforums.org/showthread.php?t=480484)

---

### Post by Pumalite on 2007-07-30
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by cecida on 2007-07-31
Hi folks,

So does anyone know what this "LBA 0ut of range" message means? So far I have used G-Parted, Cute Partition Manager, and the partition manager within Ubuntu (G-Parted as well?), and each time I try to resize the windows partition I get the same message, or a general error, a cannot continue with this operation style message. Now if this way my own laptop, I'd just format the partition and slice the disk into whatever I wanted, but this is not an option with the work laptop (custom applications and so forth).

---

### Post by Pumalite on 2007-07-31
[http://en.wikipedia.org/wiki/Logical_block_addressing](http://en.wikipedia.org/wiki/Logical_block_addressing)

---

