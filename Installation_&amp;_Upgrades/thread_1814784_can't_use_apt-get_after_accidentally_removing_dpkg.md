---
title: "can't use apt-get after accidentally removing /dpkg/"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by Jouke S on 2011-07-30
After accidentally rm -rf'ing my entire /var/lib/dpkg/ folder and spending hours trying to fix it, I have fixed most of the errors that I was getting when trying to use apt, I have restored most of the files in the folder (status file, folders etc.)

I tried many different commands and possible solutions but this problem is persistent. apt-get -f install/upgrade doesn't work, dselect doesn't work either..

There's nothing wrong with my sources.list file either.
Whenever I try to apt-get install I get returned the same list of faulty packages:
```
 akonadi-server : Depends: libakonadiprivate1 (= 1.4.0-0ubuntu1) but it is not installable
 empathy : Depends: libwebkit-1.0-2 (>= 1.1.15) but it is not installable
 gimp : Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not installable
 gvfs-backends : Depends: libimobiledevice1 (>= 0.9.7) but it is not installable
 indicator-applet : Depends: libindicator1 but it is not installable
                    Recommends: indicator-messages but it is not installed
 indicator-applet-session : Depends: libindicator1 but it is not installable
 indicator-application : Depends: libindicator1 but it is not installable
 indicator-me : Depends: libindicator1 but it is not installable
 indicator-session : Depends: libindicator1 but it is not installable
 indicator-sound : Depends: libindicator1 but it is not installable
 kdelibs5-plugins : Depends: libpolkit-qt-1-0 but it is not installable
 libakonadi-kde4 : Depends: libakonadiprivate1 (>= 1.4.0) but it is not installable
 libappindicator1 : Depends: libindicator1 but it is not installable
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.26.1-0ubuntu1) but 2.28.6-0ubuntu1 is installed
                  Depends: libglib2.0-bin (= 2.26.1-0ubuntu1) but 2.28.6-0ubuntu1 is installed
 libgnome-media0 : Depends: libgladeui-1-9 (>= 3.6.1) but it is not installable
 libgpod-common : Depends: libimobiledevice1 (>= 0.9.7) but it is not installable
 libgpod4 : Depends: libimobiledevice1 (>= 0.9.7) but it is not installable
 libgtk2.0-dev : Depends: libglib2.0-dev (>= 2.27.3) but 2.26.1-0ubuntu1 is installed
 libpango1.0-dev : Depends: libpango1.0-0 (= 1.28.2-0ubuntu1.1) but 1.28.4-0ubuntu1 is installed
 libqapt-runtime : Depends: libpolkit-qt-1-0 but it is not installable
 libubuntuone-1.0-1 : Depends: libwebkit-1.0-2 (>= 1.1.14) but it is not installable
 nautilus-sendto-empathy : Depends: libwebkit-1.0-2 (>= 1.1.15) but it is not installable
 nvidia-common : Depends: nvidia-current-modaliases but it is not installable
 python-gobject : Depends: python (>= 2.7.1-0ubuntu2) but 2.6.6-2ubuntu2 is installed
 python-twisted-core : Depends: python (>= 2.7.1-0ubuntu2) but 2.6.6-2ubuntu2 is installed
 python-twisted-names : Depends: python (>= 2.7.1-0ubuntu2) but 2.6.6-2ubuntu2 is installed
 python-ubuntuone : Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not installable
 python-webkit : Depends: libwebkit-1.0-2 (>= 1.1.14) but it is not installable
 rhythmbox : Depends: libwebkit-1.0-2 (>= 1.1.14) but it is not installable
 shotwell : Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not installable
 upower : Depends: libimobiledevice1 (>= 0.9.7) but it is not installable
 xserver-xorg-video-nouveau : Depends: libdrm-nouveau1 (>= 2.4.20-3~) but it is not installable

```
when I attempt to -f install I get a list of packages and this message at the end
```
275 upgraded, 74 newly installed, 0 to remove and 1170 not upgraded.
57 not fully installed or removed.
Need to get 0 B/336 MB of archives.
After this operation, 232 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```
I've attempted to install/upgrade twice but it keeps returning the same error as above (assuming package has no files currently installed).

Video and audio playback in mplayer, chromium and some other software ceased working and I've been experiencing a ton of program crashes lately (chromium crashes when I load a youtube page, mplayer whenever I open something).

I think the problem is that a list file of all of my packages is missing, I do still have the actual .deb files but some of them aren't working anymore. 

I've managed to get a list of all of my installed packages, can I use this to restore the missing file (is it in /dpkg/?) I've tried to force re install every single package, but no success. 

Anyone know a solution?

Some more lib errors after the list of 'missing' packages:
```
dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 6699 files and directories currently installed.)
Preparing to replace libglib2.0-dev 2.26.1-0ubuntu1 (using .../libglib2.0-dev_2.28.6-0ubuntu1_amd64.deb) ...
rm: cannot remove `/usr/share/doc/libglib2.0-dev': Is a directory
dpkg: error processing /var/cache/apt/archives/libglib2.0-dev_2.28.6-0ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libpango1.0-dev 1.28.2-0ubuntu1.1 (using .../libpango1.0-dev_1.28.4-0ubuntu1_amd64.deb) ...
rm: cannot remove `/usr/share/doc/libpango1.0-dev': Is a directory
dpkg: error processing /var/cache/apt/archives/libpango1.0-dev_1.28.4-0ubuntu1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-dev_2.28.6-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libpango1.0-dev_1.28.4-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Jouke S on 2011-07-30
update: restarting X fixed the audio and video playback issues. The unmet dependencies error still remains while trying to use apt-get

---

### Post by Jouke S on 2011-07-31
I'll say how I fixed it if anyone stumbles upon it. 
As may be clear already, some of my packages were broken (mainly lib) I followed the method described here: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)
and fixed most of the errors, apt-get works normally now.
Do keep in mind you need to reinstall some packages (keep a list of the error messages!)

---

