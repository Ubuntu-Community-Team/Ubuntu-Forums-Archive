---
title: "password problem"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by mimsmall on 2007-09-28
How do I go about changing the su password?

---

### Post by jgoguen on 2007-09-28
'su' is used to switch to a different user, by default root.  Since root is disabled on Ubuntu, you should use 'sudo' followed by the command you want to run.

If you really want to enable root (and thus allow the use of the 'su' command) open a Terminal (Applications -> Accessories -> Terminal) and type this command:
```
sudo passwd root
```
Give your password when prompted, then a new password for root, the same password again, and then root is enabled.  This is a Bad Thing, however, and if you really need a root shell you should just use this command instead:
```
sudo -s -H
```

---

