---
title: "Today's updates have trashed my desktop and filled memory"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by winlinuser-gmail on 2013-10-21
Today's 70+mb updates have left my 12.04 with a broken desktop / memory allocation???  

The desktop lost it's wallpaper and alternately flicks to black and purple.  Windows will not "close" and corrupt the screen by wiping out the underlying background image.  My memory is running just below 1GB - very unusual as it's normally around 280Mb.  I am currently able to use Firefox to complete this task.

This is a first and has never happened before - Ubuntu is so stable.  Anyone have the same problem?  Anyone got a clue what has happened and how I might fix it?

Many thanks in advance
Winlinuser.

---

### Post by ajgreeny on 2013-10-21
What hardware have you got and what were those updates?

If you can't remember, you can find them by running the command ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` which will list all upgraded packages with the date they were updated.  That list may give us and you some clues about what has gone wrong.

---

### Post by winlinuser-gmail on 2013-10-22
Hi ajgreeny, thanks for the reply.  I have, since posting, run the system with Cinnamon and it was OK.  As a result I suspect that it's the Unity DT that has corrupted somehow.  Is there a command I can use to reinstall Unity?  **Many thanks in advance.**

Meantime,  its an HP 530 Laptop, Intel Celeron M CPU 420 @ 1.60GHz 1Gb Ram as as requested...

```
alan@alan-HP-530-Notebook-PC-GU327AA-ABU:~$ grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
2013-09-06 16:25:33 upgrade initramfs-tools 0.99ubuntu13.1 0.99ubuntu13.2
2013-09-06 16:25:35 upgrade initramfs-tools-bin 0.99ubuntu13.1 0.99ubuntu13.2
2013-09-06 16:25:36 upgrade apparmor 2.7.102-0ubuntu3.8 2.7.102-0ubuntu3.9
2013-09-06 16:25:37 upgrade libroken18-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:38 upgrade libasn1-8-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:39 upgrade libhcrypto4-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:40 upgrade libheimbase1-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:41 upgrade libwind0-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:42 upgrade libhx509-5-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:43 upgrade libkrb5-26-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:44 upgrade libheimntlm0-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:25:45 upgrade libgssapi3-heimdal 1.6~git20120311.dfsg.1-2 1.6~git20120311.dfsg.1-2ubuntu0.1
2013-09-06 16:26:07 upgrade libnm-util2 0.9.4.0-0ubuntu4.2 0.9.4.0-0ubuntu4.3
2013-09-06 16:26:08 upgrade libnm-glib4 0.9.4.0-0ubuntu4.2 0.9.4.0-0ubuntu4.3
2013-09-06 16:26:09 upgrade network-manager 0.9.4.0-0ubuntu4.2 0.9.4.0-0ubuntu4.3
2013-09-06 16:26:12 upgrade duplicity 0.6.18-0ubuntu3.1 0.6.18-0ubuntu3.2
2013-09-06 16:26:14 upgrade gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2 0.9.4.0-0ubuntu4.3
2013-09-06 16:26:15 upgrade libpanel-applet-4-0 1:3.4.1-0ubuntu1.1 1:3.4.1-0ubuntu1.2
2013-09-06 16:26:15 upgrade gir1.2-panelapplet-4.0 1:3.4.1-0ubuntu1.1 1:3.4.1-0ubuntu1.2
2013-09-06 16:26:16 upgrade gnome-panel 1:3.4.1-0ubuntu1.1 1:3.4.1-0ubuntu1.2
2013-09-06 16:26:17 upgrade gnome-panel-data 1:3.4.1-0ubuntu1.1 1:3.4.1-0ubuntu1.2
2013-09-06 16:26:21 upgrade libnm-glib-vpn1 0.9.4.0-0ubuntu4.2 0.9.4.0-0ubuntu4.3
2013-09-06 16:26:22 upgrade linux-generic-pae 3.2.0.52.62 3.2.0.53.63
2013-09-06 16:26:22 upgrade linux-image-generic-pae 3.2.0.52.62 3.2.0.53.63
2013-09-06 16:26:38 upgrade linux-headers-generic-pae 3.2.0.52.62 3.2.0.53.63
2013-09-06 16:26:39 upgrade linux-libc-dev 3.2.0-52.78 3.2.0-53.81
2013-09-06 16:26:40 upgrade dh-apparmor 2.7.102-0ubuntu3.8 2.7.102-0ubuntu3.9
2013-09-13 22:10:07 upgrade tzdata-java 2012e-0ubuntu0.12.04.1 2013d-0ubuntu0.12.04
2013-09-13 22:10:08 upgrade tzdata 2012e-0ubuntu0.12.04.1 2013d-0ubuntu0.12.04
2013-09-13 22:10:14 upgrade python-httplib2 0.7.2-1ubuntu2 0.7.2-1ubuntu2.1
2013-09-13 22:10:59 upgrade libx11-data 2:1.4.99.1-0ubuntu2.1 2:1.4.99.1-0ubuntu2.2
2013-09-13 22:11:00 upgrade libx11-6 2:1.4.99.1-0ubuntu2.1 2:1.4.99.1-0ubuntu2.2
2013-09-13 22:11:02 upgrade libx11-xcb1 2:1.4.99.1-0ubuntu2.1 2:1.4.99.1-0ubuntu2.2
2013-09-13 22:11:03 upgrade flashplugin-installer 11.2.202.297ubuntu0.12.04.1 11.2.202.310ubuntu0.12.04.1
2013-09-13 22:11:04 upgrade sessioninstaller 0.20+bzr128-0ubuntu1.2 0.20+bzr128-0ubuntu1.3
2013-09-19 21:36:52 upgrade libapt-pkg4.12 0.8.16~exp12ubuntu10.12 0.8.16~exp12ubuntu10.14
2013-09-19 21:36:57 upgrade apt 0.8.16~exp12ubuntu10.12 0.8.16~exp12ubuntu10.14
2013-09-19 21:37:07 upgrade libapt-inst1.4 0.8.16~exp12ubuntu10.12 0.8.16~exp12ubuntu10.14
2013-09-19 21:37:08 upgrade language-selector-gnome 0.79.3 0.79.4
2013-09-19 21:37:10 upgrade language-selector-common 0.79.3 0.79.4
2013-09-19 21:37:13 upgrade libcurl3-gnutls 7.22.0-3ubuntu4.2 7.22.0-3ubuntu4.3
2013-09-19 21:37:15 upgrade libpolkit-gobject-1-0 0.104-1ubuntu1 0.104-1ubuntu1.1
2013-09-19 21:37:16 upgrade libcurl3 7.22.0-3ubuntu4.2 7.22.0-3ubuntu4.3
2013-09-19 21:37:17 upgrade libcurl3-nss 7.22.0-3ubuntu4.2 7.22.0-3ubuntu4.3
2013-09-19 21:37:18 upgrade libpolkit-agent-1-0 0.104-1ubuntu1 0.104-1ubuntu1.1
2013-09-19 21:37:19 upgrade libpolkit-backend-1-0 0.104-1ubuntu1 0.104-1ubuntu1.1
2013-09-19 21:37:20 upgrade libwbclient0 2:3.6.3-2ubuntu2.6 2:3.6.3-2ubuntu2.7
2013-09-19 21:37:21 upgrade libsmbclient 2:3.6.3-2ubuntu2.6 2:3.6.3-2ubuntu2.7
2013-09-19 21:37:22 upgrade apt-utils 0.8.16~exp12ubuntu10.12 0.8.16~exp12ubuntu10.14
2013-09-19 21:37:24 upgrade isc-dhcp-client 4.1.ESV-R4-0ubuntu5.8 4.1.ESV-R4-0ubuntu5.9
2013-09-19 21:37:25 upgrade isc-dhcp-common 4.1.ESV-R4-0ubuntu5.8 4.1.ESV-R4-0ubuntu5.9
2013-09-19 21:37:26 upgrade apt-transport-https 0.8.16~exp12ubuntu10.12 0.8.16~exp12ubuntu10.14
2013-09-19 21:37:27 upgrade apt-xapian-index 0.44ubuntu5 0.44ubuntu5.1
2013-09-19 21:37:28 upgrade firefox 23.0+build2-0ubuntu0.12.04.1 24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:37:34 upgrade firefox-globalmenu 23.0+build2-0ubuntu0.12.04.1 24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:37:35 upgrade firefox-locale-en 23.0+build2-0ubuntu0.12.04.1 24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:37:36 upgrade gir1.2-polkit-1.0 0.104-1ubuntu1 0.104-1ubuntu1.1
2013-09-19 21:37:37 upgrade printer-driver-postscript-hp 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:38 upgrade printer-driver-hpijs 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:39 upgrade libsane-hpaio 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:40 upgrade hplip 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:42 upgrade libhpmud0 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:43 upgrade hplip-data 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:46 upgrade printer-driver-hpcups 3.12.2-1ubuntu3.1 3.12.2-1ubuntu3.2
2013-09-19 21:37:47 upgrade policykit-1 0.104-1ubuntu1 0.104-1ubuntu1.1
2013-09-19 21:37:48 upgrade jockey-gtk 0.9.7-0ubuntu7.10 0.9.7-0ubuntu7.11
2013-09-19 21:37:50 upgrade jockey-common 0.9.7-0ubuntu7.10 0.9.7-0ubuntu7.11
2013-09-19 21:37:52 upgrade libsyncdaemon-1.0-1 3.0.2-0ubuntu1 3.0.2-0ubuntu2
2013-09-19 21:37:52 upgrade ubuntuone-client 3.0.2-0ubuntu1 3.0.2-0ubuntu2
2013-09-19 21:37:53 upgrade python-ubuntuone-client 3.0.2-0ubuntu1 3.0.2-0ubuntu2
2013-09-19 21:37:55 upgrade python-software-properties 0.82.7.3 0.82.7.5
2013-09-19 21:37:56 upgrade rtkit 0.10-2 0.10-2ubuntu0.12.04.1
2013-09-19 21:37:57 upgrade smbclient 2:3.6.3-2ubuntu2.6 2:3.6.3-2ubuntu2.7
2013-09-19 21:38:00 upgrade samba-common 2:3.6.3-2ubuntu2.6 2:3.6.3-2ubuntu2.7
2013-09-19 21:38:01 upgrade samba-common-bin 2:3.6.3-2ubuntu2.6 2:3.6.3-2ubuntu2.7
2013-09-19 21:38:05 upgrade software-properties-common 0.82.7.3 0.82.7.5
2013-09-19 21:38:06 upgrade software-properties-gtk 0.82.7.3 0.82.7.5
2013-09-19 21:38:08 upgrade thunderbird-globalmenu 17.0.8+build1-0ubuntu0.12.04.1 1:24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:38:09 upgrade thunderbird-locale-en 1:17.0.8+build1-0ubuntu0.12.04.1 1:24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:38:10 upgrade thunderbird 17.0.8+build1-0ubuntu0.12.04.1 1:24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:38:15 upgrade thunderbird-gnome-support 17.0.8+build1-0ubuntu0.12.04.1 1:24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:38:16 upgrade thunderbird-locale-en-us 1:17.0.8+build1-0ubuntu0.12.04.1 1:24.0+build1-0ubuntu0.12.04.1
2013-09-19 21:38:17 upgrade ubuntu-system-service 0.2.2 0.2.2.1
2013-09-19 21:38:18 upgrade usb-creator-gtk 0.2.38 0.2.38.2
2013-09-19 21:38:20 upgrade usb-creator-common 0.2.38 0.2.38.2
2013-09-19 21:59:16 upgrade libicu48 4.8.1.1-3 4.8.1.1-12~precise1
2013-09-19 21:59:19 upgrade libwpd-0.9-9 0.9.4-1 0.9.9-1~precise1
2013-09-19 21:59:21 upgrade libwps-0.2-2 0.2.4-1 0.2.9-1ubuntu1~precise1
2013-09-19 21:59:22 upgrade libreoffice-base 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:25 upgrade libreoffice-calc 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:30 upgrade libreoffice 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:39 upgrade libreoffice-emailmerge 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:39 upgrade libreoffice-style-human 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:42 upgrade libreoffice-style-tango 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:43 upgrade libreoffice-draw 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:46 upgrade libreoffice-gtk 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:47 upgrade libreoffice-impress 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:49 upgrade libreoffice-writer 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 21:59:55 upgrade libreoffice-common 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 22:00:55 upgrade libreoffice-gnome 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 22:01:14 upgrade libexttextcat-data 3.2.0-1ubuntu1 3.4.0-1~precise1
2013-09-19 22:01:26 upgrade uno-libs3 3.5.7-0ubuntu4 4.1.1-0ubuntu1~precise1
2013-09-19 22:01:43 upgrade libreoffice-base-core 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 22:01:48 upgrade python-uno 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 22:01:50 upgrade libreoffice-math 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-19 22:01:52 upgrade ure 3.5.7-0ubuntu4 4.1.1-0ubuntu1~precise1
2013-09-19 22:01:56 upgrade liblcms2-2 2.2+git20110628-2ubuntu3.1 2.5-0ubuntu1~precise1
2013-09-19 22:01:57 upgrade fonts-opensymbol 2:102.2+LibO3.5.7-0ubuntu4 2:102.3+LibO4.1.1-0ubuntu1~precise1
2013-09-19 22:02:00 upgrade libreoffice-java-common 1:3.5.7-0ubuntu4 1:4.1.1-0ubuntu1~precise1
2013-09-23 21:21:08 upgrade libraw5 0.14.4-0ubuntu2.1 0.14.4-0ubuntu2.2
2013-09-23 21:21:11 upgrade python-openssl 0.12-1ubuntu2 0.12-1ubuntu2.1
2013-09-24 21:53:28 upgrade libwbclient0 2:3.6.3-2ubuntu2.7 2:3.6.3-2ubuntu2.8
2013-09-24 21:53:29 upgrade libsmbclient 2:3.6.3-2ubuntu2.7 2:3.6.3-2ubuntu2.8
2013-09-24 21:53:31 upgrade smbclient 2:3.6.3-2ubuntu2.7 2:3.6.3-2ubuntu2.8
2013-09-24 21:53:34 upgrade samba-common 2:3.6.3-2ubuntu2.7 2:3.6.3-2ubuntu2.8
2013-09-24 21:53:35 upgrade samba-common-bin 2:3.6.3-2ubuntu2.7 2:3.6.3-2ubuntu2.8
2013-09-28 12:33:37 upgrade libgnutls26 2.12.14-5ubuntu3.4 2.12.14-5ubuntu3.5
2013-09-28 12:33:58 upgrade rsyslog 5.8.6-1ubuntu8.4 5.8.6-1ubuntu8.5
2013-09-28 12:34:01 upgrade linux-generic-pae 3.2.0.53.63 3.2.0.54.64
2013-09-28 12:34:02 upgrade linux-image-generic-pae 3.2.0.53.63 3.2.0.54.64
2013-09-28 12:34:18 upgrade linux-headers-generic-pae 3.2.0.53.63 3.2.0.54.64
2013-09-28 12:34:19 upgrade linux-libc-dev 3.2.0-53.81 3.2.0-54.82
2013-10-01 21:12:19 upgrade libpython2.7 2.7.3-0ubuntu3.2 2.7.3-0ubuntu3.4
2013-10-01 21:12:20 upgrade python2.7 2.7.3-0ubuntu3.2 2.7.3-0ubuntu3.4
2013-10-01 21:12:24 upgrade python2.7-minimal 2.7.3-0ubuntu3.2 2.7.3-0ubuntu3.4
2013-10-01 21:12:36 upgrade printer-driver-postscript-hp 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:37 upgrade printer-driver-hpijs 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:38 upgrade libsane-hpaio 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:40 upgrade hplip 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:43 upgrade libhpmud0 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:46 upgrade hplip-data 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:48 upgrade printer-driver-hpcups 3.12.2-1ubuntu3.2 3.12.2-1ubuntu3.3
2013-10-01 21:12:49 upgrade vino 3.4.2-0ubuntu1.2 3.4.2-0ubuntu1.3
2013-10-02 11:16:19 upgrade libaudio2 1.9.3-4 1.9.3-4ubuntu0.1
2013-10-09 16:12:39 upgrade libldap-2.4-2 2.4.28-1.1ubuntu4.3 2.4.28-1.1ubuntu4.4
2013-10-09 16:12:40 upgrade libpulse0 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:42 upgrade libpulse-mainloop-glib0 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:43 upgrade libpulsedsp 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:44 upgrade ifupdown 0.7~beta2ubuntu8 0.7~beta2ubuntu10
2013-10-09 16:12:45 upgrade python-problem-report 2.0.1-0ubuntu17.4 2.0.1-0ubuntu17.5
2013-10-09 16:12:46 upgrade python-apport 2.0.1-0ubuntu17.4 2.0.1-0ubuntu17.5
2013-10-09 16:12:48 upgrade apport 2.0.1-0ubuntu17.4 2.0.1-0ubuntu17.5
2013-10-09 16:12:50 upgrade apport-gtk 2.0.1-0ubuntu17.4 2.0.1-0ubuntu17.5
2013-10-09 16:12:51 upgrade pulseaudio-utils 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:53 upgrade pulseaudio 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:55 upgrade pulseaudio-module-gconf 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:56 upgrade pulseaudio-module-x11 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-09 16:12:57 upgrade gnome-settings-daemon 3.4.2-0ubuntu0.6.2 3.4.2-0ubuntu0.6.3
2013-10-09 16:13:00 upgrade pulseaudio-module-bluetooth 1:1.1-0ubuntu15.3 1:1.1-0ubuntu15.4
2013-10-10 20:36:26 upgrade libapt-pkg4.12 0.8.16~exp12ubuntu10.14 0.8.16~exp12ubuntu10.15
2013-10-10 20:36:31 upgrade gpgv 1.4.11-3ubuntu2.3 1.4.11-3ubuntu2.4
2013-10-10 20:36:37 upgrade gnupg 1.4.11-3ubuntu2.3 1.4.11-3ubuntu2.4
2013-10-10 20:36:46 upgrade apt 0.8.16~exp12ubuntu10.14 0.8.16~exp12ubuntu10.15
2013-10-10 20:36:55 upgrade libapt-inst1.4 0.8.16~exp12ubuntu10.14 0.8.16~exp12ubuntu10.15
2013-10-10 20:36:56 upgrade apt-utils 0.8.16~exp12ubuntu10.14 0.8.16~exp12ubuntu10.15
2013-10-10 20:36:57 upgrade accountsservice 0.6.15-2ubuntu9.6 0.6.15-2ubuntu9.6.1
2013-10-10 20:36:59 upgrade libaccountsservice0 0.6.15-2ubuntu9.6 0.6.15-2ubuntu9.6.1
2013-10-10 20:37:00 upgrade apt-transport-https 0.8.16~exp12ubuntu10.14 0.8.16~exp12ubuntu10.15
2013-10-10 20:37:00 upgrade gir1.2-accountsservice-1.0 0.6.15-2ubuntu9.6 0.6.15-2ubuntu9.6.1
2013-10-17 20:04:31 upgrade dpkg 1.16.1.2ubuntu7.1 1.16.1.2ubuntu7.2
2013-10-17 20:04:43 upgrade liblockfile-bin 1.09-3 1.09-3ubuntu0.1
2013-10-17 20:04:44 upgrade liblockfile1 1.09-3 1.09-3ubuntu0.1
2013-10-17 20:04:45 upgrade libdrm2 2.4.43-0ubuntu0.0.2 2.4.43-0ubuntu0.0.3
2013-10-17 20:04:46 upgrade libdrm-intel1 2.4.43-0ubuntu0.0.2 2.4.43-0ubuntu0.0.3
2013-10-17 20:04:47 upgrade libdrm-nouveau1a 2.4.43-0ubuntu0.0.2 2.4.43-0ubuntu0.0.3
2013-10-17 20:04:48 upgrade libdrm-radeon1 2.4.43-0ubuntu0.0.2 2.4.43-0ubuntu0.0.3
2013-10-17 20:04:49 upgrade libglib2.0-data 2.32.3-0ubuntu1 2.32.4-0ubuntu1
2013-10-17 20:04:50 upgrade libglib2.0-bin 2.32.3-0ubuntu1 2.32.4-0ubuntu1
2013-10-17 20:04:53 upgrade libglib2.0-0 2.32.3-0ubuntu1 2.32.4-0ubuntu1
2013-10-17 20:05:00 upgrade libwildmidi-config 0.2.3.4-2.1 0.2.3.4-2.1precise1
2013-10-17 20:05:01 upgrade libwildmidi1 0.2.3.4-2.1 0.2.3.4-2.1precise1
2013-10-17 20:05:02 upgrade tzdata-java 2013d-0ubuntu0.12.04 2013g-0ubuntu0.12.04
2013-10-17 20:05:04 upgrade tzdata 2013d-0ubuntu0.12.04 2013g-0ubuntu0.12.04
2013-10-17 20:05:25 upgrade procps 1:3.2.8-11ubuntu6 1:3.2.8-11ubuntu6.1
2013-10-17 20:05:27 upgrade cinnamon 1.8.8-0ubuntu1~precise1 2.0.2-20131011040307-precise
2013-10-17 20:05:31 upgrade cinnamon-common 1.8.8-0ubuntu1~precise1 2.0.2-20131011040307-precise
2013-10-17 20:05:35 upgrade libmuffin0 1.8.2-20130525024003-precise 2.0.1-20131011003005-precise
2013-10-17 20:05:36 upgrade muffin-common 1.8.2-20130525024003-precise 2.0.1-20131011003005-precise
2013-10-17 20:05:38 upgrade gir1.2-muffin-3.0 1.8.2-20130525024003-precise 2.0.1-20131011003005-precise
2013-10-17 20:05:54 upgrade cinnamon-screensaver 1.8.0-20130505194857-precise 2.0.0-20131011013003-precise
2013-10-17 20:05:55 upgrade dpkg-dev 1.16.1.2ubuntu7.1 1.16.1.2ubuntu7.2
2013-10-17 20:05:56 upgrade libdpkg-perl 1.16.1.2ubuntu7.1 1.16.1.2ubuntu7.2
2013-10-17 20:05:57 upgrade libdvdread4 4.2.0-1ubuntu3 4.2.0-1ubuntu4
2013-10-17 20:06:00 upgrade nemo-fileroller 1.8.0-20130505195020-precise 2.0.0-20131011020004-precise
2013-10-17 20:06:01 upgrade python-software-properties 0.82.7.5 0.82.7.6
2013-10-17 20:06:02 upgrade software-properties-common 0.82.7.5 0.82.7.6
2013-10-17 20:06:03 upgrade software-properties-gtk 0.82.7.5 0.82.7.6
2013-10-17 20:06:05 upgrade xserver-common 2:1.11.4-0ubuntu10.13 2:1.11.4-0ubuntu10.14
2013-10-17 20:06:06 upgrade xserver-xorg-core 2:1.11.4-0ubuntu10.13 2:1.11.4-0ubuntu10.14
2013-10-17 20:06:08 upgrade gnome-settings-daemon 3.4.2-0ubuntu0.6.3 3.4.2-0ubuntu0.6.4
2013-10-19 19:04:01 upgrade procps 1:3.2.8-11ubuntu6.1 1:3.2.8-11ubuntu6.2
2013-10-19 19:04:03 upgrade libgnome-control-center1 1:3.4.2-0ubuntu0.12 1:3.4.2-0ubuntu0.13
2013-10-19 19:04:04 upgrade gnome-control-center-data 1:3.4.2-0ubuntu0.12 1:3.4.2-0ubuntu0.13
2013-10-19 19:04:05 upgrade gnome-control-center 1:3.4.2-0ubuntu0.12 1:3.4.2-0ubuntu0.13
2013-10-19 19:04:07 upgrade linux-firmware 1.79.6 1.79.7
2013-10-21 19:59:45 upgrade libc6-dev 2.15-0ubuntu10.4 2.15-0ubuntu10.5
2013-10-21 19:59:48 upgrade libc-dev-bin 2.15-0ubuntu10.4 2.15-0ubuntu10.5
2013-10-21 19:59:49 upgrade linux-libc-dev 3.2.0-54.82 3.2.0-55.85
2013-10-21 19:59:51 upgrade libc-bin 2.15-0ubuntu10.4 2.15-0ubuntu10.5
2013-10-21 20:00:00 upgrade libc6 2.15-0ubuntu10.4 2.15-0ubuntu10.5
2013-10-21 20:00:08 upgrade cinnamon-desktop-data 2.0.1-20131011011505-precise 2.0.1-20131021011504-precise
2013-10-21 20:00:10 upgrade libcinnamon-desktop0 2.0.1-20131011011505-precise 2.0.1-20131021011504-precise
2013-10-21 20:00:11 upgrade libnemo-extension1 1.8.4-20130709192009-precise 2.0.1-20131021010006-precise
2013-10-21 20:00:12 upgrade cinnamon-translations 2.0.1-20131011040406-precise 2.0.1-20131021040407-precise
2013-10-21 20:00:14 upgrade cinnamon 2.0.2-20131011040307-precise 2.0.3-20131021040307-precise
2013-10-21 20:00:18 upgrade cinnamon-common 2.0.2-20131011040307-precise 2.0.3-20131021040307-precise
2013-10-21 20:00:20 upgrade gir1.2-cinnamondesktop-3.0 2.0.1-20131011011505-precise 2.0.1-20131021011504-precise
2013-10-21 20:00:21 upgrade libmuffin0 2.0.1-20131011003005-precise 2.0.2-20131021003031-precise
2013-10-21 20:00:22 upgrade muffin-common 2.0.1-20131011003005-precise 2.0.2-20131021003031-precise
2013-10-21 20:00:24 upgrade gir1.2-muffin-3.0 2.0.1-20131011003005-precise 2.0.2-20131021003031-precise
2013-10-21 20:00:25 upgrade libcjs0c 2.0.0-20131011020603-precise 2.0.0-20131021020602-precise
2013-10-21 20:00:26 upgrade cjs 2.0.0-20131011020603-precise 2.0.0-20131021020602-precise
2013-10-21 20:00:26 upgrade cinnamon-session 2.0.1-20131011043004-precise 2.0.1-20131021043004-precise
2013-10-21 20:00:27 upgrade nemo 1.8.4-20130709192009-precise 2.0.1-20131021010006-precise
2013-10-21 20:00:29 upgrade nemo-data 1.8.4-20130709192009-precise 2.0.1-20131021010006-precise
2013-10-21 20:00:31 upgrade cinnamon-settings-daemon 2.0.1-20131011004504-precise 2.0.3-20131021004509-precise
2013-10-21 20:00:58 upgrade multiarch-support 2.15-0ubuntu10.4 2.15-0ubuntu10.5
2013-10-21 20:01:20 upgrade cinnamon-screensaver 2.0.0-20131011013003-precise 2.0.1-20131021013003-precise
2013-10-21 20:01:22 upgrade linux-generic-pae 3.2.0.54.64 3.2.0.55.65
2013-10-21 20:01:23 upgrade linux-image-generic-pae 3.2.0.54.64 3.2.0.55.65
2013-10-21 20:01:37 upgrade linux-headers-generic-pae 3.2.0.54.64 3.2.0.55.65
2013-10-21 20:01:38 upgrade nemo-fileroller 2.0.0-20131011020004-precise 2.0.0-20131021020004-precise


```

---

### Post by winlinuser-gmail on 2013-10-22
Tonight I ran:  sudo apt-get install --reinstall unity All went well but nothing has changed?  See new screenshot.  Really puzzled?

---

### Post by ajgreeny on 2013-10-22
Sorry but I don't use unity so I'm the probably the wrong person to try to help you more with this, apart from noting that there was a new kernel and headers installed:-
2013-10-21 20:01:22 upgrade linux-generic-pae 3.2.0.54.64 3.2.0.55.65 
2013-10-21 20:01:23 upgrade linux-image-generic-pae 3.2.0.54.64 3.2.0.55.65 
2013-10-21 20:01:37 upgrade linux-headers-generic-pae 3.2.0.54.64 3.2.0.55.65

You could possibly need to reinstall your graphic card driver for that kernel if you use a proprietary driver, but I have no idea about that as I use only the open source drivers for my Intel GPU.  You could also try booting to the previous kernel from the grub menu to see if the new version is the cause of your problem.

---

### Post by krakonos on 2013-10-22
I have problems with that update too (but in Gnome classic) - and I believe that it has something to do with cinnamon - in my case switch to older kernel didn't help

---

### Post by Frogs Hair on 2013-10-22
I had a similar problem when experimenting with the Cinnamon 2.0 PPA on 13.04.Cinnamon ran fine, but had the same result when logging back into Unity. I purged the PPA which solved the problem have and installed 13.10 since then w/o Cinnamon.

---

### Post by anders.gullhav on 2013-10-23
I had the same type of problem after an update yesterday. I'm running 12.04, and had the same type of problems (black desktop background, flickering colors, etc) when running Unity 3d. However Unity 2d and Cinnamon worked without problem. I thought this might have something to do with my graphics card driver (fglrx), but after removing Cinnamon (and rebooting) the problems have disappeared.

Thank you!
Anders

---

### Post by winlinuser-gmail on 2013-10-23
Hi ajgreeny - thanks for the guide.  I'm not sure if I am just as happy to continue with Cinnamon until it fixes itself - or not :-D
Many Thanks

---

### Post by winlinuser-gmail on 2013-10-23
Hi Krakonos  that's interesting.  I had hoped that Ubuntu was going to allow multi DT's as a matter of policy.  Perhaps I was dreaming.  if Cinnamon and Gnome are having issues, I wonder if anyone using Mate is affected?  Ho Hum - perhaps it's just a one-off slip :oops:

---

### Post by winlinuser-gmail on 2013-10-23
Hi Frogs Hair - this is starting to look like a "trend".  Many thanks for your post :-)

---

### Post by winlinuser-gmail on 2013-10-23
Hi Anders - Oh this is interesting.  Many thanks for posting.  I am on 12.04 too and whilst I am trying to like Unity, I really like Cinnamon and would prefer to keep it (for now at least).  Perhaps, as others appear to be having similar issues, the Ubuntu team / Cinnamon Team will generate a fix soon.  fingers crossed.

Many thanks to all of you who have posted replies - greatly appreciated guys.

---

### Post by coffeecat on 2013-10-23
> **winlinuser-gmail said:**
> Hi Krakonos  that's interesting.  I had hoped that Ubuntu was going to allow multi DT's as a matter of policy.  Perhaps I was dreaming.  if Cinnamon and Gnome are having issues, I wonder if anyone using Mate is affected?  Ho Hum - perhaps it's just a one-off slip :oops:

You installed Cinnamon from a PPA did you not? A PPA is a 3rd party repo. Which means that Cinnamon in 12.04 is not an Ubuntu official package. Judging by the comments in this thread it seems that a Cinnamon update has broken Unity, which is down to the Cinnamon PPA maintainers to fix. Nothing to do with the Ubuntu team and nothing to do with being able to run multiple DE's. When a bug in an unofficial desktop breaks the official desktop, that sounds like a significant bug in an unofficial package to me.

---

### Post by winlinuser-gmail on 2013-10-23
Hi Coffee Cat - Clearly I have things to learn about how "Linux" functions :-D.  I hope that the Cinnamon team are able to fix this issue - the most serious one I have ever encountered.  It is obvious that there are issues to be sorted by using multy 3rd party DT's (I thought it was too good to be true) but perhaps it is early days in this respect.  
**Many thanks for your post.**

---

### Post by coffeecat on 2013-10-23
Sure - I can understand how this sort of thing can look bad, especially since Ubuntu (through launchpad) provides facilities for PPA repos, but it is important to remember that PPA packages may not be as thoroughly tested as official repo packages. That's not meant as a criticism, merely a reflection of the resources available to lone maintainers or small teams. Also, a cautionary comment from two wiki pages about validation:

[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> PPAs have not undergone the same process of validation as regular ubuntu packages. End users install PPAs at their own risk. Although each key is cryptographically signed, in order to confirm an uploader, keys are not matched to specific individuals, except via their "launchpad" accounts.  

I see that Cinnamon is now available through the Universe repository for the latest two releases of Ubuntu, which means that you don't have to install a PPA, but even from the Universe repository, it will not be an officially supported package.

---

### Post by winlinuser-gmail on 2013-10-23
Hi Coffee Cat - many thanks for the comments - makes perfect sense.  I really can't remember where I loaded Cinnamon from (getting old) but I understand that MY actions are no reflection on Ubuntu which is now on all of my machines and with which I am VERY VERY pleased.  I had used Mint 9 previously (outstanding) but subsequent releases have been "problematic" on my hardware - hence my trouble free move to Ubuntu.  Even my father (88) has swapped from XP to Ubuntu and is delighted.

---

### Post by edubkendo on 2013-10-23
Phew, so glad to find this. Also had a copy of cinnamon installed from ages ago when I wanted to check it out. It never ran very cleanly on my hardware and so I had almost forgotten about it. Had exactly zero suspicions that it was the cause of these problems (exactly like the OP's screenshots and descriptions) and following recent updates to kernel and whatnot. Here's hoping this works, and this is a good lesson for me on removing packages I don't use.

EDIT: Definitely appears to have resolved it.

---

### Post by winlinuser-gmail on 2013-10-24
Hi [[COLOR=#000000]edubkendo[/COLOR]]("http://ubuntuforums.org/member.php?u=1557667") - sorry to hear you had this problem too - but so glad it was not just me :-D
Certainly, Cinnamon is the problem.  Let's hope the Cinnamon team fix it soon and we can all get back to "normal".

---

### Post by vmsman on 2013-10-25
Glad to see that everyone has been noting this issue.  I started to see the problem at times in 13.04 but when I went to 13.10, I encountered not only the black wallpaper and "smeared" windows but also a login loop.  I tried numerous times to correct the problem but the only thing that worked was purging cinnamon and therefore nemo completely.  The problem occurs once you apply the gsettings to allow cinnamon to manage the desktop rather than nautilus.  Apparently in Saucy Cinnamon does not play well with Unity.  

This has given me a lot of grief because the new nautilus is a real letdown considering it's lack of ability to remember individual folder preferences.  That's the main thing that drove me to Nemo.  Nemo has got some tremendous features and is stabile but I have also learned how to customize and work with Unity and can't see going back to gnome at this point.  IN 13.04 there was a patched version of nautilus that ran like the older nautilus version but that version does not play with saucy.

I totally agree that cinnamon is the problem here and it is not a Canonical issue at all.  The Canonical issue is why they have not provided a more reobust file manager and instead appear to have taken backward steps with the current deprecated version of Nautilus.  I am looking for any ideas on how to get a file manager into saucy that will at least remember folder preferences at the very least.

This one hurts I hate to say.

---

### Post by winlinuser-gmail on 2013-10-25
Hi [[COLOR=#000000]vmsman[/COLOR]]("http://ubuntuforums.org/member.php?u=1482284") is looks like you are more aware of the technical issues than I.  If you uncover a solution please post it to this thread  there are a number of people awaiting some good news :-D
Many thanks for your post.

---

### Post by winlinuser-gmail on 2013-10-30
Yesterday Ubuntu reported a system error with Cinnamon running.  I've had enough and uninstalled Cinnamon.  Unity was trashed but the basic OS was OK.  I had to reinstall Unity (easy) and now all is well.  Just as well I can use Unity....

---

