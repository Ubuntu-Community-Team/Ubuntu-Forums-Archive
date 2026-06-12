---
title: "Errors on install on AMD 64 system"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by CrashTECH on 2007-04-03
I have decided to switch my server at home from windows to ubuntu, as that is what is used at work. I figure why not do at home what I do at work? I can only benefit in both worlds.

Anyway, here are the system specs (I got a new uber laptop which runs ubuntu just fine, so I moved my desktop rig to server duty).

AMD Athlon 64 3500+
2 GB Corsair Ram
Nvidia GForce 6600GT 128mb
Chaintech Nforce 4 motherboard (can't recall the exact board atm)
several Hard drives, dvd-burner

I tried both server editions of 6.06 LTS and 6.10 for the x64 arch... same results on both...

Decompressing Linux...done.
Booting the kernel.
[xx.xxxxxxxxx] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[xx.xxxxxxxxx] i8042.c: Can't read CTR while initializing i8042.
(system pauses for a about 40 seconds)
[xx.xxxxxxxxx] ohci_hcd 0000:00:02.0: USB NC takeover failed! (BIOS/SMM bug)
[xx.xxxxxxxxx] ohci_hcd 0000:00:02.0: can't setup
[xx.xxxxxxxxx] ohci_hcd 0000:00:02.0: init 0000:00:02.0 fail. -16

boots to install....

I got to a couple different places in the install, but not very far, just around selecting the language. It just stopped wherever it got to without my intervention at all.

System was locked up and I couldn't do anything... same results with different cds, different versions, et al.

Advice?

---

### Post by webjames on 2007-04-03
i'm not sure if this will help but i know that error is to do with your grfx card. if you have onboard video you could try removing your grfx card and using that to install. once you have ubuntu installed it should be easier to diagnose the problem with the grfx card drivers and xorg config.

regards, James

---

### Post by CrashTECH on 2007-04-03
I hope it does! I don't remember to be honest.

Yay for PCI-Express :)

I will try tonight when I get home and post back the results.

---

### Post by CrashTECH on 2007-04-03
No dice. No onboard video card. Are their any boot options I can sling in there that might get me around this?

---

