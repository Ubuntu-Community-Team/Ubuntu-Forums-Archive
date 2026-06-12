---
title: "Dual Boot Problems_2 HD"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by bparham on 2006-08-19
Ok, here is the problem. I want to Dual Boot XP and Dapper. Originally I wanted to put Dapper on my new HD, make it the Primary and make my existing XP HD the slave. Problem is that for whatever reason, my computers BIOS simply won't recognize the XP drive when connected as the slave. I thought that perhaps I had a cable problem, but the BIOS recognizes the Dapper drive when it is connected as slave. That leads me to my problem. 

How can I change grub so that I can boot Dapper as the Slave without changing the mbr for XP?

---

### Post by K.Mandla on 2006-08-20
Not to oversimplify, but are either of the jumpers on the drives set to the wrong state? I mean, are both jumpers set for the proper spot on the cable? 

I was thinking if the XP drive's jumper is set to master, it might be confusing the BIOS.

Anyway, just an idea.

---

### Post by bparham on 2006-08-20
I've gone through multiple settings. The XP drive only has 5 jumper settings to try, and I've tried them all, it simply refuses to work as the slave drive. I even thought it was the cable, but seeing as how BIOS sees the Dapper drive when it is connected as slave that can't be the problem.

I thought about disconnecting the primary drive and re-installing Dapper, the problem is that my BIOS doesn't recognize that any drives are connected when the primary drive isn't connected. 

I'm just out of ideas. I really want to keep the two separate because I expect that I'm going to trash Dapper on multiple occassions and I don't want to have to worry about it ever effecting XP (not that I really like it!) Just can't afford to be without the computer and I value my life (my wife would kill me if I screwed up XP).

---

### Post by bparham on 2006-08-20
Hallelujah!!! I got it figured out.

---

