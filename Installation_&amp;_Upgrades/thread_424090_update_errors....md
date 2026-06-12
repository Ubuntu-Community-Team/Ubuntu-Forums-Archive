---
title: "update errors..."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by peterbug on 2007-04-26
ok so whenever I update any software I get the following errors:

Errors were encountered while processing:
msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Try to recover:
Setting pu msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: usr/lib/X11/fonts/truetype does not exist or is not a directory 


and


=> ´./andale32.exe'
Resolving switch.dl.sourceforge.net... 32.1.6.32
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out
Giving up

Andale32.exe: No such file or directory




can anyone help me?

---

### Post by zvacet on 2007-04-26
```
sudo aptitude install msttcorefonts
```

---

### Post by peterbug on 2007-04-26
never helped the same errors came up.

---

