---
title: "Update Manager Error"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2007-03-17
When the update manager finishes here is the error it gives.

E: virtualbox: subprocess post-installation script returned error exit status 1


Dont know if the updates completed successfully or not. What can I do?

Thanks,

---

### Post by kevinlyfellow on 2007-03-17
go to your terminal and type

```
sudo aptitude update
sudo aptitude upgrade
```

See if that gives you an error.

It seems like only the package named virtualbox was not updated.

---

### Post by dontgetshocked on 2007-03-17
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



_____________________________________________
W: You may want to run apt-get update to correct these problems
david@dave-desktop:~$ apt-get update

---

### Post by kevinlyfellow on 2007-03-17
I think there is just one package that isn't installing.  You can go to synaptic and choose "custom filters" at the bottom left and in the list click on upgradable to see whats not installing.  Chances are there is nothing that you can do about it until the package is fixed (except  for letting the people who run the repository know).

---

### Post by Kateikyoushi on 2007-03-17
I would try to reinstall the package if necessary redownload it manually and run the following command on the package.
```
sudo dpkg -i packagename.deb
```

---

### Post by dontgetshocked on 2007-03-18
Thanks, issue is resolved by editing the init.d/package file and then un-installing it.

---

