---
title: "Slow Performance 10.10"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by kpm1 on 2011-04-14
Hi,

I'm new to Linux, finally jumped in with 10.10 install on an IBM Thinkpad X40 laptop.

I thought Linux was supposed to be much faster than Windows, but my performance is horrible. Just runnnng firefox - no other aps running and every action seems to hit the hard drive... 

long lags constantly. Do I need to modify the install to optimise performance?

Thanks!!

---

### Post by mörgæs on 2011-04-14
Please give the specifications, especially the amount of memory.

---

### Post by kpm1 on 2011-04-14
IBM Thinkpad X40
CPU: Intel Pentium M 1.2GHz
Memory: 512 MB

Thanks

---

### Post by KegHead on 2011-04-14
Hi!

Ram is a little low, but should work fine.(the more the better!)

Please do the following;

sudo apt-get autoclean

sudo apt-get autoremove

You could also try installing bleachbit and Ubuntu Tweak.

KegHead

---

### Post by mörgæs on 2011-04-14
I don't think that this will help, sorry. 


The machine will not be really fast, but there are some steps you can take:

In all browsers, install Flashblock. After this run **top** while doing normal work to see what puts the biggest load on the system.

---

### Post by kpm1 on 2011-04-14
OK - did the actions both of you suggested. 

I installed Flashblock, but how do I run **top**?

---

### Post by KegHead on 2011-04-14
Hi!

goto terminal and type "top'

Enter and post your results!

KegHead

---

### Post by kpm1 on 2011-04-14
Thanks - here you go.

top - 16:11:34 up  4:46,  2 users,  load average: 2.08, 1.78, 1.64
Tasks: 134 total,   1 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.5%us, 19.8%sy,  0.0%ni, 63.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    499312k total,   438132k used,    61180k free,    15688k buffers
Swap:  1648636k total,   100564k used,  1548072k free,   139792k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  654 root      15  -5     0    0    0 S 17.9  0.0   6:52.82 kslowd000          
 1562 kieran    20   0  430m  74m  16m S  7.6 15.3  17:04.84 firefox-bin        
 3240 kieran    20   0 95072  13m  10m S  7.0  2.8   0:02.61 gnome-terminal     
  883 root      20   0 84140  32m 7208 S  2.6  6.7   5:49.16 Xorg               
 3263 kieran    20   0  2624 1112  832 R  0.7  0.2   0:00.63 top                
    6 root      20   0     0    0    0 S  0.3  0.0   0:01.83 events/0           
 2318 kieran    20   0  119m  18m 4800 S  0.3  3.9   0:20.69 acroread           
    1 root      20   0  2892  932  624 S  0.0  0.2   0:00.51 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.66 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm

---

### Post by mörgæs on 2011-04-14
The sudo commands mentioned above only frees a minimal amount of hard disk space. They don't increase speed. 

You don't need to post the **top** results, since they are dynamic. Just keep an eye on it and see if one particular application is eating all your CPU cycles, when you feel the machine is getting slow. 



The CODE tag (used below) makes the list easier to read, but again: There is not much information in a snapshot. 

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  654 root      15  -5     0    0    0 S 17.9  0.0   6:52.82 kslowd000          
 1562 kieran    20   0  430m  74m  16m S  7.6 15.3  17:04.84 firefox-bin        
 3240 kieran    20   0 95072  13m  10m S  7.0  2.8   0:02.61 gnome-terminal     
  883 root      20   0 84140  32m 7208 S  2.6  6.7   5:49.16 Xorg               
 3263 kieran    20   0  2624 1112  832 R  0.7  0.2   0:00.63 top                
    6 root      20   0     0    0    0 S  0.3  0.0   0:01.83 events/0           
 2318 kieran    20   0  119m  18m 4800 S  0.3  3.9   0:20.69 acroread           
    1 root      20   0  2892  932  624 S  0.0  0.2   0:00.51 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.66 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm
```

---

### Post by KegHead on 2011-04-14
Hi Morgaes,

I don't see any real problems do you? (besides 512 ram)

KegHead

---

### Post by mörgæs on 2011-04-14
No, top looks normal, but we don't know how much workload was on the machine while the picture was taken.

I am a little unhappy with seeing kslowd000. It seems to have made trouble earlier: 
[http://ubuntuforums.org/showthread.php?t=1594239](http://ubuntuforums.org/showthread.php?t=1594239)

More later...

---

### Post by KegHead on 2011-04-14
Hi!

Thanks for the info, I'm really curious now!

KegHead

---

### Post by K_45 on 2011-04-14
Upgrade your RAM:  [http://www-307.ibm.com/pc/support/site.wss/MIGR-54352.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-54352.html)    That laptop should support 1GB and this will improve performance. I'd also install Xubuntu if you upgrade the memory so you can squeeze a little bit more speed out.

---

### Post by mörgæs on 2011-04-14
Xubuntu is not much lighter than Ubuntu. If something else is to be installed (which might be the solution), it should be Lubuntu 10.04. 

Kpm1, please post the result of 

```
uname -a
```

---

### Post by kpm1 on 2011-04-23
Sorry for the delay posting - I seem to have OK performance now - about the same as before with XP. Not sure what was bogging the system down before, but hasn't been an issue any more.

Thanks for all the input.

Cheers.

---

