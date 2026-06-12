---
title: "update manager bug"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by capateke on 2014-01-31
When I tried to use Update Manager I received error message "Could not initialise the package information. Unresolvable problem while initialising package information. E: Problem parsing dependency Depends, E: Error occurred while processing openjdk-6-jre-headless (New Version 2), E: Problem with MergeList/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages,E: The package lists or status file could not be parsed or opened." Any suggestions?

---

### Post by Bashing-om on 2014-01-31
capateke; Hi !


The first thing to attempt is just to delete the package lists as they are likely in an inconsistent state:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial

```
And then rebuild the index files:
```

sudo apt-get update

```

Now see if the packages will update:
```

sudo apt-get upgrade

```

Maybe the first shot will be on-target.
else:
These will provide info to continue troubleshooting.

[INDENT][INDENT]checks and balances
[/INDENT][/INDENT]

---

### Post by capateke on 2014-02-01
Bingo! Thanks for your help Bashing-om:KS

---

### Post by Bashing-om on 2014-02-01
capateke; Great !

That warm fuzzy feeling of contentment in a stable system ->

[INDENT][INDENT]can't be beat
[/INDENT][/INDENT]

---

