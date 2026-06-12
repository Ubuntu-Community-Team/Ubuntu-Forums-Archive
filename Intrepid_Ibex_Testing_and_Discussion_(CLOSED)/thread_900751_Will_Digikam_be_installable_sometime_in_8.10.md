---
title: "Will Digikam be installable sometime in 8.10"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-08-25
I have been trying to install Digikam for a while but I keep getting these errors, has anyone managed to ge it going on there PC?

digikam:
 Depends: kdebase-kio-plugins  but it is not installable
 Recommends: kdeprint  but it is not installable
 Recommends: kipi-plugins but it is not going to be installed


Cary

BTW I have all repo's enabled & pointing to the main server.

---

### Post by Steveway on 2008-08-25
Did you try digikam-kde4?
That should be the correct package.

---

### Post by TheMono on 2008-08-25
AFAIK they are supposed to be providing both KDE3 and KDE4 digikam as the KDE4 version is not stable yet. They don't use package-kde4 unless they are also providing the KDE3 one by default...

---

### Post by caryb on 2008-08-25
This is my output from apt-get, also tried aptitude with same result


oot@stinkpad:/var/cache/apt/archives# apt-get install digikam-kde4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  digikam-kde4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After this operation, 25.3MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe digikam-kde4 0.10.0~beta1-0ubuntu2 [10.1MB]
Fetched 10.1MB in 2min51s (58.8kB/s)
dpkg: regarding .../digikam-kde4_0.10.0~beta1-0ubuntu2_amd64.deb containing digikam-kde4:
 digikam-kde4 conflicts with digikam
  digikam (version 2:0.10.0~beta1-1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/digikam-kde4_0.10.0~beta1-0ubuntu2_amd64.deb (--unpack):
 conflicting packages - not installing digikam-kde4
Errors were encountered while processing:
 /var/cache/apt/archives/digikam-kde4_0.10.0~beta1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@stinkpad:/var/cache/apt/archives#


Cary

---

### Post by TheMono on 2008-08-25
sudo dpkg -r digikam
sudo apt-get install digikam-kde4

Then file a bug on the Digikam package...

---

