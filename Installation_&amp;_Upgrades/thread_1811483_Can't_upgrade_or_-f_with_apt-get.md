---
title: "Can't upgrade or -f with apt-get"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by linkxs on 2011-07-24
Hi, I'm having a really weird issue on my server: 
First, I run 'apt-get update', everything is fine. 
This is what happens when I run 'apt-get upgrade':

```
~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libgs9 : Depends: libpaper1 but it is not installed
 libpaper-utils : Depends: libpaper1 but it is not installed
E: Unmet dependencies. Try using -f.
```

Then, comes the obvious 'apt-get -f install':

```
:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libpaper1
The following NEW packages will be installed:
  libpaper1
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
549 not fully installed or removed.
Need to get 0 B/20.9 kB of archives.
After this operation, 106 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libpaper1_1.1.24_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: error: `/var/cache/apt/archives/libpaper1_1.1.24_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libpaper1_1.1.24_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libpaper1_1.1.24_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Googled it, haven't found anything. Also, tried 'apt-get remove libgtk2.0-common':

```
~# apt-get remove libgtk2.0-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gir1.2-gtk-2.0 : Depends: libgtk2.0-common but it is not going to be installed
 gtk2-engines-pixbuf : Depends: libgtk2.0-common but it is not going to be installed
 libgs9 : Depends: libpaper1 but it is not going to be installed
 libgtk2.0-0 : Depends: libgtk2.0-common but it is not going to be installed
 libgtk2.0-bin : Depends: libgtk2.0-common but it is not going to be installed
 libpaper-utils : Depends: libpaper1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Thanks for any help!

---

### Post by garvinrick4 on 2011-07-25
What happens with:
```
sudo dpkg --configure -a
```

---

### Post by raja.genupula on 2011-07-25
@garvinrick4
hey how it sounds if we remove all the source from /etc/lib/apt/lists and then doing update again .

---

### Post by dino99 on 2011-07-25
as your problem is with libpaper, download it again:

[http://packages.ubuntu.com/fr/natty/libpaper-utils](http://packages.ubuntu.com/fr/natty/libpaper-utils)

---

### Post by linkxs on 2011-07-29
> **garvinrick4 said:**
> What happens with:
```
sudo dpkg --configure -a
```

```
Setting up dictionaries-common (1.9.3ubuntu1) ...
dpkg: dependency problems prevent configuration of libgs9:
 libgs9 depends on libpaper1; however:
  Package libpaper1 is not installed.
dpkg: error processing libgs9 (--configure):
 dependency problems - leaving unconfigured
Setting up consolekit (0.4.4-1) ...

```

I guess that didn't help. I've let it run for a while and finish its thing..

> @garvinrick4
hey how it sounds if we remove all the source from /etc/lib/apt/lists and then doing update again .

I doubt that's a long term solution in my case, as I'd need to uncomment all the repositories again right afterwards. 

> as your problem is with libpaper, download it again:

[http://packages.ubuntu.com/fr/natty/libpaper-utils](http://packages.ubuntu.com/fr/natty/libpaper-utils)

Well, that didn't work as the issue was with libpaper1. So, i got it from here:  [http://pkgs.org/download/debian-lenny/debian-main-i386/libpaper1_1.1.23+nmu1_i386.deb.html](http://pkgs.org/download/debian-lenny/debian-main-i386/libpaper1_1.1.23+nmu1_i386.deb.html) , installed it with dpkg, and then apt-get update ran fine. Then, I ran apt-get upgrade, and it wanted to install libpaper1 once again.. and of course hit an error. What's going on? 

Thank you for all your help so far!

---

