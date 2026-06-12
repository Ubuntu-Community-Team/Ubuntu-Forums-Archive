---
title: "Toshiba A105-S2716 failed to install or upgrade to 9.10 (Karmic Koala)"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by idbar on 2009-11-30
I'm new to the forums. But I spent the whole holiday weekend trying to install Ubuntu (hopefully netbook remix) to a friend's laptop (yes, I think I had her converted) :D.

The issue is the following:
1. Installing from scratch doesn't work, unless I add the option "acpi=off". In which case, I need to add this option both, when installing and after installed. The result, is that the release doesn't detect battery charging, AC connected or lid closing events.
2. I installed 8.10, then upgraded to 9.04 and worked fine. Upgrading to 9.10, broke again. However, grub remained the same, but I still need to add the acpi=off if I want to boot.
3. I have a the BIOS Phoenix 1.8 and tried to upgrade to 2.00 but that causes the BIOS to misbehave and takes long time to enter its menu (ubuntu unrelated hopefully). Unfortunately, none of the BIOS worked anyways.

The report, when I disable acpi (i.e. I manage to login to the machine), is attached. Please let me know if any more information is needed.

Any help is greatly appreciated. Moreover, I would also thank if you point me out to what acpi=off really means, what other options I have (I also tried acpi=ht, but seems to have the same effect).


EDIT: 
Details:
One more detail: 
When installing from scratch, after booting with "acpi=off", no graphical interface will come up. Trying to bring it up with "startx", will show the whole desktop, but the mousepad and keyboard will not respond. 
When I upgraded from 8.10 (installed 8.10 from scratch and then upgrade), this didn't happen.

I'm sorry my English is not that good.

---

