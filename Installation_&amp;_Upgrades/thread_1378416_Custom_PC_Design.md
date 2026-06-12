---
title: "Custom PC Design"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-01-11
So I have a dilema on how to build my PC. I have about 5 different ideas for setups, but I would like the least complicated one and the best all-around. I need backup, security, and speed. I would like to have RAID if possible and clone my drives. Is it necessary to have striped RAID, if I'm going to have 6GB RAM, 64 bit OS, 64 bit processor? So here are my possible scenarioes below. Please tell me what you think is the best choice 1-6 OR list your own choice. Thanks.
 
1. hd1 - Win7/Ubuntu
hd2, hd3, hd4 - Striped RAID, Data and Apps here
Clone: hd1, hd2, hd3, hd4 all separate clones
 
2. hd1 - Win7/Ubuntu
hd2, hd3, hd4 - Striped w/ parity
Clone: hd1, hd2, hd3, hd4
The parity would fix if hdd went down won't do anything for a virus
 
3. hd1 - Win7/Ubuntu
hd2, hd3, hd4 - Striped w/ parity
No image Clone
 
4. hd1 - Win7/Ubuntu
hd2 - data
No security here when booting to linux.
 
5. hd1 - Win7/Ubuntu
partition 3 - data
MAYBE security here if I set the permissions in NTFS in both Ubuntu and Win.
 
6. hd1 - Win7/Ubuntu
Keep data with win, keep data with linux
Clone: the whole drive

---

### Post by kakashi_12 on 2010-01-12
? :(

---

### Post by cascade9 on 2010-01-12
I'm a little confused. Its probably better to talk about actual RAID levels, not 'striped' and 'striped w/ parity'

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Just from what you've said...what I would do depends on how much money I had. But what I think would be reasonable would be something like this- 

Sda1- 60GB/120GB SSD. Linux (/root, /home) and Windows (C:, maybe D: depending on how you setup windows)

Sda2, 3, 4- RAID 5, 1TBx3. 2TB usable space. (or possibly 4x1TB in RAID6)

External ESATA- 1x2TB. Backup drive.

---

