---
title: "root pwd"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by tjmoes on 2006-07-18
:confused: I upgraded to v6.06 yesterday now i cant get into my root wont accept any of my pwd that i thot was the pwd  i wood hate to reinstall](*,)

---

### Post by taurus on 2006-07-18
What root password?  Did you create one because you run it with the sudo command?

---

### Post by tjmoes on 2006-07-18
I tried to do a sudo chroot (after reading the help section) with my user login and that didnt work so tried to login as root with no success

---

### Post by taurus on 2006-07-18
You can't log in as root since the account, root, is locked.  Do you belong to the right groups?  Log into your account and open a terminal, Applications -> Accessories -> Terminal, and type

```

id

```
Do you see both adm & admin in there?  Otherwise, just paste the output here and we can go from there.

---

### Post by tjmoes on 2006-07-18
uid=1000(ted) gid=1000(ted) groups=4(adm) ,20(dialout) ,24(cdrom) ,25(floppy) ,29(audio) ,30(dip) ,44(video) ,46(plugdev) ,104(lpadmin) ,105(scanner) ,106(admin) ,1000(ted)

---

### Post by taurus on 2006-07-18
From a terminal, what happens when you run these two commands?

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by tjmoes on 2006-07-18
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [43.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [36.8kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [25.0kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [9082B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Fetched 182kB in 8s (21.9kB/s)
Reading package lists... Done
ted@teds:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  linux-image-2.6.15-26-386
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.6MB of archives.
After unpacking 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by taurus on 2006-07-18
Well, looks like sudo is working just fine for you then.  If you need to run something as root from now on, then do

```

sudo <command>

```

---

### Post by tjmoes on 2006-07-18
I cant get into root to change my permissions no natter what command i use i gave me rwe permisions thru gnome users and groups link but still cant write to any folder( trying to install new java bin)

---

### Post by aysiu on 2006-07-18
I think you're missing something. You don't need to get into root.

*sudo* gives you temporary root privileges.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

