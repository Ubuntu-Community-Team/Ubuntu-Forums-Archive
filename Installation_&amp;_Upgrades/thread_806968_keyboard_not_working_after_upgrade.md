---
title: "keyboard not working after upgrade"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by farhanali on 2008-05-25
due to power failure my upgrade from gutsy to hardy was a mess...

after a lot of messing around an about over a 100 restarts my computer now seems to be ok. i upgraded using the alternate cd that downloaded. only a few problems remain as follows:


[LIST=1]
[*]now my number pad does not work in x. at login screen when i enter my user id i can enter number and symbols from numkeypad but later wen i am in gnome ... numberkeypad doesnt work. i have checked xorg.conf manually and my layout seems to be ok as follows


```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

```

[*] when i run "sh cdrom/cdromupdate" that i get a message saying 

```
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/g/gimp-help/gimp-help-common_2.4.0-2_all.deb Hash Sum mismatch
```

otherwise everything seems to be running fine. i un-installed the file then i tried  reinstalled the package but i got the same message.[/LIST]

---

