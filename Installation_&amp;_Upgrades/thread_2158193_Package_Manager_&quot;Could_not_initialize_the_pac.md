---
title: "Package Manager: &quot;Could not initialize the package information&quot;"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by raochetan on 2013-06-28
I am getting following error from package manager. This is observed since yesterday after I had updated packages on my system. Any known issue?
______________________________________________________________________________________________________________________________________________________________________________________________________________
Could not initialize the package information


An unresolvable problem occurred while initializing the package information.


Please report this bug against the 'update-manager' package and include the following error message:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/fi.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
______________________________________________________________________________________________________________________________________________________________________________________________________________
 How do I report such errors.

-Chetan

---

### Post by ajgreeny on 2013-06-28
Try renaming the /var/lib/apt/lists folder with ```
sudo mv /var/lib/apt/lists /var/lib/apt/listsbackup
``` then update your sources with ```
sudo apt-get update
``` That should solve the problem, I think.  If not come back again and we can look a bit further.

---

