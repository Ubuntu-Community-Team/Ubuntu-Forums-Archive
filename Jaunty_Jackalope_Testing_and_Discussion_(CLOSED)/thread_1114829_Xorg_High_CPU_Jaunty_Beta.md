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

### Post by gnomeuser on 2009-04-03
Very likely X is executing on behalf of something else. It's one of these wonderfully opaque UNIX designs that make it dead simp.. oh wait idiotically hard to figure out what is actually using the CPU.

You can try using the xrestop to peek inside maybe that will shine much required light on the guilty parties

---

### Post by zevans on 2009-04-03
Have you pulled the absolute latest - a bunch of stuff came out yesterday that fixed a lot of this kind of thing for me.

---

### Post by andrewabc on 2009-04-03
> **CB500 said:**
> Hi,

I have upgraded my kubuntu to Jaunty Beta and now xorg is consuming a lot of cpu, even with desktop effects off.

I have an Intel Q965 that works great with 8.10.


I have g965 x3000, and I've had high xorg CPU since 2007. It has gotten better over time, but I still notice it with compiz enabled and scrolling in firefox. It shouldn't be using 20% CPU just to scroll a simple page in firefox. Is this a problem you had?

With compiz disabled in intrepid, xorg is currently using 17% CPU to scroll fast while typing this. It used 25% when I click "post" to bring me to this thread.

---

### Post by CB500 on 2009-04-03
Problem solved.

I don't know why, but after the upgrade the kernel modules for nvidia cards where instaled and caused the high cpu usage. After some apt-get purge, everything got back to normal.

This pc never had a nvidia card installed

Thanks

---

### Post by nicksanders on 2009-04-03
Same here, after the upgrade to nvidia 180.44 xorg was running at a consistent 15% cpu. This is without desktop effects which I can't get to work for more than 5 minutes before windows stop refreshing without moving them.

Anyway to fix it I reverted back to 180.37. 

sudo dpkg -i /var/cache/apt/archives/*180.37*

---

