---
title: "Main power button needs to be turned off and back on for starts"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by sbhattacharjee on 2008-02-18
I have a Gigabyte DS3 motherboard. Installed Gusty Gibbon and everything seems to work flawlessly except, this power issue...

Basically after I shutdown successfully, trying to start back the computer on pressing the power button, doesn't seem to work. I can see power/fan turning on, but I dont any screen showing the BIOS 'POST' screen. If I now now turn off the power supply button at the back of the computer, and turn back on...and then try to power up (using the front power button) it works just fine.

i am think this has to with BIOS settings. It did have hackintosh installed on it before, but i completely wiped it to install Ubuntu. Can't quite reason as to why it will do something like that, the main power off and on would mean some kind of reset, but when I shutdown Ubuntu ..it seems to power down everything just fine...

Anything in particular I should be looking...or is this somewhat related to power shutdown and restart in Ubuntu? Never had this issue before, b/c always used a laptop, and there is only one power switch...

---

### Post by Whiffle on 2008-02-18
Sounds like ACPI isn't working.  You might check to see if that was turned off or something in your bios.

---

### Post by Kivech on 2008-02-19
Having a Gigabyte motherboard myself, I can assure you that this is Bios related. I had some bios issues a while ago and had the exact same behaviour.

What you could do is reset the bios to its factory safe defaults and see if your computer still behaves in the same fashion.

It's not like you upgraded your bios lately, or maybe you should upgrade it.

Anyway, I'd look for a solution in this area.

Kivech

---

