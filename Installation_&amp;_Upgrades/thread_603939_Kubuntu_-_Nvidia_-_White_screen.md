---
title: "Kubuntu - Nvidia - White screen"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by GEdWay Ingasia on 2007-11-05
I have a problem whit starting Kububuntu Install went well..
I used : Kubuntu 7.10 i38 (alternative cd (not live))
I think iam online internet
This is the link to the problem Video made around 1 min.. 
[http://www.youtube.com/watch?v=IS1UTJzAp7E](http://www.youtube.com/watch?v=IS1UTJzAp7E)
Is link broken search for Tig3rgutt3n only one video
--
-
--
Screen is white.. whith green Stripes downwise..(top to buttom)(some few blue red and some other colors that are short)
some short going side to side diffrent colors
--
-
--
Specs on Pc
Intel 915 3,0ghz
gigabyte 775 itel mainboard
Nvidia g-force 6600 256mb(ram) pci ex
g-15 locgitech keyboard SE editon
g-5 locgiteach mouse
4gb (2x2gb)pc2 Kingston pc5300 Dimm 667mhz ram\memory "cl-5" 
dvd burner aopen 52x48x48'
usb 2
--
-
--
Plz some1 help me.. Iam so lost :P
Ever how Ty for all help in advance and for all trying to help:D

---

### Post by GEdWay Ingasia on 2007-11-06
Yeah since no1 could help i helped my self
reconfiguer xserver and set it to "NVitia" vesa and push enter all way true:)
atp-get update 
and start kdm:) and wolla:) atleast get into Linux;)

---

### Post by dr_liu on 2008-01-30
i got a set of hardware similar to yours , but i could not login linux even the recovery mode

---

### Post by Partyboi2 on 2008-01-30
> **dr_liu said:**
> i got a set of hardware similar to yours , but i could not login linux even the recovery mode
Are you having the same problems as the original poster was having or are you having problems with login (Where you are asked for username and password and it won't let you go past that screen)
If its the same problem as the original poster then when you get to the white screen press Ctrl+Alt+F2
 and type
```
sudo dpkg-reconfigure xserver-xorg
```then choose nv for the driver and answer all the questions right through. If unsure choose the default answers. then type
```
startx
```If that does not work then do it again but choose vesa as the driver. (This will get you to the desktop where you can install the correct drivers.

---

