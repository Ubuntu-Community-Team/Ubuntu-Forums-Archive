---
title: "A question about repositories."
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by xardas on 2006-11-29
Just a quick question. I was wondering if there was any way to download packages for edgy ubuntu from the repositories without using the apt-get or aptitude, sort of like downloading those packages in a .deb file which I can later install? :-k

---

### Post by akshaysrinivasan on 2006-11-29
The .deb files are stored under /var/cache/apt/archives .Believe me installing from .debs is a nightmare without using apt.Dependancy ,inter dependency ,i spent two hours installing gnome-office in that way!
  If you just want to download it ,there is a option in Synatic

---

### Post by matthew on 2006-11-29
You can also look at [http://packages.ubuntu.com](http://packages.ubuntu.com) and search/download individual packages there. You will have the issue of dependencies to contend with doing it this way, but they are listed for each package so if you take your time and make sure you download all of each package's dependencies as well (and their dependencies and so on) you will be fine. It's a long, rather tedious process this way, but certainly doable--I've done it for a computer without internet access by downloading to removable media and then moving the files over and installing. If the computer has internet access, apt/aptitude/synaptic are the way to go because they were invented to take care of all that leg work for you. If you don't, this method will work.

---

### Post by xardas on 2006-11-29
Ok, thanks I'll give it a try.

---

### Post by az on 2006-11-29
> **xardas said:**
> Just a quick question. I was wondering if there was any way to download packages for edgy ubuntu from the repositories without using the apt-get or aptitude, sort of like downloading those packages in a .deb file which I can later install? :-k

You can use apt-get to download only.  Just use the -d switch.

sudo apt-get -d install apache2

You can use some tools to make a cd with a repository on it.

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
or
[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

I beleive there is a spec with a more sophisticated way (GUI) of doing this, though.  I don't know the status of that project.

---

### Post by matthew on 2006-11-29
azz, that's awesome. How have I been using Ubuntu for two years and missed apt-get -d? Thanks for the knowledge.

---

