---
title: "How do i use &quot;Testdisk&quot; for recovering media on 10.04"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Nightstrike2009 on 2010-05-10
I have heard of a program recommended by dino99 "testdisk"

Its in repos so to install in terminal:

> sudo apt-get install testdisk

when installed just type:

> sudo testdisk

in terminal to run, i've no idea how its used, though "(create) Create a new log file", then select drive seems the way forward how would i use this to recover a corrupted memory card / usb drive?

---

### Post by karthick87 on 2010-05-10
After installing testdisk goto terminal and type

```
sudo photorec
```


and follow the instruction...

---

### Post by Nightstrike2009 on 2010-05-10
Huh answering my own posts again eh?

Here goes a google search [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

hope this provides some answers :-)

I am I right to assume that a windows formatted memory stick / usb stick has no partition table?

PS: Thanks getyourkarthick we posted at exactly the same time my friend

---

### Post by mh2ack on 2010-05-16
I got here trying to solve an issue with reading Memory Stick Pro Duo cards. Nothing like clicking links. For those who are having problems reading a Memory Stick Pro Duo card, it may simply be a matter of FAT12 vs FAT16. FAT12 is readable by Ubuntu 8.04 but not by Ubuntu 9.10 or Ubuntu 10.04. I have tested several cards and found that ones with FAT16 were readable while ones with FAT12 were not. My phone uses the cards and does not care which FAT it is. And my old setup with Ubuntu 8.04 did not care either. But for Ubuntu 10.04 it does matter.

---

