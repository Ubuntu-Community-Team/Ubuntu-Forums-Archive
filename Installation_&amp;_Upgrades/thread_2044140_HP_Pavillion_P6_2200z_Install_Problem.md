---
title: "HP Pavillion P6 2200z Install Problem"
date: 2012-08-18
forum: Installation &amp; Upgrades
---

### Post by tm-hart on 2012-08-18
**Installation Problem with Ubuntu 12.04 on an HP Pavillion P6 2200z Desktop Computer.**

I recently purchased a new Pavillion desktop computer and planned to replace Windows-7 with Ubuntu 12.04.  After writing a new download of  &#8220;ubuntu-12.04-desktop-i386.iso&#8221; to a disk, I found that it would not boot the new computer.  Old disks with either Ubuntu 9.10 or Ubuntu 10.04 did boot the machine and were ready to install software.

However, two new disks with Ubuntu 12.04 began the normal boot process and then, apparently, went into the text mode.  They offered me a language choice and promptly crashed.  The HP Pavillion P6 2200z Specs include:

Processor
    AMD E2-3200 dual-core processor [2.4GHz, 1MB L2 Cache]
Memory
    4GB DDR3-1600MHz SDRAM
Hard drive
    500GB 7200 rpm SATA hard drive
Graphics
    Integrated graphics
    512MB AMD HD 7350 [DVI, HDMI, VGA adapter]
Optical drive
    SuperMulti DVD burner

In order to load Ubuntu 12.04 on the new Pavillion, I removed the new hard drive from the new computer and installed it in an older HP desktop.  After booting the older computer with the 12.04 disk, I was able to install the operating system on the new hard drive and make all updates.  After returning the new hard drive to the new computer, it loaded without any problems.

I suspect that the new &#8220;iso&#8221; file that I used to make the 12.04 start up disks is the culprit.  For some reason, it does not work with the Pavillion P6 2200z hardware, although it works on other HP computers.

An alternative approach to hard-disk-ectomy might be to merge appropriate start up files from either the 9.10 or 10.04 disks with the 12.04 system - am not sure how to do that however..

---

### Post by mörgæs on 2012-08-20
Swapping the hard disk is a good, classic method if everything else fails. 

If you want to diagnose the problem further, you could try booting 12.04 from a USB stick.

---

