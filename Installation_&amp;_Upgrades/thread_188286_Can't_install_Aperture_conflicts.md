---
title: "Can't install: Aperture conflicts?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Durian on 2006-06-03
Hi Linux people. This will be my second or third time installing Linux, although once I install it I never end up using it, because I use a winmodem and it's nearly impossible to get it work in a non-Windows environment. I'm trying it on a laptop now, so maybe I'll actually use it this time.

My laptop is an Acer Aspire 5003WLMi, with an AMD 64 processor and an empty partition so I don't even have to fool around with repartitioning the hard drive. The Ubuntu wiki doesn't say that it works on the Aspire 5003, but it doesn't say that it doesn't work, either. And it works on the 5002 and 5004, so why not 5003?

I have a fresh new Dapper Drake disc, and when I try to boot from it, it shows the first screen very well. I can press Fs 1-6 to configure stuff, but it chokes on the installation part. Whether I choose to install in text or OEM mode, or even if I choose to check the disc for defects, I can't get past the part where it loads the kernel. It flashes a message on the screen and goes black and stalls. To the best of my memory, the message is this

**agpart: Aperture conflicts with PCI Mapping**

Is there anything I can do about this? Anything at all?

---

### Post by Durian on 2006-06-04
It can't be a hardware problem, because I did some searching and someone got Breezy Badger to run on an Aspire 5003 just fine. [http://www.ubuntuforums.org/showthread.php?t=167067&highlight=acer+aspire+5003](http://www.ubuntuforums.org/showthread.php?t=167067&highlight=acer+aspire+5003)

---

### Post by Durian on 2006-06-04
Update 2: I looked at the message again and I think it said "agpgart" instead of "agpart". *Now* I get it.

Edit: Searching Google for this newly discovered keyphrase, I found that a lot of people had the same problem, and this stuff about NVIDIA I see floating around probably applies to me. Still, it would be nice if someone were to spoon-feed me the solution.

Edit2: My display adapter is SiS M760GX, which has nothing to do with NVIDIA. God, I have no idea what I'm doing.

---

### Post by leap on 2007-12-10
Hello i have a acer aspire 5002 wlmiwith the 64 bit running 7.04 feisty fawn and windows xp so said that i have to keep xp :(. Put it took a bit to get the wireless to work but it's all good now. Good luck with your install:)

---

