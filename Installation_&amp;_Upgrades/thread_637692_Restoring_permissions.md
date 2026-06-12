---
title: "Restoring permissions?"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by dannysauer on 2007-12-11
So, I tried setting up a NFS root system using OpenFiler.  It worked fine, but when I made what appeared to be an innocent change in the webGUI, it recursively reset the ownership and permissions on all files in the directory.  Essentially, I'm left with the results of "chown -R nobody:nogroup /" and a "chmod 770 -R /".  As one might guess, this is pretty aggravating (and a bit of a bug in the OpenFiler interface that it didn't mention the irreversible results it would cause, which is one reason that I'll no longer be using that system, just using Ubuntu like a normal person). :)

Anyway, I can fix most of the non-package'd files manually.  I suppose I could probably fix them all, for that matter.  But I'd like to have a way to automatically do the bulk of things.  Does dpkg have a way to list the install-time permissions for package-owned files?  I'm thinking of something like RPM's "rpm --verify" mode.  I'm just not as familiar with dpkg as I'd like to be, despite over a decade of Linux administration... ;)

Thanks.

---

