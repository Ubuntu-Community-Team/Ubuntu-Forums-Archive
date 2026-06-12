---
title: "Package Manager Seems Broken"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2014-04-18
Any time I try to do anything with apt-get, it gives me an error. Here are a few examples:

```
deemar@Olsen:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gnome-games : Depends: gnome-sudoku (>= 1:3.8) but it is not installed
E: Unmet dependencies. Try using -f.
deemar@Olsen:~$ 

```

```
deemar@Olsen:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cdparanoia filezilla-common k3b-data libctemplate0 libflac++6
  libgoocanvas-common libgoocanvas3 libhsqldb1.8.0-java libk3b6 libmlt++3
  libmlt-data libmlt5 libquicktime2 libsdl-image1.2 libsox-fmt-alsa
  libsox-fmt-base libsox2 libtar0 libtinyxml2.6.2 libva-x11-1
  libxcb-composite0 libxcb-xv0 melt openshot-doc psensor-common python-mlt5
  python-pygoocanvas python-pysqlite2 vlc-plugin-notify vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-sudoku
The following NEW packages will be installed:
  gnome-sudoku
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 771 kB of archives.
After this operation, 2,343 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ saucy/main gnome-sudoku all 1:3.8.1-1 [771 kB]
Fetched 771 kB in 0s (1,829 kB/s)    
dpkg: warning: files list file for package 'libmad0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pithos' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-3.2.0-030200-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aspell' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-image0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-debtagshw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmysql++3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libzeitgeist-1.0-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-gfxpayload-lists' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-load-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgeronimo-jpa-2.0-spec-java' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ftp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmng1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xcftools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfelix-bundlerepository-java' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparams-validate-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhtml-form-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vcdimager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-liberation' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-oss' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libswitch-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'laptop-detect' missing; assuming package has no files currently installed
(Reading database ... 720998 files and directories currently installed.)
Unpacking gnome-sudoku (from .../gnome-sudoku_1%3a3.8.1-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-sudoku_1%3a3.8.1-1_all.deb (--unpack):
 symbolic link '/usr/share/help/de/gnome-sudoku/keyboard-shortcuts.page' size has changed from 62 to 3
No apport report written because MaxReports is reached already
                                                              Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-sudoku_1%3a3.8.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any attempts to install, reinstall, purge or remove anything end in the dkpg error code 1.
My main goal here is to upgrade to Ubuntu 14.04 (desktop) but I need another 353 mebibytes of space before it'll let me upgrade. So therefore I'm trying to remove some things to accomplish this, hoping the upgrade will fix the broken package manager.

If it helps, I do have multiple partitions on my drive, I have:
- /
- /home
- SWAP

I've tried using Gparted to make /home smaller and that was successful, however I don't know how to add that empty space to /. I'm lost here.

---

### Post by Maheriano on 2014-04-19
I ended up solving this, luckily I had Aptitude installed. I opened Aptitude and used that to fix the broken packages, plus install / remove anything I wanted done. After I was done with Aptitude I was able to use apt-get again.

---

