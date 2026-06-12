---
title: "Which kernel for HP DL580 G2 ?"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by dtushing on 2010-04-02
Hi, 

I have a HP DL580 G2 server with 4 x Intel Zeon 2.8ghz and 8gig of RAM. 

Can I run a 64bit kernel and recognize the full 8gig of RAM ?

I've tried a 32bit kernel but I don't think it's seeing past 4gig of RAM. 

The standard 64bit kernel install give me an error "Kernel requires x86_64 CPU but only detected i686 CPU"

Thanks in advance for your help.

D

---

### Post by conradin on 2010-04-02
Yep, there is a 4GB limit on 32-Bit systems for ram. If you use a 64 bit system you can make use of all your 8GB of ram and or install / utilize more if you can install it.(yes, the OS uses more ram for its operation but 8GB is well above the minimum required for 64-bit systems.)

not sure whats up with your cpu. can you give us the output of 
```

cat /proc/cpuinfo

```

I also wonder about your bios settings. Is this a multi core server with 4 separate single core CPUs?

---

### Post by dtushing on 2010-04-02
Hi, 

It's actuall 4 separate CPU's - I can see each of them in a top output so it does detect them okat with the 32 bit kernel. I think they are just 32bit CPU's.
Thanks for your help. Somebody has suggested trying the PAE kernel so I'm going to give that a go.

Thanks 
D

---

### Post by conradin on 2010-04-03
you might surf around in your BIOS config and see if any options for running in 64 bit mode are available.  Also you might consider open MPI. Finally though, check the mother board manufacturer for lists on compatible OSes

---

