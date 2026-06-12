---
title: "Upgrade: synaptic tries to deinstall some apps!"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by broseman on 2005-04-08
Hello community!

I'm trying to upgrade from warty to hoary by the help of [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)
following Pre-Upgrade > With hoary CD and Synaptic

Unfortunatly synaptic marks a lot of (excactly: 102(!)) apps for *removal*, i.e. even evolution. That can't be correct, is it?

Where is my mistake?

Thanks in advance,

 broseman

---

### Post by p!=f on 2005-04-08
Hi,

please post your /etc/apt/sources.list here.

---

### Post by broseman on 2005-04-08
[QUOTE=p!=f]Hi,

please post your /etc/apt/sources.list here.[/QUOTE]
 Thx for your help!
Here ist my sources.list. You will see that I used third party repositories a lot. Maybe this is the reason for my trouble?

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ unstable main main/debian-installer restricted restricted/debian-installer  

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse   
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse  
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted   
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

# deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./ 

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

# deb [http://tutuxclan.free.fr/debs/](http://tutuxclan.free.fr/debs/) ./ 

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main universe

---

### Post by p!=f on 2005-04-08
[QUOTE=broseman]
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ unstable main main/debian-installer restricted restricted/debian-installer  

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse   
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse  
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted   
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

# deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./ 

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

# deb [http://tutuxclan.free.fr/debs/](http://tutuxclan.free.fr/debs/) ./ 

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 

# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main universe[/QUOTE]
The easiest method (if you have a network connection) is to replace the above links with:
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse   
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted   
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

# deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./ 

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 

# deb [http://tutuxclan.free.fr/debs/](http://tutuxclan.free.fr/debs/) ./ 

# Hoary Backports
# deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
# deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

# deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 

Run 
```

sudo apt-get update
sudo apt-get dist-upgrade

```
It should upgrade your machine to Hoary.

---

### Post by broseman on 2005-04-11
Thanks for your help!

You were right! I had a lot of trouble, when I tried to install from CD. It worked, when I used the install via internet.

> Upgrade tool --Matt Zimmerman, Wed, 06 Apr 2005 21:34:59 +0100

We are in fact planning a simplified upgrade tool for the Ubuntu 5.10 release, in the same spirit as update-notifier, update-manager and gnome-app-install 
from [wiki.ubuntulinux.org](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=121760) 

We definitly need this...

---

