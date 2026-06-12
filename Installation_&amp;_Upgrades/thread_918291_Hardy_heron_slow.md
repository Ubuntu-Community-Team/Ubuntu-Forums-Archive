---
title: "Hardy heron slow?"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by laxmidd50 on 2008-09-12
I updated to hardy heron recently and my computer is very slow now. I am considering reformatting (and installing hardy heron again) because a lot of people say that the update isnt the best thing to do. However, it would be nice if i didnt have to do that. In system monitor there are a LOT of processes running (40-50), but most take up no cpu. I think the problem is xgl though. It is taking up 40% on average. What can i do about this? My computer was never this slow before.
Thanks

---

### Post by laxmidd50 on 2008-09-13
Any thoughts on this? I think i may have been using a different graphics driver before, but the upgrade defaulted to xgl? I dont remember the name though.

---

### Post by Sef on 2008-09-13
1) How much ram do you have?

2) Applications > Accessories > Terminal  then paste or type in this code:

```
top
```

it will show you what is running and what is using the most.   Paste the results here.

---

### Post by laxmidd50 on 2008-09-13
Have 1 gig of ram, and ati radeon 200M xpress. Shouldn't be a ram problem because gutsy ran perfectly.

```
top - 15:52:44 up 12 min,  2 users,  load average: 0.37, 0.63, 0.46
Tasks: 132 total,   2 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s): 36.5%us, 15.9%sy,  0.0%ni, 47.2%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    904048k total,   644544k used,   259504k free,    13760k buffers
Swap:  2642652k total,        0k used,  2642652k free,   296048k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6714 nowa      20   0  231m  70m  20m S 23.2  7.9   0:33.14 Xgl                
 7047 nowa      20   0 52112  20m  13m S 13.9  2.4   0:11.62 gnome-system-mo    
 6978 nowa      20   0  137m  50m  19m S  6.0  5.7   0:10.09 firefox            
 6768 nowa      20   0 45012  17m  12m S  2.0  1.9   0:01.46 gnome-panel        
 6560 root      20   0  182m  27m 7588 R  1.3  3.1   0:04.08 Xorg               
 6776 nowa      20   0 15292 2652 1808 S  0.7  0.3   0:00.44 gnome-screensav    
 6787 nowa      20   0 21024  13m 4632 S  0.7  1.5   0:03.40 compiz.real        
 6908 nowa      20   0 18904 9772 6880 S  0.7  1.1   0:00.44 gtk-window-deco    
 6976 nowa      20   0  2308 1128  852 R  0.7  0.1   0:00.90 top                
 6747 nowa      20   0 40028 9.9m 7880 S  0.3  1.1   0:00.46 gnome-settings-    
 6770 nowa      20   0 67948  21m  13m S  0.3  2.4   0:00.55 nautilus           
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.22 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0  
```

---

### Post by laxmidd50 on 2008-09-16
Any ideas? Should I reformat?

---

