---
title: "ubuntu won't install (pci problems???)"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by larscapaldi on 2011-07-06
Ok so I just recently bought a second hand computer which has windows on it, and I've been trying to install ubuntu for the past couple of days but it wont work.
 
when I put in the cd I get to the menu where I can choose between 'Try Ubuntu', 'install', etc...
 
I first selected Install Ubuntu but the screens just goes blank and sits there doing nothing. Tried with a newly downloaded cd written at the slowest speed but it gave me still the same. So I decided to select 'Try Ubuntu' and at first it did nothing, but after a while (180 seconds i thought it said) it began to give me error codes, being
 
```
udevd[72]: worker [78] failed while handling
'/devices/pci0000:00/0000:00:01.0/0000:01:05.0'
```
 
I did some research and found that it probably has something to do with my pci graphics card (as it's the only one plugged into a pci slot) but I haven't got a clue as to what to do to solve the problem.
 
Any ideas?
 
Thanks in advance,
 
Lars

---

### Post by Quackers on 2011-07-06
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok check the cd for errors.

---

### Post by larscapaldi on 2011-07-06
yes I did both and both were ok

---

### Post by larscapaldi on 2011-07-07
no ideas? :(

---

