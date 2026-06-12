---
title: "Thinkpad iSeries 1161-11U, Xubuntu, blank screen"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by emang on 2008-03-07
Thanks in advance to the Ubuntu community.

I am having trouble getting Xubuntu to run on my old laptop, which is a Thinkpad iSeries whose type is "1161-11U".  After having installed the laptop using text mode of the Alternative CD (without having internet access), upon reboot of the system, I am unable to hit the login screen.

I have tried using the boot options specified [here]("http://ubuntuforums.org/showthread.php?t=473510#3").  That didn't seem to work.  According to "top", which I run in recovery mode, I have 158344k of memory.  The processor is a 550Mhz Celeron.

I tried installing using the Live CD, but the machine would just shut down on me a little bit after the partitioning process.  I was thinking that maybe if this LiveCD install process were able to completely play its way through, then it might be better, because I'm able to use a PCMCIA Wireless card to connect to the internet, and perhaps the install process would download the appropriate drivers to boot up properly after the install.  I couldn't figure out how to get wireless to work during the Alternative CD install.

Any help would be greatly appreciated.

THANKS!

---

### Post by emang on 2008-03-08
I want to clarify, the options "vga=792 acpi=force irqpoll" enabled me to start xubuntu for the live CD install.  Without those options, I get the same blank screen that I get after having successfully installed using the alternate CD.

Unforunately the LiveCD dies during the install, and unfortunately these same options don't get me to my desktop given my current install.

Thanks!

---

### Post by patfett on 2008-03-17
Mine is actually a Thinkpad 1161-260, but the differences are minor.

I'm trying to install Xubuntu 7.10 on a machine with 192 Mb RAM, and I know the machine is in working order. In trying to install, I keep getting the notice that "No common CD-ROM Drive was detected" - although I'm installing from the CD-ROM drive. I've gone through the list of optional CD drivers provided on the disk, and none of them load with my config.

Any ideas? In case you haven't noticed, I'm a complete newbie with all things Linux.

Thanks.

---

### Post by patfett on 2008-03-25
AFter fumbling around with 7.10 for a while, and upon the recommendation of a colleague, I just installed Xubuntu 6.06 onto my old Thinkpad 1161-260. It was completely seamless - no problems with the install at all, whereas I could not get 7.10 to install on the machine at all.

I'm sure I have some work ahead of me to get the driver for my D-Link wireless card, but everything else installed from the 6.06 desktop CD with no problems at all.

---

