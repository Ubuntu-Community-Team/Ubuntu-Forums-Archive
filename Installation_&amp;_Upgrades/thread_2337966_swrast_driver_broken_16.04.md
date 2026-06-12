---
title: "swrast driver broken 16.04"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by fistofmetal226 on 2016-09-23
Running Ubuntu 16.04 LTS Xenial
i've noticed it used to be a problem in 14.04, from what i could find on the web. But all i could find for 16.04 were steam launching errors, (which i also have) && posted about here: 
( [https://ubuntuforums.org/showthread.php?t=2337713](https://ubuntuforums.org/showthread.php?t=2337713) )
it only seems to happen through either PlayOnLinux or wine, etc.
All native games run fine, like Minecraft or Champions of Regnum.

this is the error i always come accross:

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

```
~$ ldconfig -p | grep libGL.so.1
    libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-370/libGL.so.1
    libGL.so.1 (libc6) => /usr/lib/i386-linux-gnu/mesa/libGL.so.1
    libGL.so.1 (libc6) => /usr/lib32/nvidia-370/libGL.so.1
    libGL.so.1 (libc6) => /usr/lib/libGL.so.1
```
i know it has something to do with nvidia openGL or 32-bit mesa libraries. i don't know a single thing about either, really.
i've tried reverting to other graphics drivers (propriety or not) & back to default, nothing changed.

what's my next step? do i have a config file pointing in the wrong place? or is something completely broken?
i'm ripping my hair out on this one, can't figure it out.

---

### Post by fistofmetal226 on 2016-09-26
[https://wiki.archlinux.org/index.php/Steam/Troubleshooting#Steam_runtime_issues](https://wiki.archlinux.org/index.php/Steam/Troubleshooting#Steam_runtime_issues)
i'm trying this now, will post here my results. i'm no expert linux user, so this might deem pretty impossible for me. 
fingers crossed.

---

### Post by fistofmetal226 on 2016-09-26
i've tried reinstalling the mesa libs, tried reinstalling the glx libs, tried removing steam and reinstalling, tried deleting certain files, replacing others, i don't know where i am anymore.

tried using this guide, (as many as i could understand)
now i just get a bunch of LD_PRELOAD errors aswell.
[https://wiki.archlinux.org/index.php/Steam/Troubleshooting#Steam_runtime_issues](https://wiki.archlinux.org/index.php/Steam/Troubleshooting#Steam_runtime_issues)

this is what i get:
```

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

```

this isn't just steam, this is for all wine games aswell. anything that doesn't run native on linux
i'm stuck. can anyone help? please?

---

### Post by sisco311 on 2016-09-26
Threads merged. Please don't post multiple threads with the same topic.

---

