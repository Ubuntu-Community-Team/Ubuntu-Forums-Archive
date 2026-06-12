---
title: "How to completely remove Eclipse"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by PkgMafaw on 2012-09-18
I'm trying to completely remove Eclipse and start fresh because when I tried to upgrade I get an error that doesn't allow software to install. There is an Eclipse directory in my /usr/lib directory and I would like to get rid of as well so there are hopefully no traces of an old version with plugins and such to interfere. When the new software tries to remove old files there is an error that points to this directory that says it failed in removing the older files. What's the best way to go about it? Thanks for any help.

---

### Post by gardnan on 2012-09-18
Have you looked at apt-get purge? It should remove a package, as well as any configuration. Also, be sure to do an autoremove to remove any dangling dependencies afterwards.

---

### Post by PkgMafaw on 2012-09-18
> **gardnan said:**
> Have you looked at apt-get purge? It should remove a package, as well as any configuration. Also, be sure to do an autoremove to remove any dangling dependencies afterwards.

I've done the apt-get purge and no more removals than were already done. How do I do an autoremove?

---

### Post by cortman on 2012-09-18
To autoremove, run

```
sudo apt-get autoremove
```

If you think there is still eclipsian residue on your system, you can run

```
dpkg -L eclipse
```

to list all files related to the eclipse package. Once you've looked at the list to make sure it's innocuous, you can either pipe the whole list to rm to be deleted, or manually delete each one.

---

### Post by QIII on 2012-09-18
Remember that there is also probably a hidden .exclipse directory in your home directory.  It probably holds user-specific configuration settings that you may or may not want when you reinstall.

---

### Post by PkgMafaw on 2012-09-18
> **cortman said:**
> To autoremove, run

```
sudo apt-get autoremove
```

If you think there is still eclipsian residue on your system, you can run

```
dpkg -L eclipse
```

to list all files related to the eclipse package. Once you've looked at the list to make sure it's innocuous, you can either pipe the whole list to rm to be deleted, or manually delete each one.

Is it possible to remove a directory and it's contents without having to empty it first?

---

### Post by PkgMafaw on 2012-09-18
> **QIII said:**
> Remember that there is also probably a hidden .exclipse directory in your home directory.  It probably holds user-specific configuration settings that you may or may not want when you reinstall.

Yes that's what I'm trying to get rid of but I'm trying to find a faster way than deleting each file and directory. Do you know a way to do that?

---

### Post by gardnan on 2012-09-19
To remove a directory recursively (e.g remove a directory and all of its elements), you can use the -r switch to the rm command. In other words:

```
rm -r *directory*
```

However, you should use this command CAUTIOUSLY, as deleting whole directories off your system could be dangerous.

---

### Post by cortman on 2012-09-19
Well, you can run

```
dpkg -L | xargs rm
```

But since that will delete the entire return of dpkg -L I would be careful and check the output first.

---

