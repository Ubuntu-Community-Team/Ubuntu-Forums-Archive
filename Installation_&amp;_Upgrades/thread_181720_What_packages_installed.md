---
title: "What packages installed"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by endfx on 2006-05-24
Is there a way to find out what packages have been installed on an Ubuntu system.
I'm really just trying to find out if an ati driver was installed during the intial setup, but I figure knowing howto see what packages have been installed in general would be handy.

I'm thinking this may have something to do with an "apt" type command but I couldn't find it in any of the man pages.

Thanks.

---

### Post by aysiu on 2006-05-24
Can't you just check in System > Administration > Synaptic Package Manager or KMenu > System > Adept?

---

### Post by Dr. Nick on 2006-05-24
If you are in a gui then run synaptic and one of the filters on the side will show all intalled packages. I imagine apt can be used aswell, im just not sure of the command. maybe someone else can post it

---

### Post by geek.de.nz on 2006-09-21
I had this question for ages too. After playing around with ara 
('apt-get install ara'), I found that all (installed?) packages are in a file on debian based systems.

So, the following will give you a list of all installed packages (correct me if I'm wrong, I didn't thoroughly check this):
```

awk '/Package:/ {print $2}' /var/lib/dpkg/status

```The above just prints the package names listed in the debian package database. Please someone check this and confirm. I don't have time right now.

Hope that helps.

Edit:
```

dpkg --get-selections | awk '{print $1}'

```
seems to do the same thing.

---

### Post by Jose Catre-Vandis on 2006-10-21
This is very handy. An extension to this is to send the output to file for future reference:

```
dpkg --get-selections | awk '{print $1}' > packages.txt
```

but this is even better you get a good listing with descriptions

```
dpkg -l > packages.txt
```

---

### Post by az on 2006-10-21
> **geek.de.nz said:**
> I had this question for ages too. After playing around with ara 
('apt-get install ara'), I found that all (installed?) packages are in a file on debian based systems.

So, the following will give you a list of all installed packages (correct me if I'm wrong, I didn't thoroughly check this):
```

awk '/Package:/ {print $2}' /var/lib/dpkg/status

```The above just prints the package names listed in the debian package database. Please someone check this and confirm. I don't have time right now.

Hope that helps.

Edit:
```

dpkg --get-selections | awk '{print $1}'

```
seems to do the same thing.

dpkg -l

will list all packages.

dpkg -l |grep gnome

will list all packages with the word gnome in the name or short description.

dpkg -L upstart

will list all the files in the package named "upstart"

---

