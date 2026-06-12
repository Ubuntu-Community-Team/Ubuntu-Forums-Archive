---
title: "Upgrade help"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by MeThePeople on 2006-12-24
Hi, i just recently made the switch over to linux and as a what you would call advanced windows user im picking up linux pretty quick with the help of ubuntu of course. my problem as of now is i downloaded version 6.10 from ubuntu.com. I did a no cd install using grub so i dont have a cd to reinstall. For some reason everything is saying i have 5.10 breezy badger edition installed. when i enter gksu "update-manager -c"  in console it says your system is up to date but also has a pop up window saying there is a new release of ubuntu available. A new release with the codename 'edgy' is available. Please see [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/) for upgrade instructions. that site takes me to the same place i originally downloaded 6.10 from. anyone have any clues to how i can upgrade without redownloading and doing a fresh install?

---

### Post by PriceChild on 2006-12-24
Please post the output of
```
cat /etc/apt/sources.list
```

---

### Post by MeThePeople on 2006-12-24
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse

---

### Post by PriceChild on 2006-12-24
That's the only thing displayed?

---

### Post by MeThePeople on 2006-12-24
yes just the one line

---

### Post by PriceChild on 2006-12-24
please type```
gksudo gedit /etc/apt/sources.list
```Replace the entire file that appears with```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
```Save and exit.
 
Then run```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```And tell me how that goes.

---

### Post by MeThePeople on 2006-12-24
this is the results

root@ubuntu:~# gksudo gedit /etc/apt/sources.list
root@ubuntu:~# sudo apt-get update
Get:1 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy Release [30.9kB]
Get:3 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/main Packages [585kB]
Get:4 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:5 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/main Sources [232kB]
Get:6 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:7 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:8 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:9 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/universe Sources [915kB]
Get:10 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Fetched 4212kB in 11s (358kB/s)
Reading package lists... Done
root@ubuntu:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~#

---

### Post by PriceChild on 2006-12-24
Please please please don't run in a root terminal. [uwiki]RootSudo[/uwiki]

Please just use sudo for root access when needed.

now run:
```
gksudo "update-manager -d"
```

---

### Post by MeThePeople on 2006-12-24
I ussualy dont run in root but it was the only way i could save changes to sources.list.

and as for running gksudo "update-manager-d"  i am having the same problem still and have included a screenshot

[IMG]http://img148.imageshack.us/img148/4209/screenshot1yq2.png[/IMG]

---

### Post by PriceChild on 2006-12-24
```
gksudo gedit /etc/apt/sources.list
```Replace every instance of "breezy" with "dapper" then```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```do another upgrade and dist-upgrade to make sure, then restart your computer.

Repeat this process with "edgy".

---

### Post by alecjw on 2006-12-24
And change "ax" to your contry code (eg gb, fr, de, es, us etc) in sources.list, it will get you to a mirror nearer to you.

---

### Post by MeThePeople on 2006-12-24
im still in the process of upgrading dapper and i got this 
Configuration file `/etc/login.defs'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** login.defs (Y/I/N/O/D/Z) [default=N] ?
just curious as to which to choose and also will i choose the same option when i do this for edgy?

---

### Post by alecjw on 2006-12-24
> **MeThePeople said:**
> im still in the process of upgrading dapper and i got this 
Configuration file `/etc/login.defs'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** login.defs (Y/I/N/O/D/Z) [default=N] ?
just curious as to which to choose and also will i choose the same option when i do this for edgy?

Press Y, unless you've already customised your system.

---

### Post by PriceChild on 2006-12-24
Y

---

### Post by MeThePeople on 2006-12-24
after i asked that last question i afked for 10 min only to find my comp froze. after reboot i am now getting this

brian@ubuntu:~$ sudo apt-get update
Get:1 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper Release
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/main Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/main Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/universe Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/universe Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/multiverse Sources
Fetched 1B in 0s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
brian@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
brian@ubuntu:~$
 
you begged me not to do root so i have no clue what to do

---

### Post by alecjw on 2006-12-24
> **MeThePeople said:**
> after i asked that last question i afked for 10 min only to find my comp froze. after reboot i am now getting this

brian@ubuntu:~$ sudo apt-get update
Get:1 [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper Release
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/main Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/main Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/universe Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/universe Sources
Hit [http://ax.archive.ubuntu.com](http://ax.archive.ubuntu.com) dapper/multiverse Sources
Fetched 1B in 0s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
brian@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
brian@ubuntu:~$
 
you begged me not to do root so i have no clue what to do

Put sudo in front of a command to run it as root. Eg:
```
sudo dpkg --configure -a
```

---

