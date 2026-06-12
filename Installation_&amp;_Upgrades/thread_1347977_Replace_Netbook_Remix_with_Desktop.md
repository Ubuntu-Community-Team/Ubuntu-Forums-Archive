---
title: "Replace Netbook Remix with Desktop"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by JasonSilver on 2009-12-06
I would like to replace my netbook remix with desktop, but I can't figure it out. 

I've done a few things but still can't:
1. see files on the desktop
2. see a start menu (I mapped the menu key to the menu tho)
3. get rid of the automatically maximized windows

Is there anything I can do to make this change without losing all my settings etc. in Remix? (Like Firefox plugins, saved passwords, mapped network drives etc)

Thanks,
Jason

---

### Post by quixote on 2009-12-07
Do you want to change to a regular gnome install, or are you just trying to change the look and actions of a few things but stay with Remix?

Your preferences and settings are all in hidden files in your /home directory.  So, for instance, firefox settings are in ~/.mozilla/firefox, nautilus settings in ~/.nautilus, and so on.  Under gnome, the look-and-feel prefs are all under 3 dirs that start with .gnome.  If you have a look (Ctrl-h to show hidden files in nautilus), it'll probably be pretty easy to figure out which one has the remix settings.  Back up all the *other* settings folders, since those are the ones you want to keep unchanged.  Then you can at least always get your other settings back if something goes wrong.

---

