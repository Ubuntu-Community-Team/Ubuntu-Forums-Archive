---
title: "Cleaning up Hardy Installation"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by theravenproject on 2008-07-05
I installed Hardy about a month ago (Moving up from Dapper but on a Brand new system) and my os feels bloated and filthy.  How can I go about doing a general cleanup of unneeded programs/files temp internet files etc..I am not very good with nautilus but okay with terminal..are their any apps that help do any general "Clean-up" trim down?  How can I accomplish this without getting rid of anything important?

---

### Post by Tanker Bob on 2008-07-05
A good first step would be to go through Adept or KPackage and uninstall stuff that you no longer use. After completing that, execute the following from the shell:

```
sudo apt-get autoremove
```

That should sweep up most of the misc pieces laying around. 

Another useful program is 'GtkOrphan' which you can install from the repositories. It scours your system for orphaned packages and offers to remove them for you. You can read the details on each orphan before deleting just to be sure.

---

