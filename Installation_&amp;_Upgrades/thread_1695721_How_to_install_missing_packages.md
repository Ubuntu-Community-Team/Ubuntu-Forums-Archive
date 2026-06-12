---
title: "How to install missing packages ?"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by chinnaraaju on 2011-02-26
Hi 

I was trying to install google chrome linux version on to my ubuntu system(8.04). During this operation, while correcting the dependencies of libraries , unknowingly i gave the answer 'Y' to one of the question.

As a result, it uninstalled many main packages like Nautilus Desktop,firefox and many others. Now i am able to login to desktop but the desktop is not fully loading with all panels and icos. only wall paper is getting displayed.

i am able to work in FailSafe mode terminal. Please let me know the command to give in terminal to install all missing important packages of Ubuntu 8.04 and fix all the broken and dependency issues.

Thanks for your support.
-Chinnaraj.

---

### Post by chinnaraaju on 2011-02-27
Experts-

Do you have any clue on the command to use to installing the missing packages ?

Thanks
-Chinnaraj.

---

### Post by Frogs Hair on 2011-02-27
Without knowing what was removed that caused all those packages to removed all at once . it's to say what  command would be needed.

Have you attempted so reinstall the packages you know to be missing ?  I don't know what terminal you are looking at  so I don't know if sudo apt-get install package name is an option. Example:  sudo apt-get install nautilus

---

### Post by sikander3786 on 2011-02-27
Just try to re-install the ubuntu-dekstop package. Before trying to do so, search and fix any broken packages. Follow these commands, one-by-one.

```
sudo apt-get update && sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by chinnaraaju on 2011-02-27
Thanks a lot sikander3786 !!!

Your three commands did all the magic...now my ubuntu desktop is up and running... 

Regards,
Chinnaraj.

---

