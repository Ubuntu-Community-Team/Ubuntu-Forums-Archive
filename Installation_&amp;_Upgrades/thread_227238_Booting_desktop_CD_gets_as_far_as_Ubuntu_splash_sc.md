---
title: "Booting desktop CD gets as far as Ubuntu splash screen"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by david_1982 on 2006-08-01
I have a problem with the Ubuntu 6.06 Desktop CD. I'm trying to use it as a live CD, but I can't get it to load properly!

Basically everything looks like it's working fine when booting off the CD, until I get into X. I get the brown desktop, even the cool sound, but I don't get any further than the Ubuntu splash screen.

I've installed previous versions of Ubuntu on this PC before, so I don't think it's a mobo/memory/gfx card issue. Perhaps I should remove all USB devices and try again.

Anyone have any other ideas?

---

### Post by zxee on 2006-08-01
Maybe you can open a shell at the stuck in splash situation? > Alt+Ctrl+F1 and type > dmesg <enter> What does that output?

---

### Post by david_1982 on 2006-08-01
Alt+Ctrl+F1 gets me to a blank screen with a flashing cursor (no prompt). Typing [FONT="Courier New"]dmesg[/FONT] elicits no response.

All the other consoles display the same, except F7 which takes me back to X and F8, which shows the boot log. All the items have [FONT="Courier New"][ ok ][/FONT] after them. The last entry on this log is 

> [FONT="Courier New"]* Starting periodic command scheduler[/FONT]

Which also says [FONT="Courier New"][ ok ][/FONT] after it.

---

### Post by david_1982 on 2006-08-01
Just unplugged all my USB devices (iPod dock, HP Photosmart 8250, cable for my camera - all but the printer weren't in use) and the live CD booted into X (no splash screen this time) and the console on F8 had

> [FONT="Courier New"]* Starting deferred execution scheduler[/FONT]

as the last entry - with no [FONT="Courier New"][ ok ][/FONT] at the end.

---

