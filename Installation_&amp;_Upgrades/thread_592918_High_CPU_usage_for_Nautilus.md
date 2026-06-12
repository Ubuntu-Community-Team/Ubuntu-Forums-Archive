---
title: "High CPU usage for Nautilus"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Ed.Corcoran on 2007-10-26
For some reason, Nautilus is using massive amounts of my CPU. I turned trackerd and visual effects off, and that didn't change anything. This has happened since I updated to Gutsy. Here is the results of top

```
top - 17:43:09 up 3 days, 10:28,  2 users,  load average: 3.76, 3.75, 3.21
Tasks: 129 total,   4 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s): 54.0%us, 45.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   1035380k total,   983724k used,    51656k free,   408744k buffers
Swap:  1614492k total,   133328k used,  1481164k free,   181604k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
29802 root      25   0  229m 154m 1032 R 46.6 15.3   2678:39 nautilus           
31310 ed        25   0  250m  33m  10m R 45.3  3.3  23:05.60 nautilus           
31953 root      15   0 46956  31m 6912 S  3.7  3.1   0:33.12 Xorg               
32198 ed        15   0 57276  16m  10m S  2.0  1.6   0:00.56 gnome-terminal     
32109 ed        16   0  189m  81m  22m S  1.0  8.1   1:27.24 firefox-bin        
    1 root      15   0  2948  120   68 S  0.0  0.0   0:01.10 init               
    2 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.09 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.57 events/0           
    7 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.84 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  145 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  171 root      10  -5     0    0    0 S  0.0  0.0   0:14.64 kswapd0     
```

---

### Post by jagrav on 2007-10-27
Same thing here. Nautilus remains running at nearly 100%cpu even if I log out of gnome and go into kde. The only line in nautilus-debug-log.txt is "debug log dumped due to signal 11".

---

### Post by Psykotik on 2007-10-27
it is a bug :
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471)

---

