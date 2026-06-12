---
title: "Wireless on a Thinkpad 600E"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by RayRuest on 2007-12-28
Hi all,

I've been fighting with this for 3 days.  I have an old Thinkpad 600E.  I've been through the how-to wikis and have the newest BIOS, have sound working, the screen set to 16-bit, ACPI off, etc..  So far so good.  Heres the weird part.  When I boot the machine using the Live-cd, my Netgear MA401 RevD finds my network, and I can use it.  I was impressed.  Quicker config than Windoze ever gave me.  Now.. reboot to the install on the hard drive and the 600E will lock up part way through the boot (early) and the scroll lock and caps lock LEDs begin blinking together.  If I insert the card after the boot process, the LED on the card blinks, but Ubuntu never shows the card as being inserted.

Why would I get different behavior using the Live CD vs the install?  I have tried installs using the live CD as well as the alternate with the same result.  If the card works from Live... what do I need to change to get the install to work?  Any help is much appreciated.  I'm an Ubuntu convert for about a year...  but this is still beyond me.  Googled my brains out on this too.

Thanks!
Ray

---

### Post by Crumpets and Jam on 2007-12-29
> **RayRuest said:**
> Hi all,

I've been fighting with this for 3 days.  I have an old Thinkpad 600E.  I've been through the how-to wikis and have the newest BIOS, have sound working, the screen set to 16-bit, ACPI off, etc..  So far so good.  Heres the weird part.  When I boot the machine using the Live-cd, my Netgear MA401 RevD finds my network, and I can use it.  I was impressed.  Quicker config than Windoze ever gave me.  Now.. reboot to the install on the hard drive and the 600E will lock up part way through the boot (early) and the scroll lock and caps lock LEDs begin blinking together.  If I insert the card after the boot process, the LED on the card blinks, but Ubuntu never shows the card as being inserted.

Why would I get different behavior using the Live CD vs the install?  I have tried installs using the live CD as well as the alternate with the same result.  If the card works from Live... what do I need to change to get the install to work?  Any help is much appreciated.  I'm an Ubuntu convert for about a year...  but this is still beyond me.  Googled my brains out on this too.

Thanks!
Ray

According to [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") you need the orinoco driver.

---

### Post by RayRuest on 2007-12-30
Tried that...no go.  I slapped in a Linksys card, same problem.  Am starting to think its the PCMCIA.  Am going ot borrow some other non-wireless cards from work.  I know I've got a SCSI and a compact flash reader laying around somewhere.  I've adjusted the acpi settings as instructed, still locks up.  If I can suffer through another Live CD boot, I am going to take a look to see what the config files look like there.  Any suggestions to make sure I cover all the bases?  If it works with the live CD..it should work with the install !

Thanks
Ray

---

