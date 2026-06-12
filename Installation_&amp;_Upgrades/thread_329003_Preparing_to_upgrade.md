---
title: "Preparing to upgrade"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by Rhapsody on 2006-12-31
I'm currently about ready to upgrade from Kubuntu Dapper to Kubuntu Edgy, but I have one minor problem to solve before I start.

I plan to wipe out my root partition and start again with Edgy Eft to avoid any possibility of the nasty upgrade problems I've been hearing about. However, I have installed a fair amount of applications from the repositories that would be lost while doing that. I remember hearing about a way to get a full list of everything installed on the system so I can reinstall them more easily once I get to Edgy Eft, but I can't seem to recall this, and I've no idea how I'd find it on the forums now.

So could someone please tell me how this is done so I don't have to try and remember or write down everything?

---

### Post by matrooswolf on 2006-12-31
I have got these commands from this site:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

Maybe this can help you, but be warned, I have not tried it, and I have no idea if it will work from dapper to edgy ...
To save package list
```
dpkg –get-selections > mypackages.txt
```
To restore them
```
sudo dpkg –set-selections < mypackages.txt
sudo apt-get dselect-upgrade
```

---

### Post by Rhapsody on 2006-12-31
> **matrooswolf said:**
> I have got these commands from this site:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

Maybe this can help you, but be warned, I have not tried it, and I have no idea if it will work from dapper to edgy ...
To save package list
```
dpkg &#8211;get-selections > mypackages.txt
```
To restore them
```
sudo dpkg &#8211;set-selections < mypackages.txt
sudo apt-get dselect-upgrade
```

Well I don't plan to try and restore it exactly (that would be asking for problems since a lot of the stuff wouldn't have exact matches in the Edgy repositories) but such a list could certainly help as reference. I just don't want to lose any of the numerous applications I have here.

Edit: Erm, wow? How did I get through 1179 packages in six months? I should've seen that coming. Sorry for wasting time here, I think I'll just make a list of my applications.

---

