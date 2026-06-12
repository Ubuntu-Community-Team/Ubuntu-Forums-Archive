---
title: "capplets-data program"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lohapuk on 2010-03-31
Hi just wondering if anyone has a work around for 

apt-get install ubuntu-desktop gnome-control-center capplets-data

The following packages have unmet dependencies:
  capplets-data: Recommends: gnome-control-center (>= 1:2.30.0-0ubuntu3) but 1:2.30.0-0ubuntu2 is to be installed
                 Breaks: gnome-control-center (< 1:2.30.0-0ubuntu3) but 1:2.30.0-0ubuntu2 is to be installed

---

### Post by Stingr on 2010-03-31
I was able to fix this by downloading the right version of capplets-data from packages.ubuntu.com, installing it using dpkg and then re-installing ubuntu-desktop.  The various commands are below:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.30.0-0ubuntu2_all.deb

sudo dpkg -i ./capplets-data_2.30.0-0ubuntu2_all.deb

sudo apt-get install ubuntu-desktop
```

After doing this, restart GDM and you should be good to go.

---

### Post by jhuckabee on 2010-03-31
Thank you!  I had this same problem this morning, and installing the proper capplets-data fixed it.

---

