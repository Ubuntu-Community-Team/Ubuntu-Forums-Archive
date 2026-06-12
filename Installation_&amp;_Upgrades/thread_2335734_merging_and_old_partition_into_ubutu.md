---
title: "merging and old partition into ubutu"
date: 2016-08-31
forum: Installation &amp; Upgrades
---

### Post by persephon-eeeek on 2016-08-31
[FONT=book antiqua]so, a bit of backstory: when i originally installed ubuntu (14.04, at the time) on this (windows) laptop, i made seperate /home and /root partitions. my headphone jack always worked wierdly on this computer, and my brother had the same model and the same problem so we assumed it was a hardware issue. i ran into some posts the other day that made me realize it was most likely a issue with ubuntu and, for the first time in maybe a year, actually booted windows up, and the sound worked fine. soooo i decided trying to use different fixes for sound/audio jack problems, and... messed up something with alsamixer, which tbh i had never even heard of, and in trying to correct THAT, I ****ed up my kernel. i did a fresh install, but because i was already on the latest version (16.04), i couldn't just upgrade and leave my partitions as is. i would have chosen "something else" and placed the partititions where their old versions where, but i never labelled mine when i originally partitioned and then couldn't tell which partition had been home and which had been root (i know i know, im and idiot), so i just backed up some important files on my phone (i coulndn't access the internet even through internet because of whatever i did), and wiped my old install. [/FONT][HR][/HR][FONT=book antiqua]
but, and here's where my actually question starts, the installer didn't make a seperate home partition, and left mine alone. it's now a mountable seperate partition wth all my old files untouched, and my home folder is in my root partition. is there a way to change my home folder to that seperate partition, oooor if i just merged the two partitioned (they are next to one another) where would i then find the folders? would they be in a folder in /? thans for the help[/FONT]

---

### Post by Bashing-om on 2016-08-31
persephon-eeeek; Hello; Welcome to the forum.

There are a number of things one can do here to gain access to your old home.
1st up is to identify the partition containing your old home.
post back the outputs - between code tags - of terminal commands :
```

sudo parted -l
sudo fdisk -lu
mount

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and with this we start mounting the partitions and looking to identify your target files.
Once access if gained .. then you decide what you want to do.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by persephon-eeeek on 2016-08-31
oh no i have acess, it isn't really an issue it just seems clunky and disorganized to have those things in a separate partition. i mean i have a lot of files in my windows os partition so again it's not like it really matters, but im just trying to figure out the best way to reintegrate the folders. it's not a priority at all

---

### Post by Bashing-om on 2016-08-31
persephon-eeeek; Well;

As a thought, I also multi-boot and what I do is move shared files to a 'data' partition.

[INDENT][INDENT]many paths to an end
[/INDENT][/INDENT]

---

