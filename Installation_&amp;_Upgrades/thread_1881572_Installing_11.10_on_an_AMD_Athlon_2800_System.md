---
title: "Installing 11.10 on an AMD Athlon 2800 System?"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by robn30 on 2011-11-15
Can Ubuntu 11.10 be successfully installed on this older system?  I believe the machine in question is running only 1 Gig of DDR 333 or 400.  Will that be sufficient if I set a large swap area partition.  Any advice or information would be much appreciated.  Thanks.

---

### Post by robn30 on 2011-11-15
bump.  Anyone any thoughts.

---

### Post by kurt18947 on 2011-11-16
I had a machine with very similar specs.  The only thing I found lacking was flash performance on certain web sites.  The CPU usage would be very near 100% and the video was still very jerky.  Flash on linux has gotten somewhat better so you might give it a go.  Lubuntu is a good choice for older/less capable machines.  There are also a couple distros what will play flash from a live install to see if your machine is capable.  I'm pretty sure Mint & PCLinuxOS will both do that.  PCLinuxOS does seem lighter.

---

### Post by mastablasta on 2011-11-16
i have an old maschine with 1.3 GB DDR 333 or 400 and it runs Kubuntu well, with most effects on (the unimportant one are off). youtube videos play nicely. the only issue is some websites with lots of scripts load slow.
 
a lt will depend on how well your graphics card is suspported. if it is supported well then it will run nicely. if not, or if the card is weak you might have better luck with Unity 2D or use Xubuntu. 
 
as said you can alway use a liveCD/liveUSB to try out the system without making any changes to it. ofcourse they dont' work as fast as real yinstall but it gives you a chance to see if it all works and loads as it should.

---

### Post by robn30 on 2011-11-17
> **kurt18947 said:**
> I had a machine with very similar specs.  The only thing I found lacking was flash performance on certain web sites.  The CPU usage would be very near 100% and the video was still very jerky.  Flash on linux has gotten somewhat better so you might give it a go.  Lubuntu is a good choice for older/less capable machines.  There are also a couple distros what will play flash from a live install to see if your machine is capable.  I'm pretty sure Mint & PCLinuxOS will both do that.  PCLinuxOS does seem lighter.

> **mastablasta said:**
> i have an old maschine with 1.3 GB DDR 333 or 400 and it runs Kubuntu well, with most effects on (the unimportant one are off). youtube videos play nicely. the only issue is some websites with lots of scripts load slow.
 
a lt will depend on how well your graphics card is suspported. if it is supported well then it will run nicely. if not, or if the card is weak you might have better luck with Unity 2D or use Xubuntu. 
 
as said you can alway use a liveCD/liveUSB to try out the system without making any changes to it. ofcourse they dont' work as fast as real yinstall but it gives you a chance to see if it all works and loads as it should.

Good deal.  Thanks for the input and I will give it a go and see how it works out.

---

### Post by efflandt on 2011-11-17
I just tried 64-bit 11.10 on Athlon64 3200+ (2 GHz) 2 GB RAM legacy ATI X1300 video from bootable iso on USB memory stick and it ran fine (of course boot is slow from memory stick).  Using System Monitor along with a script to monitor its cpu speed it seemed to idle at 20% of 800 MHz and just briefly bumped 2 GHz for a second or so when starting Firefox or starting to load a web page.

With persistent data, I downloaded/installed Supertuxkart using the Software Center and that ran fine using 50% of the cpu.

I use this terminal script to test or monitor cpu speed, which will show multiple actual or virtual (hyperthreading) cores if you have them.  My Athlon64 only has one core, but it shows all 4 virtual cores of my i5:

```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```

---

