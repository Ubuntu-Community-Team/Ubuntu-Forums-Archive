---
title: "how to get rid of a package with unmet dependencies?"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2013-05-30
It seems I have installed skype using the wrong command. I was trying to install something and here is the result

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 exaile : Depends: python-mutagen but it is not going to be installed
          Recommends: gstreamer0.10-ffmpeg but it is not going to be installed
          Recommends: python-cddb but it is not going to be installed
          Recommends: python-mmkeys but it is not going to be installed
 skype:i386 : Conflicts: skype-bin
              Conflicts: skype-bin:i386 but 4.2.0.11-0ubuntu0.12.04.1 is to be installed
 skype-bin:i386 : Breaks: skype:i386 (< 4.1.0.20.0-0ubuntu0.12.04.1) but 4.1.0.20-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

[/HTML]

I then run 
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-timezonemap-1.0 libipc-run-perl realpath moreutils
  libdmraid1.0.0.rc16 libdebconfclient0 kpartx-boot gir1.2-json-1.0
  libio-pty-perl user-setup kpartx rdate libdebian-installer4 btrfs-tools
  apt-clone localechooser-data archdetect-deb dmraid python-pyicu
  gir1.2-xkl-1.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  skype:i386
The following packages will be upgraded:
  skype:i386
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/15.9 kB of archives.
After this operation, 36.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of skype:i386:
 skype-bin:i386 (4.2.0.11-0ubuntu0.12.04.1) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed.
  Version of skype:i386 to be configured is 4.1.0.20-1.
dpkg: error processing skype:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

how to get rid of this?

---

### Post by fantab on 2013-05-30
Use the follwing:

sudo dpkg --purge skype skype-bin:i386 
sudo apt-get remove --purge skype skype-bin:i386
sudo apg-get autoremove 
sudo apt-get clean 
sudo apt-get -f install 
sudo apt-get update 
sudo apt-get dist-upgrade 
sudo apt-get install skype

---

### Post by abelito8 on 2013-05-31
Thanks, it worked

---

