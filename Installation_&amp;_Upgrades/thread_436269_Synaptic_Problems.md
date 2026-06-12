---
title: "Synaptic Problems"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by northyj0e on 2007-05-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/113151](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/113151) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently upgraded to feisty, and upon trying to run Add/remove Programs, Synaptic Package Manager Or the update manager (which I believe is another synaptic app) I get this Problem code 

```

E: Dynamic MMap ran out of room
E: Error occurred while processing kdebase-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-proposed_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-amd64_Packages)
```
 Any ideas on what would help/ Anyone else suffered this problem?

---

### Post by zvacet on 2007-05-08
Remove duplicated line in source list and try again.

---

