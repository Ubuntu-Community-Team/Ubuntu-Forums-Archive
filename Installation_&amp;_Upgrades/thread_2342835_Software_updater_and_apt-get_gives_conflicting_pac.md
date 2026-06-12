---
title: "Software updater and apt-get gives conflicting packages to update"
date: 2016-11-10
forum: Installation &amp; Upgrades
---

### Post by ldewit on 2016-11-10
Hi guys

If I update my system using 

apt-get update
apt-get upgrade

I get a whole lot of packages recommended for removal with 

apt-get autoremove

But if I autoremove them, I get the "Software updater" will reinstall these packages the next time it runs.

Can anyone help me out (or point me to documentation) that can explain why these two tools would apparently be out of sync? Any ideas how to sync them up again?

My system is:
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

The output of apt-get upgrade

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libaspell15:i386 libdbusmenu-qt5:i386 libegl1-mesa:i386 libevdev2:i386 libgbm1:i386 libgdbm3:i386 libgudev-1.0-0:i386 libhunspell-1.3-0:i386
  libinput10:i386 libkf5archive5:i386 libkf5attica5:i386 libkf5bookmarks-data libkf5codecs5:i386 libkf5completion-data libkf5configcore5:i386
  libkf5dbusaddons-bin:i386 libkf5dbusaddons-data libkf5globalaccel-data libkf5i18n5:i386 libkf5jobwidgets-data libkf5kdelibs4support-data
  libkf5notifications-data libkf5parts-data libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5:i386 libkf5textwidgets-data
  libkf5xmlgui-bin:i386 libkf5xmlgui-data libmtdev1:i386 libpcre16-3:i386 libperl5.22:i386 libpolkit-agent-1-0:i386 libpolkit-gobject-1-0:i386
  libproxy1v5:i386 libpulse-mainloop-glib0:i386 libqt5core5a:i386 libqt5dbus5:i386 libqt5network5:i386 libqt5script5:i386 libqt5test5:i386
  libqt5xml5:i386 libvoikko1:i386 libwacom2:i386 libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1-mesa:i386 libwayland-server0:i386
  libxcb-icccm4:i386 libxcb-image0:i386 libxcb-keysyms1:i386 libxcb-randr0:i386 libxcb-render-util0:i386 libxcb-shape0:i386 libxcb-util1:i386
  libxcb-xfixes0:i386 libxcb-xkb1:i386 libxkbcommon-x11-0:i386 libxkbcommon0:i386 sonnet-plugins:i386
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gtk2-engines-qtcurve:i386
```


If anyone has ideas, thanks!

---

### Post by Bucky Ball on 2016-11-10
You shouldn't be running in a terminal as permanent root. You should use 'sudo' to get there.

Do the whole process in the terminal. Do this:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Your machine should now be completely up to date with whatever needed to be reinstalled, reinstalled. Check with Software Centre if you like and see if that's got an update. They are both using 'apt' so sounds like you might be doing an 'autoremove' in a terminal then switching to Software Updater for some reason. Finish the job in the terminal and always run 'sudo apt update' before the 'full-upgrade' command.

'sudo apt full-upgrade' will not upgrade your release to a newer version.

PS: Please use [code] tags for terminal output. See green link in my signature below for how. ;)

---

### Post by ldewit on 2016-11-10
Hi Bucky Ball

Thanks for the reply. Let me try to explain what's happening a little better.

Usually, I'm quite happy to install software using the gui tools, and that works well. Occationally though, it's useful to do so via the command line. Like you say all the tools use apt in the background, and I've never before had a situation where using the tools interchangeably led to problems.

Today I used the command line to install some packages I needed. I usually run autoremove after making changes, and doing so cleaned out some unneeded packages.

Later, the GIU software updater tool ran (it runs on the ubuntu default schedule), surprising me by insisting on installing the packages autoremove had just autoremoved. I let software updater install the packages it wanted, thinking that something must have changed necessitating those packages. 

Wanting to be sure of what was going on, I checked in the command line again. Sure enough, apt wants to remove the exact packages just installed. 

I can sit in this endless loop forever - from the command line it will seem like the packages can be removed, after removal from the gui interface they seem required.

I usually use apt-get rather than apt. Do you recommend using apt rather? I tried with the appropriate apt commands as you suggested, but the behaviour is the same as if I were using apt-get. I do always use sudo as you suggested.

Something is differenct between the GUI tools and the command line. I'd like to understand what the difference is, and how I can resolve this.

```
leond@LEONDLINUX:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libaspell15:i386 libdbusmenu-qt5:i386 libegl1-mesa:i386 libevdev2:i386 libgbm1:i386 libgdbm3:i386 libgudev-1.0-0:i386 libhunspell-1.3-0:i386
  libinput10:i386 libkf5archive5:i386 libkf5attica5:i386 libkf5bookmarks-data libkf5codecs5:i386 libkf5completion-data libkf5configcore5:i386
  libkf5dbusaddons-bin:i386 libkf5dbusaddons-data libkf5globalaccel-data libkf5i18n5:i386 libkf5jobwidgets-data libkf5kdelibs4support-data
  libkf5notifications-data libkf5parts-data libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5:i386 libkf5textwidgets-data
  libkf5xmlgui-bin:i386 libkf5xmlgui-data libmtdev1:i386 libpcre16-3:i386 libperl5.22:i386 libpolkit-agent-1-0:i386 libpolkit-gobject-1-0:i386
  libproxy1v5:i386 libpulse-mainloop-glib0:i386 libqt5core5a:i386 libqt5dbus5:i386 libqt5network5:i386 libqt5script5:i386 libqt5test5:i386
  libqt5xml5:i386 libvoikko1:i386 libwacom2:i386 libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1-mesa:i386 libwayland-server0:i386
  libxcb-icccm4:i386 libxcb-image0:i386 libxcb-keysyms1:i386 libxcb-randr0:i386 libxcb-render-util0:i386 libxcb-shape0:i386 libxcb-util1:i386
  libxcb-xfixes0:i386 libxcb-xkb1:i386 libxkbcommon-x11-0:i386 libxkbcommon0:i386 sonnet-plugins:i386
0 to upgrade, 0 to newly install, 61 to remove and 1 not to upgrade.
After this operation, 66.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 2195687 files and directories currently installed.)
Removing sonnet-plugins:i386 (5.18.0-0ubuntu1) ...
Removing libaspell15:i386 (0.60.7~20110707-3build1) ...
Removing libdbusmenu-qt5:i386 (0.9.3+16.04.20160218-0ubuntu1) ...
Removing libwayland-egl1-mesa:i386 (11.2.0-1ubuntu2.2) ...
Removing libegl1-mesa:i386 (11.2.0-1ubuntu2.2) ...
Removing libinput10:i386 (1.2.3-1ubuntu1) ...
Removing libevdev2:i386 (1.4.6+dfsg-1) ...
Removing libgbm1:i386 (11.2.0-1ubuntu2.2) ...
Removing libperl5.22:i386 (5.22.1-9) ...
Removing libgdbm3:i386 (1.8.3-13.1) ...
Removing libwacom2:i386 (0.18-1) ...
Removing libgudev-1.0-0:i386 (1:230-2) ...
Removing libhunspell-1.3-0:i386 (1.3.3-4ubuntu1) ...
Removing libkf5archive5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5attica5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5bookmarks-data (5.18.0-0ubuntu1) ...
Removing libkf5codecs5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5completion-data (5.18.0-0ubuntu1) ...
Removing libkf5xmlgui-bin:i386 (5.18.0-0ubuntu1) ...
Removing libkf5configcore5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5dbusaddons-bin:i386 (5.18.0-0ubuntu1) ...
Removing libkf5dbusaddons-data (5.18.0-0ubuntu1) ...
Removing libkf5globalaccel-data (5.18.0-0ubuntu1) ...
Removing libkf5i18n5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5jobwidgets-data (5.18.0-0ubuntu1) ...
Removing libkf5kdelibs4support-data (5.18.0-0ubuntu1) ...
Removing libkf5notifications-data (5.18.0-0ubuntu1) ...
Removing libkf5parts-data (5.18.0-0ubuntu1) ...
Removing libkf5service-data (5.18.0-0ubuntu1) ...
Removing libkf5solid5-data (5.18.0-0ubuntu1) ...
Removing libkf5sonnetcore5:i386 (5.18.0-0ubuntu1) ...
Removing libkf5sonnet5-data (5.18.0-0ubuntu1) ...
Removing libkf5textwidgets-data (5.18.0-0ubuntu1) ...
Removing libkf5xmlgui-data (5.18.0-0ubuntu1) ...
Removing libmtdev1:i386 (1.1.5-1ubuntu2) ...
Removing libqt5xml5:i386 (5.5.1+dfsg-16ubuntu7.2) ...
Removing libqt5network5:i386 (5.5.1+dfsg-16ubuntu7.2) ...
Removing libqt5test5:i386 (5.5.1+dfsg-16ubuntu7.2) ...
Removing libqt5dbus5:i386 (5.5.1+dfsg-16ubuntu7.2) ...
Removing libpolkit-agent-1-0:i386 (0.105-14.1) ...
Removing libpolkit-gobject-1-0:i386 (0.105-14.1) ...
Removing libproxy1v5:i386 (0.4.11-5ubuntu1) ...
Removing libpulse-mainloop-glib0:i386 (1:8.0-0ubuntu3) ...
Removing libqt5script5:i386 (5.5.1+dfsg-2build1) ...
Removing libvoikko1:i386 (4.0.1-3ubuntu1) ...
Removing libwayland-cursor0:i386 (1.9.0-1) ...
Removing libwayland-client0:i386 (1.9.0-1) ...
Removing libwayland-server0:i386 (1.9.0-1) ...
Removing libxcb-icccm4:i386 (0.4.1-1ubuntu1) ...
Removing libxcb-image0:i386 (0.4.0-1build1) ...
Removing libxcb-keysyms1:i386 (0.4.0-1) ...
Removing libxcb-randr0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-render-util0:i386 (0.3.9-1) ...
Removing libxcb-shape0:i386 (1.11.1-1ubuntu1) ...
Removing libxcb-util1:i386 (0.4.0-0ubuntu3) ...
Removing libxcb-xfixes0:i386 (1.11.1-1ubuntu1) ...
Removing libxkbcommon-x11-0:i386 (0.5.0-1ubuntu2) ...
Removing libxcb-xkb1:i386 (1.11.1-1ubuntu1) ...
Removing libxkbcommon0:i386 (0.5.0-1ubuntu2) ...
Removing libqt5core5a:i386 (5.5.1+dfsg-16ubuntu7.2) ...
Removing libpcre16-3:i386 (2:8.38-3.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
leond@LEONDLINUX:~$ sudo apt update
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]
Hit:2 http://za.archive.ubuntu.com/ubuntu xenial InRelease                                            
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]                           
Hit:4 http://za.archive.ubuntu.com/ubuntu xenial-updates InRelease                                       
Hit:5 http://download.virtualbox.org/virtualbox/debian xenial InRelease  
Fetched 106 kB in 0s (137 kB/s)                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
leond@LEONDLINUX:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gtk2-engines-qtcurve:i386
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
leond@LEONDLINUX:~$ 

```

PS: Thanks for the tip on the formatting.

---

### Post by ldewit on 2016-11-11
After more wrangling last night I managed to solve this by removing multiarch support:
```
sudo apt-get remove .*:i386
```
and then 
```
sudo dpkg --remove-architecture i386
```
I'm still not sure how the GUI and apt-get interfaces could produce different results. Any light on this would be appreciated.

---

