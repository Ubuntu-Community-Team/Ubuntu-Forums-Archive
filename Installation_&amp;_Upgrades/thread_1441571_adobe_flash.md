---
title: "adobe flash"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by robertd15 on 2010-03-28
hi im new to ubuntu im running 9.10 and my problem is that in firefox i am trying to install flash but when i click on the apt link it doesn't open or anything it just stays on the same page

 any help would be appreciated greatly

---

### Post by zvacet on 2010-03-29
Install it from software center.

---

### Post by blur xc on 2010-03-29
> **zvacet said:**
> Install it from software center.

Look for the ubuntu-restricted-extras package in syanptic or the software center, and install that.  

Or- (more simple) just enter:
```
sudo aptitude install ubuntu-restricted-extras
```
on the command line (Applications -> Accessories -> Terminal)

This will install a bunch of codecs and other good stuff, as well as 32bit flash.  If you are runnng 64bit, this will work, but if you want the 64bit flash plugin, you'll need to get it from adobe's website.  There are instructions floating around the forums on how to do that.

BM

---

### Post by robertd15 on 2010-03-29
ok i did that but now in firefox it won't open any apturl links (i installed flash this is just another question and its not because of flash)

---

### Post by blur xc on 2010-03-29
> **robertd15 said:**
> ok i did that but now in firefox it won't open any apturl links (i installed flash this is just another question and its not because of flash)

Are you using normal Ubuntu?  I think I recall hearing that apturl links only work for normal ubuntu/gnome setups...  I may be wrong though...

BM

---

### Post by Megafag on 2010-03-29
> **blur xc said:**
> Are you using normal Ubuntu?  I think I recall hearing that apturl links only work for normal ubuntu/gnome setups...  I may be wrong though...

BM

It wouldnt work with my crunchbang setup.
I think it will only work with my run of the mill ubuntu.

---

### Post by robertd15 on 2010-03-30
yes im running normal ubuntu/gnome 9.10

---

