---
title: "mount volume"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by jrlrocks on 2008-01-07
Quick question. 

I just installed 7.10 X64.. I like it. Here's my question.

2 37GB drives
6GB /root on 1 drive
2GB /swap on the other.
I mounted /home after the swap partition as it had the 'most' free space.

I have about 28GB empty space on the /root drive that i don't know how to turn into usable storage for videos, music etc? Any insights? to leave it... seems a waste!

J

---

### Post by logos34 on 2008-01-07
sudo gparted

create ext3 partition

add to fstab and mount:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

