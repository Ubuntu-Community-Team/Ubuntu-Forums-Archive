---
title: "Problems installing Latest Ubuntu 8.10"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by ctcabm on 2008-11-09
I have been trying to install the latest Ubuntu straight from the cd to a clean hard drive.
These are the steps that I have taken but they have all failed
1. I used the alternate  install cd and  checked the md5 sums-they were good
2. used RW-CD at slow burn using ImGBurn and md5-checked the contents- all good.
The Problem is that I goes as far as 6 percent in the installing programs then freezes and about an hour later says that there was an error.
The strange thing is that I have used both the regular install cd and the alternate install CD to no avail.
Also strange is that the Ubuntu 8.04.1 installs worked fine so I am stuck with 8.04.1

Any suggestion would be greatly appreciated

below are my system stats
Pentium 4 2.8 GHz
1 gig of ram
500 GB WD BARRACUDA Sata drive

---

### Post by Topsiho on 2008-11-09
You say you installed Ubuntu 8.04.1 without problem, so you are not new to installing Ubuntu.
You say you tried to install on a clean hard drive? What do you mean with that? Was Ubuntu 8.04.1 not installed on a clean hard drive?

When installing you should either let the install program do the partitioning of the hard disk, or, better, do it manually, creating a /home partition (ext3, not too small, let's say 10 GiB), a swap partition of twice your RAM memory, and the rest for your /home partition, also ext3.

If you did all of these an it is just a piece of cake for you, then I suggest that you stick with 8.04.1 (reinstall), nothing wrong with that, and it will be supported longer, as it is an LTS version :)

Topsiho

---

### Post by ctcabm on 2008-11-09
Thank you for responding

To answer your first question-by clean hard drive I mean that I used Gparted-live cd to delete all the partitions on the drive so that there were none left.

The problem I am having is that it goes through all the steps- it partitions fine but when it starts installing the base system I hangs at 6%.

I will probably stay with 8.04.1 but I just wanted to check out the newest release.:smile:

---

### Post by Topsiho on 2008-11-10
I have not any idea what may be the cause of all this. If the installing hangs at 6%, the only thing I can think of (but I am not an expert by a long shot) is that a. a file can not be found or parsed, which would mean that your CD is not quite perfect, or b. there is not room enough to install the files from the CD in, which would mean that your / partition is (way) too small (or non-existent? You did define a root partition did you? You should define the mount points during the install, where you are partitioning your disk)

Anyway, if reinstalling Ubuntu 8.04.1 goes well, I would stick with that. Hardy 8.04.1 is quite OK (which I sadly can not say of the first release, Hardy 8.04, which froze repeatedly on several of my computers.

Topsiho

---

