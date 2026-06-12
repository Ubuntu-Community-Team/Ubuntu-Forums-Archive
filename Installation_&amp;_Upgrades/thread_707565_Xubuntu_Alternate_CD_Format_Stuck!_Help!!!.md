---
title: "Xubuntu Alternate CD Format Stuck! Help!!!"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by JordanII on 2008-02-25
I want to install Xubuntu Gutsy to the HD of my old PIII, 128MB RAM, 11GB HD laptop. The problem is, I think I have bad RAM. If I use the bad RAM module (64MB) with the live install CD, Xubuntu (and all other distros I've tried) doesn't start. So I decided to try taking out the bad RAM and use the alternate CD. I put the CD in the drive and booted up, I got LOADS of white text all over my screen (which I have never seen on the alternate CD install before.) It was a bunch of stuff about different drives and ports on my laptop. The text was taking forever... it never went away, so I decided to run the alternate CD WITH my bad RAM. Surprisingly, it seemed to work.... until I got to the Partitions Formatting part. I set it to make my / partition 10GB (Swap 1GB) with the ext3 filesystem. It began formatting and it seems to be stuck at 33% (this happened twice.) I've left it for about 40 minutes and nothing has changed. What do you suggest? Should I remove the bad RAM and give the "white text" more time or should I wait a bit longer for the formatting with the bad RAM? 

Yes, I know Xubuntu is slow on 64MB RAM, I'm planning on moving over to either IceWM or Fluxbox after the installation. 

Thanks for your time! :)

---

### Post by Pumalite on 2008-02-25
With that RAM, I'd stick to Puppy or Damn Small Linux.

---

### Post by plucky on 2008-02-25
JordanII,

Get the Gparted live Cd and create a root partition and swap partition and then retry the installation.

good luck.

p.s If that doesn't work,try what Pumalite says.I managed to get DSL running on a P133 with 16Mb of memory with a 1.5Gb hard disk.Good fun.

---

