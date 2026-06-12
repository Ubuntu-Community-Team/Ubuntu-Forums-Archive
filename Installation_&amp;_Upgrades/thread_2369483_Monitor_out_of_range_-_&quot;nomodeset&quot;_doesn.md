---
title: "Monitor out of range - &quot;nomodeset&quot; doesn't solve it."
date: 2017-08-23
forum: Installation &amp; Upgrades
---

### Post by AshleyT on 2017-08-23
Hi there,

I'm trying to install ubuntu version 16.04 however I keep getting an issue with my monitor being out of range. 

I've googled around and found you need to change a setting to "nomodeset" - however when I do this the problem still persists. 

I've also tried acpi=off and noapic but none of these work either. 

I have a GTX 1080 if this makes any difference?

---

### Post by gordintoronto on 2017-08-23
How do you know your monitor is "out of range"?

Have you tried 17.04?

---

### Post by BenginM on 2017-08-23
Hiya , I'm not sure why the GTX card isn't playing nice with the free Nvidia kernel driver "[I]Nouveau" ! it's loaded in the kernel by default and should give you a functional desktop at least ..

[/I] i don't suppose the machine's CPU has a built-in integrated  GPU/APU , if so you may want boot with it and disable the GTX 1080 card  in the BIOS , after the installation is done and ones you boot to the  desktop for the first time , use the additional drivers section to  download & install the proper driver for the GTX 1080 , it seems to  be this driver nvidia-367 .
        here is the official ubuntu method to install nvidia driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Bucky Ball on 2017-08-24
Perhaps describe exactly how you are adding 'nomodeset' or provide a link to the 'how to' you are following.

When you get to the desktop, eventually, then 'Additional Drivers' and you will find the Nvidia driver you need there (provided you have the 'Canonical Partners' repository enabled in 'Software and Updates> Other Software' tab).

This card runs fine in 16.04 LTS. 16.04 is also a long-term support release, supported until 2021. 17.04 will see you reinstalling a new OS or upgrading your current one in March 2018 as that's when it reaches end-of-life. If you want to be cutting edge, must have the latest and don't mind reinstall or upgrading your OS every six months, go for it.

([Here's a 1070 (same diff) running fine on 16.04]("https://ubuntuforums.org/showthread.php?t=2368969") after nomodeset and installing the Nvidia driver when at the desktop.)

---

