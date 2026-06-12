---
title: "Breezy on VIA Samuel 2 -&gt; Bad Idea!"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by mdoering on 2005-10-10
After hanging in front of an AMD Athlon XP powered box for some time, making noise and wasting energy for just browsing the web and programming, I decided to make my room less noisy and bought a PC-Chips mainboard with a VIA Samuel 2 CPU. The whole PC now just needs about 20 watts in normal operation compared to 130 before. All in all this machine is very satisfying for the things I want to do. Most people will laugh about this chip. :) 

After having hoary running for a longer time and beeing mostly satified with it, more than with any other distribution, I tried to install the actual breezy preview the "recommended" way. Everything runs relatively fine now, after I did re-activate the network interface graphically and some other minor things.

The real big problem I have now: My system freezes from time to time. It comes at random times and seems to have nothing to do with some specific program or such. Since I switched off ACPI and USB it seems, that the systems get's a bit more stable. But it still happens.

To my surprise my machine identifies itself as i686, when asked with "uname -m". This is shurely wrong, since the VIA samuel 2 processor lacks one importent instruction: All Pre-’Nehemiah’ core C3s are missing an instruction that is present on proper i686 chips! The instruction in question is CMOV, which may be present in code compiled for an i686 platform.

I read a lot about frozen machines driven by the new release. Mostly it seemed to have something to do with some specific hardware, like WLAN cards or some USB camera devices. I do not make use of such things.

May my problem be catagorized as a bug? I think it shurely must be. If yes, what could I do? Write this to [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/) ? And does somebody have an idea, where uname does get it's information from? From /proc? 

Fortunately I could stop synaptic while installing libc-i686 over the standard version which came with the dist-upgrade. If it would have succeeded I shurely would not be able to use the system in any kind I think.

--
Regards, Martin

---

