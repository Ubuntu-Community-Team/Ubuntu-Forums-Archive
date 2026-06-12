---
title: "Need Troubleshooting Advice on Installing File2Air"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by GutsyGibbonMarc on 2008-04-08
Not sure why it works but apparently more recent distros have slightly different wireless.h files?  Anyway, I edited the wireless.h file with an include statement to include the if.h file.  (#include <linux/if.h> at the top of the wireless. h file. Aparently, this statement was there in Feisty and some other releases but not in all.  That did it. ALL the errors went away.
________________________________________________
It seems simple. I have installed the LORCON drivers without issue. I run a make command and I get these errors.  Much searching and googling, I think it might have to do with some include statements in the wireless.h file but that is all I have.  Any help would be appreciated.

I am running 7.10

root@ds1:/usr/sw/file2air# ls 
CHANGELOG  crc.c  crc.o       file2air.h  packets  utils.c  utils.o 
common.h   crc.h  file2air.c  Makefile    README   utils.h 
root@ds1:/usr/sw/file2air# make 
cc -Wall -ggdb -g3 -pipe file2air.c -o file2air utils.o crc.o -lorcon -lm 
In file included from file2air.c:39: 
/usr/include/linux/wireless.h:650: error: expected specifier-qualifier-list before '__s32' 
/usr/include/linux/wireless.h:663: error: expected specifier-qualifier-list before '__u16' 
/usr/include/linux/wireless.h:677: error: expected specifier-qualifier-list before '__s32' 
/usr/include/linux/wireless.h:688: error: expected specifier-qualifier-list before '__u8' 
/usr/include/linux/wireless.h:704: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:717: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:744: error: expected specifier-qualifier-list before '__u8' 
/usr/include/linux/wireless.h:806: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:820: error: expected specifier-qualifier-list before '__u16' 
/usr/include/linux/wireless.h:834: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:842: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:851: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:863: error: expected specifier-qualifier-list before '__u16' 
/usr/include/linux/wireless.h:886: error: 'IFNAMSIZ' undeclared here (not in a function) 
/usr/include/linux/wireless.h:901: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:945: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:1046: error: expected specifier-qualifier-list before '__u32' 
/usr/include/linux/wireless.h:1064: error: expected specifier-qualifier-list before '__u16' 
make: *** [file2air] Error 1 
root@ds1:/usr/sw/file2air#

---

### Post by Kopfgeldjaeger on 2008-06-01
Wow... Thanks a bunch ;)

---

