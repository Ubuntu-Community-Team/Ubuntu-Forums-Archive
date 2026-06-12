---
title: "Fresh install -- hangs at mounting root fs -- stickies no help"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by badfrog on 2006-09-05
Hey all, I've got a new xubuntu Dapper install that hangs at "mounting root filesystem," and eventually dumps to a console with an "hda1 does not exist!" error message.

I had this problem with the LiveCD, which would dump me out to the console with an "MP-BIOS bug" message. I corrected it with a combination of acpi=off boot option and unplugging the PC's USB mouse. That got me into the live cd, where I used the install function to install xubuntu. 

I read over the "READ THIS FIRST" sticky, and found the section on hung boots. Using acpi=off and unplugging USB devices do not help, like they did with the Live CD. /etc/fstab does not exist when I get dumped to the console (which I think is odd). I've tried disabling power management in the bios, and using the irqpoll boot option, neither of these worked.

This is a non-SATA, Asus A7V8X, AMD Athlon 2800+, with a single 60GB hdd, CDRW and DVD-ROM. I've run out of ideas to get around this, and I'd really like some suggestions ](*,) 

Thanks

---

