---
title: "Please help resolve &quot;E: Unable to correct problems, you have held broken packages.&quot;"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by Metallinut on 2016-09-21
I believe this may have begun when I attempted to upgrade from 14.04 to 16.04.

I'm on 14.04 now. If I try to upgrade via Software Updater it fails at "Calculating the changes". At the time, I gave up for the moment. Now, still on 14.04, I wanted to install some software, and when installing dependencies, some packages fail. Here is an example:

```

jp@mythtv:~$ sudo sudo apt-get install php5-sqlite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5-sqlite : Depends: phpapi-20121212
               Depends: php5-common (= 5.5.9+dfsg-1ubuntu4.19) but 5.6.7+dfsg-1 is to be installed
E: Unable to correct problems, you have held broken packages.
jp@mythtv:~$

```

Another package is libdbd-sqlite3-perl:
```
jp@mythtv:~/Videos/TV$ sudo apt-get install  libdbd-sqlite3-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdbd-sqlite3-perl : Depends: perlapi-5.18.1
E: Unable to correct problems, you have held broken packages.

```

I saw [this]("http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed"), but Synaptic doesn't show any packages with status 'broken'

---

### Post by ian-weisser on 2016-09-21
You have a version conflict.
Uninstall your non-Ubuntu software, and disable the non-Ubuntu source you got it from.

---

### Post by Metallinut on 2016-09-21
> **ian-weisser said:**
> You have a version conflict.
Uninstall your non-Ubuntu software, and disable the non-Ubuntu source you got it from.

Oh man, there's probably a lot. Is there a quick and dirty way to find it all? Or at least find the software that's preventing these specific packages from installing?

---

### Post by ian-weisser on 2016-09-21
> **Metallinut said:**
> Oh man, there's probably a lot. Is there a quick and dirty way to find it all?

The system is, at heart, Debian. The system doesn't know nor care about 'Ubuntu' vs 'non-Ubuntu'.
Like a faithful dog, the system assumes it's master (you) are infallible, and surely won't add sources that destroy it.

> **Metallinut said:**
> Or at least find the software that's preventing these specific packages from installing?

Sure, whatever it is, it uses perl. You already know that.

Start uninstalling one PPA at a time until you find the culprit.
It's slow and messy...like unclogging a drain...if you don't keep track of your non-Ubuntu software.

---

### Post by Metallinut on 2016-09-22
[IMG]http://i.imgur.com/2t7ddY6.jpg[/IMG]

---

### Post by ian-weisser on 2016-09-22
It's not difficult.
Show us the complete output of the following terminal commands, and we might be able to narrow the search.
```
sudo apt update
apt-cache policy php5-common
apt-cache policy php5-sqlite
```

---

### Post by Metallinut on 2016-09-22
Thank you!

```
jp@mythtv:~$ sudo apt update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://dl.google.com stable Release.gpg
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://extras.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Ign http://archive.canonical.com trusty InRelease
Hit http://dl.google.com stable Release
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://dl.google.com stable/main amd64 Packages
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.canonical.com trusty Release.gpg
Hit http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://extras.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://archive.canonical.com trusty Release
Hit http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://archive.canonical.com trusty/partner Sources
Hit http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://us.archive.ubuntu.com trusty Release
Hit http://ppa.launchpad.net trusty InRelease
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://extras.ubuntu.com trusty/main i386 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Ign http://dl.google.com stable/main Translation-en_US
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Ign http://dl.google.com stable/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Hit http://ppa.launchpad.net trusty/main Translation-en
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done
jp@mythtv:~$
```

```
jp@mythtv:~$ apt-cache policy php5-common
php5-common:
  Installed: 5.5.9+dfsg-1ubuntu4.19
  Candidate: 5.5.9+dfsg-1ubuntu4.19
  Version table:
 *** 5.5.9+dfsg-1ubuntu4.19 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.9+dfsg-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
jp@mythtv:~$
```

```
jp@mythtv:~$ apt-cache policy php5-sqlite
php5-sqlite:
  Installed: 5.5.9+dfsg-1ubuntu4.19
  Candidate: 5.5.9+dfsg-1ubuntu4.19
  Version table:
 *** 5.5.9+dfsg-1ubuntu4.19 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.9+dfsg-1ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```



Looks like there are other broken packages milling about as well
```
jp@mythtv:~$ !grep
grep Broken /var/log/dist-upgrade/apt.log
Broken perl-base:amd64 Breaks on perl-modules [ amd64 ] < 5.20.2-3+deb8u1 > ( perl ) (< 5.22.1~)
Broken perl-base:amd64 Breaks on perl-modules [ i386 ] < none > ( none ) (< 5.22.1~)
Broken findutils:amd64 Breaks on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (< 3.4.4-2)
Broken libgnutls30:amd64 Conflicts on libhogweed2 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs )
Broken libgnutls30:amd64 Conflicts on libnettle4 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs )
Broken systemd:amd64 Conflicts on systemd-services [ amd64 ] < 204-5ubuntu20.19 > ( admin )
Broken systemd:amd64 Conflicts on systemd-services [ i386 ] < none > ( none )
Broken libtext-charwidth-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libopencv-core2.4v5:amd64 Conflicts on libopencv-core2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libtext-iconv-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-wrapi18n-perl:amd64 Depends on libtext-charwidth-perl [ amd64 ] < 0.04-7+b3 > ( perl )
Broken libasprintf0v5:amd64 Breaks on libasprintf0c2 [ amd64 ] < 0.18.3.1-1ubuntu3 > ( libs )
Broken mysql-client-5.7:amd64 Conflicts on mysql-client-5.5 [ amd64 ] < 5.5.52-0ubuntu0.14.04.1 > ( database )
Broken mysql-client-5.7:amd64 Conflicts on virtual-mysql-client [ amd64 ] < none > ( none )
Broken libopencv-imgproc2.4v5:amd64 Conflicts on libopencv-imgproc2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libmyth-0.28-0:amd64 Conflicts on libmyth-0.27-0 [ amd64 ] < 2:0.27.6+fixes.20160627.3783dc8-0ubuntu0mythbuntu4 > ( libs )
Broken libsocket6-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libllvm3.8:amd64 Breaks on libllvm3.8v4 [ amd64 ] < 1:3.8-2ubuntu3~trusty4 > ( libs )
Broken dictionaries-common:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken libtag1v5:amd64 Conflicts on libtag1c2a [ amd64 ] < 1.9.1-2.2~ppa~trusty > ( libs )
Broken gnome-icon-theme:amd64 Conflicts on gnome-icon-theme-full [ amd64 ] < 3.10.0-0ubuntu2 > ( gnome )
Broken bluez:amd64 Conflicts on bluez-alsa [ amd64 ] < 4.101-0ubuntu13.1 > ( admin )
Broken python3-cupshelpers:amd64 Breaks on python-cupshelpers [ amd64 ] < 1.4.3+20140219-0ubuntu2.6 > ( gnome ) (< 1.5.0+20140805-0ubuntu3)
Broken mysql-common:amd64 Conflicts on mysql-server-5.5 [ amd64 ] < 5.5.52-0ubuntu0.14.04.1 > ( database )
Broken libxapian22v5:amd64 Conflicts on libxapian22 [ amd64 ] < 1.2.16-2ubuntu1 > ( libs )
Broken libproxy1v5:amd64 Conflicts on libproxy1 [ amd64 ] < 0.4.11-0ubuntu4 > ( libs )
Broken qemu-system-common:amd64 Breaks on qemu-keymaps [ amd64 ] < 2.0.0+dfsg-2ubuntu1.27 > ( otherosfs )
Broken qemu-system-common:amd64 Breaks on qemu-keymaps [ i386 ] < none > ( none )
Broken libatkmm-1.6-1v5:amd64 Conflicts on libatkmm-1.6-1 [ amd64 ] < 2.22.7-2ubuntu1 > ( libs )
Broken libebml4v5:amd64 Breaks on libebml4 [ amd64 ] < 1.3.0-2+deb8u1build0.14.04.1 > ( libs )
Broken libclass-c3-xs-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libpython3.4-stdlib:amd64 Depends on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libsidplay1v5:amd64 Conflicts on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken libnet-libidn-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libapt-pkg-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libsigc++-2.0-0v5:amd64 Conflicts on libsigc++-2.0-0c2a [ amd64 ] < 2.2.10-0.2ubuntu2 > ( libs )
Broken libgtkmm-3.0-1v5:amd64 Conflicts on libgtkmm-3.0-1 [ amd64 ] < 3.10.1-0ubuntu2 > ( libs )
Broken libglibmm-2.4-1v5:amd64 Conflicts on libglibmm-2.4-1c2a [ amd64 ] < 2.39.93-0ubuntu1 > ( libs )
Broken libmatroska6v5:amd64 Breaks on libmatroska6 [ amd64 ] < 1.4.1-2+deb8u1build0.14.04.1 > ( libs )
Broken libwinpr-thread0.1:amd64 Breaks on libfreerdp1 [ amd64 ] < 1.0.2-2ubuntu1 > ( libs ) (< 1.1.0~git20140921.1.440916e+dfsg-1)
Broken libparams-util-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libopencv-calib3d2.4v5:amd64 Conflicts on libopencv-calib3d2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken mysql-client-core-5.7:amd64 Conflicts on mysql-client-core-5.5 [ amd64 ] < 5.5.52-0ubuntu0.14.04.1 > ( database )
Broken fonts-guru-extra:amd64 Breaks on ttf-punjabi-fonts [ amd64 ] < 1:0.5.14ubuntu1 > ( fonts ) (< 2:1.0)
Broken libgnutls-deb0-28:amd64 Depends on libhogweed2 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs ) (>= 2.7)
Broken libgnutls-deb0-28:amd64 Depends on libnettle4 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs ) (>= 2.7)
Broken libopencv-highgui2.4v5:amd64 Conflicts on libopencv-highgui2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libktoblzcheck1v5:amd64 Conflicts on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs )
Broken libsidplay2v5:amd64 Conflicts on libsidplay2 [ amd64 ] < 2.1.1-14 > ( libs )
Broken libgdome2-cpp-smart0v5:amd64 Conflicts on libgdome2-cpp-smart0c2a [ amd64 ] < 0.2.6-6ubuntu1 > ( libs )
Broken libopencv-flann2.4v5:amd64 Conflicts on libopencv-flann2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libopencv-legacy2.4v5:amd64 Conflicts on libopencv-legacy2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libopencv-features2d2.4v5:amd64 Conflicts on libopencv-features2d2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libgnutls28:amd64 Depends on libhogweed2 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs ) (>= 2.7)
Broken libgnutls28:amd64 Depends on libnettle4 [ amd64 ] < 2.7.1-1ubuntu0.1 > ( libs ) (>= 2.7)
Broken libopencv-video2.4v5:amd64 Conflicts on libopencv-video2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libopencv-objdetect2.4v5:amd64 Conflicts on libopencv-objdetect2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libopencv-contrib2.4v5:amd64 Conflicts on libopencv-contrib2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken hunspell-en-us:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.10)
Broken mysql-server-core-5.7:amd64 Conflicts on mysql-server-core-5.5 [ amd64 ] < 5.5.52-0ubuntu0.14.04.1 > ( database )
Broken libopenobex2:amd64 Breaks on libopenobex1 [ amd64 ] < 1.5-2.1 > ( libs ) (< 1.7.1-4)
Broken libical1a:amd64 Breaks on libical1 [ amd64 ] < 1.0-0ubuntu1 > ( libs )
Broken libaqbanking34-plugins:amd64 Depends on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs ) (>= 1.19)
Broken libgtk2-notify-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken miscfiles:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 1.0)
Broken libfcgi-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-soundex-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken vlc:amd64 Breaks on vlc-plugin-pulse [ amd64 ] < 2.1.6-0ubuntu14.04.2 > ( video ) (< 2.2.1-4~)
Broken libgtk2-trayicon-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libvncclient1:amd64 Breaks on libvncserver0 [ amd64 ] < 0.9.9+dfsg-1ubuntu1.1 > ( libs ) (< 0.9.9+dfsg-3)
Broken wbritish:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.20)
Broken python-pip-whl:amd64 Breaks on python-chardet-whl [ amd64 ] < 2.2.1-2~ubuntu1 > ( python ) (< 2.3.0-2)
Broken python-pip-whl:amd64 Breaks on python-colorama-whl [ amd64 ] < 0.2.5-0.1ubuntu2 > ( python ) (< 0.3.6-1)
Broken python-pip-whl:amd64 Breaks on python-distlib-whl [ amd64 ] < 0.1.8-1ubuntu1 > ( python ) (< 0.2.2-1)
Broken python-pip-whl:amd64 Breaks on python-html5lib-whl [ amd64 ] < 0.999-3~ubuntu1 > ( python ) (< 0.999-4)
Broken python-pip-whl:amd64 Breaks on python-requests-whl [ amd64 ] < 2.2.1-1ubuntu0.3 > ( python ) (< 2.9.1-3)
Broken python-pip-whl:amd64 Breaks on python-setuptools-whl [ amd64 ] < 3.3-1ubuntu2 > ( python ) (< 20.1.1-1)
Broken python-pip-whl:amd64 Breaks on python-six-whl [ amd64 ] < 1.5.2-1ubuntu1 > ( python ) (< 1.10.0-3)
Broken python-pip-whl:amd64 Breaks on python-urllib3-whl [ amd64 ] < 1.7.1-1ubuntu4 > ( python ) (< 1.13.1-2)
Broken libtag1v5-vanilla:amd64 Breaks on libtag1-vanilla [ amd64 ] < 1.9.1-2.2~ppa~trusty > ( libs )
Broken libopencv-ml2.4v5:amd64 Conflicts on libopencv-ml2.4 [ amd64 ] < 2.4.8+dfsg1-2ubuntu1 > ( libs )
Broken libpangomm-1.4-1v5:amd64 Conflicts on libpangomm-1.4-1 [ amd64 ] < 2.34.0-1ubuntu1 > ( libs )
Broken libcogl20:amd64 Breaks on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs )
Broken libmediainfo0v5:amd64 Conflicts on libmediainfo0 [ amd64 ] < 0.7.67-2ubuntu1 > ( libs )
Broken libvlccore7:amd64 Depends on vlc-data [ amd64 ] < 2.1.6-0ubuntu14.04.2 -> 2.2.2-5 > ( universe/graphics ) (= 2.1.6-0ubuntu14.04.2)
Broken libgstreamer-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken abiword-plugin-mathview:amd64 Depends on abiword [ amd64 ] < 3.0.0-4ubuntu1.1 -> 3.0.1-6ubuntu0.16.04.1 > ( universe/gnome ) (= 3.0.0-4ubuntu1.1)
Broken libperl5.20:amd64 Depends on perl-base [ amd64 ] < 5.20.2-3+deb8u1 -> 5.22.1-9 > ( perl ) (= 5.20.2-3+deb8u1)
Broken libzen0v5:amd64 Conflicts on libzen0 [ amd64 ] < 0.4.29-1 > ( libs )
Broken libcairomm-1.0-1v5:amd64 Conflicts on libcairomm-1.0-1 [ amd64 ] < 1.10.0-1ubuntu3 > ( libs )
Broken libkyotocabinet16v5:amd64 Conflicts on libkyotocabinet16 [ amd64 ] < 1.2.76-4 > ( libs )
Broken gstreamer0.10-plugins-ugly:amd64 Depends on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken apache2-mpm-prefork:amd64 Depends on apache2 [ amd64 ] < 2.4.7-1ubuntu4.13 -> 2.4.18-2ubuntu3.1 > ( web ) (= 2.4.7-1ubuntu4.13)
Broken findutils:amd64 Breaks on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (< 3.4.4-2)
Broken debconf-i18n:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken debconf-i18n:amd64 Depends on libtext-wrapi18n-perl [ amd64 ] < 0.06-7 -> 0.06-7.1 > ( perl )
Broken debconf-i18n:amd64 Depends on libtext-charwidth-perl [ amd64 ] < 0.04-7+b3 > ( perl )
Broken libtext-charwidth-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-iconv-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-wrapi18n-perl:amd64 Depends on libtext-charwidth-perl [ amd64 ] < 0.04-7+b3 > ( perl )
Broken libio-socket-inet6-perl:amd64 Depends on libsocket6-perl [ amd64 ] < 0.25-1+b1 > ( perl )
Broken libsocket6-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken aspell-en:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.49.2)
Broken dictionaries-common:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken lintian:amd64 Depends on libapt-pkg-perl [ amd64 ] < 0.1.29+b2 > ( perl )
Broken libcgi-fast-perl:amd64 Depends on libfcgi-perl [ amd64 ] < 0.77-1+b1 > ( perl )
Broken libdata-optlist-perl:amd64 Depends on libparams-util-perl [ amd64 ] < 1.07-2+b1 > ( universe/perl )
Broken libpython3.4-stdlib:amd64 Depends on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libsidplay1v5:amd64 Conflicts on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken libapt-pkg-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libparams-util-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libktoblzcheck1v5:amd64 Conflicts on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs )
Broken libaqbanking34-plugins:amd64 Depends on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs ) (>= 1.19)
Broken libfcgi-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken xchat:amd64 Depends on libperl5.20 [ amd64 ] < 5.20.2-3+deb8u1 > ( libs ) (>= 5.20.1)
Broken libcogl-pango15:amd64 Depends on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken libcogl20:amd64 Breaks on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs )
Broken libperl5.20:amd64 Depends on perl-base [ amd64 ] < 5.20.2-3+deb8u1 -> 5.22.1-9 > ( perl ) (= 5.20.2-3+deb8u1)
Broken gstreamer0.10-plugins-ugly:amd64 Depends on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken findutils:amd64 Breaks on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (< 3.4.4-2)
Broken debconf-i18n:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken debconf-i18n:amd64 Depends on libtext-wrapi18n-perl [ amd64 ] < 0.06-7 -> 0.06-7.1 > ( perl )
Broken debconf-i18n:amd64 Depends on libtext-charwidth-perl [ amd64 ] < 0.04-7+b3 > ( perl )
Broken libtext-charwidth-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-iconv-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libtext-wrapi18n-perl:amd64 Depends on libtext-charwidth-perl [ amd64 ] < 0.04-7+b3 > ( perl )
Broken libio-socket-inet6-perl:amd64 Depends on libsocket6-perl [ amd64 ] < 0.25-1+b1 > ( perl )
Broken libsocket6-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken aspell-en:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.49.2)
Broken dictionaries-common:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken lintian:amd64 Depends on libapt-pkg-perl [ amd64 ] < 0.1.29+b2 > ( perl )
Broken libcgi-fast-perl:amd64 Depends on libfcgi-perl [ amd64 ] < 0.77-1+b1 > ( perl )
Broken libdata-optlist-perl:amd64 Depends on libparams-util-perl [ amd64 ] < 1.07-2+b1 > ( universe/perl )
Broken libpython3.4-stdlib:amd64 Depends on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libsidplay1v5:amd64 Conflicts on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken libapt-pkg-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libparams-util-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken libktoblzcheck1v5:amd64 Conflicts on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs )
Broken python3.4-minimal:amd64 Depends on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libaqbanking34-plugins:amd64 Depends on libktoblzcheck1c2a [ amd64 ] < 1.44-1ubuntu1 > ( libs ) (>= 1.19)
Broken libfcgi-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken xchat:amd64 Depends on libperl5.20 [ amd64 ] < 5.20.2-3+deb8u1 > ( libs ) (>= 5.20.1)
Broken libcogl-pango15:amd64 Depends on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken libcogl20:amd64 Breaks on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs )
Broken libpython3.4:amd64 Depends on libpython3.4-stdlib [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libperl5.20:amd64 Depends on perl-base [ amd64 ] < 5.20.2-3+deb8u1 -> 5.22.1-9 > ( perl ) (= 5.20.2-3+deb8u1)
Broken libcogl-path20:amd64 Depends on libcogl20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.18.0)
Broken libclutter-gst-3.0-0:amd64 Depends on libcogl20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.17.4)
Broken gstreamer0.10-plugins-ugly:amd64 Depends on libsidplay1 [ amd64 ] < 1.36.59-5ubuntu1 > ( libs )
Broken debconf-i18n:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken libio-socket-inet6-perl:amd64 Depends on libsocket6-perl [ amd64 ] < 0.25-1+b1 > ( perl )
Broken aspell-en:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.49.2)
Broken aspell:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (> 0.40)
Broken ubuntu-minimal:amd64 Depends on debconf-i18n [ amd64 ] < 1.5.51ubuntu2 -> 1.5.58ubuntu1 > ( admin )
Broken libmythtv-perl:amd64 Depends on libio-socket-inet6-perl [ amd64 ] < 2.71-1 -> 2.72-2 > ( perl )
Broken lintian:amd64 Depends on libapt-pkg-perl [ amd64 ] < 0.1.29+b2 > ( perl )
Broken libcgi-fast-perl:amd64 Depends on libfcgi-perl [ amd64 ] < 0.77-1+b1 > ( perl )
Broken libdata-optlist-perl:amd64 Depends on libparams-util-perl [ amd64 ] < 1.07-2+b1 > ( universe/perl )
Broken python3.4:amd64 Depends on python3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.3 > ( python ) (= 3.4.3-1ubuntu1~14.04.3)
Broken libenchant1c2a:amd64 Depends on aspell-en [ amd64 ] < 7.1-0-1 -> 7.1-0-1.1 > ( text )
Broken libenchant1c2a:amd64 Depends on myspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on aspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on ispell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on hunspell-dictionary [ amd64 ] < none > ( none )
Broken libnet-dns-perl:amd64 Depends on libio-socket-inet6-perl [ amd64 ] < 2.71-1 -> 2.72-2 > ( perl )
Broken gir1.2-cogl-1.0:amd64 Depends on libcogl20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.21.2)
Broken libclutter-1.0-0:amd64 Depends on libcogl-path20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.17.4)
Broken hunspell-en-us:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.10)
Broken libclutter-gtk-1.0-0:amd64 Depends on libclutter-1.0-0 [ amd64 ] < 1.16.4-0ubuntu2 -> 1.24.2-1 > ( libs ) (>= 1.23.7)
Broken libchamplain-0.12-0:amd64 Depends on libcogl-path20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.17.4)
Broken xchat:amd64 Depends on libperl5.20 [ amd64 ] < 5.20.2-3+deb8u1 > ( libs ) (>= 5.20.1)
Broken libcogl-pango20:amd64 Depends on libcogl20 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (>= 1.17.4)
Broken libcheese8:amd64 Depends on libclutter-gst-3.0-0 [ amd64 ] < none -> 3.0.18-1 > ( libs ) (>= 3.0.4)
Broken libemail-valid-perl:amd64 Depends on libnet-dns-perl [ amd64 ] < 0.81-2 -> 0.81-2build1 > ( perl )
Broken libsub-exporter-perl:amd64 Depends on libdata-optlist-perl [ amd64 ] < 0.109-1 > ( universe/perl )
Broken libenchant1c2a:amd64 Depends on aspell-en [ amd64 ] < 7.1-0-1 -> 7.1-0-1.1 > ( text )
Broken libenchant1c2a:amd64 Depends on myspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on aspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on ispell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on hunspell-dictionary [ amd64 ] < none > ( none )
Broken enchant:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gir1.2-clutter-1.0:amd64 Depends on gir1.2-cogl-1.0 [ amd64 ] < none -> 1.22.0-2 > ( libs )
Broken libabiword-3.0:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken abiword:amd64 Depends on libabiword-3.0 [ amd64 ] < 3.0.0-4ubuntu1.1 -> 3.0.1-6ubuntu0.16.04.1 > ( universe/libs ) (>= 3.0.1)
Broken gir1.2-gtkclutter-1.0:amd64 Depends on gir1.2-clutter-1.0 [ amd64 ] < none -> 1.24.2-1 > ( libs )
Broken gir1.2-coglpango-1.0:amd64 Depends on gir1.2-cogl-1.0 [ amd64 ] < none -> 1.22.0-2 > ( libs ) (= 1.22.0-2)
Broken libgetopt-long-descriptive-perl:amd64 Depends on libsub-exporter-perl [ amd64 ] < 0.986-1 > ( universe/perl )
Broken libwebkitgtk-3.0-0:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gir1.2-cheese-3.0:amd64 Depends on gir1.2-clutter-1.0 [ amd64 ] < none -> 1.24.2-1 > ( libs )
Broken libdata-section-perl:amd64 Depends on libsub-exporter-perl [ amd64 ] < 0.986-1 > ( universe/perl )
Broken libwebkitgtk-1.0-0:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken libsexy2:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs )
Broken libwebkit2gtk-4.0-37-gtk2:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken libgtkspell3-3-0:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gnucash:amd64 Depends on libwebkitgtk-1.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (>= 1.3.10)
Broken libwebkit2gtk-4.0-37:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gir1.2-webkit-3.0:amd64 Depends on libwebkitgtk-3.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (>= 2.4.6)
Broken libpod-readme-perl:amd64 Depends on libgetopt-long-descriptive-perl [ amd64 ] < none -> 0.099-1 > ( universe/perl )
Broken libenchant1c2a:amd64 Depends on aspell-en [ amd64 ] < 7.1-0-1 -> 7.1-0-1.1 > ( text )
Broken libenchant1c2a:amd64 Depends on myspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on aspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on ispell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on hunspell-dictionary [ amd64 ] < none > ( none )
Broken libsoftware-license-perl:amd64 Depends on libdata-section-perl [ amd64 ] < 0.200006-1 > ( universe/perl )
Broken libwebkitgtk-3.0-0:amd64 Depends on libjavascriptcoregtk-3.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (= 2.4.10-0ubuntu0.14.04.1)
Broken libwebkitgtk-3.0-0:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gnome-software:amd64 Depends on libgtkspell3-3-0 [ amd64 ] < none -> 3.0.7-2 > ( libs )
Broken python-gnucash:amd64 Depends on gnucash [ amd64 ] < 1:2.6.1-2 -> 1:2.6.12-1 > ( universe/gnome ) (= 1:2.6.12-1)
Broken libwebkit2gtk-4.0-37:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken gir1.2-webkit2-4.0:amd64 Depends on libwebkit2gtk-4.0-37 [ amd64 ] < none -> 2.12.5-0ubuntu0.16.04.1 > ( libs ) (>= 2.12.0)
Broken gir1.2-webkit-3.0:amd64 Depends on libwebkitgtk-3.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (>= 2.4.6)
Broken software-center:amd64 Depends on gir1.2-webkit2-4.0 [ amd64 ] < none -> 2.12.5-0ubuntu0.16.04.1 > ( introspection )
Broken ubuntu-release-upgrader-gtk:amd64 Depends on gir1.2-webkit2-4.0 [ amd64 ] < none -> 2.12.5-0ubuntu0.16.04.1 > ( introspection )
Broken libtext-iconv-perl:amd64 Depends on perlapi-5.20.0 [ amd64 ] < none > ( none )
Broken dictionaries-common:amd64 Depends on libtext-iconv-perl [ amd64 ] < 1.7-5+b2 > ( perl )
Broken aspell-en:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (>= 0.49.2)
Broken aspell:amd64 Depends on dictionaries-common [ amd64 ] < 1.20.5 -> 1.26.3 > ( text ) (> 0.40)
Broken libenchant1c2a:amd64 Depends on aspell-en [ amd64 ] < 7.1-0-1 -> 7.1-0-1.1 > ( text )
Broken libenchant1c2a:amd64 Depends on myspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on aspell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on ispell-dictionary [ amd64 ] < none > ( none )
Broken libenchant1c2a:amd64 Depends on hunspell-dictionary [ amd64 ] < none > ( none )
Broken enchant:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
Broken libwebkit2gtk-4.0-37-gtk2:amd64 Depends on libenchant1c2a [ amd64 ] < 1.6.0-10ubuntu1 -> 1.6.0-10.1build2 > ( libs ) (>= 1.6.0)
jp@mythtv:~$
```


Using this as a learning experience to Debian/Ubuntu package management!

---

### Post by cariboo on 2016-09-22
Removed to duplicate posts.

---

### Post by ian-weisser on 2016-09-22
Please show the complete output of
```
sudo apt upgrade
```

---

### Post by Metallinut on 2016-09-22
```
jp@mythtv:~$ sudo apt upgrade
[sudo] password for jp:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jp@mythtv:~$
```

---

