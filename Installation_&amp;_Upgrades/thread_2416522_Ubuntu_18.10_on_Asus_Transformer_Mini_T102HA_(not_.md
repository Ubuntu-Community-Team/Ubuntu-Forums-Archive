---
title: "Ubuntu 18.10 on Asus Transformer Mini T102HA (not T100)"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by jsmith87 on 2019-04-10
[COLOR=#000000][FONT=Arial]If you have an Asus Transformer Mini T102HA let me save you some time and trouble: it has a 64 bit UEFI boot loader (not 32 bit EFI) and installs out of the box with Ubuntu 18.10 (64-bit) off a live USB created from Rufus with an iso written to the usb in GPT format. You don't need to do any of those weird UEFI 32 bit hacks.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Nearly all of the hardware issues mentioned in those old T100 threads have been fixed. As of April 2019 there's still an issue with suspend/resume on lid close but the following all work without tweaks: UEFI boot loader, suspend/resume via the power menu, 5ghz wifi, touch screen, keyboard, and sound.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If you happen to be trying other efi loaders and get a black screen that sends you back to the Aptio bios firmware setup, it's likely you have a 32 bit efi that you're trying to load with a 64 bit only UEFI on the T102HA. This cost me hours of pain and was not obvious, since all the instructions lead you down the old jwells bootia32.efi (32 bit UEFI) workaround. Occam’s razor killed me. If you're looking for additional bootloader info, check out refind, jwells posts, and a post from AdamW about how UEFI works.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by hamishshort on 2019-04-11
The default install of 18.10 on my Asus t102ha worked for me too.... all touch and rotate functions work well.
I have the same problems with lid closed as noted.  Sound seems to be working ok.

Also NOT working is the stylus/pen which works ok in portrait mode, but not in landscape mode.
The camera is not working either.

hope that someone will find a way to fix these !

---

