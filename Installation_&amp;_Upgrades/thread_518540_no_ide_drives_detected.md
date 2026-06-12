---
title: "no ide drives detected"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by red777 on 2007-08-06
I don't know why but I can't get any further than starting up PC then it comes up with detecting ide drives & stops. I am using an install disk to get this thru.
can anyone help please.

---

### Post by Wim Sturkenboom on 2007-08-06
Nobody can help you without hardware specifications. Did you buy second hand? Or is it a new system? If the latter, return it under warranty. Stupid question but do you have harddisks in your machine? Have you seen it working before? Did you build it yourself?

---

### Post by red777 on 2007-08-06
system was working fine until re start today.

running Ubuntu 7.04 & kubuntu for the last 3 months with no problem,I had the option at startup as to which kernel to load
 then suddenly wham no drives detected. Checked in BIOS & everything seems to be all there.It peeves me that I had only just got it all setup just right & was going to backup TODAY then this
as much info as I recall,if theres any more info I can give just ask
AMD athlon 64 3000mhz
Nvidia GE6600 Draphic card
WDA 160gig HDD as master Ubuntu/Kubuntu 
WDA 120gig HDD as secondary Windows XP (not used)


I suspect a GRUB loading problem but I'm totally lost at the moment

---

### Post by Wim Sturkenboom on 2007-08-06
So Grub tells you that there are no HDs and the BIOS tells you that there are. To be honest, I doubt that very much (but I'm not a Grub expert).

I had a similar problem on one of my boxes. This was (in simple terms) due to the HD not being woken up completely when the BIOS checks for its presence (not sure why). It could be solved by switching the Quick Power On Selftest off (so a full memory test was done). That give the HD more time to wake up and solved the issue.
It's worth a try.

---

