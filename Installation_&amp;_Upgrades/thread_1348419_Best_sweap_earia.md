---
title: "Best sweap earia"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by MMALLOW on 2009-12-07
Hi 
 
some people said sweap must be your ram *2
 
 i have 4 giga ram , i made my sweap 8 giga ( 4*2)
 
this correct 
or what
 
and my frind told me make 6 giga  ONLY beacuse 
 
operating system32 read 6 giga only
 
i want ask you this true ,
 
and which sweap size   better

---

### Post by audiomick on 2009-12-07
Hallo.
I learned recently that the rule for SWAP = 2*RAM is out of date. I came from times when swap was still only 256MB or so.

For functions like suspend and hibernate (i.e. put the computer to sleep), the swap needs to be at least as large as the RAM, because the contents of the RAM get written into swap in the process.

If you are wondering whether your system is seeing all your RAM, open the system monitor at system> administration> systerm monitor.

On the third tab of this, "resources" you can see how much RAM the computer has recognized and what it is doing with it.

---

### Post by MMALLOW on 2009-12-07
HI
I CANT UNDERSTAND YOY
 
FIRST 
 
I WANT TO KNOW MY SWEAP SIZE 8 (4*2)
 
THIS CORRECT OR NOT
 
AND WHAT THE RIGHT
 
SECOND 
 
IF IGO TO system> administration> systerm monitor
CAN YOU EXPLAIN THIS TO ME , WHAT I WILL DO , AND CAN YO GIV ME EXAMPLE

---

### Post by presence1960 on 2009-12-07
> **MMALLOW said:**
> HI
I CANT UNDERSTAND YOY
 
FIRST 
 
I WANT TO KNOW MY SWEAP SIZE 8 (4*2)
 
THIS CORRECT OR NOT
 
AND WHAT THE RIGHT
 
SECOND 
 
IF IGO TO system> administration> systerm monitor
CAN YOU EXPLAIN THIS TO ME , WHAT I WILL DO , AND CAN YO GIV ME EXAMPLE

First do not type in all CAPS- it is considered rude- the equivalent of angrily yelling. Plus it is hard on the eyes!

While it is not wrong to have swap at RAM x 2, you generally won't ever need that much. If you want to use suspend and hibernate your swap should be equal to your installed RAM since whatever processes are running when you use that function will be copied from your RAM to the swap partition. Unless you are low on disk space i would leave the swap as is for now.

32 bit Operating Systems (whether Windows, linux, mac) can not address a full 4 GB of RAM. But 64 bit Operating Systems can.

---

### Post by kimberlite on 2009-12-07
Note that Ubuntu has both 32-bit and 64-bit versions too. You may want to use the later to enjoy your 4GB RAM...
In system-monitor at "system" tab you can see how much RAM is usable by your box.

---

