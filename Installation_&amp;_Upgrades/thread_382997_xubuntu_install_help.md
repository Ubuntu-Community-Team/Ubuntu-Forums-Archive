---
title: "xubuntu install help"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by freshspinach on 2007-03-12
i'm trying to install xubuntu 6.10 from the alternate install CD on to my dell inspiron 5000. it has:

PIII 500Mhz
128 MB RAM
6 GB Hard Drive

I've followed the instructions and everything seems to install OK but when i reboot and login I get the following error: 

X: cannot stat /etc/X11/X (No such file or directory), aborting

i'm very new to this but it looks like i'm missing some files.

i need help.

---

### Post by Kateikyoushi on 2007-03-12
After the error are you thrown back to terminal ? If not try to boot singleuser mode, and post the output of the following command.

```
ls /etc/X11
```

---

### Post by freshspinach on 2007-03-13
After I get the Xserver error, I get thrown back to the prompt.

when i run

ls /etc/X11

i get a list:

app-defaults                     rgb.txt   Xresources   Xsession.options
default-display-manager     xinit        Xsession      Xwrapper.config
gdm                               xkb         Xsession.d

---

### Post by Kateikyoushi on 2007-03-13
X is missing from that directory, try to reinstall it, then configure it with the second command.

```
sudo aptitude reinstall xserver-xorg
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by freshspinach on 2007-03-14
For some reason, X was not installed, so I installed it and configured it with default settings (I wasn't able to make a decision on most of them) and now I'm getting more errors relating to the 'default font' and the monitor.

---

### Post by Kateikyoushi on 2007-03-14
Then let's see if you have everything installed nothing else is missing.

```
sudo aptitude install xubuntu-desktop
```

Then try to configure your X.
```
sudo dpkg-reconfigure xserver-xorg
```

---

