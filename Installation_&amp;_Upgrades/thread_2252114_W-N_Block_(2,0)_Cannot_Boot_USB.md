---
title: "W-N Block (2,0) Cannot Boot USB"
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by michael_3 on 2014-11-09
[COLOR=#333333][FONT=Helvetica Neue]I have Ubuntu on a USB and a Windows 8 laptop. Secure Boot is off and I also have Legacy Support enabled. When I choose to boot from my USB, the CAPS lock icon light flashes and then I get a bunch of commands. The first line is something along the lines of W-N Block (2,0), etc. I was thinking[/FONT][/COLOR]
[INDENT]Well, you can just format the disk using GParted.
[/INDENT][COLOR=#333333][FONT=Helvetica Neue]But then I was like[/FONT][/COLOR]
[INDENT]Wait, I can't even live boot.
[/INDENT][COLOR=#333333][FONT=Helvetica Neue]Can I fix this somehow? I have an HP Envy M6.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Update: Just tried booting Fedora and it is a blank black screen. This USB works on other devices.[/FONT][/COLOR]

---

### Post by ubfan1 on 2014-11-10
Can you boot in UEFI mode?  Turning on legacy mode is a bad path to follow.  HP's do tend to have odd requirements on the naming of the bootloaders, but you should be able to boot the live media.

---

### Post by michal15 on 2014-11-25
[COLOR=#000000]Hi, I was experiencing the same issue with USB install (Ubuntu 14.04). The USB was originally formatted with NTFS. Formatting as FAT32 made this particular screen disappear, but installation did not work anyways.. I run disk check (from Ubuntu installation menu) - results showed 2 erroneous files. I finally decided to try 14.1 - this one installed without any issues. Hope this helps.[/COLOR]

---

