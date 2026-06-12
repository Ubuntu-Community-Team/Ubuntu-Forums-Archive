---
title: "How can I enable OSD option in /boot/config?"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by nolodude on 2005-02-17
Hi there, I'm having problems with my DVB card (it won't show OSD), and using Google I have learned that this might be because the OSD support has been left out in 2.6.8 kernel. So I looked into my /boot/config-2.6.8.1-4-386 and it says:
```

# Supported SAA7146 based PCI Adapters 
#
CONFIG_DVB_AV7110=m 
# CONFIG_DVB_AV7110_OSD is not set 

```
I figured that there is my problem. I need to enable the above line for OSD. But my questions are:

1) How can I enable it? I need to recompile my kernel, right?

1b) If so, can it be done so that other applications, configurations etc. stay? Because I'v gotten my system to work like I want it to, along with all the apps, daemons, etc and I'd hate to do it all again :)

1c) Is there a step-by-step kernel recompile guide somewhere? I couldn't find any from Ubuntu or Debian sites.

---

### Post by nolodude on 2005-02-17
Ok sorry for the post, I got it working byt compiling my kernel with instructions I found [here](http://www.ubuntuforums.org/showthread.php?t=13757).

Thanks everybody and especially Tichondrius! :)

---

