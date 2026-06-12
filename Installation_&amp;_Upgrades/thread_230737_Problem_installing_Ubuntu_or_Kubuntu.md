---
title: "Problem installing Ubuntu or Kubuntu"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by Sar on 2006-08-06
Same thing happens with both of the 6.06 distros off a live CD.

The live cd boot process will go ok, and everything will load until it gets to "Starting kernel log", at which point the screen will go black with a blinking cursor in the top left, which freezes after 10 seconds or so.

No keyboard input is apparently working, other than ctrl-alt-del, which ejects the CD and reboots the PC a few seconds later.

My hardware is:

AMD 64 3500+
Nvidia PCI-e Geforce 7600GT
Viewsonic VA2012w 20" LCD
Foxconn 6100K8MA-RS Motherboard
Realtek NIC
Soundblaster Audigy 2 ZS

I'd really like to get either distro working, and try to get away from WinXP :)

TIA!

---

### Post by pdub on 2006-08-06
I had a similar problem with Ubuntu on one of my PC's and was able to get past it by adding acpi=off to the kernel line during boot.

When at the initial boot menu choose 'e' to edit the commands.

Then choose the kernel line and choose 'e' to edit.

Then add acpi=off to the end of the kernel line

Then enter.

Then esc to get back to the main menu.

Then enter to boot.

Hopefully this will help.

---

### Post by Sar on 2006-08-06
Tried adding acpi=off to it, as well as live acpi=off and boot: acpi=off, and it still hangs in exactly the same place each time.

This is with the live CD, so I'm hitting F6 to add these options to the options line.

Complete linux noob, so any further help would be appreciated!

---

### Post by Sar on 2006-08-06
Even tried disabling USB, and removing my USB devices and adding various commands to the boot options, but no dice.

Apparantly the latest kernel, as used in Dapper, doesn't like nforce4 chipsets, which is what my mobo uses.

I'm downloading the 5.10 distro of kubuntu to see if that installs ok, and if so then I've nailed the problem.

---

### Post by Twinsen on 2006-08-06
That seems to be whats hapening with mine as well. Does your monitor recieve a no input siginal or does it just go black?

---

### Post by Sar on 2006-08-06
No, it's getting a signal ok, because there's a non-flashing cursor in the top left hand corner sitting there doing nothing.

I've just tried Breezy (5.10), and it installs ok, but fails boot just after "Checking battery state", with or without acpi=off apm=off in the boot line or not...

Why can't linux just work - this is why it'll never be as mainstream as Windows.

:(

---

