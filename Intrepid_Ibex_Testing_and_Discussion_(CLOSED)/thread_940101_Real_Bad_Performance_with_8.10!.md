---
title: "Real Bad Performance with 8.10!"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thyams on 2008-10-06
For some reason the vast majority of programs, windows switching, and even typing cause my computer to freeze constantly and takes forever to load.  I used Ubuntu 8.04 on a slower computer before so I thought I would try out the new 8.10.  This is like working with DOS before Win 3.x came out.

I have an ASUS G50Vm-X1 Laptop
Intel Core 2 Duo T5750 (2.00GHz/2.00GHz)
4096 MB DDR2 Dual Channel 667 Mhz
nVidia Geforce 9700M GT 512 MB DDR3
Hitachi 7200RPM SATA II 200GB

Can someone tell me why the just installed performance is using nearly 3.00GHz of processing power just to move a mouse?  Across the screen.

All updates are applied, the nvidia driver 177.76 is activated and working properly.

Only custom programs installed is Java Runtime - and a p2p Program called Frostwire.  I don't understand why the performance is so bad.  I have to type only three words at a time and wait for the damn memory buffer to spill out the text a letter at a time.  God forbid there is a typo.

---

### Post by Rocket2DMn on 2008-10-06
Moved to Intrepid Ibex Testing and Discussion

---

### Post by shifty_powers on 2008-10-06
well, tbh, it is pre-release. a beta. you can't really bitch too much if you have problems with performance...

---

### Post by philinux on 2008-10-06
> **thyams said:**
> For some reason the vast majority of programs, windows switching, and even typing cause my computer to freeze constantly and takes forever to load.  I used Ubuntu 8.04 on a slower computer before so I thought I would try out the new 8.10.  This is like working with DOS before Win 3.x came out.


What does top show?

---

### Post by jfernyhough on 2008-10-06
Disable Compiz (desktop effects). Try a clean xorg.conf (i.e. no driver setting for nvidia). I reckon the starting point is your 9700M and the Nvidia drivers.

---

### Post by thyams on 2008-10-06
Top?  You mean desktop?  It shows windows and such but they move real jerky almost like its the display drivers.  No other driver supports my card though : (

If Top means something else I apologize because I posted this initially in the Beginner Forum..

---

### Post by thyams on 2008-10-06
I also checked the Processes in System Monitor, there is nothing running but I definitely see my CPU usage fluxing between 0% and 80% just from moving the mouse, is there possibly something running in Ubuntu I am not able to see?  I am a straight up windows user and am used to hidden tasks on such and having to end process a million times to get everything turned off.

---

### Post by jfernyhough on 2008-10-06
You're running the wrong thing if you're a beginner - unless you want to learn quickly.

top is a command to show processes, normally sorted to show those using most CPU at the top. Open Terminal and type top, then press enter.

---

### Post by thyams on 2008-10-06
> **jfernyhough said:**
> Disable Compiz (desktop effects). Try a clean xorg.conf (i.e. no driver setting for nvidia). I reckon the starting point is your 9700M and the Nvidia drivers.

Going to need a little more instruction to disable Compiz,  I did check out the Nvidia X Server Settings, I disabled Anisopteric/Anti-Aliasing etc.  Then when to appearance option under System/Preferences.  After puting Visual Effects to None, it got worse, so I tried Good and Extra options... seems to have fixed my problems with the Windows going moving around and typing.  The memory buffer isn't filled after three words for sure.  Still left with sluggish performance loading apps.

---

### Post by thyams on 2008-10-06
I generally learn very fast anything I put my mind to.  Thanks for the command that might really help me out later on.


top - 18:07:35 up 52 min,  2 users,  load average: 1.15, 1.06, 0.90
Tasks: 130 total,   2 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s): 29.1%us, 15.1%sy,  0.0%ni, 54.9%id,  0.2%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   4055044k total,  1795940k used,  2259104k free,    41380k buffers
Swap:  7960168k total,        0k used,  7960168k free,   888424k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
 5881 root      20   0  431m  57m  17m R   47  1.4  25:27.31 Xorg                                                                                                       
 3698 root      15  -5     0    0    0 S   30  0.0   0:49.03 ath9k                                                                                                      
 8136 cain      20   0 1365m 268m  16m S   10  6.8   3:02.97 java                                                                                                       
 9349 cain      20   0  273m  29m  12m S    3  0.7   0:01.18 gnome-terminal                                                                                             
 6274 cain      20   0  294m  64m  29m S    3  1.6   1:09.37 compiz.real                                                                                                
    1 root      20   0  4100  912  620 S    0  0.0   0:01.30 init                                                                                                       
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                   
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0                                                                                                
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                 
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                
    7 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/1                                                                                                
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                 
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                                                                   
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1                                                                                                   
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                    
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 ftraced                                                                                                    
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                              
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                              
   53 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                  
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                  
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                     
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                               
  150 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                                     
  154 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod                                                                                                    
  205 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                    
  206 root      20   0     0    0    0 S    0  0.0   0:00.44 pdflush                                                                                                    
  207 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                    
  253 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                      
  254 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                      
 1876 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                              
 1877 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd


Looks like the cpu is going to Xorg?

---

### Post by jfernyhough on 2008-10-06
Current Ubuntu nvidia driver version: 177.76

Have a look here: [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

This is probably worth a look: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

9700M support was only added recently. It sounds as though there may be some bugs in the 2D driver. To really check this you need to disable the nvidia drivers in System,Administration,Hardware Drivers so Ubuntu uses the default which should be more reliable for 2D.

---

### Post by nowshining on 2008-10-06
yeah but that's a beta [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for a stable version...

---

### Post by Slug71 on 2008-10-06
I think something similar was brought up a while back and its because some files or something which has a lot to do with performance hasnt been implemented yet as it usually isnt with Alpha's and Beta's. Should be in the RC though.

---

### Post by jfernyhough on 2008-10-06
> **nowshining said:**
> yeah but that's a beta [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for a stable version...Actually, that's an interesting thought - 173 might be stable but I don't think it supports 9x series. thyams could check which nvidia version he's running, though I suspect it's 177.

---

### Post by crazyguy510 on 2008-10-06
Make sure you have 3d accelerated drivers install when your using 3d effects otherwise this will really slow down your system.

---

### Post by thyams on 2008-10-06
Yeah I have the 177.76 installed that comes with 8.10.  Its the same version available from nvidia.com.  The only problem is anything with 2D performance is terrible, and the flipside is if I put everything on Extra Apperance more is done by the 3D Processor.

Anyone know how I can change powermizer options?  It would greatly help me out if I could leave it on performance level 3 out of 4.  Right now its on 0 which I suspect if changed, would greatly increase work done by GPU instead of CPU.

---

### Post by philinux on 2008-10-06
0 is full speed if I remember correctly. That is my setting.
[edit] 0 is full performance see screenshot.

---

### Post by jfernyhough on 2008-10-06
> **thyams said:**
> The only problem is anything with 2D performance is terrible, and the flipside is if I put everything on Extra Apperance more is done by the 3D Processor.This is why I believe the problem is down to the driver not liking your card - it's an Nvidia issue which should be sorted with the next release. Until then you'll either have to put up with jerky 2D and fast 3D or disable the nvidia drivers and have smooth 2D but limited 3D.

Try posting to the nvidia forum and see what response you get - though they might recommend you upgrade to 177.78 (which should be coming shortly in the repos anyway).

---

### Post by psyke83 on 2008-10-06
It's vital that you tweak the nvidia driver settings to get acceptable performance. See: [http://ubuntuforums.org/showpost.php?p=5908250&postcount=3](http://ubuntuforums.org/showpost.php?p=5908250&postcount=3)

---

