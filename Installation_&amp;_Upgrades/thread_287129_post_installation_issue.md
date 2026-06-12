---
title: "post installation issue"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by faramog on 2006-10-28
I installed from CD (6.06). I have not been able to play mp3's or mpeg files.

It seems from general help that there is a 'maybe' solution ([http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29))
but this requires me to change the permissions of a file. Chmod does not work as I need to be a superuser. The problem is that during installation there is only one password asked for, that of the user.

Any ideas how to get into SU mode (and also solve the codec problem

Thanks

---

### Post by meng on 2006-10-28
prepend commands with sudo
e.g.
sudo chmod (etc)
when asked for a password, enter the userpassword
More info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by faramog on 2006-10-28
thanks ... now to get the rest installed

what is 'sudo' ?

---

### Post by meng on 2006-10-28
superuser-do:
basically lets you perform a single command/script with superuser privileges, using the user password for authorization, assuming the user is recognized as having admin privileges (which the default first user always has).

---

### Post by tpg on 2006-10-28
Basically it allows you to run the following command with root privileges (although it actually allows you to run a command as any user). Type
```
man sudo
```
at a terminal for more information.

---

### Post by TheWizzard on 2006-10-28
please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) as meng suggested. explaines everything you need to know.
the default way to manage users and administrators is different in ubuntu compared to most linux distributions. but the logic is very clear! ubuntu is meant for the desktop and in most situations the user that installs the os is also the one that maintains the box. therefore the first user gets full sudo permissions.

---

