---
title: "Sun Ultra10, screen resolution unviewable after booting Linux"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by timji on 2010-10-10
I have a Sparc Ultra10, which uses PC hardware. I see the Openboot console display at 1024x768, but when I try to boot from a Ubuntu server install CD for Sparc (for example, 7.04) the screen resolution immediately goes out of range for my monitor (according to a warning message flying around the screen).

I tried adding boot parameters to specify the resolution I want (boot: linux vga=773 screen=1024x768), but they seem to be ignored.
I guess the Ubuntu testers all have Sun monitors!

I also tried the 8.04 and 9.10 versions, but they respectively hang after the "S" in Silo and issue the fatal error "Fast Data Access MMU Miss".

I've got Silo version 1.4.14, OBP 3.31.0, and POST 3.1.0. My computer is an UltraSparc IIi at 360 Mhz, with 256 megs of memory. 

So, short of acquiring a monitor with the really strange Sun standard resolution, how can I get past this problem and get the resolution I want from Linux at boot time?

---

### Post by GatoViejo on 2010-10-10
I suggest you try the alternative CD which has a text mode installer.

---

### Post by timji on 2010-10-10
> **GatoViejo said:**
> I suggest you try the alternative CD which has a text mode installer.
I doubt that would make any difference, because I was using "text mode" installers for 7.04 and 8.04 anyway, via "boot: cli" and "boot: cli-expert". Even so, the screen resolution got changed from the 1024x768 that I had set for the OPB console as soon as I pressed ENTER, and after that the screen is black.

---

### Post by timji on 2010-10-13
> **timji said:**
> I doubt that would make any difference, because I was using "text mode" installers for 7.04 and 8.04 anyway, via "boot: cli" and "boot: cli-expert". Even so, the screen resolution got changed from the 1024x768 that I had set for the OPB console as soon as I pressed ENTER, and after that the screen is black.
Somebody reminded me how to specify the desired resolution, which fixed my problem. Now I boot the installation disk like this:

boot: install video=atyfb:1024x768@60

But I still don't have a running Linux on Ubuntu, despite trying 7.04, 8.04, 9.04, and 9.10. Half of these won't even boot the cd (despite power-off/reset-all first), and the ones that do boot (7.04 and 8.04) blow up one way or another during installation anyway. I'm trying straight Debian now, which looks promising so far.

---

