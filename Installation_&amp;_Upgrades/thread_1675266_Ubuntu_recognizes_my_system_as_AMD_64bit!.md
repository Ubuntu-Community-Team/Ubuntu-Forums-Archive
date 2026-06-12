---
title: "Ubuntu recognizes my system as AMD 64bit!"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Fatapf on 2011-01-25
Hello everyone! I'm new to Ubuntu, i just installed it yesterday, version 10.10, desktop edition, downloaded from Ubuntu's site; running it along side Windows; and love it from the get go, but... I can't get the Flash plugin to work. I'm running a Toshiba Satellite Pro P505-S8945 with this specs:

2.0GHz Intel Core2 Duo P7350 Processor
400GB Hard Drive, DVD SuperMulti Drive
Microsoft Windows 7 Home Premium (32bit), 4GB RAM
ATI Radeon HD 4570 Graphics

I tried installing the 32bit version on Flash but kept getting error messages about "wrong architecture i386", so, I went to the (sorry if i make a mistake I'm paraphrasing) "Ubuntu software center", the application within Ubuntu where you can go to the repositories and get software upgrades, and I realized that for some reason Ubuntu is recognizing my system as running on an AMD 64 processor, which I'm not! Mind you, I haven't tried to install the 64bit version of flash, just wondering really, the reason why Ubuntu would say that I'm running on a 64bit AMD processor!? How could I fix this?

Thank you all in advance!

---

### Post by Zzl1xndd on 2011-01-25
If my memory is correct AMD was the first to implement the 64-bit spec and sometime around 2003 they changed the name from x86-64 to AMD64. So its likely just that Ubuntu is recgnizing your system as 64bit and not specifically an AMD processor. 

If you installed the 64-Bit version of Ubuntu then you should use 64-bit flash as well.

---

### Post by presence1960 on 2011-01-25
Your processor architecture is AMD64. As the previous poster mentioned AMD64 is the name given to 64 bit architecture because AMD is the one that rolled it out. So your Intel core duo is AMD64 architecture.

---

### Post by coffeecat on 2011-01-25
Have a look at the filename of the ISO you downloaded to install 64-bit Ubuntu. Now have a look in /var/cache/apt/archives at the filenames of all the cached deb packages. The ISO and most of the latter have 'amd64' in the filename. It's just a shorthand, mainly because AMD was first off the block with 64-bit processors.

Don't worry about it! :) I have "amd64" Ubuntu running just fine on my Intel-powered laptop - 64-bit flash included.

Welcome to Ubuntu and welcome to the forum!

---

### Post by Fatapf on 2011-01-25
Thank you guys for the quick responses! Really helpful, can't wait to get home from work to get immersed in Ubuntu!
:D

---

### Post by Yougo on 2011-01-25
Go to System > Administration > System Monitor, then click on the System tab. That should give you the basic info on your CPU architecture, as well as the architecture of Ubuntu version you have installed.

if you do have a 64bit system, it's quite a waste to be running 32bit windows on it :-?...Welcome to Ubuntu :cool:

---

### Post by cascade9 on 2011-01-25
> **tweakedenigma said:**
> If my memory is correct AMD was the first to implement the 64-bit spec and sometime around 2003 they changed the name from x86-64 to AMD64. So its likely just that Ubuntu is recgnizing your system as 64bit and not specifically an AMD processor. 

If you installed the 64-Bit version of Ubuntu then you should use 64-bit flash as well.

Yes, AMD changed the name from x86-64 to a marketing name of AMD64. Not that much different to i(ntel)386, etc.. Though I bet that intel is still unimpressed about AMD64, not just because of the name, but also because AMD64 cut down intels plans to change a fortune for itanium (pure 64bit, not x86-64 at all). 

+1 to run 64bit flashas well. If you dont want to install the flash plugin manually, try the flash-aid firefox add-on.

---

### Post by Fatapf on 2011-01-25
I know it would be a waste... lol; but as far as I know, my system is 32bit, I'll certainly check on it though! I'm positive that the version of Ubuntu I installed is 32bit!

Thanks a lot!

---

### Post by cascade9 on 2011-01-25
> **Fatapf said:**
> I know it would be a waste... lol; but as far as I know, my system is 32bit, I'll certainly check on it though! I'm positive that the version of Ubuntu I installed is 32bit!

Thanks a lot!

All the Core 2 Duo CPUs are 64bit capable. ;)

---

### Post by srs5694 on 2011-01-25
> **cascade9 said:**
> Yes, AMD changed the name from x86-64 to a marketing name of AMD64.

Actually, AMD invented the architecture that is now known as "AMD64," "x86-64," "x64," "EM64T," and probably other things. Thus, they *can't* have "changed the name" from one thing to another, and certainly not in the sense of stamping their own name on a pre-existing market. (Perhaps "x86-64" was used internally during development, though; I can't speak to such things.) I wrote [an article in 2004](http://www.linux-mag.com/id/1699) on the architecture, and in that article, I referred to the platform as "AMD64" because that was the most common name at the time. Only after Intel released their implementation did the more vendor-neutral "x86-64" become common.

> Not that much different to i(ntel)386, etc.. Though I bet that intel is still unimpressed about AMD64, not just because of the name, but also because AMD64 cut down intels plans to change a fortune for itanium (pure 64bit, not x86-64 at all).

The earliest generations of Itanium CPUs could run x86 code, and so could be considered hybrid 32-/64-bit CPUs, much like x86-64 CPUs. I believe Intel dropped that support a few years ago, but I haven't followed this very closely. FWIW, the entire history of the x86 line of CPUs is one of adding features while attempting to maintain backwards compatibility for the benefit of legacy software. AMD64 did this more successfully than Itanium did (as I recall, early Itaniums could only run 32-bit code when booted in 32-bit mode, whereas AMD64 CPUs can run 32-bit code even in a 64-bit OS.) Newer and cleaner designs haven't stood much chance against the market force of the x86 platform, at least not on desktop systems and low-end servers.

---

### Post by cascade9 on 2011-01-25
> **srs5694 said:**
> Actually, AMD invented the architecture that is now known as "AMD64," "x86-64," "x64," "EM64T," and probably other things. Thus, they *can't* have "changed the name" from one thing to another, and certainly not in the sense of stamping their own name on a pre-existing market. (Perhaps "x86-64" was used internally during development, though; I can't speak to such things.) I wrote [an article in 2004]("http://www.linux-mag.com/id/1699") on the architecture, and in that article, I referred to the platform as "AMD64" because that was the most common name at the time. Only after Intel released their implementation did the more vendor-neutral "x86-64" become common.

You almost answered this yourself. x86-64 was used internally at AMD up to at least 2001, and was used on some public documents- 

[http://www.amd.com/us/press-releases/Pages/Press_Release_751.aspx](http://www.amd.com/us/press-releases/Pages/Press_Release_751.aspx)
[http://www.amd.com/us/press-releases/Pages/Press_Release_715.aspx](http://www.amd.com/us/press-releases/Pages/Press_Release_715.aspx)

IIRC it wasntuntill late 2002/early 2003 that the 'AMD64' naming popped up. Right when the marketing droids would have started work. Engineers then to be a bit less marketing/brand driven in my experince. ;) 

> **srs5694 said:**
> The earliest generations of Itanium CPUs could run x86 code, and so could be considered hybrid 32-/64-bit CPUs, much like x86-64 CPUs. I believe Intel dropped that support a few years ago, but I haven't followed this very closely. FWIW, the entire history of the x86 line of CPUs is one of adding features while attempting to maintain backwards compatibility for the benefit of legacy software. AMD64 did this more successfully than Itanium did (as I recall, early Itaniums could only run 32-bit code when booted in 32-bit mode, whereas AMD64 CPUs can run 32-bit code even in a 64-bit OS.) Newer and cleaner designs haven't stood much chance against the market force of the x86 platform, at least not on desktop systems and low-end servers.

Honestly, I dont know anything about having to boot in 32-bit mode, I've never owned one. I was meant to be getting one to play with, but that fell though. 

True, the early itaniums did have hardware support for IA-32 (confusing naming, considering that itanium was IA-64, which is not x86-64, but thats what happens when the marketing droids get involved). 

I dont really count the IA-32 support for itanium, or count it as a x86 CPU. I know, they will run that code, but itanium was bad enough with native code, IA-32 code was horribly slow. IIRC on release even the fastest itanium was slower than any of the P3s at IA-32. It was so bad that the newer itanium 2 chips got a software IA-32 emulator that was faster..... 

I would have thought that intel would have learned the lesson of the pentium pro (which failed in part because it ran 16-bit code a lot more slowly than other similar CPUs of the time) but I'd guess that intel made a gamble that the industry would go for itanium, and lost that bet. Just another part of how AMD managed to catch Intel at all, let alone get in front for a few years.

---

### Post by srs5694 on 2011-01-25
> **cascade9 said:**
> True, the early itaniums did have hardware support for IA-32 (confusing naming, considering that itanium was IA-64, which is not x86-64, but thats what happens when the marketing droids get involved).


The IA-32/IA-64 naming makes perfect sense from Intel's perspective, ca. 2000: IA-64 (Itanium) was intended to replace IA-32 (x86), starting with high-end systems and eventually working down. The platform was slow to launch and had problems, though, so when AMD eventually produced AMD64/x86-64 (after the IA-64 name was in use), AMD64/x86-64 took over at the low and mid-range, blocking Intel's plans for IA-64. The fact that x86-64 has much more in common with IA-32 than IA-64 does is irrelevant, since IA-64 was named before x86-64 emerged. Besides which, "IA" means "Intel Architecture," and x86-64 was invented by AMD (albeit built upon the older IA-32), so even if IA-64 weren't already in use by Itanium, IMHO it would be inappropriate to apply it to x86-64.

Naming schemes for products can get twisted up pretty quickly! ;)

---

### Post by Fatapf on 2011-01-25
Thank you everyone for all the help and info! I have flash now up and running! Liking Ubuntu more and more by the minute!

---

