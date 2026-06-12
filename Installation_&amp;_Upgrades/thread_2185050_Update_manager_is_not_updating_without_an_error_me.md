---
title: "Update manager is not updating without an error message about dkms"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2013-10-31
It seems my synaptic-dkms is half configured or not there. I am using Ubuntu 12.04 Precise


I have looked in synaptic by searching for dkms. Of the many packages with dkms in the name only 2 are installed:

dkms
synaptics-dkms (v.1.0.0)

I can also other items that are half configured in the log below:


What should I do about these half configurations?


dpkg.log:

```
2013-10-31 21:44:45 startup archives unpack
2013-10-31 21:44:49 upgrade compiz-gnome 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:49 status half-configured compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:50 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:50 status half-installed compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:50 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-10-31 21:44:50 status half-installed compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:50 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-10-31 21:44:50 status triggers-pending man-db 2.6.1-2ubuntu1
2013-10-31 21:44:50 status half-installed compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:50 status half-installed compiz-gnome 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:51 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:51 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:51 upgrade compiz-plugins 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:51 status half-configured compiz-plugins 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:51 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:51 status half-installed compiz-plugins 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:51 status half-installed compiz-plugins 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:51 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:51 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:52 upgrade compiz-plugins-default 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:52 status half-configured compiz-plugins-default 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:52 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:52 status half-installed compiz-plugins-default 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:52 status half-installed compiz-plugins-default 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:52 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:52 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:52 upgrade libdecoration0 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:52 status half-configured libdecoration0 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:52 status unpacked libdecoration0 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status half-installed libdecoration0 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status half-installed libdecoration0 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status unpacked libdecoration0 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:53 status unpacked libdecoration0 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:53 upgrade compiz-core 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:53 status half-configured compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status unpacked compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:53 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:44:53 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status triggers-pending bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:44:54 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:44:54 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status half-installed compiz-core 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status unpacked compiz-core 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:54 status unpacked compiz-core 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:54 upgrade compiz 1:0.9.7.12-0ubuntu2 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:54 status half-configured compiz 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status unpacked compiz 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status half-installed compiz 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:54 status half-installed compiz 1:0.9.7.12-0ubuntu2
2013-10-31 21:44:55 status unpacked compiz 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:55 status unpacked compiz 1:0.9.7.12-0ubuntu3
2013-10-31 21:44:55 upgrade firefox 24.0+build1-0ubuntu0.12.04.1 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-configured firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status unpacked firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:55 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status half-installed firefox 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:58 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:58 upgrade firefox-globalmenu 24.0+build1-0ubuntu0.12.04.1 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:58 status half-configured firefox-globalmenu 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status unpacked firefox-globalmenu 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status half-installed firefox-globalmenu 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status half-installed firefox-globalmenu 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:58 status unpacked firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:59 status unpacked firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:59 upgrade firefox-locale-en 24.0+build1-0ubuntu0.12.04.1 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:59 status half-configured firefox-locale-en 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:59 status unpacked firefox-locale-en 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:59 status half-installed firefox-locale-en 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:59 status half-installed firefox-locale-en 24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:44:59 status unpacked firefox-locale-en 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:44:59 status unpacked firefox-locale-en 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:00 upgrade libupower-glib1 0.9.15-3git1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:00 status half-configured libupower-glib1 0.9.15-3git1
2013-10-31 21:45:00 status unpacked libupower-glib1 0.9.15-3git1
2013-10-31 21:45:00 status half-installed libupower-glib1 0.9.15-3git1
2013-10-31 21:45:00 status half-installed libupower-glib1 0.9.15-3git1
2013-10-31 21:45:00 status unpacked libupower-glib1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:00 status unpacked libupower-glib1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:00 upgrade gir1.2-upowerglib-1.0 0.9.15-3git1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:00 status half-configured gir1.2-upowerglib-1.0 0.9.15-3git1
2013-10-31 21:45:00 status unpacked gir1.2-upowerglib-1.0 0.9.15-3git1
2013-10-31 21:45:00 status half-installed gir1.2-upowerglib-1.0 0.9.15-3git1
2013-10-31 21:45:00 status half-installed gir1.2-upowerglib-1.0 0.9.15-3git1
2013-10-31 21:45:00 status unpacked gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:00 status unpacked gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:01 upgrade upower 0.9.15-3git1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:01 status half-configured upower 0.9.15-3git1
2013-10-31 21:45:01 status unpacked upower 0.9.15-3git1
2013-10-31 21:45:01 status half-installed upower 0.9.15-3git1
2013-10-31 21:45:01 status half-installed upower 0.9.15-3git1
2013-10-31 21:45:01 status half-installed upower 0.9.15-3git1
2013-10-31 21:45:01 status unpacked upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:01 status unpacked upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:02 upgrade rhythmbox-ubuntuone 3.0.0-0ubuntu1 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:02 status half-configured rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status unpacked rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status half-installed rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status half-installed rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status half-installed rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status half-installed rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status half-installed rhythmbox-ubuntuone 3.0.0-0ubuntu1
2013-10-31 21:45:02 status unpacked rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:02 status unpacked rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:02 trigproc gconf2 3.2.5-0ubuntu2 3.2.5-0ubuntu2
2013-10-31 21:45:02 status half-configured gconf2 3.2.5-0ubuntu2
2013-10-31 21:45:05 status installed gconf2 3.2.5-0ubuntu2
2013-10-31 21:45:05 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-10-31 21:45:05 status half-configured man-db 2.6.1-2ubuntu1
2013-10-31 21:45:07 status installed man-db 2.6.1-2ubuntu1
2013-10-31 21:45:07 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-10-31 21:45:07 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:45:07 status installed desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:45:08 trigproc bamfdaemon 0.2.126-0ubuntu1 0.2.126-0ubuntu1
2013-10-31 21:45:08 status half-configured bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:45:08 status installed bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:45:08 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-10-31 21:45:08 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:45:08 status installed gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:45:09 startup packages configure
2013-10-31 21:45:09 configure synaptics-dkms 1.0.0 <none>
2013-10-31 21:45:09 status half-configured synaptics-dkms 1.0.0
2013-10-31 21:45:09 configure libdecoration0 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:09 status unpacked libdecoration0 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status half-configured libdecoration0 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status installed libdecoration0 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status triggers-pending libc-bin 2.15-0ubuntu10.5
2013-10-31 21:45:09 configure compiz-core 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:09 status unpacked compiz-core 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status half-configured compiz-core 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status installed compiz-core 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 configure compiz-plugins-default 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:09 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:09 status half-configured compiz-plugins-default 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status installed compiz-plugins-default 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 configure compiz-gnome 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:10 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status half-configured compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status installed compiz-gnome 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 configure compiz-plugins 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:10 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status half-configured compiz-plugins 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status installed compiz-plugins 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 configure compiz 1:0.9.7.12-0ubuntu3 <none>
2013-10-31 21:45:10 status unpacked compiz 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status half-configured compiz 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 status installed compiz 1:0.9.7.12-0ubuntu3
2013-10-31 21:45:10 configure firefox 25.0+build3-0ubuntu0.12.04.1 <none>
2013-10-31 21:45:10 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:10 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status unpacked firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status half-configured firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status installed firefox 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 configure firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1 <none>
2013-10-31 21:45:11 status unpacked firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status half-configured firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:11 status installed firefox-globalmenu 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:12 configure firefox-locale-en 25.0+build3-0ubuntu0.12.04.1 <none>
2013-10-31 21:45:12 status unpacked firefox-locale-en 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:12 status half-configured firefox-locale-en 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:12 status installed firefox-locale-en 25.0+build3-0ubuntu0.12.04.1
2013-10-31 21:45:12 configure libupower-glib1 0.9.15-3git1ubuntu0.1 <none>
2013-10-31 21:45:12 status unpacked libupower-glib1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status half-configured libupower-glib1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status installed libupower-glib1 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 configure gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1 <none>
2013-10-31 21:45:12 status unpacked gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status half-configured gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status installed gir1.2-upowerglib-1.0 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 configure upower 0.9.15-3git1ubuntu0.1 <none>
2013-10-31 21:45:12 status unpacked upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status unpacked upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status unpacked upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status half-configured upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 status installed upower 0.9.15-3git1ubuntu0.1
2013-10-31 21:45:12 configure rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1 <none>
2013-10-31 21:45:12 status unpacked rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:12 status half-configured rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:12 status installed rhythmbox-ubuntuone 4.2.0-0ubuntu0.0.1
2013-10-31 21:45:12 trigproc libc-bin 2.15-0ubuntu10.5 <none>
2013-10-31 21:45:12 status half-configured libc-bin 2.15-0ubuntu10.5
2013-10-31 21:45:13 status installed libc-bin 2.15-0ubuntu10.5
2013-10-31 21:45:13 startup packages configure
2013-10-31 21:45:13 configure synaptics-dkms 1.0.0 <none>
2013-10-31 21:45:13 status half-configured synaptics-dkms 1.0.0
2013-10-31 21:46:31 startup archives unpack
2013-10-31 21:46:31 upgrade thunderbird-locale-en 1:24.0+build1-0ubuntu0.12.04.1 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:31 status half-configured thunderbird-locale-en 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:31 status unpacked thunderbird-locale-en 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:31 status half-installed thunderbird-locale-en 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status half-installed thunderbird-locale-en 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status unpacked thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status unpacked thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 upgrade thunderbird 1:24.0+build1-0ubuntu0.12.04.1 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status half-configured thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status unpacked thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status triggers-pending man-db 2.6.1-2ubuntu1
2013-10-31 21:46:32 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:46:32 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status triggers-pending bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:46:32 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:32 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:46:32 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:34 status half-installed thunderbird 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:34 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:34 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 upgrade thunderbird-gnome-support 1:24.0+build1-0ubuntu0.12.04.1 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-configured thunderbird-gnome-support 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status unpacked thunderbird-gnome-support 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-installed thunderbird-gnome-support 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-installed thunderbird-gnome-support 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status unpacked thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status unpacked thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 upgrade thunderbird-locale-en-us 1:24.0+build1-0ubuntu0.12.04.1 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-configured thunderbird-locale-en-us 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status unpacked thunderbird-locale-en-us 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-installed thunderbird-locale-en-us 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:35 status half-installed thunderbird-locale-en-us 1:24.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:36 status unpacked thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:36 status unpacked thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:36 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2013-10-31 21:46:36 status half-configured man-db 2.6.1-2ubuntu1
2013-10-31 21:46:37 status installed man-db 2.6.1-2ubuntu1
2013-10-31 21:46:37 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-10-31 21:46:37 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:46:37 status installed desktop-file-utils 0.20-0ubuntu3
2013-10-31 21:46:37 trigproc bamfdaemon 0.2.126-0ubuntu1 0.2.126-0ubuntu1
2013-10-31 21:46:37 status half-configured bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:46:37 status installed bamfdaemon 0.2.126-0ubuntu1
2013-10-31 21:46:37 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-10-31 21:46:37 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:46:37 status installed gnome-menus 3.4.0-0ubuntu1
2013-10-31 21:46:37 startup packages configure
2013-10-31 21:46:37 configure synaptics-dkms 1.0.0 <none>
2013-10-31 21:46:37 status half-configured synaptics-dkms 1.0.0
2013-10-31 21:46:38 configure thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1 <none>
2013-10-31 21:46:38 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status unpacked thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status half-configured thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status installed thunderbird 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 configure thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1 <none>
2013-10-31 21:46:38 status unpacked thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status half-configured thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status installed thunderbird-locale-en 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 configure thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1 <none>
2013-10-31 21:46:38 status unpacked thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status half-configured thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status installed thunderbird-gnome-support 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 configure thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1 <none>
2013-10-31 21:46:38 status unpacked thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status half-configured thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 status installed thunderbird-locale-en-us 1:24.1.0+build1-0ubuntu0.12.04.1
2013-10-31 21:46:38 startup packages configure
2013-10-31 21:46:38 configure synaptics-dkms 1.0.0 <none>
2013-10-31 21:46:38 status half-configured synaptics-dkms 1.0.0
```

---

### Post by Bashing-om on 2013-10-31
Robbyx; Hi !

My suggestion:
Terminal codes:
```

sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```

Hey
[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Robbyx on 2013-11-01
Can you please suggest a way forward.
The first line of your code produced this response:

 sudo apt-get -f install
[sudo] password for robins: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libboost-program-options1.46.1 libboost-thread1.46.1
  libubuntuoneui-3.0-1 libxml++2.6-2 gnash-common libboost-filesystem1.46.1
  libboost-system1.46.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up synaptics-dkms (1.0.0) ...
Loading new synaptics-1.0.0 DKMS files...
**Error! /usr/src/synaptics-1.0.0.dkms.tar.gz does not exist.**
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 synaptics-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by grahammechanical on 2013-11-01
You might want to look through this thread and see posts 5 and 6

[http://ubuntuforums.org/showthread.php?t=1738264](http://ubuntuforums.org/showthread.php?t=1738264)

As regards the packages listed as automatically installed and no longer required you can remove them by running the command that was suggested. This is something not to do with the synaptics-dkms issue.

```
apt-get autoremove
```

Regards.

---

### Post by Robbyx on 2013-11-01
Thank you for your help. The error has now gone away.

---

