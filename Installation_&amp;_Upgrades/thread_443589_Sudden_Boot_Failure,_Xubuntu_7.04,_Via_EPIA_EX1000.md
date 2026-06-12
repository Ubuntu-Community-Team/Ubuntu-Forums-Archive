---
title: "Sudden Boot Failure, Xubuntu 7.04, Via EPIA EX1000EG, Failsafe, openchrome"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by mengedej on 2007-05-14
Hi,

Recently got all of my peices for my project, so I eagerly put it together and it worked fine for a few days, out of the box, while I was trying to get openchrome running, no luck by the way, see further down...

--Boot Issue--

Basically I had it all running playing around with xorg.conf when I figured I probably should have a look at the BIOS setup. For some reason I changed it to Display Device:CRT and saved the changes (I have a LCD monitor, and I am stupid). So, I had to run and get a CRT monitor from upstairs and use it instead (no problemo) changed it back in BIOS to LCD and choosed to load the failsafe settings to see if this would help me resolve the driverproblem (see below).

This is where the real problem starts. Since that change it will not boot. 
I have tried booting from HDD (sata) and DVD (ide) but it fails at line "NET: Registered Protocol family 2" and leaves me with a blinking cursor. I have no Idea what to do. It was working just a few minutes (well, now, hours) ago.

Any ideas anyone? Since the HDD is new I started with a 'clean' Xubuntu installation, the only changes to it was the installation of Openchrome drivers libdrm and DRM modules and the required packages. 
xorg.conf changes was (as far as I can remember) only driver vesa -> via and to use kernel FB.

----- Driver Issue ---

My other problem is related to the installation of the openchrome driver (i have followed combined instructions from openchrome and ubuntuforums. I have a CX700M2.

I compile and install without (apparent) errors, change to "via" in xorg.conf and I get failure to startXserver: 
No Devices detected, fatal server error, no screens found
Can this be related ot DRM Module not being loaded? Am I missing something (agpgart, via-agp? i'm running 2.6.20-15) should I use the experimental drivers?  Im just guessing, can anyone please point me in the right direction?

last, but not least, thank you.
Tor
thie question is also posted at:
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77816&enterthread=y]("http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77816&enterthread=y")

---

### Post by mengedej on 2007-05-15
Resolved the boot problem by setting [APIC Mode -> Enabled] in BIOS

---

### Post by mengedej on 2007-05-16
Driver issue resolved by using openchrome experimental branch (CX700M2) and adding Option "VBEModes" "true" to xorg.conf (as per openchrome ticket  #88 )

---

