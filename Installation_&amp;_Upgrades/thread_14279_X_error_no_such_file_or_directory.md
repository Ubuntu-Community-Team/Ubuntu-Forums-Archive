---
title: "X error no such file or directory"
date: 2005-02-06
forum: Installation &amp; Upgrades
---

### Post by boosted on 2005-02-06
after installing ubuntu and it auto updating, it tried to load X but failed, it asked if i wanted to view the error log, i did.  It said 
X: cannot stat /etc/X11/X (no such file or directory)
how can this be?

please help...  i am a linux newbie!!!

---

### Post by boosted on 2005-02-06
i tried sudo dpkg-reconfigure xserver-xfree86

Package 'xserver-xfree86' is not installed and no info is available.

why would ubuntu installation not install X???  how do i fix this problem? re-install X?? how do i install X?

i do have a /etc/X11 directory
in the directory i type ls
app-defaults ...................... rgb.txt .... Xresources .... xsm ...............
cursors .............................. rstart ...... xserver .......... Xwrapper.config ..........
default-display-manager ......sysconfig .... Xsession ..........
fonts ................................. xinit ......... Xsession.d..........
gdm ..................................  xkb ......... Xsession.options.........

---

### Post by kultuur on 2005-02-06
You can install XFree86 with:
```
sudo apt-get install --reinstall xserver-xfree86
```

---

### Post by boosted on 2005-02-06
ok it says it is downloading...  so hopefully this works.  so after it is done downloading, will it auot install and configure or do i have to do all this manual?  I have no idea how to install packages manually.

---

