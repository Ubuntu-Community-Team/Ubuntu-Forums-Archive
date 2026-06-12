---
title: "installing on Nvidia 680i SLI motherboard?"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by rkannan on 2006-12-08
Hi,
I have a E6400 processor on a NVidia 680i SLI motherboard with the new Nvidia 8800 GTX card. 
I am trying to install Ubuntu 6.10. The stock installation failed starting up the X server. I tried the alternate server and that fails with APIC errors. I tried the noapic boot options but still no luck. 

Has anyone had success installing Ubuntu on this motherboard?

--Kannan.

---

### Post by hagakure on 2006-12-09
> The stock installation failed starting up the X server.

That's because there is no 8800 driver for linux from nvidia yet.

> I tried the alternate server and that fails with APIC errors.

I had that problem on my i386 install from another computer when I swapped the hard drives, I passed the command noapic to the kernel to fix that.

*edit* I just saw that part about noapic, sorry I didn't see that.

---

### Post by wood2395 on 2006-12-12
> **rkannan said:**
> Hi,
I have a E6400 processor on a NVidia 680i SLI motherboard with the new Nvidia 8800 GTX card. 
I am trying to install Ubuntu 6.10. The stock installation failed starting up the X server. I tried the alternate server and that fails with APIC errors. I tried the noapic boot options but still no luck. 

Has anyone had success installing Ubuntu on this motherboard?

--Kannan.

Hey, I've got the exact same setup.  It rocks in XP, but I too cannot get Ubuntu installed....:-k

---

### Post by nikki on 2006-12-13
I got it installed on my 680i, my problem though is that I can't get it to see my network or internet.

---

### Post by hagakure on 2006-12-17
The networking on this mobo/chipset doesn't work in linux, ubuntu anyways. Search forcedeth, it has worked for some. It doesn't work for me though. I got a PCI network card, and I'm using that until its fixed (if ever!)

---

### Post by wdiz on 2006-12-26
> **hagakure said:**
> The networking on this mobo/chipset doesn't work in linux, ubuntu anyways. Search forcedeth, it has worked for some. It doesn't work for me though. I got a PCI network card, and I'm using that until its fixed (if ever!)

It is fixed with the P23 bios from EVGA...

rkannan : for your 8800GTX, you can use the latest linux driver 97.46

---

