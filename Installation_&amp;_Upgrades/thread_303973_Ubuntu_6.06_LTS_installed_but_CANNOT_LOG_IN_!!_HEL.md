---
title: "Ubuntu 6.06 LTS installed but CANNOT LOG IN !! HELP!"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by guillem on 2006-11-21
Hello there,
I downloaded the installation CD of Ubuntu 6.06 LTS, burned it, then boot from it and did install with the following partitioning specifications : 
12 Giga for root
251 Mega for boot
1 or 2 Giga for swap
81 Giga for home
50 Giga for windows. 
I did not reformat home/ and windows/ to avoid loosing my datas.

The installation finished perfectly, reboot the computer, I choose to boot ubuntu. It asked me for my username, then password and problems started. I had the following messages and don't know what to do : "
Your session only lasted 10 seconds. If you have not logged out yourself this could mean that there is some installation problem or you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."
I checked that I have enough disk space in every partition.
The error message also show me the xsessions-error file :
> /etc/gdm/PreSession/default : Registering your session with wtmp and utmp
> /etc/gdm/PreSession/default : Running : /usr/bin/sessreg -a -w  /var/log/wtmp -u  /var/run/utmp -x  "/var/lib/gdm/ :0. Xservers" -h ""-l":0" "myusername"
> /etc/gdm/Xsession : Beginning session setup ...
> Could not set mode 700 on private per user gnome configuration directory '/home/myusername/.gnome2_private/' : Operation not permitted
                                              "
So..... I have no idea of what it means and what I should do to solve it. Can you help me please ??
bye
/guillem

---

### Post by Jussi Kukkonen on 2006-11-21
It looks like you don't have rights to open your own files... Try opening a virtual console (ctrl-alt-F1) and  login there, or if that doesn't work boot into "Safe Mode". Then take a look at your home dir and some of the files mentioned:
```
ls -al /home/
ls -al  /home/username/
```
if you are not the owner, or you do not seem to have the correct permissions, fix that:
```
chown -R username:username /home/username/
chmod -R u+rwX /home/username/
```
EDIT: you need to use sudo for the above commands if you logged in as yourself

---

### Post by guillem on 2006-11-21
Ok when I made ls -al command I saw all files with the permissions rwx followed by numbers like 500 500 except for some files which had root root or  username username owners. So I wrote what you said about chown -R ... first it did not work saying operation not permited. So I tried the same command in sudo mode and finally it works great !!

Thanks a lot Jussi !!

---

