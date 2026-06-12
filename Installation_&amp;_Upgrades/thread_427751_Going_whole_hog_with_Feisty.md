---
title: "Going whole hog with Feisty"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by dileepfrog on 2007-04-29
A few months ago I got fed up with Windows crashiness and decided to try out Ubuntu with a dual boot setup. It worked fantastic, and now that I have WinXP running in a virtual machine with Qemu/KVM, I no longer have a need for my Windows partition. Does anyone know if it's possible for me to reclaim the 39G my Windows partition is currently using *without* wiping out my Feisty setup?


(parted) print                                                            

Disk /dev/sda: 58.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary  fat16             
 2      49.4MB  41.6GB  41.6GB  primary  ntfs         boot 
 3      41.6GB  54.8GB  13.2GB  primary  reiserfs          
 4      54.8GB  58.5GB  3668MB  primary  linux-swap

---

### Post by innactpro on 2007-04-29
I just used GParted live cd

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

a couple of hours ago to resize my WinXP partition to make room for Ubuntu and WinXP still boots just fine. I would assume then you could use GParted  to claim the portion of your hdd now occupied by Windows and you shouldn't lose anything. You may want to do a little research into it before using GParted though to make sure you shouldn't lose anything.

---

### Post by dileepfrog on 2007-04-29
Yeah gparted would let me use the windows partition, but then I would have two partitions. I kinda wanted to have just 1 big partition for linux - maybe I'm just being anal. Is there anything akin to Norton Ghost for linux? Then I could burn my current sweet setup to a few DVDs, do a clean wipe with reiserfs, and restore.

:guitar: 

I know that smiley was uncalled for. I've just never seen one nearly as cool.

---

### Post by innactpro on 2007-04-29
osalt.com lists Partition Image

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

and Ghost for Unix

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

as "Open source Norton Ghost alternatives." I have never used these so I don't know anything about these other than the info on osalt.com.

---

### Post by dileepfrog on 2007-04-30
Cool thanks - I'll give partimage a go. I'll maybe have to sack up and do a clean wipe though :(

---

