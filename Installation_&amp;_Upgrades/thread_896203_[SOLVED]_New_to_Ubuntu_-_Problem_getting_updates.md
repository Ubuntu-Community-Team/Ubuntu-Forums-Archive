---
title: "[SOLVED] New to Ubuntu - Problem getting updates"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by craz-usr on 2008-08-20
Tried to download a converter that was recommended by this forum by typing in command "sudo apt-get update," and later found out that it didn't work. The next day I found out that I couldn't get my updates like I regularly do. Keep getting error message "E:Type '--23:35:42--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read." Don't know how or if I should try to delete the file "medibuntu.list" Please help.


JimE

---

### Post by Partyboi2 on 2008-08-21
Try re-downloading the file and replacing the existing one. In a terminal (Applications>Accessories>Terminal)
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list
```
then
```
sudo mv ./hardy.list /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update
```

---

### Post by craz-usr on 2008-08-21
Thanks for the help Partyboi2. I tried it and it worked.

---

