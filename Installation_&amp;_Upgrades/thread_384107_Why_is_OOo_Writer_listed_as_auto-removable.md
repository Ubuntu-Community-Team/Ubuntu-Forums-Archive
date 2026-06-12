---
title: "Why is OOo Writer listed as auto-removable?"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by mahy on 2007-03-14
Hi folks,

i chose to completely uninstall original Openoffice.org (due to font issues) and install a newer version. So i downloaded the 2.1.0 RPMs from the project's website, converted everything into .deb packages and then installed. It works perfectly, but there's a small glitch. OOo Writer is listed in auto-removable packages. Where's the problem and can it somehow be fixed? THX

---

### Post by yabbadabbadont on 2007-03-14
I imagine it has something to do with them being converted deb files, but you can change the status using the "apt-mark" utility.
```
sudo apt-mark unmarkauto <list of packages here>
```

---

