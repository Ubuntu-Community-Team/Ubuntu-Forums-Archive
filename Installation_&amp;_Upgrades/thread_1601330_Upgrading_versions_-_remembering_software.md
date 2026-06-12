---
title: "Upgrading versions - remembering software"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by TheSiberian on 2010-10-20
Normally when I move from one Linux version to another, I prefer to do a fresh installation. This is from experience of minor incompatibilities between software & Linux versions when upgrading.

Is there a way to list any non-standard software that I have installed on the previous version? It would be good to include anything I have installed directly from websites.

---

### Post by cariboo on 2010-10-21
It would help if you told us what distribution you were using, as the method to list installed packages varies between an rpm based distro, and one based on debs

---

### Post by Toz on 2010-10-21
> dpkg --get-selections
will list all installed debian DEBs.

As for the other software, it depends on how you are installing them. Personally, I keep a running log in a file of all non-standard installations/configurations that I do in case I need to redo them.

---

