---
title: "bootable cd\dvd"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by balagunner on 2008-03-27
How to make a bootable dvd in linux.

In nero there is a option, but how to do it in linux.

---

### Post by process91 on 2008-03-28
K3B is your Nero equivalent in Linux. Brasero is nice, and it's the standard CD/DVD burner for Ubuntu now in Hardy but it's beauty is in it's simplicity. K3B is what you can use for more advanced functions.

```
sudo apt-get install k3b
```

Chances are that if you haven't installed any KDE applications before, you're going to have to install a lot of K library dependencies. After you finish installing, start the program and begin creating your data CD. When you get to the burning step, check out the third button to the right of "Burn".

It should say "Modify the bootable settings of the current project", and that's it!

---

