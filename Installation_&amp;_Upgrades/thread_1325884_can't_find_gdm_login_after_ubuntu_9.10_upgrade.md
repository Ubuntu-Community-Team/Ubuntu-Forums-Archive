---
title: "can't find gdm login after ubuntu 9.10 upgrade"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by kinngg on 2009-11-13
Hi all, I recently upgraded from 9.04 to 9.10 and after restarting i couldn't login to my desktop, i somehow lost my gdm login page and now i don't know what to do. I tried:

sudo apt-get install gdm ubuntu-desktop

but it says its already been installed, so I don't know whats going on, I'm only able to be on the black and white screen please help

---

### Post by kinngg on 2009-11-13
i can see the loading screen but after that it just the dos screen

---

### Post by theozzlives on 2009-11-13
> **kinngg said:**
> i can see the loading screen but after that it just the dos screen

I didn't know Linux had a DOS screen. Sign in and type:
```
startx
```
then see if you have any video drivers you need to install. Also, your system specs would be helpful.

---

### Post by kinngg on 2009-11-13
It says:

X: /tmp/.x11-unix has suspicious ownershop (not root:root), aborting
giving up.
xinit: No such file or directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error

---

### Post by kinngg on 2009-11-13
It says its fully updated and upgraded, gdm and ubuntu-desktop installed. It'll load the grub and then it'll show the loading screen, however once thats done, ususally the login screen will show, but now it just have a black screen requesting for a login

---

### Post by kinngg on 2009-11-14
bump

---

### Post by f1ckratte on 2009-11-30
same problem here.
its really annoying... anyone can help here?
previous kernels also wont work. I allready have reinstalled the nvidia driver, nothing seems to work :(

---

