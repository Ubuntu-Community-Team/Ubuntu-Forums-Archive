---
title: "[SOLVED] Live CD will not boot"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by af20001 on 2008-09-29
I have a new laptop, an Advent 5312 which I am trying to install Ubuntu on.

The live CD of 8.04.1 doesn't get any further than the first segment on the progress bar of the splash screen, then it just hangs - no errors appear, it just stops.

I have also tried Live CDs of Mandriva One 2008 & PCLinuxOS 2007 and they both hang as well, although they seem to get slightly further along before stopping. I know these particular discs are OK, as I have booted from them before.

Anyone got any ideas on what I can do? I'll be really cheesed off if this laptop won't work at all with Linux - my old one was fine but the kids broke it, and this is the insurance replacement.

---

### Post by cariboo on 2008-09-29
Have you hit F4 at the menu screen and tried some of the suggested modifiers.

Jim

---

### Post by af20001 on 2008-09-30
I managed to get it to boot, by using some of the options using F6:

acpi=off noapic nolapic

Then it didn't pickup the wireless and the screen resolution was wrong. As the 8.10 beta is out this week I might try that and see if there is any improvement. But I think I'm going to return it, as there looks to be a fairly large dead spot on the LCD that I didn't notice before.

Thanks for the heads up on the start options.

---

### Post by Crafty Kisses on 2008-09-30
You might want to try the alternate CD installer.

---

