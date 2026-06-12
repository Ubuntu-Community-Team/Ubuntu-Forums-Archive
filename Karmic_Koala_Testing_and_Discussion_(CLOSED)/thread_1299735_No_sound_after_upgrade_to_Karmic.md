---
title: "No sound after upgrade to Karmic"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alinux-lb22 on 2009-10-24
Hi
I had sound running great after upgrading to Karmic I lost sound I did follow this post

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Tried everything with no luck "including installing from source"

One thing I noted is that there is no alsaconf

aplay: device_list:223: no soundcards found...

alsamixer: function snd_ctl_open failed for default: No such file or directory


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


Please help

---

### Post by mikey12561 on 2009-10-24
> **alinux-lb22 said:**
> Hi
I had sound running great after upgrading to Karmic I lost sound I did follow this post

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Tried everything with no luck "including installing from source"

One thing I noted is that there is no alsaconf

aplay: device_list:223: no soundcards found...

alsamixer: function snd_ctl_open failed for default: No such file or directory


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


Please help
I've noticed that when you upgrade things are a little tricky. I was having major problems myself and ended up doing a clean install which I still had problems. I ended up going to do a update and it said that my actual full installation of 9.10 wasn't complete and it installed missing drivers and what not.

So from my experience try doing an update you can get to update manager from System>Administration>Update Manager. After that pretty much simple to do an update.

---

### Post by alinux-lb22 on 2009-10-24
I dont really wana do a clean install and I am running the latest updated packages of everything.

---

### Post by mikey12561 on 2009-10-24
Hummm could you give me more details on the sound card.

---

### Post by alinux-lb22 on 2009-10-24
What info do you need any commands you want me to execute ?

---

