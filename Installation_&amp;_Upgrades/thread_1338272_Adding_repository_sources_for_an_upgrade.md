---
title: "Adding repository sources for an upgrade"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Ploink on 2009-11-26
I am using Intrepid, and have been thinking of upgrading to Jaunty for a while now. My University limits my daily uploads/downloads, but also has an internal mirror repo, which I use for updates. 
While upgrading my distro using upgrade manager, I've noticed that there is no option to provide alternate repositories/mirrors to download the required packages from. 
I'd like to know where upgrade manager downloads the packages from by default - does it use the mirror I've added in sources.list, or does it download from the default global repos?
I've always thought it did the latter, considering sources.list specifies the list of repos for the *current* distro, while during the upgrade, upgrade manager would need the packages for the distro it is upgrading to. If this is the case, how do I specify the location to download packages for an upgrade?

---

### Post by MelDJ on 2009-11-26
got to system-admin-software sources and choose your server. to add sources, add them under the other software tab

---

### Post by slakkie on 2009-11-26
You could do this via several ways, the update-manager/do-release-upgrade scripts will convert your sources.list for you.

If you upgrade without these scripts you would need to do it manually, see [https://help.ubuntu.com/community/Upgrades#The%20Debian%20way%20of%20upgrading](https://help.ubuntu.com/community/Upgrades#The%20Debian%20way%20of%20upgrading)

---

