---
title: "Configuration file management on upgrade/install"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by dcollins on 2009-11-13
What goes around comes around, and I'm finally paying for a misspent youth at the hands of Karmic Koala. It is likely I will be doing a fresh install soon and this got me thinking about configuration file management.

Ideally, my data and configuration files would be completely separate to facilitate upgrades. However, many applications put user-configuration files in $HOME right alongside my data. In addition, I have several configuration customizations in /etc/. This poses a challenge at upgrade time, as blindly backing up and restoring these directories often leads to mismatches between the configuration files and apps.

Some solutions I am weighing involve using a CMS to track changes to my configuration files (probably more trouble than it's worth), auto-generating patches of changes made to configuration files, or possibly putting my data in some place other than $HOME and just linking to it. No matter what I think of, I'm left hand-editing configuration files as part of each update/install.

Certainly I am not the only person to confront these issues. Does anyone have some sage advice on how to correctly handle configuration customizations during upgrades? Thanks.

---

