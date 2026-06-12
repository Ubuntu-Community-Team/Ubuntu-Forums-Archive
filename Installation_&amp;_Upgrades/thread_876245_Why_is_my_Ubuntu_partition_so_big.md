---
title: "Why is my Ubuntu partition so big"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by coober85 on 2008-07-31
Hey y'all making the move to linux was tough at first but now I spend 99% of my time on it! here's a quick question:

why is my hard drive so full of stuff? I allocated something like 19Gb worth of space and I check my filesystem partition and its like >50% full? says I have 7.7gb of free space left. what gives? I have ~10 pictures, evolution mail (with only about 70 emails  in the inbox) and a few extra programs (amorok and teeworlds). people say ubuntu takes up less space than xp but this doesn't seem to be the case. I have 8.04 LTS version which seems to come with a lot of software preinstalled (and it wont let me delete a lot of them because other programs rely on them or something). 

I have plenty of space on a removable second internal hard drive (~80GB) if worst comes to worst how can I transfer this partition on my C drive to my E drive (2nd internal)

thanks a lot guys and girls

---

### Post by mattduckman on 2008-07-31
that is odd, since on my system, everything except for /home takes up 3.3 GB.

you have emptied your trash right?

you also may want to try
```

sudo apt-get autoremove
audo apt-get autoclean

```
to get rid of unneeded packages and archives.

also there's a tool called something like Disk Usage Analyzer somewhere in the menus (i think accessories), and if you push scan filesystem and wait a while, it'll tell you where all your disk space is going to

---

### Post by coober85 on 2008-07-31
Yeah I tried auto remove. worked, but said there was nothing to do. Did the disk usage checker and it confused me. as far as I can remember heres my breakdown of partitions on my C Drive: 

80gb total 
---------
~7GB for XP
~50GB for program Files and Data (Music and xp programs basically) 
~18GB for Ubuntu (what happened to this partition in the picture?)
~2GB swap

On the file usage app
it seems to disregard my XP partition and lump my 50gb P. Files and Data and my filesystem together. and then at the top it says ~50 used 30 free. confusing! I have a feeling I'm just not reading it right, because everything outside of P. files and data totals about 3-4Gb.

I'm also loading a print screen of the properties for file system

Thanks for the help. God Bless

---

### Post by mattduckman on 2008-07-31
you're right, it is confusing, and things aren't really adding up. can you open a terminal are do
```
df -h
```
and post the output?

---

### Post by R Clemons on 2008-07-31
Ok, it appears that Disk Usage Analyzer analyzes the entire hdd(which is convenient) and everything in media is from your other partitions.  Your Ubuntu partition is everything outside of media

---

### Post by coober85 on 2008-07-31
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              13G  4.5G  7.7G  37% /
varrun                998M  124K  997M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   80K  997M   1% /dev
devshm                998M  536K  997M   1% /dev/shm
lrm                   998M   39M  959M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              11G  6.2G  4.0G  61% /media/disk
gvfs-fuse-daemon       13G  4.5G  7.7G  37% /home/leon/.gvfs
/dev/sda5              50G   38G   12G  76% /media/Programs and Data

this is the output
--
yeah I realize that everything in media is not my ubuntu partition. prob is properties display says I'm using 11Gb and I don't know what they're talking about

---

### Post by R Clemons on 2008-07-31
The partition is only 13 Gbs, that's why you have such little space left.

---

### Post by mattduckman on 2008-07-31
yeah, so your ubuntu partition isn't 18 GB like you thought, it's only 13 GB, which is why there's only 7.7 GB available. if you want to check the size of your partitions, use "sudo fdisk -l" or System Monitor if you don't like the the command line.

---

### Post by coober85 on 2008-07-31
well I cant remember exactly how big it is exactly (know its over 10Gb thought it was close to 20Gb). if you say I have 13gb and I've used up 11Gb, why does filesystem properties say I have 7.7gb left?

OK so I made it 13gb (sorry if I forgot guys)... and I've used ~6Gb and I have 7Gb left. why does it say under contents - ~350,000 files totaling **17Gb**? I'm just confused and I'd like to sort this out so I can help others, its not a big deal and I thank you two for the help very much

---

### Post by R Clemons on 2008-07-31
> **coober85 said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              13G  4.5G  7.7G  37% /
varrun                998M  124K  997M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M   80K  997M   1% /dev
devshm                998M  536K  997M   1% /dev/shm
lrm                   998M   39M  959M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              11G  6.2G  4.0G  61% /media/disk
gvfs-fuse-daemon       13G  4.5G  7.7G  37% /home/leon/.gvfs
/dev/sda5              50G   38G   12G  76% /media/Programs and Data

this is the output
--
yeah I realize that everything in media is not my ubuntu partition. prob is properties display says I'm using 11Gb and I don't know what they're talking about

if you look at the first line you have only filled 4.5G

---

### Post by coober85 on 2008-07-31
OK you know what it is I think? I set up 13gb for the partition. I HAD ~17Gb left to work with but I made it smaller for some reason (emergency space). there's about 7gbs of unpartitioned space left on my 80 gb hardrive. it was confusing because there is ~7gbs of free space left on my  Ubuntu partition and theres about 7Gbs of unpartitioned space as well! 

so to review:

~76Gb total
----------
10.8 Gb of XP partition
50GB of data

13Gb = Ubuntu partition
-4.5GB Used
-7.7GB Free
-might include the Ram partition (1-2Gb)

Unpartitioned space
~6-7GB

6-7GB of unpartitioned space + 4.5GB = ~11GB NOT FREE

7.7Gb + 4.5Gb + 1-2Gbb + 6-7Gb unpartitioned space = ~17Gb Total space

That still may be wrong for all I know! I'm just glad I've only used 4.5GB of space and not 11Gb

---

