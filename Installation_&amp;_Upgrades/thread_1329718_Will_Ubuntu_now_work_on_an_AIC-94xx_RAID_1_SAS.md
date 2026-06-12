---
title: "Will Ubuntu now work on an AIC-94xx RAID 1 SAS?"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by randall_l on 2009-11-17
Hi there.

Before I take down a production server in a desperate attempt to free our organization from Novell...

Will Ubuntu now work on a Supermicro 6015W-URB with an Adaptec AIC-9410 SAS RAID (fake raid) card?

I tried Intrepid and Jaunty without success before resorting to Novell's SLES 11 a few months ago.

Intrepid and Jaunty both recognized the RAID 1 and I followed the instructions on other posts here about copying the aic-94xx.fw file (downloaded from adaptec) to /lib/firmware during install, but on post-install boot, the system spat the dummy, claiming not to have a hard disk.

Please, oh please Ubuntu, help me be free of Novell!

Thanks in advance for any assistance you can provide.

Cheers.
Randall

---

### Post by whoop on 2009-11-17
Couldn't you just use it with software raid, as fake raid is not supported by ubuntu. Improvements from fake raid over software raid aren't that big as the cpu will do most stuff on fake raid anyway. Fake raid seems like a bit of a scam to me, unless you want to multiboot (use different os's (linux and windows for example) and use the raid from both).
If ubuntu can see all the individual disks in the machine (possibly by disabling the raid controller in your BIOS) you will be able to use software raid. This has comparable performance as fake raid, and it's supported by ubuntu. 

It works well, I use it myself, on a machine that supports fake raid actually. I just never bothered with fake raid, because it's unsupported, has no real performance gain, I feel like I have less control (I can monitor everything in software mode anyway), and it's (I'm not 100% sure about this) probably vendor specific (closed source technology) <-- if my motherboard fries it might be required to get a new one from the same make,model,vendor or chipset to get to my data again (if I would be using fake raid, that is).

---

