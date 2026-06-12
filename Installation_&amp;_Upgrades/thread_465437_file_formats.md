---
title: "file formats"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by mr.farenheit on 2007-06-05
i don't know if this is the correct area to ask this question but how do i go about using .rpm files? i usually get an error stating something about the archive manager not supporting the format. is there a program or something that i should look for or a way to modify it to where my system will read the format?

---

### Post by taurus on 2007-06-05
Use alien to convert it to .deb first before you install it.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install alien
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```

---

