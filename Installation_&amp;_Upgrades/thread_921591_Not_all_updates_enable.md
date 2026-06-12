---
title: "Not all updates enable"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2008-09-16
hello all
today appear on my computer have 43 updates but noy i can select on the box for update....appear disable
how i can select this updates....??
thank you
I use Ubuntu 7.10
Regards...

---

### Post by manishtech on 2008-09-16
You can use the command line equivalent for the same. Dont worry command-line isnt so geeky or tough. Its just a matter of choice and additional option. The command for it is

```
sudo apt-get upgrade
```

---

### Post by Casper Hansen on 2008-09-16
> **manishtech said:**
> You can use the command line equivalent for the same. Dont worry command-line isnt so geeky or tough. Its just a matter of choice and additional option. The command for it is

```
sudo apt-get upgrade
```

Don't you have to run 

```
sudo apt-get update
```

first?

Or is it just me who's run?

---

### Post by Pumalite on 2008-09-16
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by chanfle on 2008-09-16
> **Pumalite said:**
> sudo apt-get update
sudo apt-get dist-upgrade

hi all
hhhmmm....in my update manager appear the new updates but i can't select or unselect the box....
how i can fix that????

---

### Post by Pumalite on 2008-09-16
Run the commands I gave you in the Terminal

---

### Post by manishtech on 2008-09-17
> **Casper Hansen said:**
> Don't you have to run 

```
sudo apt-get update
```first?

Or is it just me who's run?

I know we should run update first, but I hardly do so.

---

### Post by Pumalite on 2008-09-17
Bad habit

---

### Post by chanfle on 2008-09-17
ok...when i type 
```
sudo apt-get upgrade
```
appear this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  amarok amarok-xine bind9-host dnsutils evolution evolution-common
  evolution-plugins firefox firefox-gnome-support gimp gimp-data gimp-python
  gstreamer0.10-esd gstreamer0.10-plugins-good kdelibs-data kdelibs4c2a
  libbind9-30 libgnutls13 libisccfg30 libpoppler-glib2 libruby1.8 libsmbclient
  libxine1 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ntfs-3g openssh-client python-libxml2
  python2.5 python2.5-minimal ruby1.8 samba-common smbclient ssh-askpass-gnome
  transmission-cli transmission-gtk xserver-xorg-core yelp
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
```
So...this is updates i can't install....

regards...

---

### Post by manishtech on 2008-09-17
so first do a 
```
sudo apt-get update
```

---

### Post by lswest on 2008-09-17
Chances are these packages are missing a dependency and aren't being installed.  You can force it, but I recommend just waiting til the dependencies are all there (they get packaged at different rates).

---

### Post by chanfle on 2008-09-17
so....what i need to do...???

---

### Post by lswest on 2008-09-18
> **chanfle said:**
> so....what i need to do...???

Wait and check the updates later today, or tomorrow, and it should all work again.

---

### Post by Pumalite on 2008-09-18
The second command is:
sudo apt-get dist-upgrade

---

### Post by lanr01 on 2008-09-18
> **manishtech said:**
> so first do a 
```
sudo apt-get update
```

 when I try to do this, I get this error msg:  IN fact anything I try to do in the terminal i get this error msg..


rick@Main:~$ sudo apt-get dist-upgrade
[sudo] password for rick: 
rick is not in the sudoers file.  This incident will be reported.
rick@Main:~$

---

### Post by Pumalite on 2008-09-18
[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)
[http://ubuntuforums.org/showthread.php?t=865922](http://ubuntuforums.org/showthread.php?t=865922)
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

---

