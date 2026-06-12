---
title: "upgrade to 7.04 fails...."
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by Mia_tech on 2007-04-03
the upgrade notification is showing up, I choose to install all the updates and in the process it shows " a new version is abailable would you like to upgrade", I choose yes but it wont fetch the upgrades, it shows an error trying to contact some repositories like  "http://us.ubuntu.something"

has anyone had that problem when upgrading, same happens when I use ALT-F2 "upgrade-manager"

Thanks

---

### Post by taurus on 2007-04-03
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Then, try it again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Mia_tech on 2007-04-03
I did that and didn't even prompt me for the new version.......

---

### Post by taurus on 2007-04-03
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Mia_tech on 2007-04-03
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude upgrade
```

yes, I removed "us." from the repo and did 

sudo aptitude update
sudo aptitude upgrade

and download lots of update but did upgrade to 7.04

---

### Post by taurus on 2007-04-03
If you want to upgrade from edgy to feisty, you need to replace the word **edgy** with **feisty** in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
When done, run

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by zvacet on 2007-04-04
Here is the easy way to change sources list
```
sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

---

### Post by Mia_tech on 2007-04-04
> **taurus said:**
> If you want to upgrade from edgy to feisty, you need to replace the word **edgy** with **feisty** in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
When done, run

```
sudo aptitude update
sudo aptitude dist-upgrade
```

how about if I'm using kubuntu, would I have to replace everything on the source.list file from ubuntu to kubuntu?

---

### Post by maheshjagadeesan on 2007-04-04
I don't think you'd have to change all occurrences of "ubuntu" to 'kubuntu", since your particular flavour (Kubuntu) would take care of downloading the correct packages.

Happy upgrading!

---

### Post by maheshjagadeesan on 2007-04-04
Sorry about the duplicate post...

---

### Post by Mia_tech on 2007-04-06
after running the upgrade and downloading all the packages, when it was time to reboot , the system got corrupted, hanged during boot up, I had to boot up from a live cd backup all my data and run a clean install, at least upgrade to 7.04 didn't work for me, would like to hear some others experiences here........


thanks

---

