---
title: "phpmyadmin"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by ben22 on 2008-01-22
Hello,

before I installed LAMP with synaptic package manager, after that I installed phpmyadmin with **sudo apt-get install phpmyadmin**

Now if i enter [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it does not find it - when I look into the var/www folder I only find apache in there

Where do I found phpmyadmin - or what should be done for installation (using gutsy)

cheers

---

### Post by eggdeng on 2008-01-23
Run
```
which phpmyadmin
```
If you get output, the program is installed to a folder in the system path and you can run it from a terminal with 
```
phpmyadmin
```
Otherwise, run
```
sudo updatedb
``` and
```
locate phpmyadmin
```
to find out where it is installed. In this case you can run it with
```
/path_to_file/phpmyadmin
```

---

