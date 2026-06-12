---
title: "Xerox Phaser 3140 Install Error"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by mertt on 2011-09-15
Hi,

I downloaded the following driver for my Xerox Phaser 3140. I'm using Ubuntu 11.04. 

[http://www.support.xerox.com/support/phaser-3140/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-3140/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB)

When I double click on the "install.sh" to run it with terminal it gives the following error message:
[B]
you are not authorize to the driver package. Only user with root privileges allowed to do this[/B]

here there is a snapshot of it:

[http://i.imgur.com/rpuFO.png](http://i.imgur.com/rpuFO.png)

Is there anyway to Install 3140?

I'm quite new to ubuntu.

---

### Post by mertt on 2011-09-15
Well I tried sudo -s command in terminal then it gave to following output:

**** It seems Qt library is not installed, or X display is not accessible.
**** Custom Qt library will be configured for use with this package.
Failed to load widget from </home/user/desktop/Linux/x86_64/install/../../noarch/install/share/ui/WizardTemplate.ui>
QMutex::unlock: unlock from different thread than locker
was locked by 0, unlock attempt from 202794912

:mad:

---

### Post by Hakunka-Matata on 2011-09-15
Hi, Welcome;
If you're in the same directory as your install.sh file, try this
```
sudo bash install.sh
```

---

### Post by mertt on 2011-09-15
how can i jump to install directory via terminal?

---

### Post by Hakunka-Matata on 2011-09-15
use the shell command 'cd'
to move down from current directory:  'cd <directory name>

to move up, and/or up, over, down, you must precede the <directory name with a **/**.  Like this:

from home:$ **cd Downloads** (commands and filenames are case sensitive), everything is case sensitive in Linux!

if you want to switch up to **root **then down to /etc for example, you'd do this:
from home:$ [B]cd /etc

[/B]If you're at your home prompt: (mine is das@das-160GB:~$) and your install.sh file resides in /home/mertt/Downloads directory:
```
mer@merttXP:~$ **sudo bash /Downloads/install.sh**
```**EDIT:** that allows you to stay in your "pwd"(print working directory) and execute a file residing in another directory w/o the need to actually change focus to the directory where the file resides.
[http://www.computerhope.com/unix/ucd.htm](http://www.computerhope.com/unix/ucd.htm)

---

### Post by mertt on 2011-09-15
That worked! Thank you very much. I had stucked with it since morning :(

---

### Post by Hakunka-Matata on 2011-09-15
You're welcome,

---

