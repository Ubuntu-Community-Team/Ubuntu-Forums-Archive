---
title: "Re-use downloaded updates and packages"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by cendant on 2006-10-23
After downloading hefty large updates and/or packages, I e.g. want to re-install Ubuntu.

Where are those updates and packages go to when you use apt-get?

Can you re-use them instead of spending more bandwidth?

---

### Post by TheWizzard on 2006-10-23
/var/cache/apt/archives

---

### Post by shoki on 2006-10-23
So if you burn this directory to a cd how would you reintroduce it back to the system? Would you add it to the repositories as a CD or would you copy them back to /var/cache/apt/archives ?

Thank you,
--Shoki

---

### Post by TheWizzard on 2006-10-23
i would cd into the directory with the deb-files. then:
```
dpkg -i *.deb
```
that's it

---

### Post by cendant on 2006-10-23
This simple, huh? Thanks!

Will care be taken of all dependencies?  Provided that all those packages were downloaded and installed OK.

---

### Post by cendant on 2006-10-23
Can I use this folder with packages

/home/andrei/repositary

as source in Software sources?

IS this syntax correct

deb /home/andrei/repositary edgy main

---

