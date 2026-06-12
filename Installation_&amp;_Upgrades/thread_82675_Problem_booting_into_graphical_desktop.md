---
title: "Problem booting into graphical desktop"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by scoorocks on 2005-10-27
Hi all,
I have installed UBUNTU enterprise server on my P4 machine. The installation was very smooth, but the only problem is that my system boots directly into text mode. I'm unable to boot into graphical mode(tried giving a "startx" command..command not found). Can anyone help me out on this please?

Regards,

Santhosh

---

### Post by heimo on 2005-10-27
Do you want full desktop on that computer? If you have network connection working, you can install Gnome with loads of applications using:
```
sudo apt-get install ubuntu-desktop
```
or KDE variant using kubuntu-desktop


If you don't want all that (for example, OpenOffice.org, evolution...), you could install x-window-core, some window manager and just the applications you need.

---

### Post by scoorocks on 2005-10-27
i thought that the windowing system was pre installed too..the reason i'm sayin this is because i saw open office etc being dumped on to my machine during the initial setup process..and i did not have this issue when i installed the desktop version of ubuntu 5.10..i'm having this issue only when i did the default installation of the server iso.

---

