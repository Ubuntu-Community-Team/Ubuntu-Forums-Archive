---
title: "Trouble mounting existing zfs pool after new install 20.04"
date: 2020-10-31
forum: Installation &amp; Upgrades
---

### Post by oehq2 on 2020-10-31
My boot drive recently crashed and after a fresh install of a new boot drive and Ubuntu 20.04 I am now unable to mount the zfs pool created in 18.04
I have performed the following commands
```
jph@jph-HEFFSVR2:~$ sudo zfs get all

jph@jph-HEFFSVR2:~$ sudo zpool import -f heffpool

jph@jph-HEFFSVR2:~$ sudo zfs list

NAME             USED  AVAIL     REFER  MOUNTPOINT
heffpool        15.0T  5.13T      219K  /heffpool
heffpool/udata  15.0T  5.13T     15.0T  /heffpool/udata
```
I am then able to see the pool  using the zfs list command however it does not seem to be mounted?

I tried using zfs  set mountpoint command but it does not seem to work?
```
jph@jph-HEFFSVR2:~$ sudo zfs set mountpoint=/heffpool heffpool 
jph@jph-HEFFSVR2:~$ sudo zfs set mountpoint=/heffpool/udata heffpool/udata
jph@jph-HEFFSVR2:~$ sudo zfs list
NAME             USED  AVAIL     REFER  MOUNTPOINT
heffpool        15.0T  5.13T      219K  /heffpool
heffpool/udata  15.0T  5.13T     15.0T  /heffpool/udata
```
when I do a LS command in the root it shows the heffpool folder but it is empty?
```
jph@jph-HEFFSVR2:~$ ls
Desktop    Downloads  Music     Public     Videos  Documents  heffpool   Pictures  Templates
```
P.S.  If I reboot the machine I have to redo:```
sudo zpool import -f heffpool
```…again in order to see the pool in the zfs list?

Any Help on making the Import permanent and having the pool auto mount on startup is greatly appreciated

Thank you

Jim

---

