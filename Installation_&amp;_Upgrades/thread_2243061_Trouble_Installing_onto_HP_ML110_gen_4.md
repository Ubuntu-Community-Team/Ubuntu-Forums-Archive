---
title: "Trouble Installing onto HP ML110 gen 4"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by nztoffee on 2014-09-06
Hi 

I am attempting to instal Ubuntu Server onto an old hp ml110 gen 4 server with a pentium D 2.8GHz processor (820?)
2 X 160Gb SATA HDD
1.5Gb RAM

There is no current operating system on the server.

I have downloaded version 14.04.1 and created a cd I also did the CD check, all ok so far.

At some point during the installation, usually around the creation of the kernel (I believe) the process just stops and the server restarts.

I have tried this with expert mode and acpi off (also noapic and nolapic) -- all at one time

Then I downloaded version 10.04.4 and this results in a kernel panic directly on choosing the install option.

What am I missing?

Sorry if I have not supplied enough information, I am new at Ubuntu

Thanks in advance for your help

Peter

---

### Post by ubfan1 on 2014-09-06
Are you trying a 64 bit or 32 bit install?  Try the other one and see if same thing happens.  There used to be an "alternate" install , but not sure if that's still around or if it even was available for the server.  Why 10.04?  12.04 is still supported, try that if 14 fails.

---

### Post by nztoffee on 2014-09-07
Thanks for your help.
I was trying a 64 bit install. I will give the 12.04 install a try.

A couple of days later:
After a frustrating time it turns out to be a hardware problem, solved that and successfully installed 14.04.1

---

