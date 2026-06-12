---
title: "getting errors using apt-get"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by aliyanage on 2006-12-16
Hi everytime I try to install something using apt-get I get these errors. The strange thing is that if I install something over the shell it will install even if these error messages come up, but it won't let me install anything over automatix2, which I would like to use though.

Could someone please help me?

```
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 emacs
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bapoumba on 2006-12-16
Hi,
you could try **sudo apt-get -f install**.
Please paste the complete output of **sudo apt-get update** and **cat /etc/apt/sources.list**.

---

### Post by aliyanage on 2006-12-17
Hi thanks for the reply... just got back into the office and this is what I get if I run apt-get update:

```
Get:1 http://ubuntu.beryl-project.org dapper Release.gpg [191B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://ch.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://ch.archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:5 http://ch.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://download.skype.com stable Release.gpg
Hit http://ubuntu.beryl-project.org dapper Release
Hit http://ch.archive.ubuntu.com dapper Release
Hit http://ch.archive.ubuntu.com dapper-backports Release
Hit http://ch.archive.ubuntu.com dapper-updates Release
Ign http://download.skype.com stable Release
Get:6 http://www.getautomatix.com dapper Release.gpg [189B]
Err http://ubuntu.beryl-project.org dapper Release

Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://download.skype.com stable/non-free Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:7 http://ubuntu.beryl-project.org dapper Release [5555B]
Hit http://download.skype.com stable/non-free Packages
Hit http://www.getautomatix.com dapper Release
Get:8 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:9 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://ch.archive.ubuntu.com dapper/main Packages
Hit http://ch.archive.ubuntu.com dapper/restricted Packages
Hit http://ch.archive.ubuntu.com dapper/main Sources
Hit http://ch.archive.ubuntu.com dapper/restricted Sources
Hit http://ch.archive.ubuntu.com dapper/universe Packages
Hit http://ch.archive.ubuntu.com dapper/universe Sources
Hit http://ch.archive.ubuntu.com dapper/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper/universe Packages
Hit http://ch.archive.ubuntu.com dapper-backports/main Packages
Get:10 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:11 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ch.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper-backports/main Sources
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ch.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://ch.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper-updates/universe Packages
Ign http://ubuntu.beryl-project.org dapper Release
Hit http://ubuntu.beryl-project.org dapper/main Packages
Ign http://ubuntu.beryl-project.org dapper/aiglx Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://www.getautomatix.com dapper/main Packages
Err http://ubuntu.beryl-project.org dapper/aiglx Packages
  404 Not Found [IP: 82.140.42.54 80]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:12 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Fetched 5756B in 43s (132B/s)
Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/aiglx/binary-i386/Packages.gz  404 Not Found [IP: 82.140.42.54 80]
Reading package lists... Done
W: GPG error: http://ubuntu.beryl-project.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

And here is my source.list:


```
deb http://ch.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://ch.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
#deb-src http://ch.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ch.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://download.skype.com/linux/repos/debian stable non-free

#deb http://www.beerokid.com/compiz edgy main-edgy
#deb http://media.blutkind.org/xgl/ edgy main-edgy
#deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy
#deb http://ubuntu.compiz.net/ edgy main-edgy
deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper multiverse
#AUTOMATIX REPOS END

#beryl#
deb http://ubuntu.beryl-project.org/ dapper main aiglx

```

---

### Post by bapoumba on 2006-12-17
Hi,

1- your beryl repos are giving you an error. I am not using beryl and such, but I can reach the repos in a web browser. You should get the authentication key :
[http://ubuntu.beryl-project.org/]("http://ubuntu.beryl-project.org/")

2- Some repos are in duplicate in your sources.list (you have both ch.archive.ubuntu and archive.ubuntu for security and backports). This is not giving you an error at the moment, but it is better to use only one mirror for these. You can use the ch. mirror, and here is an example of a sources.list (go down to the dapper section) :
[http://psychocats.net/ubuntu/sources]("http://psychocats.net/ubuntu/sources")

PLF repos are not available anymore, so do not include them in your sources.list.

After getting the beryl repos key and organizing your sources.list, run again **sudo apt-get update**.

---

### Post by aliyanage on 2006-12-17
okay thanks, so I have those two mistakes corrected but my main issue which I mentioned is still here and that is actually the one that I want to get rid of. See if I for example:

```
sudo apt-get -f install

```
I still get an error message, see the last few lines:

```
Hit http://ch.archive.ubuntu.com dapper-updates/universe Packages
Hit http://download.skype.com stable/non-free Packages
Hit http://www.getautomatix.com dapper Release
Get:10 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://ch.archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://ch.archive.ubuntu.com dapper/universe Sources
Hit http://ch.archive.ubuntu.com dapper/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper/universe Packages
Hit http://ch.archive.ubuntu.com dapper-backports/main Packages
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ch.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper-backports/main Sources
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ch.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://archive.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://www.getautomatix.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Fetched 10B in 1s (5B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://ch.archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@itnotebook04:/etc/apt# vi sources.list
root@itnotebook04:/etc/apt# apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://ch.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:4 http://ch.archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:5 http://ch.archive.ubuntu.com dapper Release.gpg [189B]
Ign http://download.skype.com stable Release.gpg
Get:6 http://www.getautomatix.com dapper Release.gpg [189B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://ch.archive.ubuntu.com dapper-updates Release
Hit http://ch.archive.ubuntu.com dapper-backports Release
Ign http://download.skype.com stable Release
Hit http://www.getautomatix.com dapper Release
Get:7 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:8 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://ch.archive.ubuntu.com dapper Release
Ign http://download.skype.com stable/non-free Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://download.skype.com stable/non-free Packages
Get:9 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:10 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://ch.archive.ubuntu.com dapper-updates/main Packages
Hit http://ch.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ch.archive.ubuntu.com dapper-updates/main Sources
Hit http://ch.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ch.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper Release
Hit http://ch.archive.ubuntu.com dapper-backports/main Packages
Hit http://www.getautomatix.com dapper/main Packages
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ch.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper-backports/main Sources
Hit http://ch.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://ch.archive.ubuntu.com dapper-backports/universe Sources
Hit http://ch.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://ch.archive.ubuntu.com dapper/multiverse Packages
Hit http://ch.archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Fetched 10B in 2s (4B/s)
Reading package lists... Done
root@itnotebook04:/etc/apt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/fame.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs21; however:
  Package emacs21 is not configured yet.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 emacs
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@itnotebook04:/etc/apt# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/fame.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs21; however:
  Package emacs21 is not configured yet.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 emacs
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@itnotebook04:/etc/apt# clear

root@itnotebook04:/etc/apt# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/fame.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs21; however:
  Package emacs21 is not configured yet.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 emacs
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bapoumba on 2006-12-17
Okay, found a couple things related to your error :
[https://launchpad.net/distros/ubuntu/+source/cedet/+bug/43577]("https://launchpad.net/distros/ubuntu/+source/cedet/+bug/43577")
[http://www.ubuntuforums.org/showthread.php?t=235608&page=2]("http://www.ubuntuforums.org/showthread.php?t=235608&page=2")

First, try to do what is suggested in the bug report
[QUOTE=bug 43577]Thats ok when emacs-snapshot installed before ecb[/QUOTE]

Then what's in the thread on post 12.
Remove the emacs related packages then **sudo dpkg --configure -a** and **sudo aptitude update**. I only use aptitude, because it gets better at handling depedencies.

If you still get the errors, or cannot make anything out of these two links, you may want to clean up  further your sources.list.
I would then comment out (put a # at the beginning of the line) the skype repos (I cannot get to them from my web browser to check what's in there) and all the non-ubuntu repos.
In fact, only keep official ubuntu repos. For example, here is part of my **edgy** sources.list. On a daily basis, I keep commented out everything but what I called base, security and updates. Even backports (there was once a problem upgrading from them).
Yours should have *dapper* instead of *edgy*, and the ch. repos instead of the .fr ones.

Then run **sudo aptitude update** and paste the errors again.

```
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

## base
deb http://fr.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## fix updates
deb http://fr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## backports
# deb http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## security
deb http://fr.security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://fr.security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
```

---

