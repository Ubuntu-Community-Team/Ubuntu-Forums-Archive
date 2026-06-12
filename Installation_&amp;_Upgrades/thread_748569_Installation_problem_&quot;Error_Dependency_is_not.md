---
title: "Installation problem: &quot;Error: Dependency is not satisfiable: phyton imaging&quot;"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by tsuwal on 2008-04-07
This error occurred while I was trying to install an application called Workaholic: [http://mundogeek.net/workaholic/](http://mundogeek.net/workaholic/)

my OS is Ubuntu 7.10 so I used the download link for distributions that use deb packages. When I opened workaholic-0.2.0.deb with the program GDepi package installer, the program sent me this message: "Error: Dependency is not satisfiable: python-imaging". I've tried the other version but ,still, I can't install the program. What should I do? 
PS: If you don't know the solution, please recommend me a program with the same porpuse.

---

### Post by Partyboi2 on 2008-04-07
Open a terminal (Applications>Accessories>Terminal) and install python-imaging
```
sudo apt-get install python-imaging
``` then try installing Workaholic again. Another option to install  is to add 
```
deb http://mundogeek.net/repo ubuntu all
``` to your etc/apt/sources.list
In a terminal type
```
gksudo gedit /etc/apt/sources.list
``` at the bottom of the sources.list file add
```
deb http://mundogeek.net/repo ubuntu all
``` then save.
Then back in the terminal type
```
sudo apt-get update
``````
sudo apt-get install workaholic
```

---

