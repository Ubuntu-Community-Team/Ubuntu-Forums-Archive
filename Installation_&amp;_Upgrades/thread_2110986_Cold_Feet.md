---
title: "Cold Feet"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by quant128 on 2013-01-31
Greetings,

I purchased a new laptop with Windows 8 preinstalled not knowing what I was getting into. I was running 12.04.1 dual with Windows 7. I intended to do the same thing with Windows 8 but Wubi and Windows don't play nice together. I read that 12.10 was configured to work with 8 under 64 bit mode. So I downloaded 12.10 64-bit, created a boot dvd, and attempted to boot from it. With UEFI active, the system refused to boot from the dvd with the dreaded missing file message which I had read I would probably encounter. So I went into the Bios and changed Secure Boot from UEFI to Legacy. Understand, I DON'T UNDERSTAND ANY OF THIS. With UEFI in Legacy mode, my computer doesn't recognize Windows at all but the DVD boots just fine. However when I say "Install Ubuntu" it says it doesn't see any other operating systems on the drive and offers to erase my entire hard drive. I say no, let's try something else and it gives me a window with 5 or six partitions which it proposes making to install it's system. However I suspect this is still incompatible with Windows 8 and I cancel without doing anything. If 12.10 is compatible with 8 then what did I do wrong? Or am I just too timid and did I misinterpret some perfectly acceptable option? Substantial hand-holding would be appreciated.

---

### Post by VeeDubb on 2013-01-31
Well, I can give you some food for thought, but that's about it.

First up, as you suggested, there's a lot of stuff you don't understand.  My most helpful advice would be to do some reading and try to understand those things before you make any decisions.

Let me try to clear a few of those up, or at least get you aimed in the right direction.  

Legacy BIOS vs UEFI: In old terms, BIOS (Basic Input Output System) is like a mini-operating system on your motherboard.  It can't do anything that is particularly apparent as useful to the end user, but it get's all the hardware started up, assigns names and addresses to everything, and controls the very core of how your computer functions.

A few years back, somebody figured out that they could make a BIOS that did a whole lot less, and actually make things run better.  The idea was that the BIOS would hand it's hardware control over to the operating system.  As long as you've got an OS that can handle it all for you, the BIOS wouldn't have to do anything more than spin up the hard drive and tell the CPU where to start processing. This is called UEFI BIOS.  

The advantage to UEFI is that your system boots MUCH faster and the OS has more control.  The downside is that it's relatively new.  For windows, it's only supported by Windows 8.  If you're going to Dual Boot with UEFI, there are probably a lot of extra steps involved, and I don't know what they are because I haven't tried to dual boot in many years and I don't have a UEFI compatible motherboard.



Miss-use of the term "compatible": There is not a single version of Ubuntu that is "compatible" with any version of Windows.  Saying that Ubuntu 12.10 is compatible with Windows 8 because they will both run on UEFI hardware is like saying that Mitt Romney and Barrack Obama are compatible because they could (in theory) drive the same car.

U12.10 is compatible with UEFI hardware.  W8 requires UEFI hardware.  To say more is to draw false conclusions.

Now, Wubi may be compatible with Ubuntu 12.10 on Windows 8, but that's still a different scenario than what you said.  I know this all sounds like a lot of pointless semantics, but sometimes semantics can make a world of difference.  Especially when you're trying to figure something out.  Go into research mode asking the wrong questions, and you'll never find the right answers.



My personal recommendation, other than doing a lot more reading, would be to stop dual-booting.  Unless you are a big gamer (and even that is getting better) or you require very specific windows-only software for work that won't run with wine, I would encourage you to just go ahead and wipe your hard drive, and install Ubuntu properly.  You'll learn a lot more, a lot faster, when you're working with it every day.

---

### Post by JKyleOKC on 2013-01-31
> **VeeDubb said:**
> The advantage to UEFI is that your system boots MUCH faster and the OS has more control.  The downside is that it's relatively new.  For windows, it's **only supported by Windows 8**.  If you're going to Dual Boot with UEFI, there are probably a lot of extra steps involved, and I don't know what they are because I haven't tried to dual boot in many years and I don't have a UEFI compatible motherboard.Not fully correct; my newest machine came with Win7 factory-installed using UEFI. I had to jump through quite a few hoops before getting it up and running.

I do dual-boot it, because I wanted to retain the possibility of running Win7 in case I ever need it to support a customer. However I always boot it into Xubuntu.

Win 8 added "secure boot" to the mix and that greatly complicates matters. You have to go into the machine BIOS settings and disable "secure boot" to have any chance of installing a Linux system correctly. You also need to disable the "fast boot" option if it's present. You then have to use the 64-bit version of 12.10, with its DVD booted into UEFI mode. With all that done, you should be able to boot the live CD and test-drive the system; if it all works under those conditions, you then go back to Windows and use its disk management tool to reduce the size of its partition to make space for Ubuntu. With that done, you can boot the DVD again and tell it to install alongside Windows. It should detect the space you made available, install there, and when you reboot, give you a menu to choose between Ubuntu and Windows. With my Win7, I get a Win7 menu first, then the Ubuntu menu, but I don't consider that a problem...

---

