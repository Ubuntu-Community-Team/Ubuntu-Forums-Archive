---
title: "lost space due to partition problems"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by Jazqas on 2012-05-28
I stuffed around with Ubuntu for a bit, and now have 200gig of my 500 gig hd doing nothing.

I installed ubuntu (10.something) on a separate partition (200gig) then changed my mind and removed it and reset the drive to one partition. then I installed wubi and am currently using 12.04. 
I have just noticed that I am running out of space, but K4DirStat only reports 299 gig used. 
: /

How do I fix this.... please help!

Jaz.

---

### Post by Old_Grey_Wolf on 2012-05-28
WUBI only allows you to use 30 GB.

---

### Post by Mark Phelps on 2012-05-28
Wubi installs Ubuntu inside a file -- which it then treats as a filesystem.  When it reports space stats, it's only reporting on the space inside the file -- not the space in the balance of the partition.

If you take the default space allocation when you install using Wubi, instead of going for the 30GB max, you will quickly run out of space inside the file.

---

### Post by Jazqas on 2012-05-29
Sure the wubi space is small. But it's the rest of the partition that I'm talking about, perhaps I didn't make that clear. 
The total space of the main partition is 452.66 GB.
The total space used by all files from /  including /host  is 298 GB

When downloading, extracting or saving files on /host/foo , I run out of space. :confused:

I'm short on a bit of space somewhere.

Jaz.

---

### Post by anonymous5 on 2012-05-29
> **Jazqas said:**
> Sure the wubi space is small. But it's the rest of the partition that I'm talking about, perhaps I didn't make that clear. 
The total space of the main partition is 452.66 GB.
The total space used by all files from /  including /host  is 298 GB

When downloading, extracting or saving files on /host/foo , I run out of space. :confused:

I'm short on a bit of space somewhere.

Jaz.

When wubi is used your ubuntu root partition can be as large as 30GB. This is not a problem as long as you place your downloaded files, videos... in a separate partition, or in your case somewhere inside the windows partition. First mount the windows partition then you can save your files in it, not in the 30GB partition.

But I've never used wubi, I suggest you do a regular dual boot install ;)

---

### Post by Jazqas on 2012-05-29
> **anonymous5 said:**
> When wubi is used your ubuntu root partition can be as large as 30GB. This is not a problem as long as you place your downloaded files, videos... in a separate partition, or in your case somewhere inside the windows partition. First mount the windows partition then you can save your files in it, not in the 30GB partition.

But I've never used wubi, I suggest you do a regular dual boot install ;)

And for those who still don't understand my problem. I am not trying to save to the linux part of my drive. I am trying to save to the windows side, mounted under /host .

I think the problem is with the partitioning that has been done since the space missing equals the space I had used for linux before I moved back (I had a number of problems with the install so I moved back).

---

### Post by anonymous5 on 2012-05-29
> **Jazqas said:**
> And for those who still don't understand my problem. I am not trying to save to the linux part of my drive. I am trying to save to the windows side, mounted under /host .

I think the problem is with the partitioning that has been done since the space missing equals the space I had used for linux before I moved back (I had a number of problems with the install so I moved back).

Ok, I see. You have unpartitionned space of 200GB. Install gparted in ubuntu, and try to resize the windows partition so that it occupies now the full hdd.

---

### Post by Jazqas on 2012-05-29
> **anonymous5 said:**
> Ok, I see. You have unpartitionned space of 200GB. Install gparted in ubuntu, and try to resize the windows partition so that it occupies now the full hdd.

Gparted reports the unallocated space as 2.49 MB
Not enough for me to worry about.

---

### Post by bcbc on 2012-05-29
What is the output of:
```
df -h
```

---

### Post by Jazqas on 2012-05-29
Ok, found it, it seems K4Dirstat was giving me some funny answers, but the Disk usage analyser has sorted it out.

thanks for the help

---

