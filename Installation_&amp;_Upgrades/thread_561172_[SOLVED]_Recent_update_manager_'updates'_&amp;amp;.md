---
title: "[SOLVED] Recent update manager 'updates' &amp;amp; header updates breaks Gnome &amp;amp; Metacity"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Scruffynerf on 2007-09-27
Much weirdness here. Help needed.

Just updated via the update notification that the update manager, and the linux headers for 2.6.20-16.31 were available for update.

So I update.

Logging back in, there is much oddness happening.

1) All of a sudden, I have a 'Computer' icon on my desktop, and a 'Garbage Bin' icon.
2) The fonts on all the desktop icons are significantly larger than what I set them to.
3) My terminal font size grew by 2 orders of magnatude. It's huge.
3) Gnome-Panel - my Active window list will not display. Most of my settings for the gnome panel are fine, just the window manager will not work
4) I run Metacity for my WM. They look odd. The controls for the windows (close, minimize etc) are all indented about an inch from the edge.
5) Opening the 'System'-'Preferences'-'Theme' results in the error message: 
```
The default theme schemas could not be found on your system. This means 
that you probably don't have metacity installed or that gconf is 
configured incorrectly
```
6) There are no icons in the menus at all.

Found this bug report ([https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150]("https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150"), but it's for Dapper. This is a Feisty install. Other than that, it's pretty much what happened.

What's going on?

Edit: Solution in bug report. Need to re-register gconf schemas. Command given is 
```
sudo gconf-schemas --register usr/share/gconf/schemas/*.schemas

```

Thanks

---

