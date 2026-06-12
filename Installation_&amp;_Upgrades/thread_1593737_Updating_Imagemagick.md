---
title: "Updating Imagemagick"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by paulsp on 2010-10-11
Hi,

I am trying to get the newest version of Imagemagick on Ubuntu 10.04. I tried to install from source using these instructions ([http://www.imagemagick.org/script/install-source.php#unix](http://www.imagemagick.org/script/install-source.php#unix)), but this did not work. Is there another way to get a new version installed? The version that comes with 10.10 is the one I need, but I can not upgrade to 10.10 yet. 

Thanks!

---

### Post by paulsp on 2010-10-12
I've been trying to get this running but no luck. But is there some way to use repositories from another Ubuntu version than the one I am using, just to install this one package? 

Check this:

ON ANOTHER COMPUTER (Ubuntu 10.10)

```
apt-cache policy imagemagick
imagemagick:
  Installed: 7:6.6.2.6-1ubuntu1
  Candidate: 7:6.6.2.6-1ubuntu1
  Version table:
 *** 7:6.6.2.6-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status
```ON THE TARGET COMPUTER (Ubuntu 10.04)

```
apt-cache policy imagemagick
imagemagick:
  Installed: (none)
  Candidate: 7:6.5.1.0-1.1ubuntu3
  Version table:
     7:6.5.1.0-1.1ubuntu3 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
     7:6.4.5.4.dfsg1-1ubuntu3.1 0
        500 http://security.ubuntu.com jaunty-security/main Packages

```I really need to get version 6.6.2, as this has functionalities that are required that the previous versions do not offer. Can I just edit my repositories list and then try to update Imagemagick? Is there a better way?

---

### Post by paulsp on 2010-10-12
I have given it a shot, to see what happens. If I change the sources.list and add the Maverick repos, and then try to upgrade imagemagick, I get this:

```
sudo apt-get install imagemagick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblzma2 ubuntu-extras-keyring xz-utils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binutils cpp-4.4 fontconfig-config g++-4.4 gcc-4.4 gcc-4.4-base gcc-4.5-base gconf-defaults-service gconf2 gconf2-common gdm gtk2-engines-pixbuf ifupdown
  initramfs-tools initramfs-tools-bin libatk1.0-0 libatk1.0-dev libc-bin libc-dev-bin libc6 libc6-dev libcdt4 libcroco3 libdbus-glib-1-2 libdconf0
  libdrm-dev libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libfontconfig1 libfontconfig1-dev libgail-common libgail18 libgcc1 libgconf2-4
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-dev libglib2.0-0 libglib2.0-bin libglib2.0-dev libgomp1 libgraph4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev libgvc5
  libkms1 liblqr-1-0 libltdl7 liblzma2 libmagickcore3 libmagickcore3-extra libmagickwand3 libmpfr4 libnetpbm10 libnih-dbus1 libnih1 libpathplan4
  libplymouth2 libpopt0 librsvg2-2 librsvg2-common libstdc++6 libstdc++6-4.4-dev libudev0 libupower-glib1 libwmf0.2-7 libwmf0.2-7-gtk libxdot4
  libxklavier16 mountall netpbm obex-data-server plymouth ubuntu-extras-keyring udev upstart ureadahead xz-utils
Suggested packages:
  binutils-doc gcc-4.4-locales g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg gcc-4.4-multilib libmudflap0-4.4-dev libgcc1-dbg libgomp1-dbg
  libmudflap0-dbg libcloog-ppl0 libppl-c2 libppl7 uswsusp gok imagemagick-doc autotrace curl enscript ffmpeg gnuplot grads hp2xx html2ps libwmf-bin mplayer
  povray radiance texlive-base-bin transfig ufraw-batch glibc-doc libglib2.0-doc python-subunit libgtk2.0-doc librsvg2-bin libstdc++6-4.4-doc watershed
Recommended packages:
  manpages-dev plymouth-theme-ubuntu-text plymouth-theme
The following packages will be REMOVED:
  libc6-i686 libgraphviz4 libmagickcore2 libmagickwand2 ubuntu-desktop usplash usplash-theme-ubuntu
The following NEW packages will be installed:
  gcc-4.5-base imagemagick initramfs-tools-bin libcdt4 libdconf0 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-dev libglib2.0-bin libgraph4 libgvc5 libkms1
  liblqr-1-0 liblzma2 libmagickcore3 libmagickcore3-extra libmagickwand3 libmpfr4 libnetpbm10 libnih-dbus1 libnih1 libpathplan4 libplymouth2
  libupower-glib1 libxdot4 libxklavier16 netpbm plymouth ubuntu-extras-keyring xz-utils
The following packages will be upgraded:
  binutils cpp-4.4 fontconfig-config g++-4.4 gcc-4.4 gcc-4.4-base gconf-defaults-service gconf2 gconf2-common gdm gtk2-engines-pixbuf ifupdown
  initramfs-tools libatk1.0-0 libatk1.0-dev libc-bin libc-dev-bin libc6 libc6-dev libcroco3 libdbus-glib-1-2 libdrm-dev libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libfontconfig1 libfontconfig1-dev libgail-common libgail18 libgcc1 libgconf2-4 libglib2.0-0 libglib2.0-dev libgomp1 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-dev libltdl7 libpopt0 librsvg2-2 librsvg2-common libstdc++6 libstdc++6-4.4-dev libudev0 libwmf0.2-7 libwmf0.2-7-gtk mountall
  obex-data-server udev upstart ureadahead
52 upgraded, 29 newly installed, 7 to remove and 1220 not upgraded.
Need to get 45.4MB of archives.
After this operation, 1,839kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Obviously I get a whole bunch of software that I am being recommended to update/remove. But as I only try to upgrade Imagemagick I should not see 29 new package to be installed (nor 52 to upgrade). So I figure typing YES here will mess up my system. Anybody can confirm this? Is this trick I am trying to pull off feasible?

---

### Post by paulsp on 2010-10-13
Anybody any idea??

---

### Post by kd5mkv on 2010-10-13
I use imagemagick on my home PC using a mapping/Ham radio program, I cannot recall the version. I looked at the Debian site,their packages were much older. Strange that the source code wouldn't make or compile. I have limited experience with opening .tgz files.
  Let me dig around! steve

---

### Post by kd5mkv on 2010-10-13
Here is something I borrowed from the Xastir CVS website for Ubuntu 10.4. This is a step in building libraries in order for the program to essentials. Your mileage may vary! May be of help

 sudo apt-get install cvs autoconf automake xorg-dev imagemagick gv libxp-dev lesstif2-dev libcurl3-dev



Of course you can probably cut and paste what you need, I do not know what version Xastir is using currently! steve

---

### Post by paulsp on 2010-10-13
Thanks Steve! However, the issue is that if I install the imagemagick package, the older version from the repositories will be installed. So I need to somehow get the newest version which is in fact available in 10.10 repositories. But if I try to force 10.10 repositories, then I get a whole bunch of other new packages which I am not sure are safe to install...

---

### Post by paulsp on 2010-10-15
Anybody any idea...??

---

### Post by paulsp on 2010-10-20
Nobody?

---

