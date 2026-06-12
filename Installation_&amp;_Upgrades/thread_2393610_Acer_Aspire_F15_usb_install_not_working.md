---
title: "Acer Aspire F15 usb install not working"
date: 2018-06-05
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2018-06-05
I have an Acer Aspire F 15: I already have a partitioned drive. Windows hiding behind the UEFI/Legacy (so effectively, no Windows at all really) --- and then I have two Ubuntus; an Ubuntu Studio distro as my primary "Computer", but then there is also just a standard 50Gig Ubuntu alongside that. When I boot up my computer, right after the Acer logo popup, I'm given an option of which linux I want to boot into (if I go into BIOS & switch my legacy/UEFI settings, the laptop boots directly into Windows).

I'd like to install Kali on that 50Gig partition. When I go into the BIOS boot options to set my USB (that already has Kali on it) so that I can do this install (and I'm wanting to overwrite the old stand alone distro), it doesn't matter which USB i'm plugged into or which USB is set as a higher priority in the BIOS, the USB never seems to boot.  I know its not that my USB ports don't work because I can use all the ports for various other things. Its only this boot up option that causes my problems. I've seen quite a bit about Acer's having some USB issues, but am curious if anyone has any ideas please.

I could probably just put the distro on to a disc & do the DVDrom install method, but it seems like there should be a USB fix. 

PS- the reason I can't just terminal upgrade the stand alone partition to Kali is that I use that OS so rarely, I've forgotten the PW ;( ;( 

Any help on fixing this USB issue would be greatly appreciated; thank you.

---

### Post by westie457 on 2018-06-05
I think the simple answer here is to reset the password for the Kali install. [https://www.technig.com/reset-lost-password-of-kali-linux/](https://www.technig.com/reset-lost-password-of-kali-linux/)
The terminal upgrade might be problematical or easy depending mainly on how old the version is.

Cannot provide help with usb booting issue simply because it has always worked for me.

---

