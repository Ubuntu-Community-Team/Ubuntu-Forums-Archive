---
title: "Nord VPN"
date: 2021-10-06
forum: Installation &amp; Upgrades
---

### Post by camprd123 on 2021-10-06
When entering this command  taken from the official NordVPN website in Terminal
sh <(wget -qO - [https://downloads.nordcdn.com/apps/linux/install.sh)s](https://downloads.nordcdn.com/apps/linux/install.sh)s)
I get the following errors
 
  E: The repository 'https://repo.nordvpn.com/deb/nordvpn/debian stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

**Any help appreciated**

---

### Post by MAFoElffen on 2021-10-06
You can do this....
```

sudo apt-get update --allow-insecure-repositories

```
Which now that you added that repository, you will have to that flag always, until you remove that as a repo. Or until they add a release file.

That gets you updated, with any changes they make to that repo.... otherwise, nordvpn also has .deb packages for download, but that would mean everything would be done manually with dpkg...

or you can edit that line in it's pertinant sources list file and add "[trusted=yes]" after the leading word "deb"...

---

### Post by ActionParsnip on 2021-10-06
Did the script launch OK?

---

