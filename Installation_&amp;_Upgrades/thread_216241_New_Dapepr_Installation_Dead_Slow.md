---
title: "New Dapepr Installation Dead Slow"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by p.n on 2006-07-15
I just did a fresh install of Dapper on my P4 3.0Ghz PC and it is dead slow.  her is the output of top;


```
Tasks:  87 total,   2 running,  84 sleeping,   0 stopped,   1 zombie
Cpu(s): 26.0% us,  2.3% sy,  0.0% ni, 71.7% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1003584k total,   464140k used,   539444k free,    12328k buffers
Swap:  2939852k total,        0k used,  2939852k free,   296408k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4365 root      16   0 65964  24m 8268 S 18.8  2.5  48:29.08 Xorg
 4954 paul      16   0 40176  14m 9232 R  7.6  1.5   0:27.51 gnome-terminal
 6264 paul      16   0  2196 1100  856 R  0.7  0.1   1:12.47 top
 4881 paul      15   0 48912  20m  12m S  0.3  2.1   0:10.80 gnome-panel
 4886 paul      16   0 17120 5300 3972 S  0.3  0.5   0:03.27 gnome-volume-ma
 4903 paul      15   0 46908 7884 6360 S  0.3  0.8   0:06.96 gnome-cups-icon
 4980 paul      15   0 14820 5168 4008 S  0.3  0.5   0:02.57 gnome-screensav
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.01 init

```

I wait litteraly ages for windows to render etc.

Something seriously wrong.

Pleae help
.

p.n

---

### Post by rcarring on 2006-07-15
Does it take long to boot up from cold on your machine?

Have you got the correct graphics driver installed?

---

### Post by p.n on 2006-07-15
I think I found the problem.  I took about a 2mm layer of dust off the top of my CPU heatsink.

---

