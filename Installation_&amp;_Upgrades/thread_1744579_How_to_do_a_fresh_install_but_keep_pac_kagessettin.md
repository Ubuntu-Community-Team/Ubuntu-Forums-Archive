---
title: "How to do a fresh install but keep pac kages/settings/configurations &amp; data?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Elludium_Q-36 on 2011-04-30
I have a box that is offline and I want to keep my configurations/data/settings/browser info, etc. so there's no need to download and do everything over.

The reason I need to do a fresh install is that I added 10.04 packages from a CD to an 8.04 system and it now won't take alternative CD upgrades with the cdromupgrade script.

The packages refuse to downgrade via the "force version" option.

I have:

*backed up the /home/ and /etc/ directories.

*Backed up my keys with command "sudo apt-key exportall > ~/repositories.key"

*Backed up "sources.list" file and "sources.list.d" folder.

I'm told I can back up the "archives" folder so I don't have to redownload all the packages.

It didn't work for me but I've read I can back up program/package configurations with commands: "dpkg --get-selections "*" >myselections" and "debconf-get-selections > debconfsel.txt"

How do I back up the Firefox profile directories.

I have been told about Keryx keryxproject.org and Remastersys but I think I need to do it old school this time.

Thanks in advance

---

### Post by dino99 on 2011-04-30
if you have a /home partition then nothing no worry about backup and else

---

### Post by Elludium_Q-36 on 2011-04-30
Yeah, i wrote that i backed up the /home/ directory, along with the /etc/ directory.  I need to back up the packages that install **after** the core system

---

