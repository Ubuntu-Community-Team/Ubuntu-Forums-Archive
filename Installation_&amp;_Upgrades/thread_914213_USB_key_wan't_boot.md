---
title: "USB key wan't boot"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by zwygart on 2008-09-08
Hi everybody,

I'm coming back with a problem. Last week I bought a USB key Verbatim 16G. I wanted to transfer all the files from my 8G to the 16G (on XP)(3G of data). This took about 7 to 8 hours with many falls and errors. I lost some data. But this is not so difficult. I want to install Puppy and Ubuntu on my key. I tried without formatting but the bios says invalid system disk. I tried with gtparted on LiveCD Ubuntu 6.10 but first time it don't let my do anything and second time I could not make more than 1 primary partition. When I wanted to make a backup of my key I saw a other problem(I was able to make the backup). I saw that Ubuntu and XP found 170G of data on a key of 16G.:lolflag: I was wondered about this. It is a directory which contains others and files with crazy names like "bÔ¶ýàÕáý.xÛd" and "»°ƒg³Ã.vó". Also this files where made some in 1961 and others in 2106. I tough we are in 2008. The problem is that I can't delete, move or rename this files. I use portableFirefox on XP and it is very slow(especially during download), may it be in relation with this? Coming back to my boot problem. When in run fdisk it prints this about my key:
```
Disque /dev/sda: 16.1 Go, 16173236224 octets
64 têtes, 32 secteurs/piste, 15424 cylindres
Unités = cylindres de 2048 * 512 = 1048576 octets

Cela ne ressemble pas à une table de partition.
Probablement vous avez sélectionné le mauvais périphérique.

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   ?      945327     1849555   925929529+  68  Inconnu
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2   ?      649505      912677   269488144   79  Inconnu
La partition 2 ne se termine pas sur une frontière de cylindre.
/dev/sda3   ?      263179      945973   699181456   53  OnTrack DM6 Aux3
La partition 3 ne se termine pas sur une frontière de cylindre.
/dev/sda4   ?      680971      680981       10668+  49  Inconnu
La partition 4 ne se termine pas sur une frontière de cylindre.

Les entrées de la table de partitions ne sont pas dans l'ordre du disque

```

It's french and means "This is not a partition table, maybe you have selected the wrong one","Partition 1,2,3,4 don't finish on a cylinder". This is probably why I can't boot. But how save is formatting looking at [http://ubuntuforums.org/showthread.php?t=912243&highlight=USB+boot&page=2](http://ubuntuforums.org/showthread.php?t=912243&highlight=USB+boot&page=2)
and how to do?

At home I have 6.10 and this will be the way I will dist-upgrade. Are they any special suggestion or can I copy only the ISO on the computer? 

N.B.: Hoping this will solve the problem of my Nvidia driver.

Thanks for any help and suggestion.

---

### Post by Pumalite on 2008-09-08
Use rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by zwygart on 2008-09-10
Is there others opinion?

I don't like using CD's, I prefer USB key but I have to format it, is this save?

---

