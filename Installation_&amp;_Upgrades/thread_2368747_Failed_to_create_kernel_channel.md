---
title: "Failed to create kernel channel"
date: 2017-08-14
forum: Installation &amp; Upgrades
---

### Post by coreproxy on 2017-08-14
This problem is reoccuring quite often, but I haven't found someone who've had this problem **after **the installation of a fresh Buntu.
I am running Ubuntu 16.04 and Windows 10 on my Dell XPS 15 9560 laptop in dual boot mode with a GRUB menu to choose which OS I wish to boot.

Here are more specs about my laptop:

Intel Core i7-7700HQ Quad-Core
512GB SSD
8GB DDR4 x2
Intel HD 630
NVidia GeForce GTX 1050 with 4GB GDDR5

For half a year that I owned this laptop, both OSs were running flawlessly.
I'm most of the time on Ubuntu and I haven't had a single problem that would prevent me from completely working.
I am now running out of ideas on how to fix it so here I am seeking help from forums.

Long story short of what happened was the following:
- Ubuntu notified me I have an update to do and I accepted it.
- Once update was complete, I have been asked to reboot and so I did.
- While rebooting, I noticed it took way too long to do the reboot (waited for about 25 minutes). 
- All I was seeing is a black screen because it didn't even shutdown yet in order to reboot.
- By lack of patience and arrogance, I forced the shutdown manually by holding the power button ([COLOR=#ff0000]BIG MISTAKE[/COLOR])
- Upon booting myself into the grub menu, I select Ubuntu and I end up on a black screen with a stack trace of error.
- Unfortunately I haven't captured that stack trace of error but I distinctly remember the last line: [I]**[DRM] FAILED TO CREATE KERNEL CHANNEL**
[/I]- I was getting the stack trace once every now and then, the other times, I would only get a plain black screen with no error trace.

Luckily, I had access to Ubuntu recovery mode and I was able to get in my OS and capture all my important files.
I would like to note that the Windows OS is still working completely fine atm.
Afterwards, I tried taking a look at the system logs but the logs indicated no error because it seems to not have recorded anything when I boot Ubuntu normally.
So after much discouragement for having my OS neatly setup like I liked it. I **nuked **the partition, made a new ext4 partition and swap partition.
With a clean new Slate, I installed a new Ubuntu from a bootable USB I made using Rufus and the Ubuntu 16.04 LTS ISO image.
Installation went smoothly up until the end. At the end, when it was time to shutdown, the computer froze upon clicking shutdown...
I waited a game-of-thrones-episode-worth-of-minutes until I decided to force the shutdown manually by holding the power button ([COLOR=#FF0000]I have a talent for this[/COLOR])

With the installation somewhat over, I was able to boot in the new Ubuntu. The only problem with the new Ubuntu is that shutdown was not working.
My computer would freeze upon confirming shutting down. Moving on, I was about to start setting myself up. But unluckily, upon opening my computer and selecting Ubuntu,
I get  ***[DRM] FAILED TO CREATE KERNEL CHANNEL  ***all over again.

I am not quite sure how to fix this, because I have erased the past Ubuntu, yet it seems something is still corrupted.

I'm running popular packages on Ubuntu (Mysql, Vibrancy Theme, Git,  etc...)
I'm willing to reinstall Ubuntu as many times as I need in order to get to the bottom of this.

My questions are:
Has this ever happened to anyone before?
Does anyone know what could the source of the problem be?
Could it be incompatible packages that could cause the entire OS to no longer work?

---

### Post by vocx on 2017-08-14
> **coreproxy said:**
> ...
Intel Core i7-7700HQ Quad-Core
512GB SSD
8GB DDR4 x2
Intel HD 630
**NVidia GeForce GTX 1050 with 4GB GDDR5**

...
I get  ***[DRM] FAILED TO CREATE KERNEL CHANNEL  ***all over again.

**Has this ever happened to anyone before?**
Does anyone know what could the source of the problem be?
Could it be incompatible packages that could cause the entire OS to no longer work?

I don't understand why people ask, "has ANY ONE ever experienced this error???". When the solution is to search online are realize that, yes, effectively many people have experienced that problem before.

I found this [https://bugs.freedesktop.org/show_bug.cgi?id=101164](https://bugs.freedesktop.org/show_bug.cgi?id=101164)
The "DRM" line stands for "Direct Rendering Manager", and basically has something to do with the video driver drawing things on screen.

It seems to be related to the "nouveau" drivers of the Nvidia graphics card. Maybe an update that you did within those first 6 months introduced a nasty bug. The solution is to use the previous version of the driver, or hope there is an updated driver that fixed the issue. The module "nouveau" is the open source driver for Nvidia, and it's included in the Linux kernel, so I'd check online for reports on an updated Linux kernel to install to correct the problem, or if there is a way to disable it in the Grub screen to be able to boot.

Also, you may try installing the proprietary drivers, simply called "nvidia". They may actually help you in this situation. Since you also have an Intel card, it may be wise to use it for the time being, until you know it's safe to re-enable the Nvidia card. Maybe you can disable the Nvidia card in the BIOS screen before Grub, so that you start your system correctly with the Intel card.

---

