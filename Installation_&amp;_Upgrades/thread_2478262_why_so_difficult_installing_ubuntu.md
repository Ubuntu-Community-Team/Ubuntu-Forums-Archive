---
title: "why so difficult installing ubuntu"
date: 2022-08-21
forum: Installation &amp; Upgrades
---

### Post by ardisugianto on 2022-08-21
hi guys, im new to linux world, im windows user for long time, but i have old netbook which is HP mini and use intel atom for processing. so after i decide to use linux and finally i choose ubuntu for my netbook, i already downloading ubuntu ISO, and also use rufus to make bootable usb, but i found its very frustating because why it take loongg time to install ubuntu, after the live ubuntu appear when i click install it very slow to load installer, i dont know whats the problem is it because of slow intel atom processor or my flash disk is old ?

---

### Post by yetimon_64 on 2022-08-21
The minimum recommended specs for the Ubuntu desktop edition is a 2 GHz dual core processor with 4 GB Ram. See [COLOR=#0000ff]--[/COLOR][[COLOR=#0000ff]here[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")[COLOR=#0000ff]--[/COLOR] to compare your hardware with the recommended specs.

You may want to consider lighter ubuntu variants, like Xubuntu or Lubuntu, for older/slower hardware.

---

### Post by mikewhatever on 2022-08-21
> **ardisugianto said:**
> ...is it because of slow intel atom processor or my flash disk is old ?

It's likely because of both, and probably also because of slow insufficient RAM, mechanical HDD, etc. Most netbooks from 2010 or thereabout were notoriosly underpowered even then, let alone now. So, temper your expectations, and don't expect miracles.

PS: What exactly is difficult about it? Where did you have to work hard?

---

### Post by yancek on 2022-08-21
Your hardware is probably to old.  Post some hardware information.  When was this computer manufactured?  You might be better off with a lighter version of LInux.  I don't think that in the years I've been using Linux and Ubuntu that it has taken over30 minutes to install.  I bought a laptop with windows 10 preinstalled which took 4+ hours to update before I could use it.

---

### Post by grahammechanical on 2022-08-21
Low powered graphics would have an effect. The live session also has to identify the hardware. And what is more is that the live session loads into memory (RAM) and if the memory is insufficient there will be a lot of paging in and out of RAM. If we tick to update during the install process then the download speed of the internet connection will slow down the install process.

This is the important question: How does Ubuntu run? Years ago Ubuntu Netbook Remix was the special edition of Ubuntu for Netbooks. I am surprised that you actually got present day Ubuntu to install and run. And your only complaint was the time it took to install.

Regards

---

### Post by ajgreeny on 2022-08-21
As others have said, your hardware is probably too old and low spec for a sensible install of Ubuntu but unfortunately you tell us almost nothing about your hardware except that it is an HP Mini with Atom cpu.
Give us as much detail as you can of the hardware and we may be able to help you much better than we have managed so far.

You are lucky (or luckier than me) that your machine is 64bit so can at least boot up the system, though slowly. Nevertheless, I think you may do a lot better to use another distro than Ubuntu.
I own and occasionally use an old 32bit netbook with an Atom N270 cpu, 1G ram, and that runs Debian but without a full DE, just Openbox window manager which is very lightweight.

Something similar may well be your  best option, though if you're not used to Openbox it might take a little getting used to.
Still worth some consideration, I think.

---

### Post by kurt18947 on 2022-08-21
I'll pile on about Ubuntu not being the right distro for that machine. There are others here more knowledgeable than me about lightweight distros but if I found myself in your position, I'd consider MXlinux. Specifically, MX-21.1_386 Xfce. Minimum specifications are 1 GB RAM (2GB recommended) and a somewhat recent 32 or 64 bit Intel processor. I would probably install the 32 bit (i686) version, that may perform better on limited hardware.

[https://mxlinux.org/download-links/](https://mxlinux.org/download-links/)

I was playing with an HP Pentium III machine with 512 MB of RAM which is most probably less capable than your machine. It would run MX Linux passably well for simple tasks. I'm certain there are more suitable distros for less capable machines but I recall MX Linux pretty straight forward to install, no hardware issues on a machine older than yours. I'm not sure about some of the really light weight distros.

---

### Post by ardisugianto on 2022-08-21
ok thanks for your feedback guys, i already tried installing Lubuntu, and work perfectly without any difficulties, yeah my netbook too old for ubuntu, now my case solved, thanx again for the feedback

---

### Post by yetimon_64 on 2022-08-21
> **ardisugianto said:**
> ...now my case solved...
That is good to hear, :-). Could you please mark your thread as [SOLVED] if you are happy with your results? The middle blue link in my sig line below has a guide for how to do so, if needed.

Cheers, yeti.

---

### Post by mIk3_08 on 2022-08-22
> **ardisugianto said:**
> now my case solved, thanx again for the feedback

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

