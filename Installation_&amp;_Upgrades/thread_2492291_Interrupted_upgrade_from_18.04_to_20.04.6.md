---
title: "Interrupted upgrade from 18.04 to 20.04.6"
date: 2023-11-06
forum: Installation &amp; Upgrades
---

### Post by syrag on 2023-11-06
My system works and does almost everything I want it to. The problem I'm trying to fix is backintime. It needs to install python3-dbus.mainloop.pyqt5, but then I end up with broken packages. I can then "Mark All Upgrades", "Apply", "Fix Broken packages" and these all succeed, but this is an infinite loop.
This seems to be the trouble maker (but I suspect there are more):

> The following packages have unmet dependencies:
 python3-pyqt5 : Depends: libpython3.8 (>= 3.8.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I have Python 3.8.16 installed. This appears to be leftover from 18.04, as the version is 3.8.16-1+bionic1.

How do I correctly upgrade python?


This is how I got here:

My upgrade via software-updater froze. I killed the process and continued via the command line. After several iterations of
"apt-get full-upgrade" and "apt auto-remove" I've ended up here:
> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdb gir1.2-peas-1.0 gnome-builder krita libpeas-1.0-0 libpython3-dev
  libsmbclient libwbclient0 mysql-client mysql-server samba-libs
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Can someone help me. I'm kind of over my head here. Thanks

---

### Post by Tadaen_Sylvermane on 2023-11-06
Post your sources list and as well as any ppas

---

### Post by MAFoElffen on 2023-11-06
Have you tried reinstalling the specific version of the base package from Focal?
```

sudo apt-get install --reinstall --with-new-pkgs -y python3=3.8.10-0ubuntu1~20.04.8

```
That is what is current in the Focal repo, should reinstall it, with all it's dependencies. Notice I said "should"...

---

### Post by syrag on 2023-11-06
> **MAFoElffen said:**
> Have you tried reinstalling the specific version of the base package from Focal?
```

sudo apt-get install --reinstall --with-new-pkgs -y python3=3.8.10-0ubuntu1~20.04.8

```
That is what is current in the Focal repo, should reinstall it, with all it's dependencies. Notice I said "should"...

Synaptic returns:

```
python3.8-full:
  Depends: python3.8 (=3.8.10-0ubuntu1~20.04.8) but 3.8.16-1+bionic1 is to be installed
 Depends: libpython3.8-testsuite but it is not going to be installed
 Depends: python3.8-venv but it is not going to be installed
 Recommends: python3.8-doc but it is not going to be installed
 Recommends: python3.8-examples but it is not going to be installed
```

---

### Post by MAFoElffen on 2023-11-06
Dang. That is tweaked & stuck there isn't it...

---

### Post by syrag on 2023-11-06
> **Tadaen_Sylvermane said:**
> Post your sources list and as well as any ppas

These are the active sources. All ppas were disabled during the upgrade, and I haven't re-enabled any yet.
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates restricted multiverse universe main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports main restricted universe multiverse #Added by software-properties
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security restricted multiverse universe main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security multiverse

---

### Post by MAFoElffen on 2023-11-06
What happens if you try
```

sudo apt-get build-dep python3=3.8.10-0ubuntu1~20.04.8

```
That may or may not complain about no having src in your source.list, but is worth a try.

---

### Post by syrag on 2023-11-06
> **MAFoElffen said:**
> Dang. That is tweaked & stuck there isn't it...

Yep.

---

### Post by MAFoElffen on 2023-11-06
If what I suggested in Post #7 doesn't work... Do you have a good backup? 

Are you familiar with how to do an Ubuntu non-destructive reinstall? If not, I can explain how.

---

### Post by syrag on 2023-11-06
> **MAFoElffen said:**
> What happens if you try
```

sudo apt-get build-dep python3=3.8.10-0ubuntu1~20.04.8

```



I added the source repository and changed the name to 'python3.8-full', since that what synaptic shows. That worked. I could install backintime. Some python was downgraded (can't remember which, and didn't write it down, dammit), so I don't know what effect that will have down the line, but for now it's working.
Thanks a lot.

---

### Post by syrag on 2023-11-06
> **MAFoElffen said:**
> If what I suggested in Post #7 doesn't work... Do you have a good backup? 

I always have a backup. That's the last thing I do before I upgrade.

> Are you familiar with how to do an Ubuntu non-destructive reinstall? If not, I can explain how.

Never heard of it. I don't want to steal your time, since everything's working, but do you have link? That could come in handy someday.

---

### Post by MAFoElffen on 2023-11-06
guiverc had written up a good explanation on that recently: [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533) 

I've done that in the past. Even with Ubuntu 10.04 LTS back in 2010... LOL. The concept does work. You just have to remember to un-select any format options, so that it just writes the new system in the existing filesystem. Otherwise everything will be gone.

The reason I suggested that, is that your system is stuck between releases. If you restored now, it would be back at 18.04. If you tried to do a non-destructive repair, with a 20.04 Installer disk, then it would replace everything in the system with the correct packages that work together... With your backups, there as a fall-back. That would get your "there" in less time than restoring back to 18.04 and trying the release upgrade over again...

---

### Post by syrag on 2023-11-06
Thanks. I've never thought of doing that.

---

### Post by MAFoElffen on 2023-11-06
So if this is fix, please select the "Thread Tools" Link ad mark this a "Solved". That helps other find solutions that worked, when they go looking to solve their ow problems. This one did come up with a few worthy treasures / suggestions that work > LOL.

---

### Post by #&amp;thj^% on 2023-11-06
+1
And it can't be said enough with that method: "**You just have to remember to un-select any format options**"

---

