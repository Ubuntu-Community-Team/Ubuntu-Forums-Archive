---
title: "Installing Opera"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by kate on 2006-03-06
I just did a fresh install of Ubuntu 5.10 onto my laptop and I've done an update, now I'm downloading and installing software I love. First off is Opera. I downloaded the source and everything was fine until this:

Do you want to install them in /etc [ y,n | yes,no ] ?
y
Could not find icon installation directory, icons not installed.
kate@ubuntulaptop:~/Desktop/opera-8.52-20060201.5-shared-qt.i386-en$

What is the matter?

---

### Post by aysiu on 2006-03-06
The best way to install Opera is to download the static Deb (circled in red) instead of the Ubuntu Deb (don't ask me why--I've just never had any luck with the Ubuntu one) to your desktop and then do this ```
cd Desktop
sudo dpkg -i opera*.deb
```

---

### Post by kate on 2006-03-06
I tried that and this is what I got:

kate@ubuntulaptop:~/Desktop$ sudo dpkg -i opera-static_8.52-20060201.1-qt_en_i386.deb
Password:
Selecting previously deselected package opera-static.
(Reading database ... 60983 files and directories currently installed.)
Unpacking opera-static (from opera-static_8.52-20060201.1-qt_en_i386.deb) ...
dpkg: dependency problems prevent configuration of opera-static:
 opera-static depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera-static (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera-static
kate@ubuntulaptop:~/Desktop$


That was with the static deb package.

---

### Post by aysiu on 2006-03-06
Can you try this? ```
sudo apt-get update
sudo apt-get install xlibs
sudo dpkg -i opera*.deb
```

---

### Post by kate on 2006-03-06
Thanks everyone! It's now working!

---

