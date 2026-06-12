---
title: "low-graphics mode after upgrade to hardy"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by bergeo on 2008-05-08
I just upgraded from Gutsy to Hardy, and now my monitor is stuck in low-graphics mode.  It worked fine before the upgrade.

I get a message saying "your screen and graphics card could not be detected correctly".  If I select 'configure', it correctly detects my monitor model (dell e196fp) but the only resolution options I get are 640x480 and 800x600.  Once the system comes up, if I run 'screen resolution' from the system preferences menu I get a big square saying 'unknown', and the same two resolution options.

I'm using the built-in graphics of my Intel DG33FB motherboard.

Any ideas how to fix this?

I saw something about 'now with easy uninstall' on the Hardy main page.  Is there an easy way to drop back to Gutsy?

George

---

### Post by dstew on 2008-05-08
If you have a graphical interface, see if there is a restricted driver available (System --> Administration --> Restricted Drivers Manager). To re-configure the display, hit alt-F2 and enter```
gksudo displayconfig-gtk
```. If you really have no managable graphical interface, you can boot in Recovery Mode (grub menu item) and try the **xfix** menu option.

EDIT: Unless you saved your Gutsy partition(s) intact, there is no easy way to go back. You would have to re-install Gutsy, I think.

---

### Post by bergeo on 2008-05-08
I checked the System --> Administration menu, but it doesn't show a 'Restricted Drivers Manager' option for me.

I can get the Screen and Graphics Preferences application using the suggested command, but it still only gives me the two resolution options.  It detects my monitor model correctly, and shows my graphics card as 'VESA driver (generic)'.  Clicking the Test button produces "Configuration test failed".

Should I be using a different option for graphics card?  I tried a few different ones (various intel, generic vga), but get the same results with each.

---

### Post by RgnadKzin on 2008-05-08
I have a KVM switch.  I had to plug the monitor directly into the ubuntu box, restart in recovery mode and use the xfix option.  After that, I was able to use all of the screen resolutions.

---

### Post by bergeo on 2008-05-08
Bingo!

I use a KVM too.  I tried the xfix trick and now it's all better.  Many thanks RgnadKzin!

George

---

### Post by linkunderscore on 2008-05-21
I am having this exact same problem...except I am not running a KVM switch. Its with my laptop. Any other suggestions?

---

### Post by NTBao on 2008-08-20
Didnt cut it for me either. Also laptop. I'm still trying to experiment with everything though. Will bring the good news if I have some.

---

