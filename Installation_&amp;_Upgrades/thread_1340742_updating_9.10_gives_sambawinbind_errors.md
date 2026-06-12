---
title: "updating 9.10 gives samba/winbind errors"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by jmarks on 2009-11-28
Dear All,
I upgraded 64-bit 9.04 to 9.10 without issues. When I update 9.10, however, I get the following errors:
```
errors were encountered while processing:
samba 
winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. trying to recover
setting up samba (2:3.4.0-3ubuntu5.1) ...
 *Starting Samba daemons
    ...fail!
invoke-rc.dL initscript samba, action "start" failed.
dpkg: error processing samba (--configure);
  subprocess installed post-installation script returned error exit status 1
Setting up winbind (2:3.4.0-3ubuntu5.1) ...
  *Starting the Winbind daemon winbind
   ...fail!
invoke-rc.d: initscript.winbind, action "start" failed.
dpkg: error processing winbind (--configure);
  subprocess installed post-installation script returned error exit status 1
Errors were encountered whle processing:
    samba
    winbind
```How do I begin to sort out these errors? is this a problem with configuration files or something large?
thanks for any and all suggestions.

---

