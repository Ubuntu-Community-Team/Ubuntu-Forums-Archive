---
title: "Swap size? (Solved)"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by hallkbrdz on 2005-11-03
Given: 
bhall@roadie2:/usr/lib$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1            110895172  16713652  88548332  16% /
tmpfs                   778128         0    778128   0% /dev/shm
tmpfs                   778128     12588    765540   2% /lib/modules/2.6.12-9-386/volatile

What is my swap size? I would think, 778MB - right? 

So why isn't the swap partition of 4448 on /dev/hda5 (inside a /dev/hda2 part) being used as shown in gparted?  This install was on a clean new drive - it should be using over 4GB for swap, right?  Sorry - questions from a long time Solaris guy.

I need at least 1.5GB to hibernate the laptop (match RAM size). Right now, I can't seem to do that, and I think it's because I'm only getting a 778MB size for swap.

Bryan

---

### Post by Xian on 2005-11-03
That command will not get you the information that you need.
Use the top command instead & then read in the first section of output.

Below is an example from my own box:

```
$ top

top - 22:27:18 up  4:13,  2 users,  load average: 0.32, 0.40, 0.27
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7% us,  1.7% sy,  0.0% ni, 94.4% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:    451660k total,   442900k used,     8760k free,     9092k buffers
Swap:  1052216k total,    35424k used,  1016792k free,   128848k cached
```

---

### Post by hallkbrdz on 2005-11-04
Thanks, yes top shows it correctly.  Note to self: on linux ignore swap shown with df. :rolleyes:

---

