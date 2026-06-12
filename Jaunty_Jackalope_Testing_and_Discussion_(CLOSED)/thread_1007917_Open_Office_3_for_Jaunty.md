---
title: "Open Office 3 for Jaunty"
date: 2008-12-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2008-12-10
Just downloaded the "LinuxIntel_install_en-US_ deb.tar.gz" and extracted it. Just need to know if I have to manually install each of the bazillion debs listed or is there a better way ?? I checked the files and there were no instructions or a readme for installation. I guess the repos are still down at launchpad, as I have tried adding main and source to my third party software sources list with no results. Thanks in advance. 

Toshiba Satellite Pro 6100 -- Pent M  1.8 Ghz processor -- 768 Gig Ram --120 Gig hd -- Ubuntu 9.04.

---

### Post by adobrakic on 2008-12-10
I'm on Linux Mint, but what I did was go the 'debs' folder and right-clicked and did 'open terminal here.' Then I did the following commands:

```

sudo apt-get autoremove openoffice.org
sudo apt-get autoremove openoffice.org-core
sudo dpkg -i *.deb
```

And then when that was finished, I went into desktop-integration, and just installed that one by opening the file and letting it install.

---

### Post by jerrynewt on 2008-12-10
I see a gnome-integration package but no desktop-integration package. Is that the one I should open and let install ??

---

### Post by adobrakic on 2008-12-10
Yeah

After you install that, you should be able to see Open Office where you normally saw it in the menu.

---

### Post by jerrynewt on 2008-12-10
All I have now is Dictionary.

---

### Post by jfernyhough on 2008-12-12
> **jerrynewt said:**
> All I have now is Dictionary.

An easier way to get OOo3 running is to use the packages from PPA:

## OOo
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) intrepid main
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) jaunty main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) intrepid main

There aren't any Jaunty packages at the moment but the Intrepid ones work fine.

---

### Post by calc on 2008-12-12
> **jfernyhough said:**
> An easier way to get OOo3 running is to use the packages from PPA:

## OOo
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) intrepid main
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) jaunty main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) intrepid main

There aren't any Jaunty packages at the moment but the Intrepid ones work fine.

That is because it is already uploaded to Jaunty. It just hasn't been built yet since it is waiting on someone to move its build depends from universe to main.

[http://launchpad.net/ubuntu/+source/openoffice.org](http://launchpad.net/ubuntu/+source/openoffice.org)

---

### Post by andrewabc on 2008-12-13
Sorry for offtopicness...

Calc, I am getting a "partial upgrade" for openoffice while using intrepid.
some openoffice packages are selected, others are not. I did try the partial upgrade, and it said it was doing a distro upgrade(!), but gave an error before doing anything (so nothing really happened, and the latest version you released on you PPA is still wanting to install, but complains of partial upgrade).
Oddly I don't see any threads opened up about this. I figured more people would have the same problem. Only found 1 other person have it [here](http://ubuntuforums.org/showthread.php?t=987181&page=3)

---

### Post by danf_1979 on 2008-12-13
> **andrewabc said:**
> Sorry for offtopicness...

Calc, I am getting a "partial upgrade" for openoffice while using intrepid.
some openoffice packages are selected, others are not. I did try the partial upgrade, and it said it was doing a distro upgrade(!), but gave an error before doing anything (so nothing really happened, and the latest version you released on you PPA is still wanting to install, but complains of partial upgrade).
Oddly I don't see any threads opened up about this. I figured more people would have the same problem. Only found 1 other person have it [here](http://ubuntuforums.org/showthread.php?t=987181&page=3)

This is no intrepid forum, but anyway, $ man apt-get, or install aptitude and $ man aptitude. With aptitude you can use full-upgrade option, read about that.

---

### Post by jfernyhough on 2008-12-14
The easy workaround I found for that was to use Add/Remove to remove OpenOffice (everything but Draw first, then Draw) then install it again. When you reinstall it picks up the packages from the PPA and doesn't ask to do weird upgrade stuff.

---

