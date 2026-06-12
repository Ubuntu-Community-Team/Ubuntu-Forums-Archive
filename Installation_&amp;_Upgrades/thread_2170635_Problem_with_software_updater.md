---
title: "Problem with software updater"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by vickysodhi67 on 2013-08-27
while runninng software updater it shows an Error opening the cache(E:Encountered a section with no package: header, E:problem with Mergelist/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_translationen,E:The package lists or status file could not be parsed or opened.And the software center is also nit working, please help me....:(

---

### Post by 1/0 on 2013-08-27
Hi and welcome to ubuntuforums! Have you tried the following 2 commands from a terminal?

```

sudo dpkg --configure -a
sudo apt-get -f install

```

---

### Post by grahammechanical on 2013-08-27
If the above recommeded commands do not work you can try this

```
sudo rm /var/lib/apt/lists/* -rf
```
```
sudo apt-get update
```

The first command removes/deletes all the sources lists in the list folder. The second command replaces the lists with new ones. I have had issues with i8n_translation before and those commands fixed the problem and also the error of no header on a package file. At the moment any utility that makes use of the package lists, Update Manager and Software Centre, cannot work because there is something wrong with one of the lists.

Regards.

---

### Post by vickysodhi67 on 2013-09-12
thanx for ur support..

---

