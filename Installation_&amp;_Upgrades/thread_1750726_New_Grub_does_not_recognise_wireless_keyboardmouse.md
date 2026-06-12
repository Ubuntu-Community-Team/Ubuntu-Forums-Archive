---
title: "New Grub does not recognise wireless keyboard/mouse"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Chosulman on 2011-05-05
I have installed Ubuntu 10.04.2 LTS onto a W-XP desktop machine which has a Logitech MK300 wireless
keyboard+mouse.  The wireless receiver module plugs into a USB port.  But there is a serious problem ...

During boot-up, the BIOS phase recognises the wireless keyboard.  I know this because ESC stops the
memory test, DEL enters BIOS edit mode, and keys also work OK in there.

When control passes to Grub (2), the keyboard is now NOT recognised.  This means that one cannot use
the up and down arrows to choose the boot option, be it Windows-XP, Ubuntu or the various other things.

When, after 10s, the boot process launches Ubuntu, the wireless keyboard/mouse work fine thereafter.
Similarly, if default boot is into W-XP, it too works fine.

And finally,  if I plug in a conventional wired keyboard, there are no problems at all.  Boot-up behaves
exactly as intended at all stages.

What needs to be tweaked to make Grub (2) recognise the wireless keyboard during the Grub boot phase?

Yes, I have spent hours searching the archive, but I did not find this matter discussed, though surely it must
be commonplace?

---

