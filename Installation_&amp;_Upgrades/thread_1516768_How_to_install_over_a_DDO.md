---
title: "How to install over a DDO?"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by Affirmative on 2010-06-24
Greetings,

I want to install Ubuntu 10.04 LTS on my laptop. I use Ubuntu on my other systems and it's proven itself to be fairly awesome.

My laptop however, is the opposite of awesome. It is an Acer Aspire 3000, ultra-fail edition. What that means is;

AMD Sempron 3100+ (which I find ok)
2GB RAM (which I find ok)
No bios upgrades to allow for 48-bit LBA (limited to 137gb drives...)
SiS M760GX (so that I can enjoy horrible graphic capabilities and want to stab myself in the eye most of the time)

So in short, the laptop is horrible, awful, terrible, and should be thrown out. However, I have sentimental attachment to this faithful device, and I want to make it work!

I currently have Windows 2000 Professional installed on it. I have a 250GB Western Digital hard drive in the device, and normally it would only recognise 137gb - so to get the full capacity of the drive, I had to use Western Digital Data Lifeguard Tools to install a Dynamic Drive Overlay.

I did some searches on this forum and have seen others have run into a similar problem but no fix appeared to be available at the time; vague references to links that are no longer valid (?), etc. Does Ubuntu 10.04 play nicely with DDO, or is there a way to get Linux to run its own overlay of the drive?

So far, my previous attempt to install Ubuntu 9.10 blew the DDO away, replacing it with a non-booting grub-rescue> prompt.

Any tips?

Regards,
Aff

---

### Post by dino99 on 2010-06-24
i'm having too a bad bios on one of my system and no more recent bios available, and actual kernel take itself the good choices over the bios.

So for your system i will try directly to install it. Have you ahci bios choice ? (im using it)

---

### Post by Affirmative on 2010-06-24
This is an Aspire3000 running a PhoenixBIOS 4 release 6.0

It is not capable of AHCI mode, and has NO configuration for hard disk in the setup utility.

---

