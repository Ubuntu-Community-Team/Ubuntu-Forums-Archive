---
title: "formatted list of available upgrades at commandline?"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by jillmashley on 2008-08-18
I am working on scripting automatic updates from an in-house debian repository. sources.list of the machines-to-update are pointed only at our repository. So I know that I want to install all available upgrades. However, before initiating the installation I would nevertheless like to determine in my update script if any/what number of upgrades and new required dependencies would be upgraded/installed if I ran apt-get upgrade.

What I know I can do is run the following sequence of commands
```
apt-get clean
apt-get update
apt-get -s upgrade
```
I could parse the output of the last command, particularly the line that reads
> 2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But it seems like there ought to be a command that will simply list the number or names of available upgrades and/or new packages to install? Is there something like this available that I am not seeing? perhaps in dpkg or another utility?

Many thanks for any suggestions or ideas.

---

