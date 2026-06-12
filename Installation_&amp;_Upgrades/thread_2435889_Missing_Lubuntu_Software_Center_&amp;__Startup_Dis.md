---
title: "Missing Lubuntu Software Center &amp; ? Startup Disk Creator not working after upgrade"
date: 2020-01-28
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2020-01-28
I just upgraded from Lubuntu 16.04 LTS to Lubuntu 18.04.3 LTS a day or two ago. After the upgrade, the Lubuntu Software Center no longer appears in the menu under System Tools. 

In addition, I have tried to use the Startup Disk Creator today (after the upgrade) and it is giving me failure messages, see attached screenshots below. The Disk Creator worked fine with two different thumb drives and two different iso images before the upgrade a couple of days ago. But after the upgrade, the Disk Creator does not work with the same thumb drives and two different iso images, one iso image is the same image that worked before. For example, I tried to make a bootable thumb drive using a SanDisk thumb drive and got a message like: *Installation failed "could not write the disk image (home/able/Downloads/lubuntu ...... to the device (/dev/sbd)." *I had used the Startup Disk Creator to make a working live boot thumb drive with one of the same drives and the same iso image a few days ago before the upgrade and it worked fine. But no longer. So I have concluded that something changed in the Startup Disk Creator.
Any suggestions anybody has as to the problem?

Thank you,

Able 

[ATTACH=CONFIG]284916[/ATTACH][ATTACH=CONFIG]284917[/ATTACH]

---

### Post by guiverc on 2020-01-28
[COLOR=#2A2E2E][FONT=&amp]Lubuntu 18.04 LTS comes with "Software" which is `gnome-software` found in main Ubuntu 18.04 LTS (bionic) desktop, as well as `synaptic` package manager  (see [/FONT][/COLOR][https://packages.ubuntu.com/bionic/lubuntu-desktop](https://packages.ubuntu.com/bionic/lubuntu-desktop))

I do remember the dropping of the Ubuntu Software Centre vaguely, some flak over the change and reasons for it.. but it's too long ago for me to remember clearly.  Now much of the database is no longer Ubuntu specific, but just upstream data as I recall (though our Software Centre does include snaps).  There were no changes in package managers.

My Lubuntu 18.04 LTS desktop besides me does have Startup Disk Creator (`usb-creator-gtk`) installed (it is by default), which I don't think I've ever used before, but my test write proceeded without issue (*I'm doing the 'Check disc for defects' now on another box to confirm write; yep perfect*)

I would `apt-cache policy usb-creator-gtk` and ensure it was updated; mine reads [COLOR=#333333][FONT=Ubuntu]0.3.5ubuntu18.04.2 for usb-creator-gtk & usb-creator-common (which fits with [/FONT][/COLOR][https://packages.ubuntu.com/search?suite=bionic-updates&searchon=names&keywords=usb-creator-gtk](https://packages.ubuntu.com/search?suite=bionic-updates&searchon=names&keywords=usb-creator-gtk)).

The *dumb* approach is to re-install it (install --reinstall) or maybe better purge & install; but I'd hope someone else has a better idea than that dumb *'hammer it harder'* approach (sorry I'm empty)

---

### Post by sudodus on 2020-01-28
+1: The Ubuntu Startup Disk Creator works for me too in Lubuntu 18.04.x LTS (which is my main operating system).

So I can also recommend that you re-install it (install --reinstall) or maybe better purge & install [FONT=Courier New]**usb-creator-gtk**[/FONT] which is the name of the program package (and executable module),

```

sudo apt update
sudo apt purge usb-creator-gtk
sudo apt install usb-creator-gtk

```

and try again.

[hr][/hr]
If there are still problems maybe you want to try something brand new: A new version of mkusb, which is very safe. It works well for **cloning all current versions of Ubuntu** and Ubuntu community flavours to create live drives just like the Startup Disk Creator should do for you.

[**mkusb-plug**](https://help.ubuntu.com/community/mkusb/plug)

It uses a plug-in method to make it really safe to identify the correct target device.

mkusb-plug can also create persistent live drives of 19.10 and newer versions (e.g. 20.04 LTS which will be relieased in April). But if you want a persistent live drive of 18.04.x LTS, you had better use mkusb version 12 alias mkusb-dus.

---

### Post by AbleTassie on 2020-01-28
> **sudodus said:**
> +1: The Ubuntu Startup Disk Creator works for me too in Lubuntu 18.04.x LTS (which is my main operating system).

So I can also recommend that you re-install it (install --reinstall) or maybe better purge & install [FONT=Courier New]**usb-creator-gtk**[/FONT] which is the name of the program package (and executable module),

```

sudo apt update
sudo apt purge usb-creator-gtk
sudo apt install usb-creator-gtk

```

and try again.

If there are still problems maybe you want to try something brand new: A new version of mkusb, which is very safe. It works well for **cloning all current versions of Ubuntu** and Ubuntu community flavours to create live drives just like the Startup Disk Creator should do for you.

[**mkusb-plug**]("https://help.ubuntu.com/community/mkusb/plug")

It uses a plug-in method to make it really safe to identify the correct target device.

mkusb-plug can also create persistent live drives of 19.10 and newer versions (e.g. 20.04 LTS which will be relieased in April). But if you want a persistent live drive of 18.04.x LTS, you had better use mkusb version 12 alias mkusb-dus.

Thanks Sudodus,

I tried the update commands above, and the upgrade did not work. I  have given the entire Terminal record below. I think the key line is: 
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...

I guess I may have broken packages, I am not sure if this portends problems in the future or not. I could try the procedures [here ]("https://www.maketecheasier.com/fix-broken-packages-ubuntu/")
to find and fix broken packages.
Do you have any comments about the reason there was an abort? I can try to install mkusb.

Able

**Record of Terminal Commands:**
able@able-Lenovo-IdeaPad-Y510:~$ sudo apt update
[sudo] password for able: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Ign:4 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic InRelease     
Err:5 [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) bionic Release       
  404  Not Found [IP: 2001:67c:1560:8008::15 80]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [427 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [844 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [621 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [638 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [203 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted amd64 Packages [20.2 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted Translation-en [5,804 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [608 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [295 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [9,656 B]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [635 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [29.3 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [7,764 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1,045 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [214 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1,005 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [323 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [9,516 B]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [7,496 B]
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
able@able-Lenovo-IdeaPad-Y510:~$ sudo apt purge usb-creator-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-runtime kde-runtime-data kde-style-breeze kde-style-breeze-qt4
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools libattica0.4
  libdbusmenu-qt2 libdlrestrictions1 libglademm-2.4-1v5 libgpgme++2v5
  libkactivities6 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5
  libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkf5style5
  libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libktexteditor4 libkxmlrpcclient4 libntrack-qt4-1 libntrack0
  libphonon4 libplasma3 libpolkit-qt-1-1 libqca2 libqca2-plugins
  libqt4-designer libqt4-opengl libqt4-qt3support libqt4-svg libqtwebkit4
  libsolid4 libstreamanalyzer0v5 libstreams0v5 libthreadweaver4
  ntrack-module-libnl-0 phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common plasma-scriptengine-javascript
  python-gobject python-xdg
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  usb-creator-gtk*
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
After this operation, 156 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 236444 files and directories currently installed.)
Removing usb-creator-gtk (0.3.5ubuntu18.04.2) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
(Reading database ... 236432 files and directories currently installed.)
Purging configuration files for usb-creator-gtk (0.3.5ubuntu18.04.2) ...
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
able@able-Lenovo-IdeaPad-Y510:~$ sudo apt install usb-creator-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-runtime kde-runtime-data kde-style-breeze kde-style-breeze-qt4 kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools libattica0.4 libdbusmenu-qt2
  libdlrestrictions1 libglademm-2.4-1v5 libgpgme++2v5 libkactivities6 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkf5style5 libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libkxmlrpcclient4 libntrack-qt4-1 libntrack0 libphonon4 libplasma3
  libpolkit-qt-1-1 libqca2 libqca2-plugins libqt4-designer libqt4-opengl libqt4-qt3support libqt4-svg libqtwebkit4 libsolid4 libstreamanalyzer0v5
  libstreams0v5 libthreadweaver4 ntrack-module-libnl-0 phonon phonon-backend-gstreamer phonon-backend-gstreamer-common plasma-scriptengine-javascript
  python-gobject python-xdg
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  usb-creator-gtk
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 21.4 kB of archives.
After this operation, 156 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 usb-creator-gtk amd64 0.3.5ubuntu18.04.2 [21.4 kB]
Fetched 21.4 kB in 0s (47.7 kB/s)        
Selecting previously unselected package usb-creator-gtk.
(Reading database ... 236432 files and directories currently installed.)
Preparing to unpack .../usb-creator-gtk_0.3.5ubuntu18.04.2_amd64.deb ...
Unpacking usb-creator-gtk (0.3.5ubuntu18.04.2) ...
Setting up usb-creator-gtk (0.3.5ubuntu18.04.2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
able@able-Lenovo-IdeaPad-Y510:~$

---

### Post by guiverc on 2020-01-28
The PPA  (I opened it in a browser & went to the 'dists/' folder

[http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/]("http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/")

shows it last had packages for 16.10 (yakkety) and doesn't support 18.04. Remove it, there's nothing useful there and it'll get rid of that error.  ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu))

To fix the 'may have broken packages' I'd try

`sudo apt -f install`

which is on your pasted log anyway (*unix says put -f first; GNU says it doesn't matter; we're using GNU so either works*).  It also mentions are `dpkg` option I'd execute if a message from `apt -f` suggested it.

There are some bad suggestions (dpkg locks) in that document (maketecheasier), so I'd suggest sticking to official Ubuntu docs if you can (ie. I add a `site:*.ubuntu.com` to my searches, and only look elsewhere if I can't find something useful on official sites)

---

