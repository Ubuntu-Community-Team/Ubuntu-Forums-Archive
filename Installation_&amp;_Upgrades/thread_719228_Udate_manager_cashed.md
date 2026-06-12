---
title: "Udate manager cashed"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by rab4567 on 2008-03-08
Ok guys I need some help I tried serval ways to correct this problem but I'm coming up snake eyes. Now I'm no command line guru but did try:

sudo dpkg --configure -a
sudo dpkg -P --force-all update-manager update-manager-core
sudo aptitude update
sudo aptitude install update-manager update-manager-core

this did not work it stop right at the point were it ask you insert the gusty disc and type yes when it layed there.

So I used

sudo apt-get install -f

then got

  gnome-themes-extras gnumeric gnumeric-common inkscape kbuild libffi4 
  libgnomecupsui1.0-1c2a libgpgme11 libpth20 libxine1-gnome libxtst-dev 
  module-assistant planner python-apsw python-ctypes python-dsv python-qt3 
  python-serial seahorse x11proto-record-dev 
The following NEW packages will be automatically installed: 
  update-manager-core 
The following packages have been kept back: 
  brasero kaffeine libnautilus-extension1 libvolume-id0 nautilus 
  nautilus-data thunderbird udev volumeid 
The following NEW packages will be installed: 
  update-manager update-manager-core 
0 packages upgraded, 2 newly installed, 29 to remove and 9 not upgraded. 
Need to get 0B/915kB of archives. After unpacking 168MB will be freed. 
Do you want to continue? [Y/n/?] y 
Writing extended state information... Done

can you guy help me out?

---

### Post by polmir on 2008-03-09
connect pc to internet

**Ctrl+Alt+F2**
your login and password
type
```
sudo su
your password 
```
```
dpkg --configure -a
```

---

### Post by rab4567 on 2008-03-10
still a no go.

---

### Post by kesman on 2008-03-10
edit your sources NOT to contain the cd, then run 
```

sudo apt-get update
sudo apt-get clean
sudo apt-get dist-upgrade

```
and maybe
```

sudo dpkg --configure -a

```

---

