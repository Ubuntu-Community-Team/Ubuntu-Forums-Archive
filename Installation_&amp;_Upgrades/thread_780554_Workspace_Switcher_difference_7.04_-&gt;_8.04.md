---
title: "Workspace Switcher difference 7.04 -&gt; 8.04"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by mdlueck on 2008-05-03
The Workspace Switcher works completely different in 8.04 than it worked in 7.04. The 7.04 way was that you could drag/drop windows between workspaces in  the little Workspace Switcher windows. The 8.04 way is that you drag the window title bar left/right and hop workspaces.

Is there any tweak to restore the 7.04 functionality of being able to drag the mini windows in right in the Workspace Switcher applet? That does not seem to work any longer.

---

### Post by p_quarles on 2008-05-03
Ubuntu 7.10 and 8.04 both have Compiz Fusion special effects enabled by default on supported systems. If you don't want these, you'll just need to return to using Gnome's default window manager, Metacity. This can be done by disabling desktop effects from the Administration menu, or by typing the following in a terminal/command prompt:
```
metacity --replace
```

---

### Post by mdlueck on 2008-05-03
I can not seem to find the correct entry on the System \ Administration menu to disable Compiz Fusion via the GUI.

Under System \ Preferences \ Appearance -> Visual Effects tab, it was already set to None. Not sure if that is controlling the same sort of thing, though.

"metacity --replace" in a term window simply cranks out a bumper crop of "Window manager warning" messages and never completes, so I Ctrl-C killed it.

Indeed it does see it is due to the Compiz Fusion stuff, per this page:
[http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

Suggestions?

---

### Post by mdlueck on 2008-05-04
This blog article had a solution to at least toggle the window manager back to Metacity.

[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)

At least Workspace Switcher is working as desired. Will reboot and see if the  setting holds or if it defaults back to the other Compiz.

---

### Post by mdlueck on 2008-05-05
Perm work around to this issue was to purge compiz* packages from the machine in question and reboot.

---

