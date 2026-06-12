---
title: "MP-BIOS bug: 8254 timer not connected to IO-APIC"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Yesideez on 2008-08-17
I just bought the Linux Format Special magazine with Ubuntu on a free DVD and when I try and boot from the disc I get this:

```
MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option.
```
Here is my setup:
AMD Athlon 5200 Dual Core 2.6GHz
4GB DDR2 800 RAM
1TB hard drive storage over 3 drives
Dual boot Windows XP Pro SP2
Creative SoundBlaster Audigy Platinum 2 eX
ATI Radeon X1650 Pro 256MB GDDR3 PCI-e x16

Any help resolving this issue would be appreciated. Can't see how I can boot with a debug and noapic option when the booting is from a DVD!

I'm interested in adding Linux as an extra boot meaning a tri-boot system. One boot of XP has my work stuff and the other boot is dedicated to running Battlefield 2.

Just searched and checked topics so I'm editing this to say it won't boot - freezes with those lines on the screen.

---

### Post by Yesideez on 2008-08-17
OK I'm typing this from Ubuntu I've managed to get working.

Seems I should have used the search feature a little longer than I did as I found that pressing "F6" to enter the options and typing "noapic" on the end of the command line got it working just fine.

Just curious, is there anything I can do to get IO-APIC working fine should I go ahead and install Linux as a third boot?

I've been into my BIOS and there's no option that I can see regarding APIC anywhere - can it be hidden under a different name?

I'm liking very much what I'm seeing. I noticed the eye candy couldn't be enabled properly so I'm even more tempted to install as an extra boot.

---

