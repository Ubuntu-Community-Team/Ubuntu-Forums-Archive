---
title: "After upgrade to 11.10 cannot detect monitor configuration and tiny fonts"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by mgmiller on 2011-10-12
After upgrading 32 bit 11.04 to 11.10 I had 2 issues.  

The first was a long list of unreadable lines headed by "Cannot detect monitor configuration".

The second was windows contents all showed the same blank icons for everything and the icon label fonts were tiny and ugly.

How to fix both issues with one change:

GUI instructions:
Open your home directory
press ctrl H to show hidden files and folders
navigate to the .config folder
find the file monitors.xml and rename it monitors.xml.bad

log off and back on

Command line instructions:
First make a backup of the original file:
```
cp ~/.config/monitors.xml monitors.xml.bad
```

Then delete the original:
```
rm ~/.config/monitors.xml
```

Log off and back on.

After a while you can just delete the monitors.xml.bad file if there are no other issues.

---

### Post by paulphillips on 2012-09-13
Thanks!  This worked for me in 12.04

---

