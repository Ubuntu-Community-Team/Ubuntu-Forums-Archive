---
title: "Help!!!!!!!!!"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by mandie7312 on 2007-06-20
It wont leet me install anything and it says 

E: /var/cache/apt/archives/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb: files list file for package `libgnome-window-settings1' is missing final newline

---

### Post by silverglade00 on 2007-06-20
Try this. Close down any package installer you have open. Then

```
sudo rm /var/cache/apt/archives/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb
``` and answer Y when it asks. 

Then try installing whatever it is again.

---

### Post by mandie7312 on 2007-06-21
thanks but then it says rm: cannot remove `/var/cache/apt/archives/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb': No such file or directory

---

### Post by mandie7312 on 2007-06-21
oh yeah and i used wubi to install ubuntu

---

### Post by mandie7312 on 2007-06-21
if that matters

---

### Post by mandie7312 on 2007-06-21
if someone wants they can help me with remote desktop by typing vncviewer ubuntu.belkin:0

---

### Post by silverglade00 on 2007-06-21
Wubi, huh? That explains why you have E: in front of that path. Try this one.

```
sudo rm E:/var/cache/apt/archives/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb
```

All I did was put the E: back in there.

---

### Post by mandie7312 on 2007-06-21
it says alnmost the same thing 


rm: cannot remove `E:/var/cache/apt/archives/libpng12-0_1.2.15~beta5-1ubuntu1_i386.deb': No such file or directory

---

### Post by silverglade00 on 2007-06-21
I'm afraid I can't much past that. Hopefully someone else can help you. Sorry. :(

---

### Post by mandie7312 on 2007-06-21
thanks anyway

---

### Post by Ultra Magnus on 2007-06-21
I don't know much about wubi but there is a forum you could try, the good folks there might have a better idea of how to help you - [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

