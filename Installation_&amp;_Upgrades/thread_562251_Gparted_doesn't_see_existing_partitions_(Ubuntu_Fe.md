---
title: "Gparted doesn't see existing partitions (Ubuntu Feisty/Mint Celena)"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Shane10101 on 2007-09-28
Hello Helpful Ubuntu Friends,

I'm rebuilding a laptop for a[nother] friend of mine - a Dell Inspiron 1100 w/ a Celeron 2.0, & an Intel 845GL chipset. (Complete specs [here]("http://www.atnf.csiro.au/people/Chris.Phillips/Dell_Inspiron_1100.html").)

I used Gparted via the LinuxMint Celena LiveCD -- a derivative of Ubuntu Feisty -- to partition the HD the way I wanted it, and then installed XP on the first ntfs partion; I have a second data partition formatted ntfs that I plan to share between the two OSs, followed by my variously-arranged Linux partitions.

Unfortunately, now that it's time to install Mint, I can't get Gparted to recognize the existing partitions! I've tried selecting "partition manually" during the install sequence, but I'm only able to see /dev/sda as a whole -- not as a partitioned drive. (It's recognized as having its full 80G still "free", despite the Windows installation.) I've also tried to view the drive by running Gparted from within the LiveCD environment, but with the same result -- no partitions recognized; just an allegedly "empty" drive.**  I'm getting the same exact result when I use the Ubuntu Feisty liveCD.**

Strangely, I am able to mount, unmount, read from, and write to both the ntfs partitions while running Mint from the LiveCD. It's just the partitioner that seems to be having the problem.  Any suggestions?? I'd appreciate them!

Thanks!

Shane
::Cross-posted to the LinuxMint forum [here]("http://linuxmint.com/forum/viewtopic.php?p=35859#35859")::

---

### Post by Pumalite on 2007-09-28
Can you see XP installed in sda?

---

### Post by Shane10101 on 2007-09-28
Yep, I can see XP installed on sda.  It even mounts the two ntfs partitions correctly when I boot from the LiveCD.  I can read & write to both, and all my XP & data files are where they should be.

I'm running a diagnostic on my HD right now.  Some goooooogling on the subject leads me to suspect that there's a problem with the partition table, and that XP is just being its overly-forgiving self & running fine despite the problem.  I'm also downloading an older version of Ubuntu (6.06) to see if there's some weird, undiscovered problem with gparted & Feisty, though I doubt it.  

I'll post the results once I know something more.

Thanks!

Shane

---

### Post by Pumalite on 2007-09-28
From Live CD or Mint, post: 
sudo fdisk -lu

---

### Post by Shane10101 on 2007-09-28
Hmm.  Something's definitely not right about this.  (Results from fdisk -lu):

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    36869174    18434556    7  HPFS/NTFS
/dev/sda2        36869175   125066024    44098425    f  W95 Ext'd (LBA)
/dev/sda3       125066025   155782304    15358140   83  Linux
/dev/sda4       155782305   156296384      257040   83  Linux
/dev/sda5        36869238   125066024    44098393+   6  FAT16

Isn't this telling me sda2 isn't formatted ntfs anymore?  Ugg.  What'd I do?!  :(

---

### Post by Shane10101 on 2007-09-28
Yep, I think I've managed to wipe out my data partition somehow.  Booting from the HD (into XP) is throwing all kinds of errors -- the kind you get when all your user profiles are gone (or just very hidden.)  

Fortunately, this is only a day-old install of XP -- not that big a loss.  I think I may be better off starting over, rather than trying to recover the data...unless you know of a quick & easy way to do so.  I just wish I knew what happened -- so I don't do it again!  ;)  

Thanks again for your help, Pumalite.  I do appreciate it!

Shane

---

### Post by Pumalite on 2007-09-28
I you can satart from scratch, that is best. Install XP first, defrag seral times, then use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone. burn to CD, boot from, program).Boot from it, right click on XP partition and from the menu, choose resize partitiom. From that newly created partitiom, you can create others if you want. Windows needs primary partition, but Ubuntu and other Linux are happy on logical or extended ones.

---

### Post by jordoex on 2007-10-01
I have the same problem but I'd rather not reinstall... Any help?
I'll try the official gparted live cd.

---

### Post by Pumalite on 2007-10-01
Explain your problem in detail.

---

