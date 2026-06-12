---
title: "Black screen start/ shutdown Gutsy w/ nVidia 8500"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Applegeek on 2007-11-11
I've got a strange problem here:  I have a newer AMD X2 box with an nVidia 8500 card and a Gigabyte Mobo.   Running Feisty 100% OK, and the system boots fine from a Feisty amd64 CD as well.  I go to start a "clean" install of Gutsy amd64 and here's what happens:

1.  If I boot the machine from the live CD, I get the initial menu screen (Start or Install, Install with updated driver disk, etc).  OK.  If I try to "Check CD for Defects" the screen blanks out.  Its like its running the program, but the display adapter isn't working - and it'll never come back. (Checked on another PC and the disk is OK).  I checked the BIOS, and there isn't an option to totally disable the on-board graphics adapter, but it is supposed to be using only the PEG in the PCIe slot anyway.  It acts like its trying to use the on-board display adapter instead of the nVidia 8500.

2.  If I try to boot in "safe graphics mode" the system just crashes. 

I'm not sure I want to proceed with Gutsy install if booting from the Live CD is already all wonky.  I don't want to "upgrade" from Feisty to Gutsy - I've already had that produce weird results.

Advice?  Should I go ahead and try the full install anyway?

---

