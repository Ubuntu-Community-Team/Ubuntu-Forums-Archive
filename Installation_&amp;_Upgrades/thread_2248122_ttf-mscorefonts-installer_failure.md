---
title: "ttf-mscorefonts-installer failure"
date: 2014-10-12
forum: Installation &amp; Upgrades
---

### Post by cbiweb on 2014-10-12
Brand new installation of Ubuntu 14.04, installed over Windows 7.

After installing, I got the following message.  And each time I boot up.  Everything works fine except that I'm getting this message:

> Data files for some packages could not be downloaded


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


ttf-mscorefonts-installer


This is a permanent failure that leaves these packages unusable on your system. You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem.


My internet connection is definitely good, and I can't actually reinstall the packages if they can't even be downloaded.

How do I fix this?

---

### Post by Vladlenin5000 on 2014-10-12
The usual procedure is to first uninstall that broken package and install it again, this time making sure you select the correct options to accept the EULA.

---

### Post by cbiweb on 2014-10-12
There is a package already installed?? I'm not aware of that, and never saw a EULA related to it.  If the package is installed, where do I go to uninstall it?

---

### Post by Vladlenin5000 on 2014-10-12
It is usually installed as part of the *ubuntu-restricted-extras* package... It provides the typical TT fonts you can find in Windows (Times New Roman, Verdana, etc.)

Remove:
```
sudo apt-get remove --purge ttf-mscorefonts-installer
```

(Obs.: The --purge parameter isn't usually necessary but just in case...)


Then install again (if you need/want):
```
sudo apt-get install ttf-mscorefonts-installer
```
During the installation you should be present with the Microsoft **E**nd-**U**ser **L**icense **A**greement. Pres TAB and then use the arrow keys to navigate the option and ENTER to confirm.

---

### Post by cbiweb on 2014-10-12
Worked perfectly, thanks!

---

### Post by Vladlenin5000 on 2014-10-12
You're welcome.
Please use the thread tools to mark this one as solved so other can benefit. Thank you.

PS - You're just 2 posts short of getting your full forum functionality which includes the ability to to edit your profile.
Happy Ubuntuing.

---

