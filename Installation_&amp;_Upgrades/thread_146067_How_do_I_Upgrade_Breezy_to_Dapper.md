---
title: "How do I Upgrade Breezy to Dapper"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by jackdirt on 2006-03-17
I apologize if this is some where in the forums, but I searched and could not find it. 

I decided I am willing to take the plunge into the beta version of Dapper but I don't want to go through the pain of reinstalling ubuntu is there a way to upgrade to it and get all the benefits of the new gnome that come with it? Maybe compiz too. 

I tried sudo apt-get update but not sure what that did. 

Any and all help is greatly appreciated. 

Thank You

---

### Post by Zeroangel on 2006-03-17
sudo apt-get dist-upgrade

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=jackdirt]I tried sudo apt-get update but not sure what that did. [/QUOTE]

sudo apt-get update is used after you make changes to your /etc/apt/sources.list file to refresh the repositores.

---

### Post by FizDev on 2006-03-17
[QUOTE=bluevoodoo1]sudo apt-get update is used after you make changes to your /etc/apt/sources.list file to refresh the repositores.[/QUOTE]

The changes bluevoodo1 is talking about are changing the "breezy" to "dapper" in the sources.list file.

---

### Post by bluevoodoo1 on 2006-03-17
[QUOTE=FizDev]The changes bluevoodo1 is talking about are changing the "breezy" to "dapper" in the sources.list file.[/QUOTE]

Well yes, one will have to change all the instances of "breezy" to "Dapper". But I was just commenting in general (to answer jackdirt's question as they were "unsure of what it did"). If you change your sources.list file in any way (for example, adding another repository) you have to run sudo apt-get update to update the sources.list file.

---

### Post by jackdirt on 2006-03-17
oh ok that makes sense so once i do the dist-upgrade need to change all instance of breezy to dapper

thanks

---

### Post by aysiu on 2006-03-17
[QUOTE=jackdirt]oh ok that makes sense so once i do the dist-upgrade need to change all instance of breezy to dapper

thanks[/QUOTE] This is the order:

1. Change sources.list
2. update
3. dist-upgrade

---

### Post by bluevoodoo1 on 2006-03-17
It is easily explained here...
[http://ubuntuforums.org/showpost.php?p=779468&postcount=2](http://ubuntuforums.org/showpost.php?p=779468&postcount=2)

---

### Post by landotter on 2006-03-17
Just be aware that you can slightly break your system doing this, often it's X that breaks and editing xorg.conf can fix it.

So you'll need to have a console editor installed just in case. Don't do Vi? Then install Nano. You'll learn it instantly.

You can also try to reconfigure a broken xserver with :
[$ sudo dpkg-reconfigure xserver-xorg]("http://ubuntuforums.org/$%20sudo%20dpkg-reconfigure%20xserver-xorg")

---

