---
title: "Kernel issues with I7 integrated graphics - total freeze at greeter"
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by sincegutsy on 2018-11-14
Hi all, 

Long term user of Ubuntu (since Gutsy Gibbon) - first time I have had to post a thread here to resolve problems. I have always been successful with searches to find and resolve problems or at least figure out a work around. 

**Issue: **
_Circa 6 months ago_
Since attempting upgrade from 17.xx LTS my system will not boot with recent kernels. I solved this originally by regressing kernel in grub to 4.4.0-124. I have been using that kernel for my workstation. If I try to boot a more recent kernel the system hangs at the greeter.** No keyboard, no mouse, no ping, no tty, no ssh. **

_Now: (a few weeks) Note: New UEFI SSD for clean install_
Because I am not a fan of gnome3, I have decided to move to KUBUNTU as my desktop environment and perform a fresh install. I downloaded the Kubuntu 18.04.1 LTS. Install went fine, reboot.. exact same issue. System hangs at the greeter. No keyboard, no mouse, no ping, no tty, no ssh. 

I have tried just about everything I can think of. At first, I thought it was an issue with graphics or firmware. Updated MB firmware to latest intel version. See below. I thought I had the issue with graphics that is reported in many threads. I have tried all the nomodeset type switches during boot. No success at all. 

Other things I have tried:
Different OS version... Ubuntu 18.04.01 0 same issue. Ubuntu 18.10 - same issue. OpenSuse Plasma/KDE - same issue (that one surprised me). So... I am pretty sure this is some sort of kernel only issue. But I don't know what it is.

Interestingly, I did get Ubuntu SERVER 18.04 running in text only mode. I thought I would try to install plasma-desktop or kubuntu-desktop packages from there, but after 30 minutes of messing with apt I could not get those to install. 

Hardware: 
Intel MB DQ77MK BIOS:MKQ7710.86A.0073.2018.0329.1426 (latest on Intel website)
Processor: Intel Core i7-3770k
Graphics: Onboard graphics only - 3 monitors. 

At the moment, I am not even sure what is installed on the new SSD. I am running my old SSD and Ubuntu 18.04.01 with Kernel 4.4.0-124. 

To try solutions, please be patient as I need time in my workday to shutdown, switch drives, install and then attempt various solutions.

Goal: Working KUBUNTU LTS version with KDE plasma desktop.

I appreciate any help!

---

