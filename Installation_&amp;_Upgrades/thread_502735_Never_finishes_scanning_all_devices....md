---
title: "Never finishes scanning all devices..."
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by madscientist327 on 2007-07-17
I've been trying to install Ubuntu on my laptop and have come across a problem. Whenever I try to partition the hard drive using the installer on the Ubuntu cd, it never finishes scanning for devices. I tried the gparted live cd as well... same problem. I'm really not experienced with Linux and I am quite frankly stumped. Any help with this issue would be most appreciated.

---

### Post by madscientist327 on 2007-07-17
I've looked around on the internet for some help and I found that on the gparted live cd if I open up the terminal and type in gparted /dev/sda1 it sees my hard drive. The only problem is that gparted thinks the entire drive is unallocated, which I know for a fact is not true. What is going on?

---

### Post by madscientist327 on 2007-07-17
This is extremely odd as gparted worked fine a couple of days ago on this laptop.  I don't really want to lose my windows partition. Is there any other way to resize it?

---

### Post by madscientist327 on 2007-07-17
Yes! I fixed it. I ran Chkdsk and fixed errors on the hard drive. Now it works! Now I just have **two** questions. **What file system should I use? ext3? ReiserFS?** **Also, what is the recommended size for a linux swap partition?** I have a gig of ram on the laptop.

---

