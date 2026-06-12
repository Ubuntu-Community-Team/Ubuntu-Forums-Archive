---
title: "Updates failing - invalid package name `libgnomecanvas2-0$' in gnome-settings-daemon"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by rayjohnterrill@gmail.com on 2008-09-13
I'm currently unable to apply updates to my system, as I receive the following message:

```
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2508 package `gnome-settings-daemon':
 `Depends' field, invalid package name `libgnomecanvas2-0$': character `$' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Any help would be appreciated.
-Ray

---

### Post by Partyboi2 on 2008-09-13
Looks like you need to remove the $ from libgnomecanvas2-0$ in your /var/lib/dpkg/status file
Press Alt+F2 and type
```
gksudo gedit /var/lib/dpkg/status
``` when it has opened the file go to "Search" then "go to line" and enter 2508 then look for  libgnomecanvas2-0$ and remove the $ from the end of it. Then save the changes.
Then try upgrading again.

---

### Post by rayjohnterrill@gmail.com on 2008-09-13
Much apprec, I removed the '$' (as well as another rogue ':' in the file, and was able to update).  I figured it would be something simple, but wasn't sure where to go to resolve it.

Any idea how that happened (did it happen for everyone, or something specific that I had done)?  Thanks again for the quick response; I love the Ubuntu community.

-Ray

---

### Post by Partyboi2 on 2008-09-13
> Any idea how that happened (did it happen for everyone, or something specific that I had done)? 
Wouldn't have a clue, I haven't come across anyone else having the problem.

---

