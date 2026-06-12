---
title: "SuperUser"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by BeeZ on 2005-06-02
how to become SuperUser in ubuntu 5.04?

is it neded to install Divx and other codec's?

cause now I get the following erros when I try to open the ./install.sh file



==>

jacob@ubuntujacob:~/Desktop/divx4linux-20030428$ ./install.sh


./install.sh: line 6: /etc/ld.so.conf: Toegang geweigerd
./install.sh: line 7: /etc/ld.so.conf: Toegang geweigerd
cp: cannot create regular file `/usr/local/lib/libdivxdecore.so': Toegang geweigerd
cp: cannot create regular file `/usr/local/lib/libdivxencore.so': Toegang geweigerd
cp: cannot create regular file `/usr/local/include/decore.h': Toegang geweigerd
cp: cannot create regular file `/usr/local/include/encore2.h': Toegang geweigerd
cp: cannot create regular file `/usr/local/include/portab.h': Toegang geweigerd
chown: cannot access `/usr/local/lib/libdivxencore.so': Onbekend bestand of map
chmod: cannot access `/usr/local/lib/libdivxencore.so': Onbekend bestand of map
ln: creating symbolic link `/usr/local/lib/libdivxencore.so.0' to `/usr/local/lib/libdivxencore.so': Toegang geweigerd
chown: cannot access `/usr/local/lib/libdivxencore.so.0': Onbekend bestand of map
chmod: cannot access `/usr/local/lib/libdivxencore.so.0': Onbekend bestand of map
chown: cannot access `/usr/local/lib/libdivxdecore.so': Onbekend bestand of map
chmod: cannot access `/usr/local/lib/libdivxdecore.so': Onbekend bestand of map
ln: creating symbolic link `/usr/local/lib/libdivxdecore.so.0' to `/usr/local/lib/libdivxdecore.so': Toegang geweigerd
chown: cannot access `/usr/local/lib/libdivxdecore.so.0': Onbekend bestand of map
chmod: cannot access `/usr/local/lib/libdivxdecore.so.0': Onbekend bestand of map
/sbin/ldconfig: Can't create temporary cache file /etc/ld.so.cache~: Permission denied



<==

---

### Post by netrattler on 2005-06-02
The sudo command is how you can do administration things, for example 
sudo apt-get update. So just type sudo in front of it and you will be fine.

Joe

---

### Post by BeeZ on 2005-06-02
[QUOTE=netrattler]The sudo command is how you can do administration things, for example 
sudo apt-get update. So just type sudo in front of it and you will be fine.

Joe[/QUOTE]
 ah thx man :)

---

