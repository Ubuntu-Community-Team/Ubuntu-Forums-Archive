---
title: "installed 9.10 won't boot kernel panic"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by mmmmna on 2010-01-27
Hey. I searched.... nothing seemed totally relevant.

Celeron D 3.33 GHz (64 bit system), 1Gig ram, Elite Group RC410L800M motherboard (ATI onboard graphics, x200 family, but not used, also is an ATI Northbridge/Southbridge solution intended for laptops.... but is used on this mATX mobo).

System has worked fine for 2 years under PCLinuxOS 2008 and 2009; this system also worked pretty decently on 64Studio before 64 came out of beta.

Why am I here?
I've tried U9.10for64, Ulite9.10, UNR9.10, KU9.10. All those releases will run just fine as a live CD. After installing them to hard disk, none of them will boot.

All installed Ubuntus throw a kernel panic, all are very close to something like this:

I get the boot options screen.
I select the normal boot. Screen blanks, I see a blinking cursor for 2 or 3 seconds, then the error message reads something _like_ this:

```
[00.0044001 Kernel panic! IO-APIC + timer doesn't work! try APIC=DEBUG and send a report, then try booting with noapic option. [00.0044001]
```

Over all the different versions, sometimes I saw the above numbers change to 00.0010000 or 00.0040000, depending on version of distro.

I then tried the suggested option to send a report, that also ends in the same kernel panic, and gives the same error message. There is your 'report' because that is all I got.

I then tried the suggested noapic option, same Kernel panic, maybe a different number by a tiny bit.

What do I do now? I've tried a few distros on this box in the past few days, PCLinuxOS 2009.2 got the closest to being useful after installation but the graphics and sound were hiccuping badly.

Posting from UNR9.1 on said system, no obvious issues.

:popcorn:

Edit 2010/02/06: reset notification to do not subscribe.

---

### Post by mmmmna on 2010-01-28
I've managed to get the system to boot by experimentation withe the GRUB entry for normal boot:
I can add either nolapi or noapic and the system boots to login and is usable.

Next to investigate is what is lapic and what is apic.

ttyl.

---

### Post by tachuela on 2010-01-28
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by mmmmna on 2010-01-28
Thanks, very interesting to know. It also has a link to LAPIC explanation, good link.

Now I have to edit the grub entry to add nolapic at boot, since I'm uniprocessor right now.

---

