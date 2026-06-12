---
title: "btrfs opens but ends in GRUB"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by dorpapst on 2022-03-23
I have an external disk which has btrfs as file system and I have booted from that one very often before. However, today, when I wanted boot from it, it failed.
In the screen where I need to type in the password, I typed in the password, it says "slot 0 open" like always but I always end up in the grub menu instead of booting the actual system (Ubuntu 20.04 LTS).

This seems very strange. I cant figure out why this is the case.

I then booted an Ubuntu stick and tried to connect to the disk via terminal and there everything works fine. I can see all my files there, nothing seems corrupted.
```
sdb      8:16   0 931.5G  0 disk  
&#9500;&#9472;sdb1   8:17   0   512M  0 part  
&#9500;&#9472;sdb2   8:18   0    16G  0 part  [SWAP]
&#9492;&#9472;sdb3   8:19   0   915G  0 part  
  &#9492;&#9472;vo 253:0    0   915G  0 crypt /media/vo
```
sdb1 is boot, sdb2 is swap and 3 is the data.


Can anybody help me to figure out what is going on here?

Many thanks

---

