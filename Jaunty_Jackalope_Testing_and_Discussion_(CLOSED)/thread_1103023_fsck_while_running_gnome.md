---
title: "fsck while running gnome"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by WitchCraft on 2009-03-22
Can I have gnome running while running fsck?
 Of course that means I have to unmount the root filesystem...

???

I recently updated my OS, and now a few icons are gone...

Looking at the icons directory in /usr/share showed that the icons that are not showing are corrupted...

---

### Post by Reiger on 2009-03-22
Probably. But why would you, instead of just rebooting in recovery mode?

---

### Post by WitchCraft on 2009-03-22
> **Reiger said:**
> Probably. But why would you, instead of just rebooting in recovery mode?

Because I have a 250 GB hard disk, and I want to work in the meantime (at least browse the web)...

---

### Post by taavikko on 2009-03-22
You should never run fsck on mounted partition, it can be done, but risks outweigh the benefit.

So better idea would be to run fsck from liveCD if needed to work on a same time.

More info
```
man fsck
```

---

### Post by ssam on 2009-03-22
from man e2fsck
> 
 Note  that  in general it is not safe to run e2fsck on mounted filesys&#8208;
       tems.  The only exception is if the -n option is specified, and -c, -l,
       or  -L  options  are not specified.   However, even if it is safe to do
       so, the results printed by e2fsck are not valid if  the  filesystem  is
       mounted.    If e2fsck asks whether or not you should check a filesystem
       which is mounted, the only correct answer is ‘‘no’’.  Only experts  who
       really know what they are doing should consider answering this question
       in any other way.


so basically no.

you could boot an ubuntu live cd, then you could browse the web without your root drive mounted.

---

### Post by WitchCraft on 2009-03-22
> **taavikko said:**
> You should never run fsck on mounted partition, it can be done, but risks outweigh the benefit.

So better idea would be to run fsck from liveCD if needed to work on a same time.

More info
```
man fsck
```

So basically I cannot start firefox, start a terminal, unmount the root partition, run fsck, and meanwhile surf ?

---

### Post by philinux on 2009-03-22
> **WitchCraft said:**
> Can I have gnome running while running fsck?
 Of course that means I have to unmount the root filesystem...

???

I recently updated my OS, and now a few icons are gone...

Looking at the icons directory in /usr/share showed that the icons that are not showing are corrupted...

One good reason for /home on it's own partition. fsck on my / of 12gig takes no time at all.

---

### Post by WitchCraft on 2009-03-22
> **philinux said:**
> One good reason for /home on it's own partition. fsck on my / of 12gig takes no time at all.

Since when would /usr/share/icons be in /home ?


> 
all:~# fsck -n -f
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
Warning!  /dev/sda3 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 204943 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 278637 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Entry 'inferno.demonoid.com_scrape_72eea606_freq' in /var/tmp/kdecache-root/http/i (720941) has deleted/unused inode 1835010.  Clear? no

Entry 'inferno.demonoid.com_announce_6fc923e1' in /var/tmp/kdecache-root/http/i (720941) has deleted/unused inode 1835009.  Clear? no

Entry 'inferno.demonoid.com_scrape_72eea606' in /var/tmp/kdecache-root/http/i (720941) has deleted/unused inode 1835011.  Clear? no

Entry '5743A2C0d01' in /root/.mozilla/firefox/pj64dvjk.default/Cache (2450197) has deleted/unused inode 2452005.  Clear? no

Entry '1A5C4281d01' in /root/.mozilla/firefox/pj64dvjk.default/Cache (2450197) has deleted/unused inode 2452007.  Clear? no

Entry '7BF562DAd01' in /root/.mozilla/firefox/pj64dvjk.default/Cache (2450197) has deleted/unused inode 2452008.  Clear? no

Entry '4B7FB949d01' in /root/.mozilla/firefox/pj64dvjk.default/Cache (2450197) has deleted/unused inode 2452009.  Clear? no

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached zero-length inode 720897.  Clear? no

Unattached inode 720897
Connect to /lost+found? no

Unattached zero-length inode 720898.  Clear? no

Unattached inode 720898
Connect to /lost+found? no

Pass 5: Checking group summary information
Block bitmap differences:  -849966 -849972 -(849993--849994) -(1019080--1019095) -1157834 -1159169 -(1164563--1164564) -1179110 -(1181784--1181786) -(1183186--1183187) -1183196 -(1183214--1183215) -1185178 -(1185183--1185184) -1185606 -(1256281--1256283) -(1261886--1261910) -(1261913--1261916) -(1261941--1261942) -1261944 -1312787 -1312792 -1312797 -1312830 -1312835 -(1325445--1325448) -1331205 -(1331207--1331209) -(1333256--1333259) -1341860 -1344026 -(1353759--1353761) -(1353764--1353765) -(1353775--1353778) -(1353780--1353782) -(1353785--1353788) -(1353790--1353792) -(1354814--1354930) -1357828 -(1361925--1361926) -1361928 -1366049 -1368069 -1368081 -(2235842--2235843) -(2253754--2253899) -(2254138--2254156) -(2257228--2257231) -(2257483--2257487) -(2855265--2855281) +(2951257--2951258) -4318438 -4318812 -(4318814--4318817) -4318820 +4318821 -5412871 -(5414921--5414923) -(7368704--7368706) -(8343502--8343551) -(8343568--8343653) -(8343656--8343711) -(8651368--8651401) -(9822145--9822207) -(9822688--9823136) -(9823174--9823185) -(9829321--9829322) -9829406 -(9829412--9829413) -(9829566--9829572) -(9829963--9829978) +(9831295--9831302) -(9831313--9831315) -(9831323--9831344) -9831352 -(19920896--19920900) +(19920920--19920923)
Fix? no




/dev/sda3: ********** WARNING: Filesystem still has errors **********

/dev/sda3: 895686/7708672 files (5.0% non-contiguous), 17456337/30822710 blocks
all:~# 




Hmmm, looks like firefox is the culprit in the first place...

---

### Post by dougfractal on 2009-03-22
> /root/.mozilla/firefox/pj64dvjk.default/Cache

Why are you running firefox under root?

---

### Post by philinux on 2009-03-22
> **WitchCraft said:**
> Since when would /usr/share/icons be in /home ?


I think you missed my point /, i.e. root, on my system is only 12 gig so fsck is fast.

---

### Post by WitchCraft on 2009-03-22
> **philinux said:**
> I think you missed my point /, i.e. root, on my system is only 12 gig so fsck is fast.

Ah ok, now it makes sense.

> **dougfractal said:**
> Why are you running firefox under root?
Because I run EVERYTHING as root...

---

### Post by dentaku65 on 2009-03-22
afaik you can't run fsck on mounted disk; but you can manually schedule fsck on the next boot with this command in console:
```
cd \
```
```
sudo touch /forcefsck
```
```
sudo reboot
```

---

### Post by nanomad on 2009-03-22
> **WitchCraft said:**
> Ah ok, now it makes sense.


Because I run EVERYTHING as root...

[OT]
You shouldn't, it is a huge security hole. It's even more dangerous in a pre-release system.

What's wrong with running things as a normal user?

[/OT]

Back to the topic, running fsck on a running system is useless. You should reboot and fsck it. Or, at least, run fsck in a live cd.

---

### Post by WitchCraft on 2009-03-22
> **nanomad said:**
> [OT]
You shouldn't, it is a huge security hole. It's even more dangerous in a pre-release system.

What's wrong with running things as a normal user?

[/OT]

Back to the topic, running fsck on a running system is useless. You should reboot and fsck it. Or, at least, run fsck in a live cd.

OK, I anyway had to restart, so I ran it on restart.

But the problem wasn't even file system corruption.
The problem was that under Debian Squeeze, image files have to fit their file extension... they had the extension .png, but as I checked that with the file utility, they were in fact windows icons...

So I just had to save them once again in the appropriate format, and my icons were back.

---

