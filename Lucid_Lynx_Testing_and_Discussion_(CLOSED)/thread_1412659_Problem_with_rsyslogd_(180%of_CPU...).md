---
title: "Problem with rsyslogd (180%of CPU...)"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-02-21
All day long:
>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5865 syslog    20   0  248m  26m 1020 S  [COLOR="Red"]188[/COLOR]  0.9   3:36.48 rsyslogd           
 3268 zika      20   0  569m 170m  25m S    2  5.6   0:27.53 opera              
 4185 zika       9 -11  328m 8936 7292 S    2  0.3   0:32.48 pulseaudio         
 4335 zika      20   0  307m  37m 9964 S    2  1.2   1:26.45 compiz             
    1 root      20   0 23620 1884 1280 S    0  0.1   0:00.92 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.46 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.23 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.69 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      20   0     0    0    0 S    0  0.0   0:01.57 events/0           
   13 root      20   0     0    0    0 S    0  0.0   0:01.55 events/1  

---

### Post by nebosuke on 2010-02-21
Please have a look in this thread: [http://ubuntuforums.org/showthread.php?t=1409440](http://ubuntuforums.org/showthread.php?t=1409440)
Here you can follow the reported bug: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/523610](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/523610)

---

### Post by zika on 2010-02-21
> **nebosuke said:**
> Please have a look in this thread: [http://ubuntuforums.org/showthread.php?t=1409440](http://ubuntuforums.org/showthread.php?t=1409440)
Here you can follow the reported bug: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/523610](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/523610)Thank You, my mistake, I did not see the thread already active on this topic. I've "solved" my problem with **sudo stop rsyslog**, did not remove it, yet... After reboot, rsyslog is burning CPU, again... So, I'll try to tame it in /etc/rc.local or somewhere similar...
Yes, putting **stop rsyslog** in **/etc/rc.local** tamed it...

---

### Post by zika on 2010-02-25
Upgrade solved the problem...

---

