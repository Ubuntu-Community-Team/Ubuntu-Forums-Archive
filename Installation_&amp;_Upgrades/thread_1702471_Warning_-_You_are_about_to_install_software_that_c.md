---
title: "Warning - You are about to install software that can't be authenticated"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by oygle on 2011-03-07
Todays updates, contained a message ..

**Warning**

You are about to install software that **can't be authenticated**. Doing this could allow a malicious individual to damage or take control of your system.

Here are the files ..

> 
avahi-autoipd (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
avahi-daemon (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
avahi-utils (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
firefox (version 3.6.14+build3+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
firefox-branding (version 3.6.14+build3+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
firefox-gnome-support (version 3.6.14+build3+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 3.6.15+build1+nobinonly-0ubuntu0.10.04.1
libavahi-client3 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-common-data (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-common3 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-core6 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-glib1 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-gobject0 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-qt3-1 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libavahi-ui0 (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
libmetacity-private0 (version 1:2.30.1-0ubuntu1) will be upgraded to version 1:2.30.1-0ubuntu1.1
libtiff4 (version 3.9.2-2ubuntu0.3) will be upgraded to version 3.9.2-2ubuntu0.4
linux-firmware (version 1.34.3) will be upgraded to version 1.34.4
metacity (version 1:2.30.1-0ubuntu1) will be upgraded to version 1:2.30.1-0ubuntu1.1
metacity-common (version 1:2.30.1-0ubuntu1) will be upgraded to version 1:2.30.1-0ubuntu1.1
python-avahi (version 0.6.25-1ubuntu6.1) will be upgraded to version 0.6.25-1ubuntu6.2
xulrunner-1.9.2 (version 1.9.2.14+build3+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1


I assumed it was okay, and went ahead. Any problems with that ?

Oygle

---

### Post by oygle on 2011-03-08
Is this a security risk or not ?

---

### Post by oygle on 2011-03-08
Is [this]("http://ubuntuforums.org/showthread.php?p=7001019#7001019") how to fix it ?

```

sudo apt-get remove debian-keyring debian-archive-keyring
sudo apt-get clean
sudo apt-get update
sudo apt-get -y install debian-keyring debian-archive-keyring

```

Oygle

---

### Post by oygle on 2011-03-11
Anyone ??

---

### Post by oldos2er on 2011-03-11
Can you post the output of **sudo apt-get update** ?

---

### Post by oygle on 2011-03-12
```

~$ sudo apt-get update

```

> 
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release.gpg                        
Ign [http://www.scootersoftware.com/](http://www.scootersoftware.com/) stable/non-free Translation-en_AU      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done


I did have to change the software source a few days ago, as the updates were stalling when I had the server as [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) , so I changed it to 'main server' , and the updates went okay.  By stalling, I mean the first part, where it goes and checks the archives.

Thanks,

Oygle

---

