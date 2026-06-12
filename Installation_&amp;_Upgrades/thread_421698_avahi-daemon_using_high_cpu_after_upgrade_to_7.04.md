---
title: "avahi-daemon using high cpu after upgrade to 7.04"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by mraudiofreak on 2007-04-24
I looked around the forums for a while and couldn't find a problem similar to mine. I've been using ubuntu and mythtv on my desktop for about a year now, and I just upgraded to feisty. Everything seems to work fine, but the avahi-daemon seems to use a lot of cpu, fluctuating between 10% and 80%. I think this may be causing my mp3's to skip occasionally. I have both a wireless and Ethernet cards (I don't need the wireless right now though). I also have the NVIDIA drivers installed if that matters. Any explanation or help would be appreciated.
Thanks

Here is an output from top
```
dan@danubuntu:~$ top

top - 15:28:36 up  3:26,  2 users,  load average: 1.63, 2.20, 2.39
Tasks: 111 total,   9 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 75.0%us,  0.7%sy,  0.0%ni, 23.0%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:   1026888k total,   816556k used,   210332k free,    33380k buffers
Swap:  2144636k total,    33884k used,  2110752k free,   586356k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                            
 4912 avahi     18   0  3248 2000 1192 R 75.1  0.2  72:34.65 avahi-daemon                       
 5006 root      15   0 47184  32m 9008 S  1.0  3.2   1:18.40 Xorg                               
    1 root      18   0  2912 1844  524 S  0.0  0.2   0:01.18 init                               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                        
    3 root      34  19     0    0    0 R  0.0  0.0   0:00.39 ksoftirqd/0                        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0                           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                       
  114 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                            
  138 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                            
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush                            
  140 root      10  -5     0    0    0 S  0.0  0.0   0:00.86 kswapd0                            
  141 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0     
```

---

