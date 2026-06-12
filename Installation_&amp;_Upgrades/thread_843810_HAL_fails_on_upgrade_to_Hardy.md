---
title: "HAL fails on upgrade to Hardy"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by glok_twen on 2008-06-28
hi. i was just upgrading to hardy for the first time. it errored on install and i picked it apart a little and it seems to be stuck with hal. it is having a problem with "...storage1..." which looks to be a name i was using as a raid drive or maybe postgres storage space i may have used at one time. but i can't remember where. any ideas on how to fix this? thanks. gt.

Preparing to replace hal 0.5.9.1-6ubuntu5 (using .../hal_0.5.11~rc2-1ubuntu8.1_i386.deb) ...
 * Stopping Hardware abstraction layer hald                                                                                 [ OK ]
rm: cannot remove `/usr/share/doc/libhal-storage1': Is a directory
Unpacking replacement hal ...
dpkg: error processing /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu8.1_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
 * Starting Hardware abstraction layer hald                                                                                 [ OK ]
Errors were encountered while processing:
 /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu8.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by PmDematagoda on 2008-06-28
Execute:-
```
sudo rm /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu8.1_i386.deb
```
and then try running the upgrade process again.

---

