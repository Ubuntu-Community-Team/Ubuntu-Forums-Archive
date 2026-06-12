---
title: "UEFI BIOS update (Asus) causes black left monitor on restarts"
date: 2023-05-29
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-05-29
Today I upgraded my Asus motherboard UEFI BIOS firmware from v3801 (dated 2021/08/12) to the current firmware version 4501 (dated 2023/05/23).  

The upgrade process itself went fine with no apparent glitches.

But now, immediately after this, when I do restarts, my main (left) monitor goes black upon the restart. This left monitor still acts on mouse and keyboard input, but stays black, unless I turn off, then on, the monitor power button.  My right monitor is OK.

Note that the monitor does NOT go black when I boot up from the computer being totally turned off, only when I do a restart.

I then flashed in the firmware version 4402 (dated 2023/02/08), which is the version just preceding v4501.  Same problem.

I may try to keep going backwards to versions 4006, 3904, then back to 3801 again, but thought I'd post here before I do all that, to see if anyone might have an idea of what's going on.

---

### Post by watchpocket on 2023-05-29
So, by trial-and-error, it turns out that all of firmware versions 4501, 4402 and 3904 caused the black monitor problem on restarts.  

(I didn't bother trying 4406).  These are all the versions that came after 3801.

So I'm back to my original firmware version 3801, which is the only one that doesn't, for me, cause that problem.

Looks like I'll be staying with version 3801 for awhile.

---

