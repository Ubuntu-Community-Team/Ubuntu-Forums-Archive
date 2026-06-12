---
title: "Resetting, removing, reinstalling Python"
date: 2019-10-05
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2019-10-05
On Ubuntu (Mate) 18.04.1 LTS 

My PYTHONPATH is

    > :/home/jim/ytini/yt-conda/bin:/home/jim/ytini/yt-conda/sbin

    $python -V 

returns

    > Python 2.7.16 :: Anaconda, Inc.


So my question is, how do I start from a blank slate. ie remove ALL Python installs and reinstall a new version or Python 2.7?

---

### Post by Skaperen on 2019-10-05
what do you get from this command?  [COLOR=#0000cd][FONT=courier new]**dpkg -l|fgrep python**[/FONT][/COLOR]

---

### Post by ubuntini2 on 2019-10-06
You asked :p

[https://paste.ubuntu.com/p/hntNrqZcFW/](https://paste.ubuntu.com/p/hntNrqZcFW/)

---

### Post by ubfan1 on 2019-10-06
Don't uninstall python, your system relies heavily on it, and you will get a nasty surprise when you try to install anything!  The python you want to remove looks like a local  copy.  Try unsetting the PYTHONPATH and see if the result lets the system version be used. /usr/bin/python  is just a link to /usr/bin/python2.7, so if your /usr/bin is before your home dir in your PATH, the system python should run with the 'python" command

---

