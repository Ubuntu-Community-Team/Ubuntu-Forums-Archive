---
title: "Is ubuntu 6.06 LTS without root user id"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2006-12-17
Is ubuntu 6.06 LTS without root user id  ?
Just only user-admin ?

I want add symbolic link as below, but Permission denied.
moonhk@edubuntu:/usr/bin$ ln -s gcc-4.0 $PWD/gcc
ln: creating symbolic link `/usr/bin/gcc' to `gcc-4.0': Permission denied
moonhk@edubuntu:/usr/bin$

---

### Post by ajgreeny on 2006-12-17
Add sudo to the beginning of your command entry and then your user password and it should work.

Have a look at:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by moonhk on 2006-12-17
Thank. it works.

moonhk@edubuntu:~$ sudo -i
cdroot@edubuntu:~# cd /usr
root@edubuntu:/usr# cd bin
root@edubuntu:/usr/bin# ls -lt gcc*
-rwxr-xr-x 1 root root 93584 Apr 21  2006 gcc-4.0
-rwxr-xr-x 1 root root 16245 Apr 21  2006 gccbug-4.0
root@edubuntu:/usr/bin# ln -s gcc-4.0 gcc
root@edubuntu:/usr/bin# exit
logout
moonhk@edubuntu:~$ gcc
gcc: no input files


moonhk@edubuntu:/usr/bin$ ls -lt gcc*
lrwxrwxrwx 1 root root     7 2006-12-17 18:43 gcc -> gcc-4.0
-rwxr-xr-x 1 root root 93584 2006-04-21 06:22 gcc-4.0
-rwxr-xr-x 1 root root 16245 2006-04-21 06:13 gccbug-4.0
moonhk@edubuntu:/usr/bin$

---

