---
title: "Problem with movies/resolution"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by DonVincenzo on 2005-06-22
Right I've finally to get everything to work happily (be it my ATI card or my audigy 2) now though I've got two problems.
-First thing is I can't play back movies, well or I can but that requires me to start (for example) two xine, first one will never display anything but second one will work flawlessly.

-Second thing when I exit UT2004 (playing fullscreen) I can't seem to revert back to my original resolution (1600x1200) I'm stuck at 1600x1200 but in virtual desktop mode.

I will gladly consider any suggestions as to how I could fix those two (minors for now) annoyances...

---

### Post by intangible on 2005-06-22
About xine: Try going into the configuration, under "GUI" change "experience level" to "Advanced", apply changes, then under the "video" tab, try chnaging the "video driver to use" to xv, and then seeing if you still have the problems, if so, try different video driver.

About the UT2004 problem: not sure why it's not returning you back to your default resolution, but this will get you back to it **xrandr -s 1600x1200** or **System->Preferences->Screen Resolution**

---

### Post by DonVincenzo on 2005-06-22
[QUOTE=intangible]About xine: Try going into the configuration, under "GUI" change "experience level" to "Advanced", apply changes, then under the "video" tab, try chnaging the "video driver to use" to xv, and then seeing if you still have the problems, if so, try different video driver.[/quote]

Xv doesn't work but thank you for the suggestion I guess I'll try every single one until I find one that works :)

> About the UT2004 problem: not sure why it's not returning you back to your default resolution, but this will get you back to it **xrandr -s 1600x1200** or **System->Preferences->Screen Resolution**

When using the screen resolution shortcut if I reselect 1600x1200 I'm stuck in a virtual desktop mode. Same with the command.

---

