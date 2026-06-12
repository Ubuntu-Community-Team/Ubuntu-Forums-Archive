---
title: "Installed programs?"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Chamelion on 2007-12-29
I know there is a command that will give a list of all the on the computer installed programs. I have seen it somewhere here on the forum, but am not able to find it any more. Could someone please point me into the right direction. The second question I have is if it is possible to use this list somehow to automatically re install everything after a new installation of Gutsy for example. I probably ask for to much here. :)
Thank you

---

### Post by oldsoundguy on 2007-12-29
Two places in Ubuntu ..
Applications> Add Remove programs 
and
System> Administration> Synaptic Package Manager
(package manager will have a graphical indication of the installed programs.  Just remember, some of the things you see are NOT the programs, but DEPENDENCIES .. or programs required to run a program.)

---

### Post by shad0w_walker on 2007-12-29
List installed packages:

```
dpkg --get-selections > installed-packages.list 
``` 

You will need to redirect the output to a file if y ou want to restore them using this command

```
sudo dpkg --set-selections < installed-packages.list
```

EDIT: Forgot to mention you will need to run some form of package manager after you setup the selections. apt-get upgrade/install or aptitude or even synaptic if you prefer GUI things.

P.S. Make sure you back up  your repos list or you will likely end up with a whole bunch of errors.

---

### Post by Herman on 2007-12-29
If you're going to be re-installing the same version of Ubuntu again, it willl save you some internet bandwidth not to mention the time it takes to wait for the download to finish if you make a backup of the contents of your /var/cache/apt/archives directory and save it somewhere with the rest of your backups.
```
mkdir debholderfolder
``````
cp  /var/cache/apt/archives/*.deb debholderfolder
```It will only take a minute.

Regards, Herman :)

Then after you re-install and you have your debholderfolder (backup of your packages) in your new home directory, to restore the packages,
```
 sudo cp debholderfolder/* /var/cache/apt/archives/
``` Then when you update and upgrade your new system it will not need to download very much if anything from the internet. 
You'll also be able to re-install all your same programs again without downloading very much if anything from the internet. 
I use apt-get to re-install most of my programs with, but probably it will also work as well with Add/Remove Programs and Synaptic too.

---

### Post by Chamelion on 2007-12-29
Thanx to all and have a happy new year!!:)

---

