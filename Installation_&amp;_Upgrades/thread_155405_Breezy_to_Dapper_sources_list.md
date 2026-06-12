---
title: "Breezy to Dapper sources list"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by Storm Rider on 2006-04-05
Hi,

I want to upgrade my Kubuntu Breezy to Dapper via dist-upgrade.  I did this and still have Breezy running.](*,) 

After reading through the forums, I see I have to edit my sources list from Breezy to Dapper.  Where is the darn list??

Is there anything else I have to do?

Thanks:)

---

### Post by aysiu on 2006-04-05
/etc/apt/sources.list

Gnome: Applications > Accessories > Terminal ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
KDE: KMenu > System > Konsole ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kwrite /etc/apt/sources.list
``` Dapper's still in testing, though, and may give you some breakage.

---

### Post by lemix on 2006-04-05
Im pretty sure that if you wanted to do it another way you can download the install disk and run synaptic off of it. I wouldnt install it without testing its integrety because of people that have errors like me and this guy...

[http://www.ubuntuforums.org/showthread.php?t=154889&page=2&highlight=ubuntu+dapper+install](http://www.ubuntuforums.org/showthread.php?t=154889&page=2&highlight=ubuntu+dapper+install)

But i burned the install disc and it said i could run synaptic off of it which would provide all of the base files for Dapper for you.

---

### Post by Storm Rider on 2006-04-06
[QUOTE=aysiu]/etc/apt/sources.list

Gnome: Applications > Accessories > Terminal ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
KDE: KMenu > System > Konsole ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kwrite /etc/apt/sources.list
``` Dapper's still in testing, though, and may give you some breakage.[/QUOTE]

Should I change this section of the sourecs list?  It seems to refer to the cd used for the istallation.
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

Thanks,:)

---

