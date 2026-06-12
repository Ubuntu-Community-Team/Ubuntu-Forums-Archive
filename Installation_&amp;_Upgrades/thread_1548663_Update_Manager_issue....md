---
title: "Update Manager issue..."
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2010-08-08
Hi all,

Received this random error from the update manager today.

Would appreciate any help in trying to track down what the problem is.

Thanks,
Matt

```

E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

---

### Post by mattlach on 2010-08-08
I rebooted and ran update manager again, got more details:

```

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_restricted_binary-amd64_Packages (1), E:The package lists or status file could not be parsed or opened.'
```

Any help would be appreciated!

---

### Post by mattlach on 2010-08-11
Help?  Please?

---

### Post by dino99 on 2010-08-12
why not using synaptic directly ?

---

### Post by mattlach on 2010-08-18
I solved this by doing the following:

```

sudo aptitude update
sudo aptitude dist-upgrade
```

---

