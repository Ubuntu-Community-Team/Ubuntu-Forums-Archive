---
title: "need help installing .tar file"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Prinz on 2008-01-03
hi everyone. i'm new to linux, and am trying to install 'moblock'. so i download the .tar.bz2 file from their website, and have it sitting on the desktop. but when i try 'tar -xzvf moblock-0.8-static-i586.tar.bz2' in the terminal it says there is no such file or directory. any help? if this is a really simple common problem i apologize.

---

### Post by taurus on 2008-01-03
You have to be in the directory where that file is before you can unpack it.  Chances are you have downloaded it to your Desktop so do

```
cd ~/Desktop
tar xvjf moblock-0.8-static-i586.tar.bz2
```

---

### Post by ~LoKe on 2008-01-03
In the future, to make things easier on you (and to keep thingy tidy), I suggest downloading all packages into your home folder, rather than your desktop.  It's just that much easier (the terminals default path is your home folder).

---

