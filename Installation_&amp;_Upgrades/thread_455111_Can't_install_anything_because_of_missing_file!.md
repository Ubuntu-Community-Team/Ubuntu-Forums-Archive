---
title: "Can't install anything because of missing file!"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2007-05-26
After a failed attempt of installing Second Life, every time I install, the output is this...
```
... Writing extended state information... Error!
E: I wasn't able to locate a file for the secondlife-install package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?


```

---

### Post by rohan! on 2007-05-26
got the same prob. apt won't work, dpkg won't work. i have deleted the contents of /var/cache/apt/archives to no avail.
...
i had started a post on this the other day [http://ubuntuforums.org/showthread.php?p=2723627#post2723627](http://ubuntuforums.org/showthread.php?p=2723627#post2723627)

---

### Post by rohan! on 2007-05-26
did you install from a deb file?

i managed to reinstall secondlife from the deb file ```
sudo dpkg -i Desktop/secondlife-install_1.16.0.5-1~getdeb1_i386.deb 
``` which has fixed the problem.

---

### Post by wersdaluv on 2007-05-26
Thanks. 

I should have waited for your reply longer. You know why? I just reformatted! LOL!

---

