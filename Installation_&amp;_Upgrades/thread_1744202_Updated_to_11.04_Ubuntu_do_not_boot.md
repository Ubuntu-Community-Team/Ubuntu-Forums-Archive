---
title: "Updated to 11.04: Ubuntu do not boot"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by chteuchteu on 2011-04-30
Hello !

I just upgraded my Ubuntu version to 11.04 yesterday without any errors...
When I wanted to start my computer, Grub said that a file was missing and that he did'nt wanted to boot. I purged Grub files and installed a new fresh Grub from the Live CD.

Then, I booted on the new updated Ubuntu... He said me (when the loading step with the three/four points blinking) that he wasn't able to boot one of my partitions. He wasn't able to do it before the update, so I pressed "S" (for "skip mounting").
But then he said that the hard disk wasn't ready yet and said me that I could wait, skip or mount manually (something like that).

I started Ubuntu 9.10 Live CD (the most recent I have) and corrected the mounting problems (I just have one partition that I can't mount but no matters).
[B]
-> [/B]So now, when I want to start my computer (Ubuntu 11.04), it just goes to the magenta screen and stops here... No matter the version of linux kernel that I choose to load on Grub, the loading just freeze at this step...

What should I do ?? Thank for any help ! =)

---

### Post by dino99 on 2011-04-30
try to boot in recovery mode ("shift" key down at bios end process to get grub menu) and select "repair packages"

then : try to boot without "splash"

sudo gedit /etc/default/grub

on line nb 11: remove "splash"

then save and

sudo update-grub

---

### Post by chteuchteu on 2011-04-30
> **dino99 said:**
> try to boot in recovery mode ("shift" key down at bios end process to get grub menu) and select "repair packages"

then : try to boot without "splash"

sudo gedit /etc/default/grub

on line nb 11: remove "splash"

then save and

sudo update-grub

I tried to push shift button just after the end of the bios loading (so before the grub screen) but nothing happens: grub loads as if a didn't pushed it...

And I deleted "splash" in the Ubuntu line (directly in grub). When I try to start Ubuntu, I have the magenta screen with some lines on it... But they're in black color and highlighted in black so I can't'read it...

---

### Post by chteuchteu on 2011-05-01
Just tried to boot again without splash:
it goes to following steps and then... Waits with the blinking "_"
* Checking battery state... [OK]
* Starting TiMidity++ ALSA midi emulation... [OK]

Also, when I start in recuperation mode -> low graphics mode, I can use my Ubuntu as if there were nothing !

I do not understand what the problem is...

---

### Post by chteuchteu on 2011-05-06
Up ?

---

