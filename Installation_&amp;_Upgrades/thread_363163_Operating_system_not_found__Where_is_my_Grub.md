---
title: "Operating system not found ? Where is my Grub ?"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by linOOb123 on 2007-02-16
Hallo everyone,

i have a big problem after installing kubuntu on my Laptop (acer aspire 1690).
I already had windows xp prof and i wanted to use both windows and kubuntu.

I took the alternate-i386-CD because i didn't want to make changes in the Master Boot Record in order to be able to backup my windows system easily... (what I have to do often)

The partitions on my 80GB harddisk before installation were:

hda1    20GB    fat32     windows xp     
hda5    30GB    fat32     files
hda6    100MB  ext3      /boot
hda7    1 GB     swap
hda8    10GB    ext3     /
hda9    15GB    ext3     /home

(I made the partitions with the installation-programm of windows xp, that i installed at first on my system)
hda1 is a primary-partition... the others are all logical drives.

Before formating a cluster-error occured... it said that the original size of one partition was a few cluster (i think about 100 clusters) bigger... i ignored it and the installation completed without any more errors. When i was asked, where to put Grub, i said "hda6". The installation of Grub was also succesfull.

But after reboot the following errors occured:
```

PXE-E61 Media test failure check
PXE-E0 ....blabla... broadcom something else

Operating System not found.

```

Finally i got rid of the PXE-Error by disabling booting from network in the BIOS.
But still my operating system is not found.

What should I do... Isn't it possible to write Grub into an own partition?  :confused: 
Do I have to reistall everything ?

I'm a complete nOOb to Ubuntu. I searched in several forums, but didn't find an answer...
I hope you can help (and I hope my english is good enough to understand) :)

---

### Post by CroEragon on 2007-02-17
You didn't make changes to MBR??? i don't get it, how did you expect to be able to boot ubuntu?? Or i musunderstood something??? About problem, i asume something went wrong with partitioning (just to let you know, i have never had success in partitioning from windows, no matter if i use Partition magic or anything else). 
Anyway, i have never encountered or read about similar problem, best thing would be to boot live cd and mount windows partition and backup everything. After then get system rescue cd and wipe  all partitions including windows one. And then do everything again.
Just note, whole process can take up to 5 hours to do including installing windows and ubuntu updating and so on. At leas it took me that long.

---

### Post by Herman on 2007-02-17
Hello linOOb123, 
You need a good boot manager,... [GAG Boot Manager]("http://gag.sourceforge.net/")! :)

Read about GAG Boot Manager here: [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Regards, Herman :)

---

