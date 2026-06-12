---
title: "Webmin"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by atl_CCk on 2005-07-08
How can we install webmin on this release of ubuntu? it is not in apt-get or the synaptic list.

---

### Post by geearf on 2005-07-08
i have it in kynaptic.

Did you unmark the right repository in sources.list ?

---

### Post by mingus on 2005-07-08
[QUOTE=atl_CCk]How can we install webmin on this release of ubuntu? it is not in apt-get or the synaptic list.[/QUOTE]

Yes it is.  It is in Hoary universe, and a newer version is in Backports.  Check your /etc/apt/sources.list file.

---

### Post by atl_CCk on 2005-07-11
Found webmin but it wants the cd and ubuntu is not mounting it. I mount it "mount /dev/cdrom /mnt" The cd stays there until i try to use it. Then it just vanishes.

---

### Post by kvidell on 2005-07-11
[QUOTE=atl_CCk]Found webmin but it wants the cd and ubuntu is not mounting it. I mount it "mount /dev/cdrom /mnt" The cd stays there until i try to use it. Then it just vanishes.[/QUOTE]
 edit /etc/apt/sources.list and remove or comment out the line with the cdrom on it (probably the first line of the file.) Then apt-get update and continue on with the install.
- Kev

---

### Post by atl_CCk on 2005-07-11
Got webmin downloaded.  Thanks

---

