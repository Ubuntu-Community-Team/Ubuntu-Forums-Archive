---
title: "Automatically using highest possible monitor res."
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by EmmEff on 2005-07-28
I just completed my second ever Ubuntu installation yesterday and had some issues monitor detection.

The Hardware in question is Sapphire RADEON 9250 video card and a NEC AccuSync 95F.

The installer seemed to detecteverything correctly, however the default was to use a video resolution of 21xx x 17xx (or something similar).

gdm starts up and I get scrambled video (no surprise).  CTRL-ALT-F1 didn't bring me back to a text console either (not sure why)

Shouldn't the installer use a sane default and let the user select something higher in Preferences->Screen Resolution?

---

### Post by mad_scientist03 on 2005-07-28
One thing you can do is to look at the file '/etc/X11/xorg.conf' (at least that's the location in Fedora; I believe it's the same location in Ubuntu. If not, do a 'locate xorg.conf' from the terminal) and see what that file tells you. 

You can look at 'Section "Screen" ' where you should find a list of your monitor's resolutions. You can delete the higher resolutions from this list.

Post back if you're having any problems.

---

### Post by EmmEff on 2005-07-28
[QUOTE=mad_scientist03]One thing you can do is to look at the file '/etc/X11/xorg.conf' (at least that's the location in Fedora; I believe it's the same location in Ubuntu. If not, do a 'locate xorg.conf' from the terminal) and see what that file tells you. 

You can look at 'Section "Screen" ' where you should find a list of your monitor's resolutions. You can delete the higher resolutions from this list.

Post back if you're having any problems.[/QUOTE]
 Yes, I've already done that and X is now working fine, however I'm quite experienced with Linux.  Somebody who isn't wouldn't know how to solve the problem.

---

### Post by mad_scientist03 on 2005-07-29
You're quite right about it being a nontrivial problem to solve for a new user, and unfortunately, I don't know how to remedy the fact that the system chooses such an inconvenient default.

It might be worth filing a bug report, or maybe look into some development mailing lists and directly notify the people who would know how such problems get fixed.

---

### Post by EmmEff on 2005-07-29
[QUOTE=mad_scientist03]You're quite right about it being a nontrivial problem to solve for a new user, and unfortunately, I don't know how to remedy the fact that the system chooses such an inconvenient default.

It might be worth filing a bug report, or maybe look into some development mailing lists and directly notify the people who would know how such problems get fixed.[/QUOTE]
 I'll probably file a bug report.

I know that Windows XP boots @ 640x480 and then tries to safely switch to 800x600 (complete with a "can you see this?" prompt).  I think this is perfectly acceptable since it's possible to change the screen resolution under Preferences in GNOME.

---

