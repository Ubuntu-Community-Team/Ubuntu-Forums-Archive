---
title: "Sis 671 chipset Linux driver 3D Not coming ?"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Biosteel on 2009-12-22
So boys after som research on the internet i believe that we have to use the 2D driver and stay without compiz and all the effects. Is it so that Sis and windows has a license agreement? Does Someone have any usefull feeback to spread some light over the situation.:confused:

---

### Post by aminmatrix on 2009-12-23
Je partage ici une solution pour installer un pilote fonctionnel en haute résolution pour les récents chipsets graphiques SIS 771/671 avec ubuntu 9.10
 Le chipset est correctement identifié par un lspci :
```

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```mais ne me permettait qu'un affichage en résolution 800x600 avec le pilote générique VESA. Toute tentative d'utilisation du pilote xserver-xorg-driver-sis se soldant par un écran noir.
 **Avertissement : La solution proposée n'est pas officielle, et fait appel à un pilote qui n'est pas inclus dans les dépôts ubuntu. Son utilisation se fait sous votre entière responsabilité, et à vos risques et périls.**


Pour l'installer, télécharger le paquet [xorg-driver-sisimedia]("http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb"), Gdebi se chargeant de l'installer.
Ce paquet remplacera votre fichier xorg.conf. Pour davantage de sécurité, faites une copie de votre fichier actuel, s'il existe.


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```En cas d'échec du nouveau pilote, vous pourrez rétablir votre fichier
fonctionnel en restaurant votre sauvegarde avec la commande :
```
sudo cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
```Après redémarrage de X, vous pouvez enfin profiter de votre résolution
optimale, bien plus confortable même si l'accélération 3D n'est pas
encore à l'ordre du jour avec ce chipset
```

xrandr
Screen 0: minimum 640 x 480, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       60.0* 
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0
``````
glxinfo | grep "direct rendering"
direct rendering: Yes
```

---

### Post by aminmatrix on 2009-12-23
> **Biosteel said:**
> So boys after som research on the internet i believe that we have to use the 2D driver and stay without compiz and all the effects. Is it so that Sis and windows has a license agreement? Does Someone have any usefull feeback to spread some light over the situation.:confused:
brother there no 3D effect in ubuntu for SIS mirage now :(:(:(:(:(:(

---

### Post by Biosteel on 2009-12-26
please for **** sace write in english german or swedish

---

### Post by Biosteel on 2009-12-30
but i can't even get a movie to play correctly though i have the 2D driver bit wont make the difference. why is everybody so quit in this thread ?

---

### Post by Elzigzag on 2009-12-31
Still without 3D for SiS 671/771,  huh? 
We, I mean in Latin American countries, are waiting for Los Reyes Magos (The Magi), may be I should ask them to bring the driver for me as a gift.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by Biosteel on 2010-01-05
> **Elzigzag said:**
> Still without 3D for SiS 671/771,  huh? 
We, I mean in Latin American countries, are waiting for Los Reyes Magos (The Magi), may be I should ask them to bring the driver for me as a gift.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

yes im still without the drivers like everybody i think ?. so the drivers for this laptop exists in the states ?

---

