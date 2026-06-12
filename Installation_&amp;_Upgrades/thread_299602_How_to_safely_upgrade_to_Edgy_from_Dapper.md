---
title: "How to safely upgrade to Edgy from Dapper?"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Aleksandersen on 2006-11-14
Hi,

How to safely upgrade from Ubuntu 6.06 Dapper Drake to 6.10 Edgy. Eft?

The last time I attempted to upgrade I had [several issues](http://bonaveo.net/2006/10/edgy-real-is-kinda-edgy/) with the upgrade.

Are there any thing I should do before upgrading to ensure a smoother upgrade? Or tips or anything!?

---

### Post by TheWizzard on 2006-11-14
> **Aleksandersen said:**
> Hi,

How to safely upgrade from Ubuntu 6.06 Dapper Drake to 6.10 Edgy. Eft?

The last time I attempted to upgrade I had [several issues](http://bonaveo.net/2006/10/edgy-real-is-kinda-edgy/) with the upgrade.

Are there any thing I should do before upgrading to ensure a smoother upgrade? Or tips or anything!?


1) ask yourself why you do want to upgrade. 

2) make sure you backup both /home and /etc

3) a clean install is - in my opinion - always better than upgrading

---

### Post by aysiu on 2006-11-14
I agree with TheWizzard. The safest way to upgrade to Edgy is to [**create a separate /home partition**](http://www.psychocats.net/ubuntu/separatehome) and then do a clean reinstall.

You can also [**make a back up of your entire partition**](http://www.psychocats.net/ubuntu/partimage), so you have an easy way to restore Dapper should something go wrong.

---

### Post by Dubbayoo on 2006-11-14
The official method worked for me. It even solved an unsolvable problem I was having with Dapper.

---

### Post by int on 2006-11-14
upgrade for me all times work for me, but all times have problems in updating some packages, and when this happen you must don't reboot untill you can install everything without any errors, or packaged miss.

Type again 
> sudo apt-get dist-update
until nothing is missing to install, and happear 0 errors.

you may use, > apt-get install -f to install packaged with broken dep, or > apt-get removeto remove some broken packages, but at the end, finish everything with > sudo apt-get dist-update and you will secure upgrade.

---

### Post by ryan on 2006-11-16
I had a problem upgrading from Dapper via the reccomended method as the install would get to certain point and hang, there was some error messages and I checked the logs and found that the edgy upgrade couldn't upgrade some libraries. When I checked synaptic I found that the 2 offending packages were from a cvs which fritzed the package updater. I did a "force version" to a non cvs package and the upgrade went fine.

---

### Post by ryan on 2006-11-16
> **aysiu said:**
> I agree with TheWizzard. The safest way to upgrade to Edgy is to [**create a separate /home partition**](http://www.psychocats.net/ubuntu/separatehome) and then do a clean reinstall.

You can also [**make a back up of your entire partition**](http://www.psychocats.net/ubuntu/partimage), so you have an easy way to restore Dapper should something go wrong.


I had a question as I was trying to do a clean install on a system that had a messed up Edgy install. I got to a certain point and then I got a message that Xorg.conf was whacked and the installation would go no further. I figured it might be the "ati" driver that was set in Xorg.conf and tryed to change it but couldn't or the change wouldn't take. I guess since there was already a Edgy install it checked for the various conf files to see what was there and then tried to start the X server according to the "xorg.conf". I would still like to reinstall so I was thinking that before I shut down I would edit Xorg.conf to something vanilla like change "ati" for "vesa" in the driver section and hope that the install would go without any problems. Any thoughts on this ? Does this seem like a good approach to get past the "xorg" weirdness ? Tks

---

