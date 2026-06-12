---
title: "Boot Freezes"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by snowniak on 2008-09-06
Intrepid Alpha4 is freezing at boot, when I use the default kernel.

It only boots if I press "esc", and choose the "2.6.24-19".

The processor goes at 100% (i can listen the cooler speed increase).

I am using a laptop, HP DV6327.

AMD Processor, X2
2 GB RAM DDR2
NVIDIA Go6150

--

As I can only use my old kernel, ubuntu dont let me use the NVIDIA driver.

So I am on a 800x600 vesa screen now.

I tried to build the module by myself, but as I need old kernel-sources, 

they are not at the APT anymore.

--

I cant report a bug because have no idean on what is going on.

--

I have made the upgrade today (6-Sep), so I think that I have the Alpha 5, but I dont know yet...

---

### Post by MJWitter on 2008-09-07
Hey, I had a similar problem(on an HP DV6363) with the latest kernel. I left it for about 5 minutes and it eventually did continue to boot. 

Otherwise adding "noapictimer" to boot parameters, as suggested elsewhere, made it load quickly.

---

