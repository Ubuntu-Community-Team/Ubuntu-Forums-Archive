---
title: "Reading and writing to a windows partition"
date: 2004-12-12
forum: Installation &amp; Upgrades
---

### Post by lameth on 2004-12-12
Okay the install of ubuntu 4.10 for amd64 went relatively smooth. What I need to do now is set up fstab to allow me to read and write from my vfat partitions containing winxp and windows 98.
I've looked around and I tried 
users.rw,auto 
and
users,auto,umask=0222

I used this in slackware 10.0
defaults,uid=1000,gid=100,umask=000 1 0
this allowed me to access and write to my winxp partition in slack
and this
defaults,uid=1000,gid=100,umask=022 1 0
allowed me to access and write to my win98 partition in slack.


But neither seems to work in ubuntu. Any advice would be appreciated

---

### Post by heema on 2004-12-12
here is my windows entry in fstab :

/dev/hda1    /mnt/win_c    vfat    umask=000    0    0

[http://ubuntuguide.org/index.html#automountfat](http://ubuntuguide.org/index.html#automountfat)

---

