---
title: "Libsane:i386 unmet dependencies"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by javiert on 2014-12-26
Hi,

I'm spending more time in this forum than ever. I wanted to install Prezi software, and I read and read, and I saw that I had to install Adobe Air, but it's not perfect in Ubuntu 14.04 LTS 64 bits. At the I think I managed to install it but now I have more unmet dependencies than ever and I can not solve them

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libsane:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
$:**  sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hplip:i386 hpoj:i386 libsane-extras:i386
The following NEW packages will be installed:
  libsane:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1.858 kB of archives.
After this operation, 8.985 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 247331 files and directories currently installed.)
Preparing to unpack .../libsane_1.0.23-3ubuntu3.1_i386.deb ...
Unpacking libsane:i386 (1.0.23-3ubuntu3.1) ...
dpkg: error processing archive /var/cache/apt/archives/libsane_1.0.23-3ubuntu3.1_i386.deb (--unpack):
 trying to overwrite shared '/lib/udev/rules.d/40-libsane.rules', which is different from other instances of package libsane:i386
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.23-3ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
$:  [B]sudo apt-get --purge autoremove libsane$:  sudo apt-get --purge autoremove libsane
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 colord : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
 hplip : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
 ia32-libs-multiarch:i386 : Depends: libsane:i386 but it is not going to be installed
 sane-utils : Depends: libsane but it is not going to be installed
 simple-scan : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
 xsane : Depends: libsane (>= 1.0.11-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

```
$:  apt-cache rdepends ia32-libs
ia32-libs
Reverse Depends:
 |boinc-nvidia-cuda
  boinc-client
  lib32z1
  lib32ncurses5
  lib32bz2-1.0
  lib32asound2
  lib32asound2
  lib32z1
  lib32ncurses5
  lib32bz2-1.0


```


I tried  dist-upgrade, apt-get clean, update but nothing works. I am still learning and I'm afraid of destroying my whole OS as I did some weeks ago. 

For example, this solution didn't work for me:
[http://askubuntu.com/questions/343976/installed-wrong-teamvierer-package-now-i-have-unmet-dependency-problems-how-to](http://askubuntu.com/questions/343976/installed-wrong-teamvierer-package-now-i-have-unmet-dependency-problems-how-to)

When I installed Adobe Air, I did this:

```


sudo dpkg --add-architecture i386
sudo apt-get update 
sudo apt-get install ia32-libs

```
not working and then: 
```
sudo -i
cd /etc/apt/sources.list.d
echo "deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse" >ia32-libs-raring.list
apt-get update
apt-get install ia32-libs
```

Can anyone help me? I can't do anything now...

---

### Post by javiert on 2014-12-26
Incredible, I solved openning the Update center. It detected some issues, and made a partial upgrade. I deleted 128 packages that weren't being used and now it seems that is working...

---

### Post by schragge on 2014-12-26
Just a word of caution from me.
> **javiert said:**
> in Ubuntu [highlight]14.04 LTS[/highlight] 64 bits and then
> ```

echo "deb http://[COLOR=red]old-releases[/COLOR].ubuntu.com/ubuntu/ [COLOR=red]raring[/COLOR] main restricted universe multiverse" >ia32-libs-raring.list

```
Ubuntu 14.04 LTS is **trusty**, Ubuntu 13.04 is **raring** (not supported anymore). Are you mixing sources for different Ubuntu releases?

---

