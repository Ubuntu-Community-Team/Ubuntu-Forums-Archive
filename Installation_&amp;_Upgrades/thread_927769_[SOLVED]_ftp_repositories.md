---
title: "[SOLVED] ftp repositories?"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by tigrezno on 2008-09-23
Do you know some repositories that work with ftp protocol?

my ISP is destroying my port 80 navigation, and some packages just stall with random errors.

i find the protocol "box" in the Software Sources useless because it only have http on it.

help me please.:confused:

---

### Post by NoReflex on 2008-09-23
I think the official repositories support ftp. For example I'm using ro.archive.ubuntu.com and no matter if I use ftp or http I seem to get the same content (in Firefox that is). If you want to test it out all you have to do is :
```
gksudo gedit /etc/apt/sources.list
```
and change http with ftp for the entries you want. My guess is it will work.

Best wishes,
NoReflex

---

### Post by tigrezno on 2008-09-23
> **NoReflex said:**
> I think the official repositories support ftp. For example I'm using ro.archive.ubuntu.com and no matter if I use ftp or http I seem to get the same content (in Firefox that is). If you want to test it out all you have to do is :
```
gksudo gedit /etc/apt/sources.list
```
and change http with ftp for the entries you want. My guess is it will work.

Best wishes,
NoReflex

that worked, thanks!

---

### Post by NoReflex on 2008-09-23
I'm glad it worked. Please mark the thread as solved.

---

### Post by tigrezno on 2008-09-23
> **NoReflex said:**
> I'm glad it worked. Please mark the thread as solved.

how can i do that? i edited the post, but it doesn't reflects in the forum.

---

### Post by NoReflex on 2008-09-24
See second post here : [http://ubuntuforums.org/showthread.php?t=856459](http://ubuntuforums.org/showthread.php?t=856459)

---

### Post by tigrezno on 2008-09-24
> **NoReflex said:**
> See second post here : [http://ubuntuforums.org/showthread.php?t=856459](http://ubuntuforums.org/showthread.php?t=856459)

thanks, years of using this sort of forums and never found that :)

---

