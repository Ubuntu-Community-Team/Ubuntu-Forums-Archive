---
title: "Help! nvidia-glx induced Xserver crash victim"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Al3xanR0 on 2006-11-17
I could really use some help, trying to install XGL/Beryl on a Dell Inspiron- E1505, Core 2 Duo, Nvidia GeForce Go 7300 [TurboCache.

However the following is a major hinderance.

FATAL: Module nvidia not found.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.


a quick ```
uname -r
```

reveals 2.6.15-27-686 as my running kernel.

a quick ```
dpkg -l | grep nvidia
```

reveals the following installed packages

nvidia-glx 1.0.8776+2.6.15.12-1
nvidia-kernel-common 20051028+1

oddly nvidia-settings is a recommended install but, any attempts will result in the removal of nvidia-glx

a quick ```
dpkg -l | grep modules
```

reveals the following installed packages

linux-restricted-modules-2.6.15-27-686
linux-restricted-modules-686
linux-restricted-modules-common

there were a few others obviously, nontheles, irrelevent.

a quick ```
dpkg -l | grep libgl
```

reveals the following installed packages

libgl1-mesa
libgl1-mesa-dri
libglitz-glx1
libglitz1

once again, there were a few others obviously, nonetheless, irrellevent.

Additionally all of the required beryl packages are installed I won't bore you with redundant output I think you have had enough, unless of course you want more.

I did not think it was necessary to include the xorg.conf because
```
nvidia-xconfig
``` generated a new xorg.conf which, those of you who executed it I am sure are familiar with. Nevertheless, it can be furnished upon request as well as any other seemingly pertinent info.

I am not quite sure what I may have overlooked, to the best of my knowledge I installed al required .debs and deps.

Please help.

P.S. I am running Dapper

---

### Post by Al3xanR0 on 2006-11-18
I suppose I can safely assume that this post will unanswered. Thanks

---

### Post by quint on 2006-11-18
You can probably get to your desktop by changing "nvidia" to "nv" in:

> /etc/X11/xorg.conf

HTH.

---

### Post by Tavslok on 2006-11-27
note by doing that you will be disabling hardware 3d 
acceleration...

i've got the same problem, not solved yet but found some
interesting topics to try later:

[http://ubuntuforums.org/showthread.php?t=306095](http://ubuntuforums.org/showthread.php?t=306095)
[http://www.nvnews.net/vbulletin/showthread.php?t=80310](http://www.nvnews.net/vbulletin/showthread.php?t=80310)
[http://ubuntuforums.org/showthread.php?t=304694&highlight=nvidia+crash](http://ubuntuforums.org/showthread.php?t=304694&highlight=nvidia+crash)
[http://www.nvnews.net/vbulletin/showthread.php?t=79902](http://www.nvnews.net/vbulletin/showthread.php?t=79902)

Good luck!!! :D

---

