---
title: "new bie help installing few packages"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by CentronicsSupport on 2007-01-06
How can i install following packages:

How to get them?

j2re1.4_1.4.2.01-1_i386.deb
php4-ioncube-loader_3.0-ubn60.build06101212_i386.deb
php5-ioncube-loader_3.0-ubn60.build06101212_i386.deb
j2sdk1.4_1.4.2.01-1_i386.deb
psa-php4-configurator_1.1.0-ubuntu6.06.build81061129.23_all.deb
psa-php5-configurator_1.1.0-ubuntu6.06.build81061129.23_all.deb

please help newbie

Thanks,
CentronicsSupport

---

### Post by taurus on 2007-01-06
You can install them one by one with

Applications -> Accessories -> Terminal
```
sudo dpkg -i **package_name**.deb
```
Or you can install them all with one command.

```
sudo dpkg -i *.deb
```

---

