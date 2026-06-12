---
title: "Installation Issue- Kernel Panic Not all CPUS entered broadcast"
date: 2017-03-20
forum: Installation &amp; Upgrades
---

### Post by btran115 on 2017-03-20
Hi,

I've been trying to install Ubuntu on my desktop for the past day, to no avail. I'll just walk through all the steps I took.
My CPU is an i5-6600 3.30Ghz, GPU is a 1060 6GB, mobo is ASRock Z170 Gaming i7.
1) I made a USB with Ubuntu 16.04.2 using Rufus
2) Upon rebooting, I get this screen: [http://imgur.com/FxURq2J](http://imgur.com/FxURq2J)
3) First, I try the USB option, which gets me to the maroon Ubuntu screen. I hit "Try Ubuntu without installing" but I get [FONT=verdana]nouveau 0000:01:00.0: unknown chipset (136000a1)
4) I try again, this time hitting F6 and marking nomodeset- doesn't work
5) I then boot with the UEFI option, which doesn't give anything new immediately. I hit 'e' and added nomodeset in front of quiet splash, which gives me a new error: [/FONT][FONT=verdana]Kernel panic- not syncing: Timeout: Not all CPUs entered broadcast exception handler

Since then, I've tried 17.04: [/FONT][http://imgur.com/ivs9j5W](http://imgur.com/ivs9j5W) , disabled Speedstep, turned off Secure and Fast Boot. I've tried removing my GPU and using the integrated graphics, but that doesn't take care of the kernel panic. After many hours googling and not getting any results, I made an account here in the hopes that someone might be able to help me. Please let me know if there's any more information I could provide.

UPDATE: Unplugging my CD drive fixed the kernel panic issue, but then I ran into a b43 unsupported phys issue. Getting rid of my wifi card fixed that problem. Then I had to type acpi=off next to nomodeset. That made some progress, and now I'm stuck at 
[http://imgur.com/Tjg7jIS](http://imgur.com/Tjg7jIS)

---

