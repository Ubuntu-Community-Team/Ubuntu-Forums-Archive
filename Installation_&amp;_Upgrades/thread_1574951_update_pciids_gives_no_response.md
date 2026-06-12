---
title: "update pciids gives no response"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by gimmemore on 2010-09-15
update pciids gives no response in ubuntu 10.04.
update usbids gives ouch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.
kamal@kamal-desktop:~$ sudo updatr-usbids
sudo: updatr-usbids: command not found
 also cant play tvtime

---

### Post by dino99 on 2010-09-15
oem@dub:~$ sudo update-usbids && sudo update-pciids
[sudo] password for oem: 
--2010-09-15 11:54:35--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Résolution de [www.linux-usb.org](www.linux-usb.org)... 216.34.181.97
Connexion vers [www.linux-usb.org|216.34.181.97|:80](www.linux-usb.org|216.34.181.97|:80)... connecté.
requête HTTP transmise, en attente de la réponse... 200 OK
Longueur: 428350 (418K) [text/plain]
Sauvegarde en : «/var/lib/usbutils/usb.ids.new»

100%[======================================>] 428 350      258K/s   ds 1,6s    

2010-09-15 11:54:37 (258 KB/s) - «/var/lib/usbutils/usb.ids.new» sauvegardé [428350/428350]

Done.
Downloaded daily snapshot dated 2010-08-27 03:15:02

---

### Post by gimmemore on 2010-09-16
"sudo update-usbids && sudo update-pciids"
i have tried this.....does not give any response!

---

