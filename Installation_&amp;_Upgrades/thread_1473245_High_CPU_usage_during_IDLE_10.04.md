---
title: "High CPU usage during IDLE 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by tagno25 on 2010-05-05
Before I upgraded my computer I was seeing around 5% CPU usage while idle, but now I am seeing about 50%.
I ran powertop and it seems "[Rescheduling interrupts] <kernel IPI>" and "[kernel scheduler] Load balancing tick" might be the problem(s).

Also ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml is being written to constantly.

---

### Post by mikewhatever on 2010-05-05
Can you just run **top** and post the output.

---

### Post by tagno25 on 2010-05-05
top - 08:33:55 up 19:33,  2 users,  load average: 2.62, 2.08, 2.02
Tasks: 208 total,   4 running, 204 sleeping,   0 stopped,   0 zombie
Cpu0  : 40.4%us, 24.1%sy,  0.3%ni, 34.8%id,  0.2%wa,  0.2%hi,  0.0%si,  0.0%st
Cpu1  : 42.9%us, 26.4%sy,  0.3%ni, 30.0%id,  0.2%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:   1930728k total,  1602196k used,   328532k free,   370212k buffers
Swap:  1951856k total,   117648k used,  1834208k free,   660140k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 1164 root      20   0 50244  25m 9924 R   12  1.3 153:42.24 Xorg                                                                                            
 2352 tagno25   20   0  8920 5428 2204 S   11  0.3 112:45.41 gconfd-2                                                                                        
 2348 tagno25   20   0  5172 2248  648 R   10  0.1 103:00.96 dbus-daemon                                                                                     
 2297 tagno25   20   0 30608 9672 6064 S    3  0.5  32:26.30 gnome-session                                                                                   
17152 tagno25   20   0 77932  28m 6308 S    2  1.5  14:20.12 compiz                                                                                          
 2405 tagno25   20   0  119m  19m  12m S    2  1.0  17:58.70 nm-applet                                                                                       
 9811 tagno25   20   0 57944  15m  11m S    2  0.8   0:02.01 gnome-terminal                                                                                  
 2420 tagno25   20   0 72308  28m  14m S    2  1.5  20:49.13 gnome-panel                                                                                     
 4342 tagno25   20   0  270m 168m  25m S    2  9.0  11:20.80 nautilus                                                                                        
 2359 tagno25   20   0 55704  36m 4324 S    2  1.9  22:05.03 at-spi-registry                                                                                 
 2416 tagno25   20   0 46044  10m 7380 S    2  0.5  13:29.71 gnome-power-man                                                                                 
 2763 tagno25   20   0 19832 7212 5588 S    2  0.4  10:25.76 gnome-screensav                                                                                 
 3982 tagno25   20   0 32940 8664 7496 S    2  0.4  17:41.24 python                                                                                          
 2915 tagno25   20   0 18784 4012 3692 S    1  0.2  15:07.87 indicator-me-se                                                                                 
 2360 tagno25   20   0 94532  11m 8864 S    1  0.6  11:45.90 gnome-settings-                                                                                 
 2397 tagno25   20   0 27248 4400 3684 S    1  0.2  10:13.44 trackerd                                                                                        
 2409 tagno25   20   0 20128 7008 6364 S    1  0.4   8:14.40 bluetooth-apple                                                                                 
 2889 tagno25   20   0 92852  16m  12m S    1  0.9   8:24.34 clock-applet                                                                                    
 4283 tagno25   20   0 40576 6584 3416 S    1  0.3  11:24.08 ubuntuone-syncd                                                                                 
 2900 tagno25   20   0 17904 4056 3688 S    1  0.2   7:09.03 indicator-sessi                                                                                 
 2919 tagno25   20   0 85072 3536 3332 S    1  0.2   6:08.55 indicator-sound                                                                                 
 3981 tagno25   20   0 93436  13m 9.9m S    1  0.7   8:58.19 evolution-alarm                                                                                 
 2407 tagno25   20   0 20040 6716 6156 S    1  0.3   7:51.37 tracker-applet                                                                                  
 2888 tagno25   20   0 69472  14m  11m S    1  0.8   8:36.55 indicator-apple                                                                                 
 2917 tagno25   20   0 24184 3608 3208 S    1  0.2   6:24.79 indicator-appli                                                                                 
 7632 tagno25   20   0 58256 5416 4216 S    1  0.3   6:01.01 conky                                                                                           
 2172 tagno25   20   0 37868 3528 2224 S    0  0.2   5:37.94 gnome-keyring-d                                                                                 
 2382 tagno25   20   0  6508 2136 1872 S    0  0.1   5:29.33 gvfsd                                                                                           
 2406 tagno25   20   0 52024 9776 7600 S    0  0.5   7:56.73 vino-server                                                                                     
 2604 tagno25   39  19 27076 4180 3668 S    0  0.2   9:29.33 tracker-indexer                                                                                 
 2905 tagno25   20   0 17428 3512 3324 S    0  0.2   6:54.79 indicator-messa                                                                                 
  937 root      20   0     0    0    0 S    0  0.0   1:55.01 kjournald

Edit:
I waited some more and noticed metacity was starting almost every second, and then disappearing a second later, then it comes back with a new PID

---

### Post by mikewhatever on 2010-05-05
What are the computer specs? Are you running Compiz?

---

### Post by tagno25 on 2010-05-06
It is a Inspiron 1501.
Specs:
```

AMD Turion 64 X2 Mobile TL-60 2.0GHz
2GB RAM
ATI Technologies Inc RS482 [Radeon Xpress 200M]
Atheros Communications Inc. AR5008 Wireless Network Adapter
```

I am running Compiz, that is why I found running metacity weird.

---

### Post by tagno25 on 2010-05-06
I finally killed metacity, and that fixed my CPU usage (`sudo killall metacity` repeat until it stopped).  Will have see if it restarts when I reboot the computer.

---

### Post by cimh on 2010-05-06
I'm getting this as well - been running lucid right thru from alphas but only noticing this since fresh install to the final version. my cpus are running on max at 1.6g and powertop shows just under 500 wakes/s for kernel scheduler- load balancer tick or somethink like that.

Done some searching for culprits but I dont have compiz installed and am running gnome with openbox not metacity. I dont run bt, cups or any other unnecessary programs at startup.

Any ideas where I should look?

Im on a 901 eee netbook with atom processors - this hi usage means faster battery drain (12w rather than 9) and the fans going all the time where as they would normally be stationary or v slow when the load is low.

I'm also running Lubuntu on a different partition on the same machine (That uses lxde/openbox on 10.04) and this shows the balancer tick waking up just 30-60times/s 

Edit
I think this would be better posted in [http://ubuntuforums.org/showthread.php?t=1390055](http://ubuntuforums.org/showthread.php?t=1390055)

sorry about that.

cimh
901

---

### Post by tagno25 on 2010-05-07
I rebooted and it came back.
I then edited ~/.gconf/desktop/gnome/session/required_components/%gconf.xml and changed "metacity" to "compiz".
You can also open gconf-editor and change the value of "/desktop/gnome/session/required_components/windowmanager" to "compiz"

---

