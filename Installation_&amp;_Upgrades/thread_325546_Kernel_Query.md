---
title: "Kernel Query"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by benjjo on 2006-12-25
I've never compiled a kernel before so this may seem like a stupid Q but i need to upgrade my "kernel source".......i think.
Hardware:> 
Laptop- presario V2000
Sempron 3000

Software:> 
OS - Dapper 6.06LTS
Kernel- 2.6.15-27-k7
I'm trying to install ndiswrapper for my wireless and it requires a better kernel.
I'm curious to know how i can tell whick kernel 'source' is compatible with my software. If i download 2.6.19.1 from ['here']("http://kernel.org/"), would that be what im after? If i follow ['these steps']("http://www.ubuntuforums.org/showthread.php?t=56835"),how would that effect the k7 aspect?
Would i be safer to just
```
$ gksu "update-manager -c"
```
Would that even work?

---

### Post by NeoLithium on 2006-12-26
[http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158) 
This is a good link to a forum walkthrough to compiling your own kernel; I followed it through all the steps and never had a problem in the least bit; just make sure you also check the links for compiling suggestions, and pay attention.  Fortunately it's a process where common sense will keep you alive, even if you're new to doing it :)

---

### Post by benjjo on 2006-12-26
> [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158) 
Awsome! Thanks Neo dude.

---

