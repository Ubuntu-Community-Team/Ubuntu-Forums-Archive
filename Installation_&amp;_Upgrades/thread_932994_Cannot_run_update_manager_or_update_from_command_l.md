---
title: "Cannot run update manager or update from command line"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by neilford on 2008-09-29
I was running an update check and I am getting errors...

From the command line I get:
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.



From the update-manager I get this:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

What is happening here?

Thanks.

neilford

---

### Post by neilford on 2008-09-29
I removed an apt-get list file and it worked.

neilford

---

