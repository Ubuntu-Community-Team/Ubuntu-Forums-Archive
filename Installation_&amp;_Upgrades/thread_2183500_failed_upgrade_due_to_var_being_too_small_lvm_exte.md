---
title: "failed upgrade due to /var being too small lvm extend needs var unmount"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by samusz on 2013-10-25
I have a failed upgrade due to /var being too small : 
```
-------------snip-----------
Calcul des modifications en cours

Espace libre insuffisant sur le disque 

La mise à niveau a échoué. La mise à niveau a besoin de 2 542 M 
d'espace libre sur le disque « /var ». Veuillez libérer un espace 
supplémentaire de 312 M sur le disque « /var ».
-------------snip-----------
```

Since var is on lvm I wanted to expand /VG/var 

I had 10 Go not used so I formated that with 
and got sda7 
I then added sda7 to VG 
with the lvextend thus I get 

```
root@AO722:/# lvscan
  ACTIVE            '/dev/VG/root' [50,00 GiB] inherit
  ACTIVE            '/dev/VG/home' [186,26 GiB] inherit
  ACTIVE            '/dev/VG/var' [15,80 GiB] inherit
```

but if I look at the var partition it is still small : 


```
root@AO722:/# df -h 
Sys. de fichiers    Taille Utilisé Dispo Uti% Monté sur
/dev/mapper/VG-root    50G    8,2G   39G  18% /
none                  4,0K       0  4,0K   0% /sys/fs/cgroup
udev                  849M    4,0K  849M   1% /dev
tmpfs                 174M    920K  173M   1% /run
none                  5,0M       0  5,0M   0% /run/lock
none                  866M    228K  865M   1% /run/shm
none                  100M     36K  100M   1% /run/user
/dev/sda1             2,4G    363M  2,0G  16% /boot
/dev/mapper/VG-home   187G    115G   72G  62% /home
root@AO722:/# 
root@AO722:/# 
root@AO722:/# df -h /var/
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
-                  3,3G    951M  2,2G  31% /var
```

>> weird it doesn't show ** /var/** on df -h !

I woud love to use **fsadm** as I didn't used the -r flag when I did lvextend but for that I need to unmount var 

Any idea how to do that ? It thays /var is in use .... do I need to reboot in single user mode or else ? 

thanks for all help 

Samusz

Edit: 

after installing system-config-lvm I see that none of the 
/dev/mapper/VG-home
/dev/mapper/VG-root
/dev/mapper/VG-var 
are initialised. 

Who come ?! 

Any help on lvm greatly apreciated. 
Also I was wondering if moving the /var partition would be a possible way to go...

---

