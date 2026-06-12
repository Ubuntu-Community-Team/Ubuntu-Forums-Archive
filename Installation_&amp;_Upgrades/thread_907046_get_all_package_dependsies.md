---
title: "get all package dependsies"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by tareq_linux on 2008-09-01
[B]hi,


how can i get all([COLOR="DarkRed"]download not install[/COLOR]) dependencies for a package so i can install it offline ??


is there any program/command to this ??

thanks[/B]

---

### Post by knattlhuber on 2008-09-01
> **tareq_linux said:**
> [B]hi,


how can i get all([COLOR="DarkRed"]download not install[/COLOR]) dependencies for a package so i can install it offline ??


is there any program/command to this ??

thanks[/B]

```
sudo apt-get -d install packagename
```

---

### Post by Partyboi2 on 2008-09-01
You can also manually do it by going [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") and searching for the package.

---

### Post by prshah on 2008-09-01
> **tareq_linux said:**
> 
how can i download not install dependencies for a package so i can install it offline ??

You can download and separately install packages with the below commands:
```
sudo apt-get --download-only install someprogramname

```

To install them, copy them to the same location on your target system, and issue the command```

sudo apt-get install someprogramname
``` _or_ if the repositories on the target machine is not updated then, ```
sudo dpkg -i /var/cache/apt/archives/*.deb
```

---

### Post by tareq_linux on 2008-09-01
thanks every one !

but when i type the command where should the downloaded packages located?

in the current dir? i can't fine this on the current path!!

Regards

---

### Post by tareq_linux on 2008-09-01
okay thanks i get it 

the location is /var/cache/apt/archives/ as prshah  stated 


thanks all ;)

i love linux

---

