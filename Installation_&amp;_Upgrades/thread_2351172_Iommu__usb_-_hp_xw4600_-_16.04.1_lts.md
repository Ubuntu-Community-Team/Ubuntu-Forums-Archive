---
title: "Iommu / usb - hp xw4600 - 16.04.1 lts"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by ebooher on 2017-01-31
Hello,

I have an XW4600, and found this on a Red Hat site concerning Fedora 12:

[COLOR=#000000][FONT=sans-serif]There are some systems currently known to be potentially affected by this issue. For all of those except the HP xw4600 Workstation and the Dell Precision M6400, all of the following conditions must be true before you hit the bug:[/FONT][/COLOR]

[LIST]
[*]You must be using the 32-bit edition of Fedora 12
[*]You must have no memory beyond the 4GB address area (practically speaking, this means you must have around 2.5GB of physical RAM or less)
[*]Virtualization features (VT-d) must be disabled in the BIOS
[/LIST]

However, it doesn't say how it affects those *with* an XW4600. Since Fedora 12 is ancient anyway ... not hopeful to find anything more there.

So, short story long. I installed 16.04 LTS (16.04.0 ?) and it worked well enough, but the menu bars looked odd, and were white with hard to read fonts. Lost that install media so downloaded a newer ISO for 16.04.1 which I believe to be most current for LTS. Installed it on a *different* XW4600 and it ran well, but had black menu bars with readable white text. So, that's not the important part but wanted to point it out.

So, using the same install media I installed 16.04.1 on the first XW4600 (Core 2 Duo, 2 GB RAM, 16GB USB Boot drive) and it ran as well as it did on the second XW4600. Awesome, now we're cooking with evil gas. However, software update struck, and installed kernel 4.4.0-59. Upon reboot I lost USB, which killed not only the boot drive, but also the keyboard and mouse so was unable to use the emergency prompt it gave.

Ok, so during boot, menu offers "Advanced Ubuntu Options." Choosing the option for 4.4.0-31 (generic) allowed the system to boot. Awesome, back in business and evil can resume. Need to reboot ... now, no offer of options from GRUB, just splash screen .... which boots to 4.4.0-59 just fine. !?

I get that my system is using IOMMU in a sloppy fashion, and the install of the new kernel somehow broke the balance. So I guess my actual question is, why is it doing this and what can I do to keep it from happening during the next kernel update?

---

