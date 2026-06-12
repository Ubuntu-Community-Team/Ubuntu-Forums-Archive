---
title: "Xorg High CPU Jaunty Beta"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CB500 on 2009-04-03
Hi,

I have upgraded my kubuntu to Jaunty Beta and now xorg is consuming a lot of cpu, even with desktop effects off.

I have an Intel Q965 that works great with 8.10.

Any help would be appreciated.

Thanks 

CB

---

### Post by Kevbert on 2009-04-03
Please go to konsole and enter
```
top
```
This will tell you what process is using the most CPU and memory.

---

### Post by CB500 on 2009-04-03
Ok. Here is an exemple with no effects.
xorg is consuming 45% of CPU

```
top - 12:12:19 up  1:11,  1 user,  load average: 0.16, 0.18, 0.29
Tasks: 141 total,   2 running, 139 sleeping,   0 stopped,   0 zombie
Cpu(s): 22.1%us,  0.8%sy,  0.0%ni, 76.9%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2576040k total,  2019512k used,   556528k free,    93652k buffers
Swap:  1951888k total,        0k used,  1951888k free,  1419840k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5758 root      20   0  592m 181m 5892 R   45  7.2  19:57.36 /usr/bin/X11/X -nolisten tcp
 6085 m80189    20   0  140m  34m  17m S    1  1.4   0:10.72 /usr/bin/konsole
  929 m80189    20   0  2448 1200  912 R    1  0.0   0:00.10 top
 5862 m80189    20   0 64240  20m  15m S    1  0.8   0:31.48 kwin
 5866 m80189    20   0  328m  44m  25m S    1  1.8   0:13.62 /usr/bin/plasma
    1 root      20   0  1904  776  564 S    0  0.0   0:01.40 /sbin/init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 [kthreadd]
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 [migration/0]
    4 root      15  -5     0    0    0 S    0  0.0   0:00.26 [ksoftir
```

---

### Post by Kevbert on 2009-04-03
It may be related to one of the reported Jaunty X bugs in [[COLOR="Red"]Launchpad[/COLOR]]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=jaunty+x+server&search=Search+Bug+Reports&field.scope=all&field.scope.target=").

---

