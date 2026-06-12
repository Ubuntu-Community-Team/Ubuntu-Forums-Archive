---
title: "After cd boot: &quot;crc error...&quot;"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by p3e2 on 2006-06-05
My fried tries to install Ubuntu but when launches something (install... test...) from the cd, he has this error:

```
crc error  kernel panic - not syncing :VFS: Unable to mount root fs on unknown-block (1,0)
```

He burned 3 cds and i give my cd to him, he always has the same error...

Pc
Pentium 4 3.0ghz , ram 512mb , hd Maxtor 160 gb and ati 9600xt 128 mb

Sorry for my "english", can anyone help up??? :(

---

### Post by Chickenmonger on 2006-06-05
On boot, did you try the "Check CD for Defects" option? It's the third option.

Also, what did you use to download the ISO? HTTP, FTP, BitTorrent, or Jigdo?

---

### Post by pepgui on 2006-06-05
I am p3e2's friend 

On boot i've tried to do that 
but I have the same error.
I've used http 
but I think is my computer because I 've used also the cd with which p3e2 has installed  his ubuntu. 

sorry for my english 

tnx

---

### Post by deadgobby on 2006-06-05
I read this ditty on Disrowatch
[COLOR="Red"]I reported this bug and received a polite response from the developers. While waiting for a fix, I've found a reasonable workaround. I edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver. I no longer experience crashes, but I can forget about playing PlanetPenguin-Racer (ppracer, formerly known as TuxRacer).[/COLOR]

---

### Post by bluelight on 2006-06-05
I've got the same error. I've downloaded the DVD Install, Alternate Install, and Desktop install (all i386) using HTTP and BitTorrent. Every time I use the options "Start or Install Ubuntu"(w/ or w/o the VGA option) and "Check the CD/DVD for Defects" I get the same crc error.

My System Specs are:
ASUS A8N-SLI Deluxe Motherboard
AMD Athlon 64 3500+ 2.21 GHz
4 GB RAM
NVidia GeForce 6600 256 MB RAM

Is it something to do with the BIOS or that I'm trying to run i386 Ubuntu on an AMD64 Processor. I don't know why that would affect it but it's a thought.

Can't wait to get Dapper working.

---

### Post by ophsj on 2006-06-18
sO has any solution to this problem been fixed... Cuz im haveing the same obsticle.

---

### Post by Vogateer on 2006-06-20
I've encountered the same error with multiple discs on my G3 machines, and after an update on my Athlon XP, I changed to the k7 kernel to fix the Athlon XP, but still no luck with the G3 PPC machines. If anyone figures out the answer, I will be very grateful.

---

### Post by loki on 2006-06-26
I was experiencing the same problem after downloading, burning & trying various versions of 6.06 from many different locations. However everytime I was burning the CD's I was using Windows and Nero, I rebooted my Laptop to Kubuntu & used K3B (Standard settings, sao I think) and.... voila... worked first time.

Can't explain it, Can think of many things it could be but to be honest I'm just happy its now worked.

Hope this helps anyone in any way????

---

### Post by saperduper on 2006-07-10
I had the same problem with xubuntu 6.06. The problem solved as i burnt the Cd at a low speed (10x)!

---

### Post by pauln600 on 2006-07-19
I have the same problem.  The installation disc verifies on another machine.

Paul N.

---

