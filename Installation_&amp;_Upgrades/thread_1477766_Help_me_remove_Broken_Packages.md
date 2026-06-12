---
title: "Help me remove Broken Packages"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by zoe-scutterbug on 2010-05-09
hiya

i upgraded to 10.04 through the packages

i have two broken packages Ldm and xubuntu-artwork which i can not remove, purge or reinstall or upgrade. the two packages are interconnected so if i try to remove one, the system wants to and fails to install the other.



help would be def appreciated

zoe

---

### Post by zvacet on 2010-05-09
In terminal type

```
sudo apt-get -f install
```

---

### Post by zoe-scutterbug on 2010-05-09
ty zvacet

i have tried that before, but no luck


zoe@zoe-desktop:~$ sudo apt-get -f install
[sudo] password for zoe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev libfreebob0    <BIG SNIP>tfs-3g54 libboost-python1.38.0
  libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ldm
The following packages will be REMOVED
  xubuntu-artwork
The following packages will be upgraded:
  ldm
1 upgraded, 0 newly installed, 1 to remove and 73 not upgraded.
2 not fully installed or removed.
Need to get 0B/78.2kB of archives.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 526383 files and directories currently installed.)
Removing xubuntu-artwork ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing xubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xubuntu-artwork
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zoe-scutterbug on 2010-05-09
more failures
zoe@zoe-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of ldm:
 ldm depends on compiz-wrapper; however:
  Package compiz-wrapper is not installed.
dpkg: error processing ldm (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ldm

zoe@zoe-desktop:~$ sudo apt-get install compiz-wrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-wrapper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-core
E: Package compiz-wrapper has no installation candidate

zoe@zoe-desktop:~$ sudo apt-get install compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-core is already the newest version.
compiz-core set to manually installed.
<SNIP>
The following extra packages will be installed:
  ldm
The following packages will be REMOVED
  xubuntu-artwork
The following packages will be upgraded:
  ldm
1 upgraded, 0 newly installed, 1 to remove and 73 not upgraded.
2 not fully installed or removed.
Need to get 0B/78.2kB of archives.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 526383 files and directories currently installed.)
Removing xubuntu-artwork ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing xubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xubuntu-artwork
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Sef on 2010-05-09
> E: Sub-process /usr/bin/dpkg returned an error code (1) 	

Because of that error, do the following:

Applications > Accessories > Terminal

then copy and paste this code in the Terminal:

```
df -h
```

copy and paste back the results.

That code will show how full your partitions are.   The -h will add the partition size in gb.

---

### Post by zoe-scutterbug on 2010-05-09
zoe@zoe-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G   14G  199G   7% /
none                  991M  280K  991M   1% /dev
none                  991M  1.2M  990M   1% /dev/shm
none                  991M  332K  991M   1% /var/run
none                  991M     0  991M   0% /var/lock
none                  991M     0  991M   0% /lib/init/rw
zoe@zoe-desktop:~$ 


ty zoe

---

### Post by zvacet on 2010-05-09
```
sudo apt-get purge --remove xubuntu-artwork
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

There is no compiz-wrapper package.I looked [here]("http://packages.ubuntu.com/lucid/ldm") and as you see it is not available.

---

### Post by zoe-scutterbug on 2010-05-09
Hiya

Many thanks for the suggested help, much appreciated. Though the previous steps failed I tried all four steps this is what I got anyways

zoe@zoe-desktop:~$ sudo apt-get purge --remove xubuntu-artwork
[sudo] password for zoe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev  < big SNIP>
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ldm
The following packages will be REMOVED
  xubuntu-artwork
The following packages will be upgraded:
  ldm
1 upgraded, 0 newly installed, 1 to remove and 73 not upgraded.
2 not fully installed or removed.
Need to get 0B/78.2kB of archives.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 525948 files and directories currently installed.)
Removing xubuntu-artwork ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing xubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)


then
 zoe@zoe-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ig   < SNIP>

zoe@zoe-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  anyevent-perl
The following packages will be upgraded:
  apt apt-transport-https apt-utils azureus chromium-browser
<big SNIP>
105 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 36.5MB/203MB of archives.
After this operation, 10.3MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main libglib2.0-dev 2.24. 
<SNIP>

dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: /var/lib/dpkg/alternatives/ldm-theme corrupt: invalid status
dpkg: error processing /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Selecting previously deselected package xubuntu-artwork.
Preparing to replace xubuntu-artwork 0.38 (using .../xubuntu-artwork_10.04.6_all.deb) ...
Unpacking replacement xubuntu-artwork ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb (--unpack):
 there is no script in the new version of the package - giving up
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

W: Duplicate sources.list entry [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)


then

zoe@zoe-desktop:~$ sudo apt-get -f install

The following extra packages will be installed:
  ldm
The following packages will be REMOVED
  xubuntu-artwork
The following packages will be upgraded:
  ldm
1 upgraded, 0 newly installed, 1 to remove and 101 not upgraded.
4 not fully installed or removed.
Need to get 0B/78.2kB of archives.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 525948 files and directories currently installed.)
Removing xubuntu-artwork ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing xubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xubuntu-artwork
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zoe-scutterbug on 2010-05-09
i forgot the dist-upgrade stage you suggested zvacet


oe@zoe-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  anyevent-perl
The following packages will be upgraded:
  apt apt-transport-https
  <sNIP> xbmc-web-pm3 xubuntu-artwork
103 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/201MB of archives.
After this operation, 10.3MB disk space will be freed.
Do you want to continue [Y/n]? y
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 525949 files and directories currently installed.)
Preparing to replace ldm 2:2.0.48-0ubuntu1 (using .../ldm_2%3a2.1.1-0ubuntu2_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: /var/lib/dpkg/alternatives/ldm-theme corrupt: invalid status
dpkg: error processing /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Selecting previously deselected package xubuntu-artwork.
Preparing to replace xubuntu-artwork 0.38 (using .../xubuntu-artwork_10.04.6_all.deb) ...
Unpacking replacement xubuntu-artwork ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zoe-scutterbug on 2010-05-09
Would the best thing be do is ...save my important doc/ find a working cd drive...and do a complete fresh install?

As i am just going round in circles & my apt system is blocked

zoe


ps... my old asus bare-bones pundit is fab...it power supply fan is broken, the case does not fit as i have had to put a wrong size fan over the dual core chippie thing which is weighted down rather than screwed..i need to fix it but funds are absent

---

### Post by Dan Z on 2010-05-09
> **zvacet said:**
> ```
sudo apt-get purge --remove xubuntu-artwork
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

There is no compiz-wrapper package.I looked [here]("http://packages.ubuntu.com/lucid/ldm") and as you see it is not available.
Just upgraded to 10.04. Upgrade said bonager broke, tried what Ubuntu suggests, but no luck.
 So I tried what you suggest, it did not work

dan@ACER-ub:~$ sudo apt-get --remove Bonager
E: Invalid operation Bonager

Any further help? thanks Dan

---

### Post by lisati on 2010-05-09
> **Dan Z said:**
> Just upgraded to 10.04. Upgrade said bonager broke, tried what Ubuntu suggests, but no luck.
 So I tried what you suggest, it did not work

dan@ACER-ub:~$ sudo apt-get --remove Bonager
E: Invalid operation Bonager

Any further help? thanks Dan

Try (without the dashes): ```
sudo apt-get remove Bonager
```

---

### Post by zoe-scutterbug on 2010-05-09
zoe@zoe-desktop:~$ sudo apt-get remove xubuntu-artwork ldm
[sudo] password for zoe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

<SNIP>

The following packages will be REMOVED
  ldm xubuntu-artwork
0 upgraded, 0 newly installed, 2 to remove and 101 not upgraded.
4 not fully installed or removed.
After this operation, 12.7MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing ldm (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 525948 files and directories currently installed.)
Removing xubuntu-artwork ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing xubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 ldm
 xubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)

<SO>

zoe@zoe-desktop:~$ sudo apt-get install  xubuntu-artwork ldm
Reading package lists... Done
Building dependency tree       
Reading state information... Done

<SNIP>

The following packages will be upgraded:
  ldm xubuntu-artwork
2 upgraded, 0 newly installed, 0 to remove and 101 not upgraded.
4 not fully installed or removed.
Need to get 0B/102kB of archives.
After this operation, 12.1MB disk space will be freed.
Selecting previously deselected package ldm.
(Reading database ... 525949 files and directories currently installed.)
Preparing to replace ldm 2:2.0.48-0ubuntu1 (using .../ldm_2%3a2.1.1-0ubuntu2_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: /var/lib/dpkg/alternatives/ldm-theme corrupt: invalid status
dpkg: error processing /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Selecting previously deselected package xubuntu-artwork.
Preparing to replace xubuntu-artwork 0.38 (using .../xubuntu-artwork_10.04.6_all.deb) ...
Unpacking replacement xubuntu-artwork ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb (--unpack):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 /var/cache/apt/archives/ldm_2%3a2.1.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/xubuntu-artwork_10.04.6_all.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
zoe@zoe-desktop:~$

---

### Post by Dan Z on 2010-05-09
ok tried----
no work
~$ sudo apt-get remove Bonager
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Bonager

---

### Post by zoe-scutterbug on 2010-05-11
I think we are stuck!
and a fresh install is the only solution

---

### Post by Soul-Sing on 2010-05-11
```
gksudo nautilus
```

navigate via nautilus to /var/lib/dpkg/info

search for "the artwork" file"( search option on the the top right)
remove xubuntu-artwork_10.04.6_all.deb

close nautilus

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by zoe-scutterbug on 2010-05-11
ohhhh...my system is unblocked, broken packages dealt with and all ok

many thanks leoquant :guitar:

---

### Post by Soul-Sing on 2010-05-11
nop enjoy Ubuntu :)

---

