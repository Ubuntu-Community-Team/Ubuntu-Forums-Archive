---
title: "kernel 2.6.31 + iwlagn --&gt; no wifi!"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-09-04
hi, i update daily karmic but i have serious problem with wifi ( intel 5100AGN ,  module: iwlagn)

[ 13.756879] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 13.756881] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 13.756930] iwlagn 0000:07:00.0: enabling device (0000 -> 0002)
[ 13.756938] iwlagn 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 13.756949] iwlagn 0000:07:00.0: setting latency timer to 64
[ 13.756964] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x565CBE3F
[ 13.909555] iwlagn 0000:07:00.0: Failed, HW not ready
[ 13.909569] iwlagn 0000:07:00.0: PCI INT A disabled

moreover, installing linux-backports, i have this message that hangs boot kernel

iwlagn: MAC is in deep sleep!



same problem with Atheros AR8121/AR8113/AR8114 (module atl1e)


karmic with kernel 2.6.30 -> wifi+eth works fine!

please fix this bug!

---

### Post by taavikko on 2009-09-04
> **biasquez said:**
> 
please fix this bug!

Please file it in launchpad. Search before reporting.
```
ubuntu-bug linux
```


Bugs reported here in the forum, doesn't get fixed. (only by great chance)

---

### Post by biasquez on 2009-09-04
> **taavikko said:**
> Please file it in launchpad. Search before reporting.
```
ubuntu-bug linux
```


Bugs reported here in the forum, doesn't get fixed. (only by great chance)

i already reported this problem here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)


no progres....

---

### Post by taavikko on 2009-09-04
> **biasquez said:**
> i already reported this problem here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)


no progres....

Please run
```
apport-collect 418933
```

To provide the bug all available info.

---

### Post by biasquez on 2009-09-04
> **taavikko said:**
> Please run
```
apport-collect 418933
```

To provide the bug all available info.

if wifi doesn't work, apport can't send report...i can report bug with old kernel where wifi works...

moreover, i have same problem with ethernet (Atheros AR8121/AR8113/AR8114)....maybe with new kernel, there is problem about networking services.

so i don't kwnow how send full report..

---

