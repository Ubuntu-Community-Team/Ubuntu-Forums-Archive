---
title: "problems to upgrade aircrack-ng"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by ercolino on 2011-09-24
Hi all.

I know that aircrck-ng is in ubuntu repositories and shpuld be enough to do something like 
sudo apt-get install aircrack-ng

But,

I don't think that ubuntu reporsitories have the latest version of aircrack-ng. This said, I downloaded the latest version from aircrack-ng, I proceeded to tar the file. After tar, I tried to do sudo make and I get the following error: 

caliban@caliban-Notebook-unter:~$ cd /home/caliban/Desktop/aircrack-ng-1.1
caliban@caliban-Notebook-unter:~/Desktop/aircrack-ng-1.1$ sudo make
make -C src all
make[1]: Entering directory `/home/caliban/Desktop/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/caliban/Desktop/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/caliban/Desktop/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/caliban/Desktop/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/caliban/Desktop/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:4189:8: error: array subscript is below array bounds
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/caliban/Desktop/aircrack-ng-1.1/src'
make: *** [all] Error 2

Any insights?

---

### Post by CharlesA on 2011-09-24
Look at the [docs]("http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=b513c0ccaa86708c0b4210f5e766cc62") for aircrack.

---

