---
title: "Upgrading of Webmin gets stuck at unpacking 17.30"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by Frank_Harland on 2015-03-21
Hi, i'm in a loop here, can not install/upgrade nor uninstall webmin. All upgrading hangs on ubuntu 14.10. This runs within a VirtualBox btw. Using dpkg. What do I do to get out of this loop? 
3.13.0-45-generic

---

### Post by ian-weisser on 2015-03-22
Could you please provide a detailed apt or dpkg terminal session output showing the hang or loop?

---

### Post by Frank_Harland on 2015-05-02
Hello, sorry this has taken so long. First attended to install a dual boot ubuntu / windows 7 machine with a raid 1 disk and had to do some work in the meantime :-|. Very glad you reacted, here is some output, but doubt if it will help you / me any. It's the copy of the log file: dpkg.log.


2015-05-03 00:16:00 status half-installed webmin:all 1.730
2015-05-03 00:16:02 status unpacked webmin:all 1.740
2015-05-03 00:16:02 status unpacked webmin:all 1.740
2015-05-03 00:16:05 upgrade base-files:amd64 7.2ubuntu5.1 7.2ubuntu5.2
2015-05-03 00:16:05 status half-configured base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:05 status unpacked base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:06 status half-installed base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:06 status triggers-pending install-info:amd64 5.2.0.dfsg.1-2
2015-05-03 00:16:06 status triggers-pending cracklib-runtime:amd64 2.9.1-1build1
2015-05-03 00:16:07 status half-installed base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:07 status triggers-pending plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:08 status half-installed base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:11 status half-installed base-files:amd64 7.2ubuntu5.1
2015-05-03 00:16:12 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:12 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:13 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-05-03 00:16:13 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-05-03 00:16:14 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-05-03 00:16:15 trigproc ureadahead:amd64 0.100.0-16 0.100.0-16
2015-05-03 00:16:15 status half-configured ureadahead:amd64 0.100.0-16
2015-05-03 00:16:15 status installed ureadahead:amd64 0.100.0-16
2015-05-03 00:16:15 trigproc install-info:amd64 5.2.0.dfsg.1-2 5.2.0.dfsg.1-2
2015-05-03 00:16:15 status half-configured install-info:amd64 5.2.0.dfsg.1-2
2015-05-03 00:16:16 status installed install-info:amd64 5.2.0.dfsg.1-2
2015-05-03 00:16:16 trigproc cracklib-runtime:amd64 2.9.1-1build1 2.9.1-1build1
2015-05-03 00:16:16 status half-configured cracklib-runtime:amd64 2.9.1-1build1
2015-05-03 00:16:17 status installed cracklib-runtime:amd64 2.9.1-1build1
2015-05-03 00:16:17 trigproc plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1 0.8.8-0ubuntu17.1
2015-05-03 00:16:17 status half-configured plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:18 status installed plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:19 status triggers-pending initramfs-tools:all 0.103ubuntu4.2
2015-05-03 00:16:19 trigproc initramfs-tools:all 0.103ubuntu4.2 0.103ubuntu4.2
2015-05-03 00:16:19 status half-configured initramfs-tools:all 0.103ubuntu4.2
2015-05-03 00:16:39 status installed initramfs-tools:all 0.103ubuntu4.2
2015-05-03 00:16:40 startup packages configure
2015-05-03 00:16:40 configure base-files:amd64 7.2ubuntu5.2 <none>
2015-05-03 00:16:40 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:41 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:41 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:41 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:42 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:42 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:43 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:43 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:44 status triggers-pending plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:44 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:45 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:45 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:45 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:46 status unpacked base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:46 status half-configured base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:47 status triggers-awaited base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:47 trigproc plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1 <none>
2015-05-03 00:16:47 status half-configured plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:48 status installed base-files:amd64 7.2ubuntu5.2
2015-05-03 00:16:49 status installed plymouth-theme-ubuntu-text:amd64 0.8.8-0ubuntu17.1
2015-05-03 00:16:49 status triggers-pending initramfs-tools:all 0.103ubuntu4.2
2015-05-03 00:16:50 trigproc initramfs-tools:all 0.103ubuntu4.2 <none>
2015-05-03 00:16:50 status half-configured initramfs-tools:all 0.103ubuntu4.2
2015-05-03 00:17:00 status installed initramfs-tools:all 0.103ubuntu4.2

---

### Post by ian-weisser on 2015-05-02
The errors provided by an apt session, or a term log (in the same dir as the log you provided!) would be much more useful.

---

