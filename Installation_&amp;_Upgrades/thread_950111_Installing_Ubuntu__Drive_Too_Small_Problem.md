---
title: "Installing Ubuntu  Drive Too Small Problem"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Arukas on 2008-10-16
A while back, I installed an older version on ubuntu on a computer and had no problems.  I am now trying to install ubuntu on my computer, the current version from just download from the website, and I am having problems.

My problem is when is when I get to the partitioner, I choose guided resize.  It gives my 160 to windows and takes 120 for itself.  My problem is it keeps saying "too small"  I know 120 gigs is more than enough for ubuntu, does anyone know what the problem is?

---

### Post by Partyboi2 on 2008-10-16
Have you tried manually creating the partitions?

---

### Post by Arukas on 2008-10-16
No I haven't.  I have no clue how to do that.  Plus I don't want to lose the data on my hard drive.

---

### Post by Arukas on 2008-10-16
I had 140 Gigs of free space on my harddrive and tried, and I gave Ubuntu 120, and it said it was to small.  So I gave it 100, and apparently it thought that was fine, don't really understand it.  But that's what I did to solve my own problem.

---

### Post by Partyboi2 on 2008-10-16
If you want to shrink down ubuntu after it is installed you can do this by using gparted on the live cd (System>Admin>Partition Editor)

---

### Post by sh_son on 2008-10-16
That's strange, I have 16GB Verbatim memory-stick with Ubuntu 8.04 installed without any problem.

It uses 1.6Gb for EXT3(Swap) and rest for EXT2(Ubuntu) partition, I have installed number of applications I often use, it runs pretty slow though but it works great. Maybe possible cause of the message 'Too small' would be wrong partition being selected? Because 120Gb is big enough for Ubuntu or any other OS.

If I was in your situation, IF there is no other data that is important, I would wipe the entire hard drive and use it only for Ubuntu. But that's just my case;

---

