---
title: "Aircrack ng 1.1 cant install error codes"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by mfenton2447 on 2010-09-13
Hello everyone, i would really be thankfull for anyhelp on this. im trying to install aircrack and i keep getting this error code. I am completely  new at this. I have ubuantu 10.10 or the latest edition. Im going to put the error code in here and if anyone knows what to do, please let me know.

Thank you

mike

mike@mike-laptop:~$ cd Downloads/
mike@mike-laptop:~/Downloads$ cd aircrack-ng-1.1/
mike@mike-laptop:~/Downloads/aircrack-ng-1.1$ make
make -C src all
make[1]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src'
make: *** [all] Error 2
mike@mike-laptop:~/Downloads/aircrack-ng-1.1$ sudo make install
[sudo] password for mike: 
make -C src install
make[1]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/mike/Downloads/aircrack-ng-1.1/src'
make: *** [install] Error 2

---

### Post by realzippy on 2010-09-13
Welcome!

1.
10.10 is still beta.Suggest using 10.04

2.You try to compile aircrack.
  No need to,aircrack is in the repos.To install:

  ```
sudo apt-get install aircrack-ng
```

3.Do not know what you want to do with aircrack,but "if completely new"
  you might get overwhelmed just after installing it.
  Anyway,there are lots of tutorials out there...good luck!

---

### Post by mfenton2447 on 2010-09-15
Hey,

Thank you for your reply. I am going to start using aircrack ng for my studies in internet security. I will try this when i get home. If this helps you understand my problem more. I downloaded it and am trying to install it from my computer. I am very very new to ubuantu so i still have a windows thought process. And i confused my os it is ubuantu 10.4 not 10.10 or what ever i wrote before.

Thank you

---

### Post by soad6 on 2010-09-19
ok hi ppls i have a problem with aircrack-ng. I have two wifi cards in my machine, one that is a belkin f5d7050 which supports injection and all good things, and the other is a realtek 8192sevB, which doesnt work with injection but does with monitor mode but doesnt set to mon0. However this isnt the problem, my problem is that with the belkin card is a usb card and when i plug it in and set it to monitor a channel and check it in airodump-ng or aireplay-ng i get mon0 is on channel -1. I wonder if anyone else has come across this?? the belkin card is set as wlan1 when inserted and and when put into monitor mode spawns a mon0 but mon0 is set to -1 as its channel even when i try : sudo aircrack-ng start wlan1 11. specified channel is 11, but it still says mon0 is -1.

---

