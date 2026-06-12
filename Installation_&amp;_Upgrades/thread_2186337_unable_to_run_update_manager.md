---
title: "unable to run update manager"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by p-nasa on 2013-11-06
Hi All,

I have v 12.04 installed. When I am running update manager the following error message is appearing:
[B]
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

Could anyone please suggest the solution.

best regards,
parveen

---

### Post by Bashing-om on 2013-11-06
p-nasa; Hi ! Welcome to the forum.

Try this and advise the results:
Terminal codes:
```

sudo rm /var/lib/apt/lists/* -vf
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Where it is suspected the index files have become corrupted (rm), "mkdir" puts a directory back inplace, "update" rebuilds the indexes, and "upgrade" updates the installed packages.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by p-nasa on 2013-11-07
Dear Friend,

It solved the problem!!
Thanks for the quick help.

best regards,
parveen

---

### Post by bapoumba on 2013-11-07
@ p-nasa : please mark your thread as solved (in the "Thread Tools" menu), thanks.

---

