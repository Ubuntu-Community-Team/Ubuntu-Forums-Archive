---
title: "Slow PC after updating &quot;Ubuntu 10.04.1 LTS&quot;"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by javiercmh on 2010-08-24
hi,
just upgraded to "Ubuntu 10.04.1 LTS" and now my PC needs much more time to show the panels and menus, and even more to let me use my USB keyboard.

What could have happened?




Update: there's nothing bad on my PC.

---

### Post by mörgæs on 2010-08-24
How much memory and which screen card does it have?

You can see the screen card by entering 
```
 hwinfo --gfxcard
```

---

### Post by javiercmh on 2010-08-24
Memory: 2gb
GPU: nVidia GeForce 9500 GT, 512mb.

Desktop Effects are enabled, I don't have problems with the graphics.
Before updating, Ubuntu worked very fast. Now is the problem :(

(thanks for answering)

---

### Post by mörgæs on 2010-08-25
This should be a fast machine, and the 9500 screen card normally works without to much struggle.

Have you thought of doing a fresh install?

---

### Post by javiercmh on 2010-08-25
I did that for installing 10.04... but for this little update, I don't think it's necessary. I want to see if there is another way.

---

### Post by mörgæs on 2010-08-25
I see. 10.04.1 and 10.04.0 are essentially the same system, so there is no need for reinstalling. The .1 version just contains the accumulated updates, which otherwise must be downloaded.

Please run **top** and post the output. Press q for quitting top.

---

### Post by javiercmh on 2010-09-13
Sorry for not answering this last 2 weeks. My computer is fine. I don't know what was the problem, but is fixed now :)
thanks for your help anyway.

---

### Post by alecive on 2010-10-08
Sorry if I refresh this thread, but I have the same problem. After an update, it appears a window that says: "Computer needs to be restarted". I've restarted it but it showed me a black screen (without effectively restarting), and so I decided to press the shutdown button on kbd for a long time.

After that , pc shutted down. After a new starting, it becomes slow! FF takes more thant 11 seconds to open. My laptop is very new, with an i5-450M inside and 4GB of RAM, so it's not a problem of computer performances!

My graphic card works well!

Here the result of "top":

```
top - 13:48:59 up 8 min,  2 users,  load average: 0.79, 0.64, 0.34
Tasks: 181 total,   1 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.2%us,  1.1%sy,  0.0%ni, 95.9%id,  0.2%wa,  0.1%hi,  0.5%si,  0.0%st
Mem:   3979848k total,   712216k used,  3267632k free,    80924k buffers
Swap:  3905528k total,        0k used,  3905528k free,   286332k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                        
 1169 root      20   0 52692  40m  13m S    8  1.0   0:22.58 Xorg                           
 1428 alecive   20   0 61520  48m  15m S    3  1.2   0:09.33 compiz                         
 1662 alecive   20   0  266m  91m  27m S    1  2.4   0:15.83 firefox-bin                    
 1708 alecive   20   0 46876  13m  10m S    1  0.4   0:00.28 gnome-terminal                 
 1684 alecive   20   0 99920  17m  12m S    1  0.5   0:01.87 plugin-containe                
    1 root      20   0  2668 1608 1208 S    0  0.0   0:00.56 init                           
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                       
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                    
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                    
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                     
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                    
    7 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1                    
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                     
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                    
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/2                    
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2                     
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                    
   13 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/3                    
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3                     
   15 root      20   0     0    0    0 S    0  0.0   0:00.01 events/0                       
   16 root      20   0     0    0    0 S    0  0.0   0:00.01 events/1                       
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 events/2                       

```

---

### Post by alecive on 2010-10-08
Why it says: "2 users"?!?

---

### Post by alecive on 2010-10-08
Update:

11 seconds to open firefox
6 seconds to open nautilus
14 to open opera

obviously, if those apps were already been opened, this not happens..

---

