---
title: "how to list installed packages?"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2010-03-03
How can I list what i have installed for current packages, excluding what normally comes with a fresh install of 9.10?

---

### Post by wojox on 2010-03-03
```
sudo dpkg --get-selections > installed-applications.txt
```

Run that in the terminal and look in your home folder. ;)

nevermind, I just saw the excluding part.

---

### Post by Enigmapond on 2010-03-03
```
dpkg --get-selections > installed-software
```

This will drop the "installed-software" file to your home directory.

---

### Post by Daremo_06 on 2010-03-03
> **Enigmapond said:**
> ```
dpkg --get-selections > installed-software
```

This will drop the "installed-software" file to your home directory.

ok how can i mass select all of those packages and install them?

---

### Post by Enigmapond on 2010-03-03
Somewhere in the forum...and you'll need to search, someone wrote a script to do just that. I thought I copied it but I did not. One DOES exist however..posted in the last two months if I remember correctly. Someone was wanting to backup all his programmes and restore them to a new distro and the script enables you to do that and then it will actually install the newer version...that's all I remember. If you find it you may want to link to it...I'll look as well because it was a very handy thing.

---

### Post by Daremo_06 on 2010-03-03
> **Enigmapond said:**
> Somewhere in the forum...and you'll need to search, someone wrote a script to do just that. I thought I copied it but I did not. One DOES exist however..posted in the last two months if I remember correctly. Someone was wanting to backup all his programmes and restore them to a new distro and the script enables you to do that and then it will actually install the newer version...that's all I remember. If you find it you may want to link to it...I'll look as well because it was a very handy thing.

Havent found it yet.. but i did find this thread..

[http://ubuntuforums.org/showthread.php?t=35087&highlight=script+backup+packages](http://ubuntuforums.org/showthread.php?t=35087&highlight=script+backup+packages)

Its from 2005 though, is it still relevant?

---

### Post by wojox on 2010-03-04
Just run:

```
sudo dpkg --get-selections > myPackages
```

Save that file and reinstall like so:

```
sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

---

### Post by Daremo_06 on 2010-03-05
> **wojox said:**
> Just run:

```
sudo dpkg --get-selections > myPackages
```

Save that file and reinstall like so:

```
sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

OOPS! hehe

I ran that, but I forgot to also save my list of software sources.  Is there a way to reconstruct it from the mypackages info?

Thanks

---

### Post by presence1960 on 2010-03-05
> **Enigmapond said:**
> Somewhere in the forum...and you'll need to search, someone wrote a script to do just that.

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Thanks to lovinglinux for sharing this info with the community!

---

