---
title: "Broken Gnome-panel"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by cu19 on 2010-03-01
i am running ubuntu 9.10.  when i try to run my updates i get a broken "pop up" due to gnome-data.  when i tell it to reinstall in package manager it fails to do so.  this is what i get - E:/var/cache/apt/archives/gnome-panel-data_1%   3a2.28.0-Oubuntu6_all.deb: corrupted filesystem tarfile - corrupted package archive   since i am new at this i am not sure what to do, any help in newbi terms would be appreciated.  Thanks

---

### Post by dstew on 2010-03-02
One thing to try is just deleting the corrupted file:```
sudo rm /var/cache/apt/archives/gnome-panel-data_1% 3a2.28.0-Oubuntu6_all.deb
```Then do ```
sudo apt-get update
sudo apt-get upgrade
```By the way, I am not sure the file name is correct. This file should have the name gnome-panel-data_2.28.0-0ubuntu6_all.deb. The extra characters in the name you list, the "1% 3a", if truly in the file name, that is an error. If not in the name, but just in the forum post for some reason, then the removal command should be```
sudo rm /var/cache/apt/archives/gnome-panel-data_2.28.0-Oubuntu6_all.deb
```

---

