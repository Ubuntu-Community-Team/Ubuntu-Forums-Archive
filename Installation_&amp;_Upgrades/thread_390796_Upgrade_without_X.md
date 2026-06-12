---
title: "Upgrade without X"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Hevoos on 2007-03-22
I've tried to upgrade Dapper to edgy with the gksu "update-manager -c" command and it went on fine. But as I was going to sleep and didn't want to listen to my old computer I canceled it, which wasn't so smart. Now it complains about X not working. I've tried the gksu "update-manager -c" command, but it needs X to work. Is there another easy way to upgrade?

I don't want to change the sources.list manually! ;)

---

### Post by Kateikyoushi on 2007-03-22
I do not think there might be another way around than editing the sources.list but it might not be necessary check whether it was already changed by time time you cancelled the upgrade.

> cat /etc/apt/sources.list

If it is upgraded then you can continue with the following command.

> sudo aptitude update
sudo aptitude dist-upgrade

---

### Post by Hevoos on 2007-03-22
For some reason it can't connect to the server, but it has changed the sources.list. Maybe something went wrong when it did that?

---

### Post by zvacet on 2007-03-22
Look in etc/network/interfaces and correct if it is something wrong there.

---

### Post by Kateikyoushi on 2007-03-22
Could try to change to a local repository mirror by editing the sources.list, or change the https to ftp in the sources.list.

---

