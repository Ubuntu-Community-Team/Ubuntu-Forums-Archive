---
title: "lib32ncurses5 ERROR &quot;subprocess installed post-removal script...&quot;"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by 2046 on 2010-06-01
I'm not entirely sure if this is the correct place to post this but hopefully someone can help me out. 

I installed Ubuntu Lucid yesterday on my Dell E510 and everything went smoothly and all my hardware was correctly recognized. But I wanted to install some programs and wasn't entirely sure how to do that. So I was messing around with the repositories and I must have made a mistake somewhere. Now I have a better idea of how everything works but I'm having a problem where every time I try to install something using Synaptic I get the following error:

E: lib32ncurses5: subprocess installed post-removal script returned error exit status 2
E: lib32v4l-0: subprocess installed post-removal script returned error exit status 2

I tried to delete the two packages using Synaptic and then reinstall them but when I go to delete them I get the above error so I can't delete them. I have tried several suggestions on similar threads and that is actually how I narrowed the problem down to the lib32ncurses5 package, but I'm not sure what I need to do to fix the problem. Any suggestions?

Here is what happens when I run 'apt-get install'

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lib32ncurses5 lib32v4l-0
0 upgraded, 0 newly installed, 2 to remove and 15 not upgraded.
2 not fully installed or removed.
After this operation, 721kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128467 files and directories currently installed.)
Removing lib32ncurses5 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing lib32ncurses5 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing lib32v4l-0 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing lib32v4l-0 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 lib32ncurses5
 lib32v4l-0
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks in advance!

---

### Post by dino99 on 2010-06-01
clean the system:

install and run : gconf-cleaner (yes to all), and bleachbit (take care about settings, read and understand before using)

---

### Post by 2046 on 2010-06-01
Awesome.

Everything works perfectly now.

Thanks!

---

