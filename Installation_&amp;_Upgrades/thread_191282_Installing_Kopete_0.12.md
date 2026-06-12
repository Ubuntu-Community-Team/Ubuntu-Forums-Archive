---
title: "Installing Kopete 0.12"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-06-07
Hi! I just downloaded kopete_0.12.0-0ubuntu1_i386.deb and installed it on my system, all went okay, then I saw a update manager icon on the clock, and fetch all update, then I found out that my kopete was return to its original version which is the 0.11.3, I tried to install the kopete_0.12.0-0ubuntu1_i386.deb, then again the update promtp me again for its update, which it said to update kopete again, when I click the fetch, instead of upgrade it turned out to be downgrade from 0.12.0 to 0.11.3. how to go with this? :)

Thanks.,

---

### Post by david_e on 2006-06-07
First install the unofficial kopete_0.12.0_i386.deb with:

```
sudo dpkg -i kopete_0.12.0_i386.deb
```
Close the upgrade notifications, but let it open at the next startup of the system.

then issue a:

```
dpkg --get-selections \* > selections.txt
```
then open selections.txt with kate search for kopete you should find:

```
kopete                   install
```
change it into:

```
kopete                   hold
```
save it and type:

```
sudo dpkg --set-selections < selections.txt
```
You should check that it worked with:

```
sudo apt-get update
sudo apt-get upgrade
```
and you should see something like this:

```
davide@acer-ferrari:~/temp$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  kopete
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
The update will continue prompting and saying it has new updates on kopete, but it will not download or install them as kopete is now on hold with apt-get... there must be a way to tell adept not to notify updates for kopete, but I don't know how to do this...

---

