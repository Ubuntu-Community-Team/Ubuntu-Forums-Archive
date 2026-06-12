---
title: "In need of Ubuntu confidence restoration"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by abyssius on 2008-04-02
I don't know if anyone wants to weigh in on this. I think my computer is fixed, but I need some confidence restoration in Ubuntu.

System under test:
[LIST]
[*]AMD Sempron 3000+
[*]ASROCK socket 754 MB,
[*]512Mb DDR, 16XDVD-RW
[*]NVidia GeForce 200,
[*]Dlink DWL520e1 wireless (hostap-driven)
[*]Audigy 1 sound card.
[/LIST]

Originally running Ubuntu Linux version 2.6.22-14-rt, now running 2.6.22-14-generic.

My computer was working fine up until a few days ago. I decided to install 8.04 beta on a new partition. The install proceeded to the very end, then the computer froze right before the reboot step. I had to press the reboot button. Upon reboot, version 8.04 didn't appear in the boot menu, and version 7.10 normal or recovery would not boot up. The problem indicated was a Bad EIP value, resulting in a Kernel Panic. 

I tried Super Grub, but it didn't see the 8.04 kernel, although I could see the partition in Gparted. I resigned my self to re-installing 7.10 from scratch. I tried to boot the live CD, but I got the same Bad EIP value, message and Kernel panic.. 

I searched the net, and although many others experienced these symptoms in various Linux versions, I could not find an understandable explanation, except that it could be bad hardware or memory. My system hardware worked fine before the the 8.04 install attempt. However, I first I ran memtest for hours with no problems indicated.

To troubleshoot my hardware (with parts I had), I removed my PCI wireless card and substituted it with a USB wireless adapter. I replaced my NVidia video adapter with an ATI Raedon, I removed the Audigy and enabled the on-board sound. I forced my BIOS back to default settings then I scaled the CPU speed down about 25%. (all this worked with Ubuntu previously).

Unfortunately, nothing changed the equation. I then tried booting with several Ubuntu live/install CD versions, (Studio, Kubuntu, 7.10, 7.04. 6.10) all resulted in the same Kernel Panic. I was able to boot a Mandriva 2008 live CD successfully. I ran the install, formatting the HD, it seemed successful, but upon reboot - all I could get was a blank screen. I next tried Mepis, which also booted and installed, but would freeze upon running from the hard-drive. I tried Knoppix live, got a kernel Panic, I tried Zenwalk live cd - it froze the computer. I was now convinced my computer had an unrepairable hardware problem.

Out of desparation, giving the PC one more chance, I tried Blag, which booted up and installed perfectly! I re-inserted all my hardware (ATI video card, Audigy, DWL520e1) ran the Blag install again. No Problem, except that I couldn't get the DWL520e1 wireless adapter to work (I've only been successful in Ubuntu with this particular card). 

I did notice that the Kernel version of Blag said it was a 686 kernel. I wasn't sure if that was significant, but in desperation, I decided to download the AMD64 version of Ubuntu to try (thank God I had a separate Windows computer to do all this). Strangely, the AMD64 live version booted right up. I restored my previous hardware configuration, I set the BIOS back to the way I had it set previous to my problems. I immediately ran an install with the AMD64 live cd (formatting the entire disk, etc.) I downloaded and installed the appropriate hostap-util, edited the interfaces file, and I'm on the Internet. It seems to be working perfectly!!! 

The only strangeness so far is that when I run [dmesg] from the command line, all that shows is this message repeated ad infinitum: **APIC error on CPU0: 40(40**). When I check the dmesg log, this doesn't appear - and it seems normal (nothing about APIC). Other than this, the computer seems to be working alright.

I'd like to go back to normal Ubuntu usage (installing all my programs, data files, etc.) but I'm hesitant to do so now. I wasn't aware that my computer was a 64-bit machine - so why does this kernel work? And, will it remain working!!! I don't know of any other tests that would give me clues as to what actually happened.

---

### Post by opscure on 2008-04-03
Sorry to hear about your troubles.  I have a few ideas about what might be happening.  First, your AMD Sempron 3000+ processor has the ability for 64bit, so if this worked then I wouldn't fight it too much.  I don't know if you have already, but you may want to try one of the alternate x86 install cd's.  I have has some issues in the past (specifically with laptops) with the regular install cds.  

As for your APIC error on CPU0: 40(40) issue, there are several ways that this could be resolved.  First, try and update your bios.  A good majority of the fixes I have seen were hardware vendor issues, but on a few this can be fixed by kernel options (grub) on boot.  You may want to try the addition of one or a combination of the following:
irqpoll
noapic
nolapic


Or removing the ohci module (firewire).

This message doesn't seem to reduce the performance of the system from what I have gathered, but I do suppose this would be annoying.  

I hope this helps you a bit and good luck.

---

### Post by abyssius on 2008-04-03
Thanks for your response, opscure.

 I had no idea about a Sempron's 64-bit ability. I did know that the Motherboard supported 64-bit processors. I bought the MB+ CPU at geeks.com for $50.00. I wanted to build a computer to try Linux, but my budget was humble. It turned out to be suprisingly fast. It's 64-bit support is even more surprising. I will try those boot options, and I'm downloading the alternate distro right now. I noticed you mentioned the OHCI module for firewire. My Audigy card includes a firewire port - and I use it to connect an external DVD burner and my DV camcorder, so I hope this is not the problem. 

It's funny, I used to think I knew lot about computers based on my experience in the Windows world. Linux has brought me down to earth big time. I hate Vista, can't afford the Mac world, so I sincerely want to switch to Linux. I've downloaded and tried over a dozen different distros. I liked the Ubuntu philosophy the best of all. It seems easy enough for beginners  like myself and it is not overtly trying to copy the Windows/Mac flashiness (fluff) like some others I've tried.

Anyway, so far the computer seems to be the most stable it has ever been. Flash was no problem, but the 64-bit kernel doesn't seem  to like Real Player. No biggie. I would like to install the real-time kernel for Rosegarden compatibility, but I'm a little nervous about this, since I have this feeling that rt created my problems in the first place.

---

