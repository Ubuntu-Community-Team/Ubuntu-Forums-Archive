---
title: "Performance difference IDE as SATA vs IDE as PATA?"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by jimdaworm on 2007-12-20
Hi everyone.

I have Ubuntu 7.10 installed and found that I had to set my IDE to PATA in my bios to get it to work.

All my drives are sata 2. 

My question is:

Is there a performance difference between setting my bios to IDE as Sata vs IDE as PATA?

---

### Post by zyghom on 2007-12-20
did you try:
```

sudo hdparm -tT /dev/sda  
```

in both settings  ?

---

### Post by jimdaworm on 2008-01-01
Hi, thanks for the reply.  I am unable to as if I start IDE as sata it does not boot.

This is the current performance though, so I guess its acceptable:
> /dev/sda:
 Timing cached reads:   9528 MB in  2.00 seconds = 4768.69 MB/sec
 Timing buffered disk reads:  208 MB in  3.02 seconds =  68.96 MB/sec
adam@buntyhome:~$ 



---

### Post by tgalati4 on 2008-01-01
The maximum performance for any physical drive is a Western Digital 10 K Raptor that tops out between 70 and 75 MB/sec.  So your drive is 69 MB/sec.  I would say that's pretty fast.

PATA will give you burst speeds of 100 to 133 MB/sec.  SATA will give you 150 to 300 MB/sec.  If you have enough RAM (say 2 GB), most of your short (burst) requests will be out of cache (L1, L2, L3 or RAM).  It's sustained reads and writes where SATA will make a difference.  But only if your physical drive can handle the higher speeds.  I don't know of any physical drive that can take advantage of the sustained SATA speeds.

I'm sure someone has done a performance comparison of IDE mode PATA vs SATA for RAID arrays and that may make a difference.  For home/desktop use, RAID doesn't make a lot of sense so you have to rely on hdparm results to gauge performance.

Perhaps you can do a BIOS upgrade to get SATA mode working.  But then again, you are getting fast speeds so unless you change your disk drive, it really won't make any difference.

If you don't have 2GB of RAM then that should be your next upgrade.

---

