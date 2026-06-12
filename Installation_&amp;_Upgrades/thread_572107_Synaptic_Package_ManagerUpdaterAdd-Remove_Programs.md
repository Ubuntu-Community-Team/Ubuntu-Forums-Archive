---
title: "Synaptic Package Manager/Updater/Add-Remove Programs"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by sekinto on 2007-10-10
[I'm running Ubuntu Feisty Fawn 7.04]
Synaptic Package Manager, Updater, and Add/Remove Programs all crash while they are loading.



Error Messages:


-----Synaptic Package Manager-----
E: Malformed 2nd word in the Status line
E: Error occurred while processing language-pack-hi (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


-----Updater-----
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed 2nd word in the Status line, E:Error occurred while processing language-pack-hi (UsePackage1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'


-----Add/Remove Programs-----
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.



What I've tried:
Totally replacing my sources.list file.
sudo apt-get update (I get an error)

---

### Post by JurB on 2007-10-10
You could report a bug at [Launchpad]("https://launchpad.net/ubuntu")

---

