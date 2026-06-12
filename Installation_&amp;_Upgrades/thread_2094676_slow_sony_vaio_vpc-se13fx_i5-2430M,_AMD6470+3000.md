---
title: "slow sony vaio vpc-se13fx: i5-2430M, AMD6470+3000"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2012-12-14
I popped in a fast SSD and installed ubuntu 12.10 (64) on it.  fresh.  4GB of RAM.  pure vanilla.

booted into it.  it makes the ARM chromebook look like a speed daemon.  last time it felt so slow ws when I had a 386 that had to swap to a mechanical drive.  I let it settle overnight to make sure that all housekeeping chores had been done, and then I just tried to find out some system details (clicked on Settings / Software Sources a few times), running a web browser with just a google search page, and a terminal to display what I am doing.  These are the processes (and look at the CPU!):

```
Tasks: 202 total,  12 running, 186 sleeping,   0 stopped,   4 zombie
%Cpu(s): 63.8 us, 10.8 sy, 24.9 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem:   3963252 total,  3098420 used,   864832 free,    84740 buffers
KiB Swap:        0 total,        0 used,        0 free,  1644620 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                         
 5714 root      25   5  453m 259m 170m R  96.5  6.7  11:53.34 aptd                                            
 8797 ivo       20   0  838m  30m  17m R  32.8  0.8   0:04.48 chromium-browse                                 
 1199 root      20   0  161m  21m 9584 S  31.5  0.6  20:24.15 Xorg                                            
 8708 ivo       20   0  624m 169m  81m R  25.1  4.4   2:07.59 software-proper                                 
 8750 ivo       20   0  551m 100m  48m R  25.1  2.6   0:36.12 software-proper                                 
 8173 ivo       20   0  561m  67m  36m R  23.3  1.8   1:41.66 chromium-browse                                 
 8742 ivo       20   0  590m 104m  49m S  22.1  2.7   0:36.88 software-proper                                 
 8746 ivo       20   0  597m 143m  81m R  19.6  3.7   0:42.25 software-proper                                 
 1547 ivo       20   0 1259m 102m  29m R  19.3  2.6  16:24.07 compiz                                          
 8748 ivo       20   0  548m  98m  48m R  18.7  2.5   0:32.47 software-proper                                 
 8744 ivo       20   0  549m  99m  48m R  15.9  2.6   0:34.31 software-proper                                 
 8725 ivo       20   0  622m 168m  81m R  15.3  4.4   1:39.45 software-proper   

```

I am guessing that a few clicks on System Details created the large process footprints (which make no sense to me, either).
what is going on here?

one aspect I noticed is that Graphics is unknown (in Settings / Details).  the mechanical switch for the graphics driver is on Stamina, which I presume is the Intel HD3000---which should be supported.

help appreciated...or I will have to switch to windows again :-(

/iaw

---

