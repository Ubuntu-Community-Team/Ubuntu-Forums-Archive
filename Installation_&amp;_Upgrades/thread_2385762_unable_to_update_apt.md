---
title: "unable to update apt"
date: 2018-02-24
forum: Installation &amp; Upgrades
---

### Post by dg658 on 2018-02-24
I am attempting to update Ubuntu from 15.10 to 16,04.

I receive this message below:

```
The required dependency 'apt (>= 1.0.10.2ubuntu2)' is not installed. 

```

I have followed the steps outlined in this link without success:

[http://mindwatering.com/SupportRef.nsf/webpg/C3D8A1EB7943316F85257FCB007333A2](http://mindwatering.com/SupportRef.nsf/webpg/C3D8A1EB7943316F85257FCB007333A2)

When I type:
```
dan@dan-All-Series:~$ sudo apt-get upgrade
```

I receive the following message:

```
dan@dan-All-Series:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-gudev-1.0 : PreDepends: dpkg (>= 1.17.14) but 1.17.5ubuntu5.6 is installed
 libmagickcore-6.q16-2 : PreDepends: dpkg (>= 1.17.6) but 1.17.5ubuntu5.6 is installed
 libmagickwand-6.q16-2 : PreDepends: dpkg (>= 1.17.6) but 1.17.5ubuntu5.6 is installed
 perl : PreDepends: dpkg (>= 1.17.17) but 1.17.5ubuntu5.6 is installed
 perl-base : PreDepends: dpkg (>= 1.17.17) but 1.17.5ubuntu5.6 is installed
 perl-modules : PreDepends: dpkg (>= 1.17.17) but 1.17.5ubuntu5.6 is installed
 udev : PreDepends: dpkg (>= 1.17.14) but 1.17.5ubuntu5.6 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by oldos2er on 2018-02-24
As you likely know, 15.10 is no longer supported, so the information in the link you provided won't work. You could try [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by dg658 on 2018-02-26
Thanks. What I did is saved everything on a portable HD. Then I made a bootable USB using this guide: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

I thought I was going to lose everything but the bootable USB drive actually let me update the machine.

---

