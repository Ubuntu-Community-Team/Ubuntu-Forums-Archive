---
title: "Where do things get installed?"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by DesiDude on 2007-11-29
When we do a apt-get <something> then where is the installation file stored? Also, where is it installed? I would like to keep backups of all packages that I download so that I can use them later offline in case I need to reinstall.

---

### Post by Soarer on 2007-11-29
In Synaptic Package manager, if you right click on an installed item, choose 'Properties' and then the 'Installed Files' tab, it will tell you where all of the files associated with that item are on your machine.

---

### Post by meatpan on 2007-11-29
> **DesiDude said:**
>  I would like to keep backups of all packages that I download so that I can use them later offline in case I need to reinstall.

If you want to script some sort of automatic archival tool, consider using the 'dpkg' command.

To list the full contents of <package-name>,  run 'dpkg -L < package-name>'.  The output is a file summary that is relatively easy to parse.

---

### Post by logos34 on 2007-11-29
Ubuntu by default keeps all the downloaded .deb pkgs in /var/cache/apt/archives.  The list and location of the files from each installed package can be found using the methods described above.  If you want to keep a safe copy of the .debs for reinstall in case your system gets borked, use AptOnCD (burn them to cd/dvd)

---

