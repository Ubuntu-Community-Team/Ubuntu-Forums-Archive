---
title: "Xubuntu/Ubuntu hybrid install, aptitude's fault? O_O"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by urbandryad on 2006-06-22
Hi! I did a server install of ubuntu breezy, then upgrades it to all the latest breezy, then I did the distro upgrade, because I didn't want my installation of xubuntu to take a billion years, which it would do if I did a dist-upgrade AFTER installing xubuntu. As it is my install of Dapper took less than four hours.

HOWEVER, I think I made a mistake by using aptitude to install xubuntu. I seem to have a good number of Gnome/Ubuntu additiont to my desktop. LIke, turning on the computer gives me the ubuntu orange logo with the loading screen, then of course the xfce mouse in a wheel and  then the xubuntu login. Shut down, however, gives me xubuntu, and then the black screen with font, (which is normal for my computer).

Finally, I have things like Alacarte and some gnome stuff installed, and under the startup gnome seems to be one of the login options.

How do I fix this, without having to remove the xubuntu default stuff that might also be shared with gnome? Or do I have a choice in the matter?

Thanks!

---

### Post by user1397 on 2006-06-22
try this guide: [http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

---

### Post by urbandryad on 2006-06-22
Thanks! That worked! I still get the orange ubuntu start up screen with the lists of functions. Oh well, better than nothing I suppose. XD

---

### Post by user1397 on 2006-06-22
[quote=urbandryad]Thanks! That worked! I still get the orange ubuntu start up screen with the lists of functions. Oh well, better than nothing I suppose. XD[/quote]no prob, to fix that other problem, paste this command in a terminal (applications > accessories > terminal): ```
 sudo update-alternatives --config usplash-artwork.so
```and choose the xubuntu one.  then paste this: ```
sudo dpkg-reconfigure linux-image-`uname -r`
```it should work.

---

### Post by aysiu on 2006-06-22
[QUOTE=urbandryad]Thanks! That worked! I still get the orange ubuntu start up screen with the lists of functions. Oh well, better than nothing I suppose. XD[/QUOTE]
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by user1397 on 2006-06-22
by the way, aptitude is actually **better** than apt-get, because it takes care of dependencies a lot better.  in the future, if you want to try out kde or gnome, paste this in a terminal: ```
sudo aptitude update
```and then either ```
sudo aptitude install ubuntu-desktop (or kubuntu-desktop)
```you must do the aptitude update, or else aptitude doesn't really work.  if you want to later remove these packages, you would just do ```
sudo aptitude remove ubuntu-desktop (or kubuntu-desktop)
```and it would remove all the packages that came along with it.

---

### Post by urbandryad on 2006-06-23
Hiyo, I got this error during the second part of the artwork instructions.


WARNING: Module /lib/modules/2.6.15-25-powerpc/madwifi-ng/new_ath_pci.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.15-25-powerpc/madwifi-ng/new_ath_rate_sample.ko ignored, due to loop
WARNING: Loop detected: /lib/modules/2.6.15-25-powerpc/volatile/new_ath_hal.ko which needs new_ath_hal.ko again!
WARNING: Module /lib/modules/2.6.15-25-powerpc/volatile/new_ath_hal.ko ignored, due to loop

---

