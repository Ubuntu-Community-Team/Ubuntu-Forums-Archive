---
title: "Prefix not set using Wubi"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by biggyk on 2012-04-27
hey everyone,
 
I wanted to use Wubi to install ubuntu 12.04. I used the default the settings and it downloaded the 12.04 iso and asked me to reboot as usual. The grub screen popped up and I picked Ubuntu but then it gave me "Syntax not set" and I had to hit reset and reboot into windows.  Anyone can help me out. I was installing to C drive which my windows parition is on.

Thanks

---

### Post by bcbc on 2012-04-27
This message is not relevant to the problem you experienced. It's an error, and it's a message, but it happens on all wubi installs, each time they boot (and has since release 11.04).

So something is happening *after* that that is causing you to have to reboot. Please provide more information:
what do you see when you boot? 
What graphics card do you have?

Any other info you can provide: computer brand/model...?

---

### Post by biggyk on 2012-04-27
After I pick Ubuntu in grub i get a black dos looking screen that says Try 0,1 Prefix not set and just stays there so after waiting I have to reset. 

I have a gigabyte gtx 460
amd x4 455 3.1ghz
8gigs ram

I installed ubuntu once on a separate hard drive on its own and unplugged my windows drive at the time so I wouldnt have the grub on my windows drive. its was fine so I dont know what the problem is here.

---

### Post by bcbc on 2012-04-27
> **biggyk said:**
> After I pick Ubuntu in grub i get a black dos looking screen that says Try 0,1 Prefix not set and just stays there so after waiting I have to reset. 

I have a gigabyte gtx 460
amd x4 455 3.1ghz
8gigs ram

I installed ubuntu once on a separate hard drive on its own and unplugged my windows drive at the time so I wouldnt have the grub on my windows drive. its was fine so I dont know what the problem is here.

Sometimes wubildr.mbr (grub4dos)takes a little a little time to find the wubildr file. How long did you wait?

---

### Post by biggyk on 2012-05-08
Yeah just had to wait longer, It all worked out.  Thanks

---

