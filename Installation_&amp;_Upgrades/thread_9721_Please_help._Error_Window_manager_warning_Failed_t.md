---
title: "Please help. Error: Window manager warning: Failed to read theme from..."
date: 2004-12-31
forum: Installation &amp; Upgrades
---

### Post by cllow on 2004-12-31
Hi everyone,

I have installed ubuntu in my laptop with minimum options via "custom" mode. I have followed the help in this page: 

[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

to setup my x-window stuff. But instead of icewm, I chose to install metacity. Everything goes on smoothly till I run startx. System stops at the grey screen with a X in the middle if it.

When I vi into .xsession.error file in my home dir, this is what I get:

Xsession: X session start for "my id" at "the date"
Window manager warning: Failed to read theme from file /usr/share/themes/Human/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/Human/metacity-1/metacity-theme-1.xml': No such file or directory
Window manager warning: Failed to load theme "Human": Failed to open file '/usr/share/themes/Human/metacity-1/metacity-theme-1.xml': No such file or directory

When I checked, /usr/share/themes/Human directory is missing.

So, how/where do I change the default theme that is in the /usr/share/themes directory?

Thanks.

---

