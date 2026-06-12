---
title: "migration USB HD -&gt; IDE/SATA HD"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by arang on 2007-07-07
hi guys, good afternoon, (wherever it is right now), u see, i've been using ubuntu for over a month i simply love it everything in my pc works from my webcam to my pda and my bluetooth stuff etc, it's working like a charm and i havent booted XP in some time, now i have a problem. 

I installed ubuntu in an external USB hard drive and i want to migrate it to either one IDE(PATA) hard disk or to my new SATA Hard disk. I was wondering if there's a way to do so without having to reinstall ubuntu again patch it download the rest of apps and fix all the stuff and problems i've been solving for the past month.

let me explain my geometry, i have 2 internal hard disks first bootable one with windows XP is a 120gb seagate PATA hardisk partitioned in 1 40gb bootable partition with XP and a 80gb partition thats mostly empty, also i got a 320gb Seagate hard disk thats just one huge partition everything use NTFS, also the USB hard drive have a first partition of 40gb FAT32 a 200mb /boot partition , a 37.8Gb / Ext3 partition and a 2Gb Swap. 

my idea is to resize the internal 120gb seagate harddisk , i wanna keep the XP bootable partition but resize the 80gb partition one so i can accomodate Ubuntu there, i would want to basicly just copy the whole partitions that belong to Ubuntu to the resized zone, but im aware that first Grub is gonna complain, and second the Fstab and everything that controls what mounts where will have to be rewrited, im ok with rewriting but i would like to know what to do more or less or if anyone got an idea about how to do this in a proper way with the less amount of work and the less amount of broken links and such? (every non linux partition will keep its name and mountpoints btw).

if any extra info needed let me know , a hand would be much appreciated.

---

### Post by iota on 2007-07-10
Yeah I had the same sort of idea. Once I'm done hopefully I'll have Feisty on two nice shiny new sata drives in raid :) Plus going to try and do that integrated windows virtualbox thing- Looks kinda cool. Except I was kind of hoping there would be something that could do it for me :P

I know there is similar software for windows (I had to use it at work, took quite a while to do though. Moving a version of windows+all software over a network connection :() but after digging around I've come up with scratch.

Looks like you're either going to be editing config files till your eyes pop out or just gonna have to bite the bullet and start anew :P

Anyway, thought I'd give you a rather long winded heads up :P Good luck if you try it regardless btw!

---

