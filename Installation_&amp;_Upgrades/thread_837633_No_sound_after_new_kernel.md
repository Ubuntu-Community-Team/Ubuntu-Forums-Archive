---
title: "No sound after new kernel"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Ginjeet on 2008-06-22
Kubuntu upgraded to newest kernel (i think 2.6.24-19) and after that i noticed that the youtube had a scratchy noise. I restarted the computer and now I have absolutely no sound system wide.

on startup it gives:
ALSA lib pcm.c:2415:(snd_pcm_open_noupdate) Unknown pcm default. I can not figure out the situation graphically and i dont have enough experience to solve the problem.

Help appreciated!

Ginjeet:confused:

---

### Post by Pumalite on 2008-06-22
Post:
lshw -C sound

---

### Post by agentsmith23 on 2008-06-22
I actually have the same thing happening and i would also like to know how to fix it. Here is what i got from running "lshw -C sound". The only difference is that I am using Ubuntu.


```
 *-multimedia UNCLAIMED  
       description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64

```

---

### Post by iaculallad on 2008-06-22
Try to install the linux-generic to get back your sound:

```
sudo aptitude install linux-generic
```

---

### Post by agentsmith23 on 2008-06-22
That worked perfectly! Thank you!

---

### Post by Ginjeet on 2008-06-23
> **Pumalite said:**
> Post:
lshw -C sound

That gives no output and also, aptitude install linux-generic doesnt help either.
:(

---

