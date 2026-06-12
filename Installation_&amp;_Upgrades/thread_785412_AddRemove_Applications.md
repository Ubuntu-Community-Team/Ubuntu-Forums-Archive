---
title: "Add/Remove Applications"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Dksgirl on 2008-05-07
In the process of installing the GCompris educational suite after upgrading to 8.04, I received the following error message. I am a neophyte when it comes to Linux. Please give me some "steps" to resolving this error?

E: /var/cache/apt/archives/gcompris-data_8.4.4-1.1ubuntu1_all.deb: failed in buffer_write(fd) (10, ret=-1)

Thanks, Nancy 
Teacher in NC

---

### Post by dabang on 2008-05-07
I'm not sure, but maybe there's no free diskspace left? At least this was the solution with a similar problem mentioned [here]("http://ubuntuforums.org/showthread.php?t=651602"). See what
```
df -h
```
tells you.

---

