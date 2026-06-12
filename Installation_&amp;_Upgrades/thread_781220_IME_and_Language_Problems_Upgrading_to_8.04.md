---
title: "IME and Language Problems Upgrading to 8.04"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by riutaro on 2008-05-04
Hello forum,

I have two problems in my keyboard after upgrading to 8.04 <Hardy Heron>.  I would appreciate if anyone can help me solve the issues.

First, I cannot start SCIM input method from the keyboard any more.  The shortcut to bring up SCIM on my Japanese 106-key model is: <hankaku/zenkaku> key (to the left of <1>).  Interestingly, I can toggle between IMEs by a keyboard shortcut once SCIM is activated and the default IME is in function.

Second, my keyboard cannot switch between keyboards any more.  I have a Hebrew keyboard installed side by side with an English keyboard but now I cannot toggle the Hebrew one.  (There may be a way to select Hebrew from control panel or somewhere which I am ignorant of.  Any info about this is also appreciated ;-) )

Probably related to the two symptoms above is an error message that pops up at computer startups.

[HTML]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/HTML]

So the two results are below:
**xprop -root | grep XKB**
```
foo@bar:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "jp106", "jp,jp", "latin,", "grp:alt_shift_toggle,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "xorg", "jp106", "jp,jp", "latin,", "grp:alt_shift_toggle,grp_led:scroll"
```

**gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
```
foo@bar:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [jp	latin,jp	,il]
 model = 
 overrideSettings = true
 options = []
```

---

