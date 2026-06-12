---
title: "I can't find an installed package"
date: 2019-06-12
forum: Installation &amp; Upgrades
---

### Post by LordOrange on 2019-06-12
HI all,

Just installed a dpkg file (both via GUI and command like using the dpkg command) and I cannot find it or run it from anywhere. If I search for it in apt I find it and it is listed as installed but when I try to find it in the gnome apps list, nothing comes up. Any ideas what I'm doing wrong?

---

### Post by deadflowr on 2019-06-12
You can try looking at the packages file listings and see if there are either 
1)a .desktop file (that is required for it to show in any graphical menu)
2)has a proper binary file listed in either /usr/bin or /bin or /sbin or some other directories.
Run
```
dpkg -L package-name-here
```
The package name isn't the installers name but the name the package has in Ubuntu.
So when you installed if the package installer was something like package-2.3.3_amd64.deb then the package name would just be package.
Well, typically at least
You can use 
```
dpkg -l | grep some-part-of-the-package-name-I-think-it-is
```
To find the package name Ubuntu knows it as.

Note that the first dpkg is a capital L and the second (with the grep pipe) is a small L.
(People can sometimes see the second as a one, for some reason)

hope it helps move things along.

---

