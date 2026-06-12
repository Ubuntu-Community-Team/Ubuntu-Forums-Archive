---
title: "Linux equivalent of the DOS diskpart /clean command?"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by junk.here on 2013-11-17
I've been switching OSes every few days these past 2 weeks, and every time I've first stuck a Windows 7 DVD in and ran diskpart /clean in order to make the next OS installation a bit smoother (at the very least I don't get asked if I'm sure I want to obliterate all existing data and at the very worst I don't have the OS installer freaking out on me because it can't delete the existing partitions for whatever reason). In light of that, I'm wondering if there's a Linux equivalent of the diskpart /clean command?

---

### Post by oldfred on 2013-11-17
If you just want to delete partitions, use gparted from Ubuntu live installer or just about any Linux repairISO or download gparted or parted magic ISOs.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You can also use command line tools like fdisk for MBR, parted or gdisk for gpt partitioned drives.
Use man command for more info.
man parted

If you want secure erase.
The brute force method is dd, but I will not post example as any typo and you destroy data.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

There are many applications for secure erase like wipe,secure-delete and others.

---

### Post by Bashing-om on 2013-11-17
n/m, oldfred beat me too it ..
Better said than I had in mind !

[INDENT]ubuntu, all things are possible
[/INDENT]

---

