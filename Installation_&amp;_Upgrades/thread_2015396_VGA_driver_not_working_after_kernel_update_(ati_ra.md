---
title: "VGA driver not working after kernel update (ati radeon)"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by deadcatt on 2012-07-03
i'm having trouble with my VGA driver on ubuntu, i just recently updated the kernel with
# aptitude safe-upgrade 

and now when i try to start for example XBMC it says it needs OpenGL rendering, Install appropriated graphics driver

Also there is strange flicker in videos pleyd with mplayer and vlc and sometimes images from web browser duplicates over to dolphin window and i have to re size the window to make it disappear.

i have a radeon graphics card and i've tryed to install radeon and fglrx with apt-get and no still no luck.

here is a paste from terminal when trying to install fglrx drivers, i see there's something about the kernel there, but not sure what to do..
[http://paste.ubuntu.com/1072739/](http://paste.ubuntu.com/1072739/)

---

### Post by msammels on 2012-07-05
deadcatt, what version of Ubuntu are you using? The following commands don't work for me:

```
michael@ubuntu:~$ sudo apt-get safe-upgrade
[sudo] password for michael: 
E: Invalid operation safe-upgrade
michael@ubuntu:~$ sudo aptitude safe-upgrade
sudo: aptitude: command not found
```

So I am unsure what you're trying to do. As for your driver problems, can you start the X server using:

```
sudo startx
```

---

