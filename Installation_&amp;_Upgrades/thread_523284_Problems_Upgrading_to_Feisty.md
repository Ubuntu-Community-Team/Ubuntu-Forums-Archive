---
title: "Problems Upgrading to Feisty"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by meanburrito920 on 2007-08-11
I have been running Edgy for a while now and finally decided to Upgrade to Feisty. However, when I go to update through update manager, I get an error message that says Error during Update:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
```

It also says that the problem probably is with my network connection, but I have checked and everything seems to be running properly, it just wont upgrade. I burned a CD of Feisty also. Is there a way to upgrade from CD without doing a clean install?

---

### Post by Pumalite on 2007-08-11
Bad idea. It's always best to do a clean install. You could save your /home data and do a clean install. There is also a way to do a clean install saving the /home partition, but the details escape me at the moment. You could do a Search: 'Install saving /home'.

---

### Post by meanburrito920 on 2007-08-11
would this preserve all my programs though?

---

### Post by Pumalite on 2007-08-11
Installing saving /home partition? It should, but /home has to be in a separate partition.

---

### Post by zvacet on 2007-08-12
```
gksudo gedit /etc/apt/sorces.list
```

Put # sign in front of that two lines.You can do the same with all unofficial repos you have in your sources list.Save the file and 

```
sudo aptitude update
```

After that you should be able to upgrade with update manager.When you are done with upgrade 

```
gksudo gedit /etc/apt/sorces.list
```

and remove all # you put before.
```
sudo aptitude update &&  sudo aptitude upgrade
```

Why do you posted same question twice?

---

