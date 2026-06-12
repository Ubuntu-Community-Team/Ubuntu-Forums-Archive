---
title: "HP tx2500z Ubuntu 8.04 Install Problems"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by stenciljunkie on 2010-04-18
I recently tried to install 8.04 on my tx2500z via USB and UNetbootin.

On my first attempt I got all the way to the partitioner and did a 70% - 30% between my Windows 7 and Ubuntu. After I pressed continue I heard a series of system beeps and my computer was frozen. By this time my computer was heating up. It kept making those system beeps and wasn't making any progress so I decided to do a force restart.

Every time I try to install Ubuntu now it gets to the loading screen, then after that it loads halfway then an error message loads up. After I press enter, the computer just shuts down...

I think the problem is directly linked to the cooling problem of this computer. I have tried to install it over 20 times with the same kind of errors. Sometimes it goes to a black screen where it will read that it has overheated and has reached a temperature that's too high...

I have tried using a Targus cooling pad as well as laying it over an inverted 20" fan (I know, stupid right, lol)... and it is currently getting stuck at the part where I get that error to press enter. =[

Here are the specs of my computer:

HP tx2500z Tablet
Current Operating System: Windows 7 Ultimate 64-bit (Build 7100)
Processor: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-82 (2 CPUs) ~2.2 GHz
Memory: 2048 MB of Ram
Graphics: ATI Radeon HD 3200 Graphics (Approx Total Memory: 946 MB)

Thanks in advance!

JPR

---

### Post by mörgæs on 2010-04-20
Have you tried other versions of Ubuntu?

---

### Post by Favux on 2010-04-20
Hi stenciljunkie,

To get the TX2500 to boot in Hardy they started off by adding 'acpi=off' to the kernel boot line.

See this thread:  [http://ubuntuforums.org/showthread.php?t=845911](http://ubuntuforums.org/showthread.php?t=845911)

Then they came up with around 3 "fixes".  Search the thread for 'acpi=off' and overheat, etc.

Hope this is helpful.

---

