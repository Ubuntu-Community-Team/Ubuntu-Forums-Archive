---
title: "Performance Issues installing 12.10 on Zbox Intel Atom D2700"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by jwaclawsky on 2013-02-21
I just installed Unbuntu 12.10 (32 bit version) on a ZOTAC ZBOX (the box print label says it has an Intel Atom D2700 dual-core, 2.13 GHz). The problem is the system is running very slow. I noticed two issues:

1- the system monitor shows 4 CPUs all running 50% to 80% even with the system sitting idle. Who do I believe: the box which says "dual-core" or the monitor that shows 4 CPUs???? - I am reasonably sure this is a dual core processor and highly suspecious that the system monitor is running correctly)

2 - The system Monitor shows the compiz process running at 160% or higher continuously. (the only other two processes showing any activity are the gnone-system-monitor (around 40%) and firefox (around 20%). 

Ther also seems to be a lot of periodic receive data shown in the system monitor every 2.5 seconds.This may be another symptom. I suspect some kind of incompatability or software version issue. The documentation is not clear but I suspect this might require 64 bit system? (...but I am running 32 bit version of Ubuntu). Any guidance on how to proceed would be appreciated.  Or where to post this problem. Thanks!

---

### Post by snowpine on 2013-02-21
1. 2 cores look like 4 cores in this case because of "hyperthreading"

2a. System monitor is, itself, a load on the system.Try the terminal command "top" for a more accurate look.

2b. Suggest you do a forum search on "cedar trail graphics" as I have seen many existing discussions about your specific chipset. (But I have no experience with it personally.) For such a low-performance processor as the Atom, you might have better luck with Xfce or LXDE (xubuntu-desktop or lubuntu-desktop). I believe Intel discontinued the D2700 last year, due to its poor performance. :(

---

### Post by jwaclawsky on 2013-02-21
Ok, I used "top" command in the terminal and got pretty much the same results with compiz at 130% CPU and Xorg at 49%, firefox at 20% and "top" itself less than 1% and a few other things less than that. This is with me typing this message in the firefox browser and no other system activity.  

This dual core chip is running at 2.13 GHz and it sure seems like it should have enough power and appears to be suitable for 32 or 64 bit architectures. I have Ubuntu running on an old Dell 9" mini with an INTEL ATOM N270 at 1.60 Ghz x2 and it is doing better that this set up (I was just looking at it with monitor and top). There is no "compiz" sucking up all the CPU on that machine. I also have 2 other laptops with Ubuntu running fine. I am wondering if compiz should be running continuously over 120% CPU? This seems wrong (is there something in compiz that needs to be adjusted?) or should I use/try 64 bit Ubuntu?

One other thing, there is a constant flow of received packets showing from the network. It is very periodic approximately every 2.5 seconds ....if that means anything. My other ubuntu machine does not show any of this (background? ...for compiz????) network activity

---

### Post by snowpine on 2013-02-21
I should have bolded this part; apologies:

> **snowpine said:**
> 2b. Suggest you do a forum search on "cedar trail graphics" as I have seen many existing discussions about your specific chipset. 

---

### Post by jwaclawsky on 2013-02-21
I appreciate your help but I am not following your logic here. Why/What am I looking for about ceder trail graphics, if compiz is running out of control? ...BTW, I guess I should mention that this machine has an Intel NM10 Express chipset and an NVIDIA GeFprce GT 520M GPU (with 512 MB DDR3 memory). Isn't this GPU going to be doing the graphics for me?

---

### Post by snowpine on 2013-02-21
Apologies, as I said I am somewhat unfamiliar with your hardware. In that case you want to search for discussions of your Nvidia card. Compiz thrashing the CPU is often indicative that you have the wrong graphics drivers.

---

### Post by jwaclawsky on 2013-02-21
Ok, ...and thanks for your help. I really appreciate it and the discussion always helps. I will start digging into that NVIDIA GPU now. BTW, Is there a better thread where I should post this problem?  ...that increases my chances of someone recognizing this problem and having an immediate answer  ...wishful thinking on my part but worth a try  :-)

---

### Post by jwaclawsky on 2013-02-22
Thanks Snowpine, you were right it was a driver issue. You got me pointed in the right direction. I just had to apply the correct driver (not the Open source one!). Now the machine is working nice and responsive. Still a couple of minor things I am investigating but this is closed.

---

