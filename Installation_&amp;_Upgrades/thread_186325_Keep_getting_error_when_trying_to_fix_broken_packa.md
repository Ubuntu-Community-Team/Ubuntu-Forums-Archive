---
title: "Keep getting error when trying to fix broken packages.. Errors from dist-upgrade"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by nismoskys on 2006-06-01
ive been trying to dist-upgrade right now... wget finally finished downloading everything when i got this error..
```
Fetched 766MB in 2h21m14s (90.3kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
Moving /etc/cups/cupsd-browsing.conf to new location /etc/cups/cups.d/browse.conf...
(Reading database ... 122071 files and directories currently installed.)
Preparing to replace perl-modules 5.8.7-5ubuntu1.2 (using .../perl-modules_5.8.7-10ubuntu1_all.deb) ...
Unpacking replacement perl-modules ...
Preparing to replace ubuntu-minimal 0.80 (using .../ubuntu-minimal_0.119_i386.deb) ...
Unpacking replacement ubuntu-minimal ...
(Reading database ... 122069 files and directories currently installed.)
Removing base-config ...
Selecting previously deselected package belocs-locales-bin.
(Reading database ... 121954 files and directories currently installed.)
Unpacking belocs-locales-bin (from .../belocs-locales-bin_2.3.5-5ubuntu7_i386.deb) ...
Replacing files in old package libc6 ...
Replacing files in old package locales ...
Preparing to replace locales 2.3.5-1ubuntu12.5.10.1 (using .../locales_2.3.18_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libc6-dev 2.3.5-1ubuntu12.5.10.1 (using .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.3.5-1ubuntu12.5.10.1 (using .../libc6_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6 ...
Replaced by files in installed package tzdata ...
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
i tried apt-get -f install but it tries to remove ubuntu-minimal.. and i dont think i should do that.. right?

so i went into synaptic to fix broken packages, found 3: libc6, libc6-i686, and ubuntu-minimal

i tried selecting all, then right click and mark for reinstallation.. but when i click apply, i get this error..```
E: /var/cache/apt/archives/locales_2.3.18_all.deb: trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
```
i tried deleting ..zoneinfo/Africa/Algiers, but that didnt work.. i tried deleting the locales deb in apt/archives to let it redownload the file.. but i still get the error.

i was thinking about trying to remove 'tzdata' first and then try reinstalling through synaptic.. but i need a more expert opinion because i dont wanna screw up my system.

so.. if thats enough info for you, please help :)

---

### Post by nismoskys on 2006-06-01
just tried apt-get -f install.. even though i was afraid.. but im getting that same error again.. ```
jaanisar@jaanisar:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-i686 libsysfs2 locales lsb-base module-init-tools pcmciautils
The following packages will be REMOVED:
  ubuntu-minimal
The following NEW packages will be installed:
  libsysfs2 pcmciautils
The following packages will be upgraded:
  libc6-i686 locales lsb-base module-init-tools
4 upgraded, 2 newly installed, 1 to remove and 1235 not upgraded.
4 not fully installed or removed.
Need to get 0B/4509kB of archives.
After unpacking 2601kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 121979 files and directories currently installed.)
Removing ubuntu-minimal ...
(Reading database ... 121978 files and directories currently installed.)
Preparing to replace locales 2.3.5-1ubuntu12.5.10.1 (using .../locales_2.3.18_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ubuntu_demon on 2006-06-01
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) gives you some tips below.

You can live without the c-libraries for a while that's the reason it wants to remove ubuntu-minimal.

Just make sure you install ubuntu-minimal right after you have removed all the broken packages and configured all remaining packages.

So :

*you might want to backup your personal files before continueing*
$ sudo apt-get -f install
$ sudo apt-get -f remove

here comes the part where you remove all broken packages by hand. For example :
$sudo apt-get remove *packageA* -f
$sudo apt-get remove *packageB *-f
$sudo apt-get remove *packageC* -f
....

Let's configure all packages that are unconfigured :
$ sudo dpkg --configure -a

Now let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If all that was succesfull you should reboot ($ sudo reboot) Otherwise post your errors and someone may be able to help you (I'm going to sleep soon).

good luck!

---

### Post by az on 2006-06-01
Are you using ubuntu repositories exclusively?

---

### Post by nismoskys on 2006-06-01
thanks ALOT for replying because i really needed the help.. but i didnt see ur reply until after i did this...

since it seemed tzdata was the problem, i ran
sudo dpkg -r tzdata
then i ran
sudo apt-get -f install
again
and it got the files w.o errors this time.

after that i ran sudo apt-get dist-upgrade again and now it seems to be installing the rest of the files fine.

---

