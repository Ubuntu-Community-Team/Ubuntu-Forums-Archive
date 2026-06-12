---
title: "Synaptic Warning"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by pdev1961 on 2005-06-22
I have installed Unbuntu on my Inspiron 1150 about 8 weeks ago and have no idea what I am doing...  (Major Newb)

When I start Synaptic I get the folowing error:

W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/universe Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/multiverse Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)

How do I fix this?
Thanks

---

### Post by desdinova on 2005-06-22
It may just be a temporary network glitch as its saying it can't find some files - does Synaptic still work (i.e can you still install software from the cd?)

---

### Post by Xian on 2005-06-22
You need to comment this line in your /etc/apt/sources.list so that it appears as below:
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```
Also, please remove the ftp.nerim.net repos as they have been replaced with the Hoary backport repositories. Add these lines to your sources list:
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Then run the following command:
```
$ sudo apt-get update
```

---

### Post by pdev1961 on 2005-06-22
Xian,
Thanks for the info.  I am affraid I have to ask for more detalis on how to achieve this...  I am VERY new at Linux.

[QUOTE=Xian]You need to comment this line in your /etc/apt/sources.list so that it appears as below:
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```
Also, please remove the ftp.nerim.net repos as they have been replaced with the Hoary backport repositories. Add these lines to your sources list:
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Then run the following command:
```
$ sudo apt-get update
```[/QUOTE]

---

### Post by Xian on 2005-06-22
First let's backup your current sources.list.
Open a terminal (Applications>System Tools>Teminal) and input this line:
```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
Now in that same terminal issue this command to open up your sources.list file in a text editor:
```
$ sudo gedit /etc/apt/sources.list
```
Now let's remove what you have. From the main toolbar of gedit:
Edit > Select All
Edit > Delete

Copy the list below and paste it into the now empty text editor:
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

#deb http://www.os-works.com/debian testing main
#deb-src http://www.os-works.com/debian testing main
```
Save the file and then issue the command below.
Do you still get error messages?
```
$ sudo apt-get update
```

---

### Post by pdev1961 on 2005-06-23
Xian
Thanks for your help.  Everything seems to be OK now.  I am applying upgrades using Synaptic right now and I am not getting any errors (so far anyway...)

Take care
Pierre

---

