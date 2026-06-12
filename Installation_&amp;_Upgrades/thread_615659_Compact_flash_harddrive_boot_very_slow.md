---
title: "Compact flash harddrive boot very slow"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by TomGar on 2007-11-17
I've installed Gutsy onto an epia via cn1000eg based system with a sandisk Extreme III 4gb compact flash (hdc0) acting as the hard drive.

Installation went brilliantly. Runs nice and quick and quiet!

But.... booting the system is the slowest process I have every seen. 

over 30 minutes to get to the grub menu

Checking the forums and googling implies it should be fast, the card boasts 20mb/s.  Left alone it does boot all the way. But something is bottlenecking it.

Any help would be appreciated.

---

### Post by TomGar on 2007-11-17
Sorry. Problem solved, Bios configuration trial and error. Disabling UDMA has fixed the speed issue.

---

### Post by TomGar on 2007-11-24
Bit of an update on the CF card boot

It is booting ok **but** has a disappointing 2 minute pause early in the boot  whilst it goes into a tiz about DMA

output in dmesg

dma_timer_expiry : dma status == 0x21 

Hunting around on google a lot of suggestions are for adding ide=nodma on the grub boot line.

But for many (including me) this makes no difference, so we then move on the suggestions to disable the "ide_dma_check" in ide-probe.c module of the kernel (?)

[http://expisoft.blogspot.com/2007/04/ide2cf-timeout-with-linux.html]("http://expisoft.blogspot.com/2007/04/ide2cf-timeout-with-linux.html")

this link details how to rebuild the kernel generically with this DMA check disabled,

Has anyone successfully done this in Ubuntu - or can they recommend a how to?

Any help gratefully accepted because I'm just about there with my totally silent myth-frontend.

---

### Post by TomGar on 2007-11-29
bump - anyone?

---

### Post by Foxray on 2008-01-18
I get the same problem. I am currently using Xubuntu on my 4gb Compact flash card and it boots ultra slow. I get like 3 of those dma timeout messages then after like 13 mins it finally gets to the login screen. I have yet to fiddle with the Bios settings I'll tell you if I make any progress.

Edit: Turned off the UDMA in the bios and boot time was reduced to 4 minutes total. The dma messages are still there and ide=nodma doesn't work for me either. There is a technique that can turn on DMA for the Compact flash card but it will require soldering 2 connections on the CF card to 2 different connections on the CF adapter. I will take a look at this and see if I can pull it off.

---

### Post by markp1989 on 2008-03-18
having the same problem with CF and dma messages, any one found any way that will work, i have tried ide=nodma ide=generic hda=nodma, and it still has a hissy fit.

---

