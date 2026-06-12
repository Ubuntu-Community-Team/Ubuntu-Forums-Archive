---
title: "Help! Kubuntu 7.10 instantly sabotages whole disk drive."
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2009-12-30
Hello,

I just attempted to add Kubuntu 7.10 to a triple boot windows installation.  It asked which drive to install to (there was only one) and then when I pressed the number 1, it proceeded to overwrite the MBR right off the bat. I stopped the installation after  5 to 10 seconds, and now, sad to say, it simply shows no operating system.  Please advise on the  easiest way to recover and then add Kubuntu.  This is very unlike previous Linux installations and the step by step guide for 7.10 that I read. I was expecting to get to a partitioning screen before any writing would take place.  I had hoped to be able to get to choose an unallocated section of the disk but wasn't given the opportunity.  A prompt reply would be much appreciated as this has put my HTPC down.

---

### Post by lmarmisa on 2009-12-30
Download the Ubuntu 9.10 desktop Live CD and burn a CD-R with it:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Start the Live CD, open a terminal and type this command:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```

This command will restore the MS boot loader in the MBR of your hard drive.

Best regards,

Luis

---

### Post by archp2009 on 2009-12-31
Thanks for the reply.  I found that removing the Kubuntu cd while it was writing to the hard disk and then attempting to run fixmbr from the XP cd screwed the partition tables up so the hard drive could no longer be accessed.  I reformatted the whole disk. Thankfully the installations were new so not much but replaceable software was lost - a day's work, at most.  I have XP back now.  The reason why I chose Kubuntu 7.10 is that I wanted to install LinuxMCE 7.10 on it.  I understood that this was the bestway to go for the MCE package to work. Any further comments on MCE would be appreciated. Is it supported in the newer Linux distros?

---

