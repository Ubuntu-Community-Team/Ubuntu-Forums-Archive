---
title: "aee not working after upgrade"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by arloth on 2010-10-18
I'm not entirely sure this is the proper place for it, but aee doesn't work anymore after upgrading to 10.10.  In both gnome terminal & konsole it says "sorry, unable to use this terminal type for screen editing" and exits.  It does this remotely even through ssh sessions.

I know aee isn't exactly a new program or anything but what gives?  It's a terminal window, how could a console based text editor go wrong. :(

---

### Post by fxmulder on 2010-10-18
try this:
ln -s /lib/terminfo /usr/lib/terminfo

it looks like the path that aee is looking for terminfo doesn't exist.

---

### Post by arloth on 2010-10-19
Making that symlink got aee running again.

The window border highlighting wasn't working correctly anymore, but that's an easy enough fix with the -n option and saving the configuration.

---

