---
title: "Visual assistance always in top right corner."
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-08
Anyone else see the blue visual assistance panel applet in the top right corner. Anyone know how to get rid of it?

---

### Post by exploder on 2009-10-08
I saw it too and still have not figured out how to get rid of it...

---

### Post by joey-elijah on 2009-10-08
> **exploder said:**
> I saw it too and still have not figured out how to get rid of it...

try just un-ticking 'Accessibility features can be toggled with keyboard shortcuts' in keyboard > Accessibility. 

If that doesn't work it may be cos of the GDM so.. 

gksudo gedit /var/lib/gdm/.gconf.mandatory/%gconf-tree.xml

replace: -

<dir name="accessibility">
<dir name="keyboard">
<entry name="enable" mtime="1253866193" type="bool" value="true"/>
</dir>
</dir>

with: -

<!--dir name="accessibility">
<dir name="keyboard">
<entry name="enable" mtime="1253866193" type="bool" value="true"/>
</dir>
</dir-->

Save and close.

gksudo -u gdm dbus-launch gnome-control-center

Go to keyboard > Accessibility and uncheck 'Accessibility features can be toggled with keyboard shortcuts'. Log out and back in if needed!

---

### Post by Sashin on 2009-10-08
Thanks, it worked perfectly. Didn't even need to log out/log in.

---

### Post by joey-elijah on 2009-10-08
> **Sashin said:**
> Thanks, it worked perfectly. Didn't even need to log out/log in.

No problem! It bugged the HELL outta me for ages.

---

