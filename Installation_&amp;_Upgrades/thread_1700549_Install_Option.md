---
title: "Install Option"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by BerneGPG on 2011-03-05
Hi,
So a new hard drive, I created two partitions 320gb each.  One for Windows one for Ubuntu, been advised install Windows first?  Anyhow, I set the file systems as advised with Ubuntu on ext4 for LINUX, am I right in saying that I install LINUX after Ubuntu or what is the correct proceedure?  So back to the booting process...windows XP is not installing correctly, all file systmes load but at the end of loading it reboots and states there is a Disc error?  Its a new 640GB drive so any advice on this welcome, I ran the Wdigital software and the disc is good.

So any offers?
 
All good advice welcome,
 
BerneGPG

---

### Post by zvacet on 2011-03-05
> am I right in saying that I install LINUX after Ubuntu 

No,because by installing Ubuntu you installed linux based distribution.In other words Ubuntu is linux distribution.Now about Windows.It is good to install Windows first.If you can not install it correctly it is prbably Windows error.You said that CD is O.K. and HD is new.Try again with Windows first and when you are sure that you installed it correctly go for Ubuntu install.It will be good to create root,home and swap partition.

1. root=10-15GB                                 mountpoint /
2. swap= ~2GB
3. home= rest of free space                     mountpoint /home

---

