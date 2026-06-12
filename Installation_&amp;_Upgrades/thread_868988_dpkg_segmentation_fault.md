---
title: "dpkg segmentation fault"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2008-07-24
Something went wrong during a reinstall of konqueror.  Now when I try to update, install, or remove anything (with aptitude, apt-get, adept or synaptic) I get the message "dpkg was interrupted, you must manually run 'dpkg --configure -a to correct the problem".

But when I run "dpkg --configure -a" (or dpkg-reconfigure konqueror) it crashes the entire system (segmentation fault).

It does this even if I boot in recovery mode & run it in terminal mode.

Is there some file I can delete to make dpkg "forget" that it was interrupted & let me replace kubuntu-desktop with gnome?

---

### Post by ajgreeny on 2008-07-24
Use ```
sudo dpkg --configure -a
``` and it might just work.  dpkg will only run as root, hence the *sudo* in front of the command.

---

### Post by bad_chicken on 2008-07-24
darn. the same thing is happening to me...

every time i run 'sudo dpkg --configure -a' the computer seems to get stuck with the line 'Running depmod.'

can anyone tell me what this means?
I'm really lost as to what to do...

---

