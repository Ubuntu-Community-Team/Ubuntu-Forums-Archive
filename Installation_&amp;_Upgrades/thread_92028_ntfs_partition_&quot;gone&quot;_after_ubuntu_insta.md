---
title: "ntfs partition &quot;gone&quot; after ubuntu install"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by afx on 2005-11-18
Hey everybody,
a strange thing happened to me after installation of gentoo. During the installation i was prompted to manage my partitions, i did it 100 times i had no problems until now. I formated 3 partitions: one as /boot, one as root and one as swap. I had (it's hopefully here yet) another 2 partitions formated with ntfs. I selected both of them to be booted as LVM. I booted up Ubuntu, it worked perfectly. I booted up Windows, it worked but my d: partition is gone! I mean it's still in My Computer but there's nothing on it. Looking at the Properties shows nothing. It says the size of partition is 0! PartitionMagic says that type of both c:\ and d:\ partitions is Type 8E! I have a feeling that my data is not destroyed it's just i can't access it. And the thing that confuses me is: why is c:\ working and d:\ not even if the same thing happened to both of them! What should i do to get my partitions back to ntfs! I miss my data!

p.s. sorry for bad english

---

### Post by aysiu on 2005-11-18
This link may help you:
[http://forums.gentoo.org/](http://forums.gentoo.org/)

---

### Post by afx on 2005-11-23
Not gentoo, I meant ubuntu of course :D LOL. It's just that I've read something about gentoo at the time when I was writing this post, so i wrote gentoo, sorry. Anyway, I solved the problem by installing ubuntu again and this time turning off  the LVM on ntfs partitions. I hope this will help someone with the same problem!

---

