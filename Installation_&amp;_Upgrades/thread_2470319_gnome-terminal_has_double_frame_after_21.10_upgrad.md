---
title: "gnome-terminal has double frame after 21.10 upgrade"
date: 2021-12-25
forum: Installation &amp; Upgrades
---

### Post by kmand on 2021-12-25
I just upgraded 21.04->21.10, I run gnome and now I have two "frames". One with just the directorytitle, and the second with the directory title, the "+" on the left and the find and settings icons on the right. That second "frame" is all I am used to getting.  (other than tab bar (if applicable) and the menu bar (if enabled).

I'm also used to getting an always present app bar  vertically on the left. Now I'm getting a horizontal one only when I hit the "diamond" key.

Have I missed some master setting? This is on my desktop. I have a laptop that I did a previous update to 21.10 that acts as I expected.

This what the 21.10 laptop shows

[IMG]http://cs.emory.edu/~km/laptop-gnome-terminal.png[/IMG]

This is what the 21.10 desktop shows

[IMG]http://cs.emory.edu/~km/desktop-gnome-terminal.png[/IMG]

I can get rid of the extra bar by using the dconf-editor to set org.gnome.Terminal.Legacy.Settings headerbar false giving

[IMG]http://cs.emory.edu/~km/legacy.png[/IMG]

Which is what the 18.04 terminals looked like, but thats not what I want. I want the "+" in the single header. I don't see any setting in the terminal itself that gets me what the laptop is showing.


I

---

### Post by grahammechanical on 2021-12-25
We can change the way Gnome Terminal functions. In the top panel you should see the "hamburger" icon. Three horizontal lines. Clicking that will open some settings that we can change. I really do not understand what you are talking about but if you select General>Open New Terminals in: and from the drop down menu select Windows instead of Tab you might get the behavior you desire.

You could also compare the settings from Gnome terminal between the desktop machine and the laptop machine to see what is different.

Regards

---

### Post by MAFoElffen on 2021-12-28
It looks like they are using different themes...

You could check that between your desktop and laptop using:
```

gsettings get org.gnome.desktop.interface gtk-theme

```

---

