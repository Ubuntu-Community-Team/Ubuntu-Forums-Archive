---
title: "Post-installation error 139"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by cristianrosa on 2007-11-18
A few days ago there was an update of the eog package. I installed it, and when it was running its post-installation script i got the following message
> dpkg: error al procesar eog (--configure):
 el subproceso post-installation script devolvió el código de salida de error 139
and now all the packages that i want to update fails because the eog configuration is still pending.
If i try to remove eog i get a seg fault!!
> Desinstalando eog ...
Segmentation fault (core dumped)
dpkg: error al procesar eog (--remove):
 el subproceso post-removal script devolvió el código de salida de error 139
Se encontraron errores al procesar:
 eog

The message is in spanish but i think it is understandable.

Any suggestions, i would like to fix this to avoid reinstalling the entire system.
Thanks!

---

### Post by cristianrosa on 2007-11-19
I fixed it!, the seg fault was caused by scrollkeeper when updating it's database. It seems it was broken somehow, so i just reinstalled it, and it rebuilded the database. The system is working fine now. :)

---

### Post by The_Aviator on 2008-06-02
Thank you, thank you, thank you......that worked a treat for me too!

---

