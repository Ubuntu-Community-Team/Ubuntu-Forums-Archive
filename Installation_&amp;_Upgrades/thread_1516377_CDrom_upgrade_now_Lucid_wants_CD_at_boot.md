---
title: "CDrom upgrade now Lucid wants CD at boot"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by ghetto2ivy on 2010-06-23
I did a cdrom upgrade with a cd image mounted on a temp directory. Now Luicd wants the temp directory to be mounted at boot. The problem is that there is no mention of the temp directory in fstab -- so where is lucid getting the idea that the directory should be mounted?

Is there a new place for fstab (/etc/fstab) or has it been replaced?

---

### Post by ghetto2ivy on 2010-06-23
Never mind -- found it. Apparently it was in fstab, just in a commented out section, but that one somehow was not commented out.

---

