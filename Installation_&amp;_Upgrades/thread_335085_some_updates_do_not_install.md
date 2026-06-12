---
title: "some updates do not install"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by $teve on 2007-01-09
Hi all, i wondered if someone would be able to help me with this problem i got; whenever updates are available and I run the update manager by clicking the icon from the gnome panel I keep getting a message saying that some updates cannot be installed, 66 of them. 

It advises me to run a distribution upgrade but when I run this I get back error message and the upgrade ceases. I am running 6.10 (edgy) and I pretty sure that my system is up to date and that this problem is some sort of confusion about what is installed :confused: 

Here is the output when I run apt-get upgrade from a terminal:

```
steve@UBUNTU:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bluez-cups bluez-pcmcia-support bluez-pin bluez-utils gaim gaim-data gksu gnome-accessibility-themes gnome-themes
  gparted gstreamer0.10-plugins-base gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice hpijs hplip hplip-data initscripts libgnomebt0 libgtk2-perl libsnmp9 locales nautilus-sendto parted
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-gadfly python-htmlgen
  python-htmltmpl python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-libxml2
  python-mysqldb python-netcdf python-pam python-parted python-pexpect python-pgsql python-pylibacl python-pyopenssl
  python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xml python-xmpp sysvinit
  ubiquity ubiquity-frontend-gtk ubiquity-ubuntu-artwork ubuntu-artwork ubuntu-minimal xterm
0 upgraded, 0 newly installed, 0 to remove and 66 not upgraded.
```


Any help would be much appreciated :D

---

### Post by scrooge_74 on 2007-01-09
No expert there but did you first did a sudo apt-get update before doing apt-get upgrade

i don't trust the update manager anyway so I do it manually

---

### Post by $teve on 2007-01-10
yes I ran the update before the upgrade. The update executes fine without any errors but the upgrade always holds back those 66 packages. 

To be honest I dont think those packages should be installed so its just more of an annoyance  why they keep showing in the update manager.

Thanks for the help anyway :)  if you have any other ideas I would be greatful

---

### Post by $teve on 2007-01-10
UPDATE: I have solved this problem after I discovered that it was a dependency issue. I simply installed the packages individually, i.e: 
```
sudo apt-get install python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xmpp
```

One thing to note is that I did have to download and re-install some of my current versions of the above packages using "dpkg -i xxx.deb" to satisfy some of the dependency issues I mentioned.

---

### Post by larpon on 2007-01-19
Awesome fix.. thx!

---

