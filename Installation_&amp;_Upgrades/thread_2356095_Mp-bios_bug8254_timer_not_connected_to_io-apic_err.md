---
title: "Mp-bios bug:8254 timer not connected to io-apic error on Ubuntu install"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by nicolas8050 on 2017-03-19
> **MAFoElffen said:**
> Not to a file...

Post #3 would help you... (The following is from memory, so bear with me)

Booting onto the live Image USB, it depends on how you created the LiveUSB image.

If from unetlogin, as it boots, arrow the menu to the option, press tab... go down to the line starting with "linux" go to the end of the line and add... "radeon.modeset=0 noapic" (without the quotes) Press <cntrl><x>

If other and it looks like the boot from LiveCD, on boot press the left shift key. When at the initial purplish panel with the keyboard/person icon at the bottom, Press <enter>. At the language selection press <enter>. You will be at the Advanced Install Menu. Press <F6>. Arrow down to noapic, press the <spacebar>, then <esc>. You should see a new line displayed under the main menu. Arrow right until just after the text "noapic" and type in "radeon.modeset=0" (no quotes, these quotes are just for you...). Press <Enter> to boot with those options.

I tried doing as you said but when I get to the part where I have to add the "noapic" to the boot line, there is no "noapic" in the boot line. I'm tried to just run off usb only. I have an old PC that hard drive broke but still want to use the pc.

---

### Post by oldos2er on 2017-03-19
Post moved to its own thread.

---

