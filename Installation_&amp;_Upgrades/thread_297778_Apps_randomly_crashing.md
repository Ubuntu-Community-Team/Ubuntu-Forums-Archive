---
title: "Apps randomly crashing"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by lofgren on 2006-11-11
**EDITS IN BOLD**

Hi all,

please help!  I am experiencing random crashes in applications.

Usually, the first to go are clock and or volume control applets.
However, things like firefox, nautilus, the panel and xwindows also crash.

There doesn't seem to be any reason and they aren't repeatable due to being random. I can leave the machine idle and they still happen. I can leave it logged out and x-windows will still crash occasionally.

I have tried several installs:
Ubuntu 6.06 live **(i386)**
Ubuntu 6.10 live **(i386)**
Kubuntu 6.10 Alternate **(i386)**
Ubuntu 6.06 **(i386)** (couldn't even get it to install the second time - installer crashed midway constantly)
Ubuntu 6.06.1 alternate **(i386)**

**Ubuntu 6.06.1 alternate - AMD64 (current)**

My hardware:
Asus KV8-MX
AMD**64** 3000+ Sempron processor
1GB RAM
80GB WD ATA
Sapphire Radeon 9250 Pro
Liteon cd burner - LTR-522465
BenQ DVD burner - DW1640

Partitions:
hda1 ~60GB - Windows xp sp2
hda2 ~14GB - ubuntu 6.06.1
hda3 ~1.5GB - Linux swap

Bootloader: grub

History:
Windows XP runs without issue.
Debian Sid ran without issue (albeit with default vid drivers) when it was installed on this box in a secondary partition)

I have posted here and people have suggested ATI drivers.
I first tried packaged Radeon drivers without joy.
I then succeeded with the packaged fglrx driver - I am pretty confident the vid driver is as good as it's going to get. 
I now have lightening fast x-windows, but apps still crash.

I have disabled serial and printer ports in BIOS, disabled the on-board vid (obviously) and a setting that allowed the onboard vid to obtain an interrupt - probably overridden by being disabled anyway.

I have set the bios from quick boot to long boot so that it runs extra tests etc.

I have run memtest for over 14 hours without errors.

I have also adjusted the swap size during the various installs - originally it was only 600MB.

[B]I have finished installing Ubuntu 6.06.1 alternate AMD64 and so far have had no crashes!

Hopefully it's all good.[/B]  

Thanks heaps,
Matt

---

### Post by lofgren on 2006-11-12
Sorry it's so long.. but any suggestions?

---

### Post by lofgren on 2006-11-13
So.. If I said I came across this link ([http://www.hardwaresecrets.com/article/201)](http://www.hardwaresecrets.com/article/201)), downloaded CPUZ and it says I have a 64 bit processor, would you laugh? :)

I did... because at the time, I opted *not* to pay the extra for the 64bit processor, finding it hard to justify the extra expense on my quick/cheap upgrade (a motherboard died on another machine).

Anyway.. I am hoping this is the cause of my unstable gnome apps and xwindows.

Does this sound likely/possible? Another post said you can run 32bit on amd64 "in most cases".

---

