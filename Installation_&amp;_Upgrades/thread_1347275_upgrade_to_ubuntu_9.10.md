---
title: "upgrade to ubuntu 9.10"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by hockey97 on 2009-12-06
I just tried to upgrade to ubuntu 9.10.

I get errors when I try to upgrade to 9.10
the errors are many packages failed to install.

then it said that the upgrade installed successfully and then displays a message saying some files weren't installed this will make your system unstable.

I get the basic error saying the package name and then followed by saying it failed ot install.  this is about half the packages being installed they get these failed error's 

Here is my dpkg.log file:
```
2009-11-06 16:04:28 startup archives unpack
2009-11-06 16:05:47 upgrade landscape-common 1.3.2.3-0ubuntu0.9.04.0 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:05:47 status half-configured landscape-common 1.3.2.3-0ubuntu0.9.04.0
2009-11-06 16:05:50 status unpacked landscape-common 1.3.2.3-0ubuntu0.9.04.0
2009-11-06 16:05:50 status half-installed landscape-common 1.3.2.3-0ubuntu0.9.04.0
2009-11-06 16:05:51 status half-installed landscape-common 1.3.2.3-0ubuntu0.9.04.0
2009-11-06 16:05:52 status unpacked landscape-common 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:05:52 status unpacked landscape-common 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:05:53 upgrade linux-image-2.6.28-16-generic 2.6.28-16.55 2.6.28-16.56
2009-11-06 16:05:53 status half-configured linux-image-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:05:53 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:05:53 status half-installed linux-image-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:07:03 status half-installed linux-image-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:07:13 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:07:16 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:07:19 upgrade update-manager 1:0.111.9 1:0.111.10
2009-11-06 16:07:19 status half-configured update-manager 1:0.111.9
2009-11-06 16:07:30 status unpacked update-manager 1:0.111.9
2009-11-06 16:07:30 status half-installed update-manager 1:0.111.9
2009-11-06 16:07:31 status triggers-pending man-db 2.5.5-1build1
2009-11-06 16:07:31 status half-installed update-manager 1:0.111.9
2009-11-06 16:07:31 status half-installed update-manager 1:0.111.9
2009-11-06 16:07:32 status unpacked update-manager 1:0.111.10
2009-11-06 16:07:32 status unpacked update-manager 1:0.111.10
2009-11-06 16:07:33 upgrade update-manager-core 1:0.111.9 1:0.111.10
2009-11-06 16:07:33 status half-configured update-manager-core 1:0.111.9
2009-11-06 16:07:33 status unpacked update-manager-core 1:0.111.9
2009-11-06 16:07:33 status half-installed update-manager-core 1:0.111.9
2009-11-06 16:07:34 status half-installed update-manager-core 1:0.111.9
2009-11-06 16:07:34 status unpacked update-manager-core 1:0.111.10
2009-11-06 16:07:35 status unpacked update-manager-core 1:0.111.10
2009-11-06 16:07:35 upgrade libclamav6 0.95.2+dfsg-4ubuntu1.2 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:35 status half-configured libclamav6 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:35 status unpacked libclamav6 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:35 status half-installed libclamav6 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:35 status half-installed libclamav6 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:36 status unpacked libclamav6 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:36 status unpacked libclamav6 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:36 upgrade clamav-daemon 0.95.2+dfsg-4ubuntu1.2 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:36 status half-configured clamav-daemon 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:38 status unpacked clamav-daemon 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:38 status half-installed clamav-daemon 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:38 status half-installed clamav-daemon 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:39 status half-installed clamav-daemon 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:39 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:39 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:39 upgrade clamav-base 0.95.2+dfsg-4ubuntu1.2 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:39 status half-configured clamav-base 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:39 status unpacked clamav-base 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:40 status half-installed clamav-base 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:49 status half-installed clamav-base 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:50 status half-installed clamav-base 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:50 status unpacked clamav-base 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:50 status unpacked clamav-base 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:50 upgrade clamav-freshclam 0.95.2+dfsg-4ubuntu1.2 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:50 status half-configured clamav-freshclam 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:53 status unpacked clamav-freshclam 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:53 status half-installed clamav-freshclam 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:53 status half-installed clamav-freshclam 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:53 status half-installed clamav-freshclam 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:53 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:54 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:54 upgrade clamav 0.95.2+dfsg-4ubuntu1.2 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:54 status half-configured clamav 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:54 status unpacked clamav 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:54 status half-installed clamav 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:54 status half-installed clamav 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:54 status half-installed clamav 0.95.2+dfsg-4ubuntu1.2
2009-11-06 16:07:55 status unpacked clamav 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:55 status unpacked clamav 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:07:55 upgrade libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:07:55 status half-configured libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1
2009-11-06 16:07:55 status unpacked libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1
2009-11-06 16:07:55 status half-installed libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1
2009-11-06 16:07:55 status half-installed libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1
2009-11-06 16:07:56 status unpacked libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:07:56 status unpacked libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:07:56 upgrade libhtml-parser-perl 3.59-1ubuntu1 3.59-1ubuntu1.1
2009-11-06 16:07:56 status half-configured libhtml-parser-perl 3.59-1ubuntu1
2009-11-06 16:07:56 status unpacked libhtml-parser-perl 3.59-1ubuntu1
2009-11-06 16:07:56 status half-installed libhtml-parser-perl 3.59-1ubuntu1
2009-11-06 16:07:57 status half-installed libhtml-parser-perl 3.59-1ubuntu1
2009-11-06 16:07:57 status half-installed libhtml-parser-perl 3.59-1ubuntu1
2009-11-06 16:07:57 status unpacked libhtml-parser-perl 3.59-1ubuntu1.1
2009-11-06 16:07:58 status unpacked libhtml-parser-perl 3.59-1ubuntu1.1
2009-11-06 16:07:58 upgrade linux-headers-2.6.28-16 2.6.28-16.55 2.6.28-16.56
2009-11-06 16:07:58 status half-configured linux-headers-2.6.28-16 2.6.28-16.55
2009-11-06 16:07:58 status unpacked linux-headers-2.6.28-16 2.6.28-16.55
2009-11-06 16:07:58 status half-installed linux-headers-2.6.28-16 2.6.28-16.55
2009-11-06 16:08:27 status half-installed linux-headers-2.6.28-16 2.6.28-16.55
2009-11-06 16:08:29 status unpacked linux-headers-2.6.28-16 2.6.28-16.56
2009-11-06 16:08:31 status unpacked linux-headers-2.6.28-16 2.6.28-16.56
2009-11-06 16:08:32 upgrade linux-headers-2.6.28-16-generic 2.6.28-16.55 2.6.28-16.56
2009-11-06 16:08:32 status half-configured linux-headers-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:08:32 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:08:32 status half-installed linux-headers-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:08:39 status half-installed linux-headers-2.6.28-16-generic 2.6.28-16.55
2009-11-06 16:08:40 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:08:40 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:08:41 upgrade linux-libc-dev 2.6.28-16.55 2.6.28-16.56
2009-11-06 16:08:41 status half-configured linux-libc-dev 2.6.28-16.55
2009-11-06 16:08:42 status unpacked linux-libc-dev 2.6.28-16.55
2009-11-06 16:08:42 status half-installed linux-libc-dev 2.6.28-16.55
2009-11-06 16:08:43 status half-installed linux-libc-dev 2.6.28-16.55
2009-11-06 16:08:44 status unpacked linux-libc-dev 2.6.28-16.56
2009-11-06 16:08:44 status unpacked linux-libc-dev 2.6.28-16.56
2009-11-06 16:08:44 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-11-06 16:08:44 status half-configured man-db 2.5.5-1build1
2009-11-06 16:08:49 status installed man-db 2.5.5-1build1
2009-11-06 16:08:51 startup packages configure
2009-11-06 16:08:51 configure landscape-common 1.3.2.3-0ubuntu0.9.04.1 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:08:51 status unpacked landscape-common 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:08:51 status half-configured landscape-common 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:09:08 status installed landscape-common 1.3.2.3-0ubuntu0.9.04.1
2009-11-06 16:09:08 configure linux-image-2.6.28-16-generic 2.6.28-16.56 2.6.28-16.56
2009-11-06 16:09:08 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:09:08 status half-configured linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:10:19 status installed linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:10:19 configure update-manager-core 1:0.111.10 1:0.111.10
2009-11-06 16:10:19 status unpacked update-manager-core 1:0.111.10
2009-11-06 16:10:19 status unpacked update-manager-core 1:0.111.10
2009-11-06 16:10:19 status unpacked update-manager-core 1:0.111.10
2009-11-06 16:10:19 status half-configured update-manager-core 1:0.111.10
2009-11-06 16:10:21 status installed update-manager-core 1:0.111.10
2009-11-06 16:10:21 configure update-manager 1:0.111.10 1:0.111.10
2009-11-06 16:10:21 status unpacked update-manager 1:0.111.10
2009-11-06 16:10:21 status half-configured update-manager 1:0.111.10
2009-11-06 16:10:32 status installed update-manager 1:0.111.10
2009-11-06 16:10:32 configure libclamav6 0.95.3+dfsg-1ubuntu0.09.04 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status unpacked libclamav6 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status half-configured libclamav6 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status installed libclamav6 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status triggers-pending libc6 2.9-4ubuntu6.1
2009-11-06 16:10:32 configure clamav-base 0.95.3+dfsg-1ubuntu0.09.04 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status unpacked clamav-base 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:32 status half-configured clamav-base 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status installed clamav-base 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 configure clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:10:59 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:00 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:00 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:00 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:00 status unpacked clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:00 status half-configured clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status installed clamav-freshclam 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 configure clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status unpacked clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:10 status half-configured clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:32 status installed clamav-daemon 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:33 configure clamav 0.95.3+dfsg-1ubuntu0.09.04 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:33 status unpacked clamav 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:33 status half-configured clamav 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:33 status installed clamav 0.95.3+dfsg-1ubuntu0.09.04
2009-11-06 16:11:33 configure libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:11:33 status unpacked libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:11:33 status half-configured libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:11:33 status installed libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1
2009-11-06 16:11:33 configure libhtml-parser-perl 3.59-1ubuntu1.1 3.59-1ubuntu1.1
2009-11-06 16:11:33 status unpacked libhtml-parser-perl 3.59-1ubuntu1.1
2009-11-06 16:11:33 status half-configured libhtml-parser-perl 3.59-1ubuntu1.1
2009-11-06 16:11:33 status installed libhtml-parser-perl 3.59-1ubuntu1.1
2009-11-06 16:11:33 configure linux-headers-2.6.28-16 2.6.28-16.56 2.6.28-16.56
2009-11-06 16:11:33 status unpacked linux-headers-2.6.28-16 2.6.28-16.56
2009-11-06 16:11:33 status half-configured linux-headers-2.6.28-16 2.6.28-16.56
2009-11-06 16:11:33 status installed linux-headers-2.6.28-16 2.6.28-16.56
2009-11-06 16:11:33 configure linux-headers-2.6.28-16-generic 2.6.28-16.56 2.6.28-16.56
2009-11-06 16:11:33 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:11:34 status half-configured linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:11:40 status installed linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-06 16:11:40 configure linux-libc-dev 2.6.28-16.56 2.6.28-16.56
2009-11-06 16:11:40 status unpacked linux-libc-dev 2.6.28-16.56
2009-11-06 16:11:40 status half-configured linux-libc-dev 2.6.28-16.56
2009-11-06 16:11:40 status installed linux-libc-dev 2.6.28-16.56
2009-11-06 16:11:40 trigproc libc6 2.9-4ubuntu6.1 2.9-4ubuntu6.1
2009-11-06 16:11:40 status half-configured libc6 2.9-4ubuntu6.1
2009-11-06 16:11:42 status installed libc6 2.9-4ubuntu6.1
2009-11-11 14:03:44 startup archives unpack
2009-11-11 14:04:00 upgrade libqt4-opengl-dev 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:00 status half-configured libqt4-opengl-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:00 status unpacked libqt4-opengl-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:00 status half-installed libqt4-opengl-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:01 status half-installed libqt4-opengl-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:01 status unpacked libqt4-opengl-dev 4.5.0-0ubuntu4.3
2009-11-11 14:04:01 status unpacked libqt4-opengl-dev 4.5.0-0ubuntu4.3
2009-11-11 14:04:02 upgrade libqt4-dev 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:02 status half-configured libqt4-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:02 status unpacked libqt4-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:02 status half-installed libqt4-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:04 status triggers-pending man-db 2.5.5-1build1
2009-11-11 14:04:04 status half-installed libqt4-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:07 status half-installed libqt4-dev 4.5.0-0ubuntu4.2
2009-11-11 14:04:11 status unpacked libqt4-dev 4.5.0-0ubuntu4.3
2009-11-11 14:04:11 status unpacked libqt4-dev 4.5.0-0ubuntu4.3
2009-11-11 14:04:12 upgrade libqt4-scripttools 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:12 status half-configured libqt4-scripttools 4.5.0-0ubuntu4.2
2009-11-11 14:04:12 status unpacked libqt4-scripttools 4.5.0-0ubuntu4.2
2009-11-11 14:04:12 status half-installed libqt4-scripttools 4.5.0-0ubuntu4.2
2009-11-11 14:04:12 status half-installed libqt4-scripttools 4.5.0-0ubuntu4.2
2009-11-11 14:04:13 status unpacked libqt4-scripttools 4.5.0-0ubuntu4.3
2009-11-11 14:04:13 status unpacked libqt4-scripttools 4.5.0-0ubuntu4.3
2009-11-11 14:04:13 upgrade qt4-qtconfig 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:13 status half-configured qt4-qtconfig 4.5.0-0ubuntu4.2
2009-11-11 14:04:13 status unpacked qt4-qtconfig 4.5.0-0ubuntu4.2
2009-11-11 14:04:13 status half-installed qt4-qtconfig 4.5.0-0ubuntu4.2
2009-11-11 14:04:13 status half-installed qt4-qtconfig 4.5.0-0ubuntu4.2
2009-11-11 14:04:13 status half-installed qt4-qtconfig 4.5.0-0ubuntu4.2
2009-11-11 14:04:14 status unpacked qt4-qtconfig 4.5.0-0ubuntu4.3
2009-11-11 14:04:14 status unpacked qt4-qtconfig 4.5.0-0ubuntu4.3
2009-11-11 14:04:14 upgrade libqt4-qt3support 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:14 status half-configured libqt4-qt3support 4.5.0-0ubuntu4.2
2009-11-11 14:04:14 status unpacked libqt4-qt3support 4.5.0-0ubuntu4.2
2009-11-11 14:04:14 status half-installed libqt4-qt3support 4.5.0-0ubuntu4.2
2009-11-11 14:04:15 status half-installed libqt4-qt3support 4.5.0-0ubuntu4.2
2009-11-11 14:04:16 status unpacked libqt4-qt3support 4.5.0-0ubuntu4.3
2009-11-11 14:04:16 status unpacked libqt4-qt3support 4.5.0-0ubuntu4.3
2009-11-11 14:04:16 upgrade libqt4-designer 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:16 status half-configured libqt4-designer 4.5.0-0ubuntu4.2
2009-11-11 14:04:16 status unpacked libqt4-designer 4.5.0-0ubuntu4.2
2009-11-11 14:04:16 status half-installed libqt4-designer 4.5.0-0ubuntu4.2
2009-11-11 14:04:17 status half-installed libqt4-designer 4.5.0-0ubuntu4.2
2009-11-11 14:04:20 status unpacked libqt4-designer 4.5.0-0ubuntu4.3
2009-11-11 14:04:20 status unpacked libqt4-designer 4.5.0-0ubuntu4.3
2009-11-11 14:04:21 upgrade libqt4-script 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:21 status half-configured libqt4-script 4.5.0-0ubuntu4.2
2009-11-11 14:04:21 status unpacked libqt4-script 4.5.0-0ubuntu4.2
2009-11-11 14:04:21 status half-installed libqt4-script 4.5.0-0ubuntu4.2
2009-11-11 14:04:21 status half-installed libqt4-script 4.5.0-0ubuntu4.2
2009-11-11 14:04:21 status unpacked libqt4-script 4.5.0-0ubuntu4.3
2009-11-11 14:04:22 status unpacked libqt4-script 4.5.0-0ubuntu4.3
2009-11-11 14:04:22 upgrade libqt4-dbus 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:22 status half-configured libqt4-dbus 4.5.0-0ubuntu4.2
2009-11-11 14:04:22 status unpacked libqt4-dbus 4.5.0-0ubuntu4.2
2009-11-11 14:04:22 status half-installed libqt4-dbus 4.5.0-0ubuntu4.2
2009-11-11 14:04:22 status half-installed libqt4-dbus 4.5.0-0ubuntu4.2
2009-11-11 14:04:22 status unpacked libqt4-dbus 4.5.0-0ubuntu4.3
2009-11-11 14:04:23 status unpacked libqt4-dbus 4.5.0-0ubuntu4.3
2009-11-11 14:04:23 upgrade libqt4-xml 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:23 status half-configured libqt4-xml 4.5.0-0ubuntu4.2
2009-11-11 14:04:23 status unpacked libqt4-xml 4.5.0-0ubuntu4.2
2009-11-11 14:04:23 status half-installed libqt4-xml 4.5.0-0ubuntu4.2
2009-11-11 14:04:23 status half-installed libqt4-xml 4.5.0-0ubuntu4.2
2009-11-11 14:04:23 status unpacked libqt4-xml 4.5.0-0ubuntu4.3
2009-11-11 14:04:23 status unpacked libqt4-xml 4.5.0-0ubuntu4.3
2009-11-11 14:04:24 upgrade libqt4-sql-mysql 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:24 status half-configured libqt4-sql-mysql 4.5.0-0ubuntu4.2
2009-11-11 14:04:24 status unpacked libqt4-sql-mysql 4.5.0-0ubuntu4.2
2009-11-11 14:04:24 status half-installed libqt4-sql-mysql 4.5.0-0ubuntu4.2
2009-11-11 14:04:24 status half-installed libqt4-sql-mysql 4.5.0-0ubuntu4.2
2009-11-11 14:04:24 status unpacked libqt4-sql-mysql 4.5.0-0ubuntu4.3
2009-11-11 14:04:24 status unpacked libqt4-sql-mysql 4.5.0-0ubuntu4.3
2009-11-11 14:04:24 upgrade libqt4-help 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:24 status half-configured libqt4-help 4.5.0-0ubuntu4.2
2009-11-11 14:04:24 status unpacked libqt4-help 4.5.0-0ubuntu4.2
2009-11-11 14:04:25 status half-installed libqt4-help 4.5.0-0ubuntu4.2
2009-11-11 14:04:25 status half-installed libqt4-help 4.5.0-0ubuntu4.2
2009-11-11 14:04:25 status unpacked libqt4-help 4.5.0-0ubuntu4.3
2009-11-11 14:04:25 status unpacked libqt4-help 4.5.0-0ubuntu4.3
2009-11-11 14:04:25 upgrade libqt4-sql 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:25 status half-configured libqt4-sql 4.5.0-0ubuntu4.2
2009-11-11 14:04:25 status unpacked libqt4-sql 4.5.0-0ubuntu4.2
2009-11-11 14:04:25 status half-installed libqt4-sql 4.5.0-0ubuntu4.2
2009-11-11 14:04:26 status half-installed libqt4-sql 4.5.0-0ubuntu4.2
2009-11-11 14:04:26 status unpacked libqt4-sql 4.5.0-0ubuntu4.3
2009-11-11 14:04:26 status unpacked libqt4-sql 4.5.0-0ubuntu4.3
2009-11-11 14:04:26 upgrade libqt4-webkit 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:26 status half-configured libqt4-webkit 4.5.0-0ubuntu4.2
2009-11-11 14:04:26 status unpacked libqt4-webkit 4.5.0-0ubuntu4.2
2009-11-11 14:04:26 status half-installed libqt4-webkit 4.5.0-0ubuntu4.2
2009-11-11 14:04:28 status half-installed libqt4-webkit 4.5.0-0ubuntu4.2
2009-11-11 14:04:31 status unpacked libqt4-webkit 4.5.0-0ubuntu4.3
2009-11-11 14:04:31 status unpacked libqt4-webkit 4.5.0-0ubuntu4.3
2009-11-11 14:04:31 upgrade libqt4-svg 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:31 status half-configured libqt4-svg 4.5.0-0ubuntu4.2
2009-11-11 14:04:31 status unpacked libqt4-svg 4.5.0-0ubuntu4.2
2009-11-11 14:04:31 status half-installed libqt4-svg 4.5.0-0ubuntu4.2
2009-11-11 14:04:31 status half-installed libqt4-svg 4.5.0-0ubuntu4.2
2009-11-11 14:04:32 status unpacked libqt4-svg 4.5.0-0ubuntu4.3
2009-11-11 14:04:32 status unpacked libqt4-svg 4.5.0-0ubuntu4.3
2009-11-11 14:04:32 upgrade libqt4-opengl 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:32 status half-configured libqt4-opengl 4.5.0-0ubuntu4.2
2009-11-11 14:04:32 status unpacked libqt4-opengl 4.5.0-0ubuntu4.2
2009-11-11 14:04:32 status half-installed libqt4-opengl 4.5.0-0ubuntu4.2
2009-11-11 14:04:32 status half-installed libqt4-opengl 4.5.0-0ubuntu4.2
2009-11-11 14:04:33 status unpacked libqt4-opengl 4.5.0-0ubuntu4.3
2009-11-11 14:04:33 status unpacked libqt4-opengl 4.5.0-0ubuntu4.3
2009-11-11 14:04:33 upgrade libqtgui4 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:33 status half-configured libqtgui4 4.5.0-0ubuntu4.2
2009-11-11 14:04:33 status unpacked libqtgui4 4.5.0-0ubuntu4.2
2009-11-11 14:04:33 status half-installed libqtgui4 4.5.0-0ubuntu4.2
2009-11-11 14:04:35 status half-installed libqtgui4 4.5.0-0ubuntu4.2
2009-11-11 14:04:37 status unpacked libqtgui4 4.5.0-0ubuntu4.3
2009-11-11 14:04:37 status unpacked libqtgui4 4.5.0-0ubuntu4.3
2009-11-11 14:04:37 upgrade libqt4-assistant 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:37 status half-configured libqt4-assistant 4.5.0-0ubuntu4.2
2009-11-11 14:04:37 status unpacked libqt4-assistant 4.5.0-0ubuntu4.2
2009-11-11 14:04:37 status half-installed libqt4-assistant 4.5.0-0ubuntu4.2
2009-11-11 14:04:37 status half-installed libqt4-assistant 4.5.0-0ubuntu4.2
2009-11-11 14:04:38 status unpacked libqt4-assistant 4.5.0-0ubuntu4.3
2009-11-11 14:04:38 status unpacked libqt4-assistant 4.5.0-0ubuntu4.3
2009-11-11 14:04:38 upgrade libqt4-xmlpatterns 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:38 status half-configured libqt4-xmlpatterns 4.5.0-0ubuntu4.2
2009-11-11 14:04:38 status unpacked libqt4-xmlpatterns 4.5.0-0ubuntu4.2
2009-11-11 14:04:38 status half-installed libqt4-xmlpatterns 4.5.0-0ubuntu4.2
2009-11-11 14:04:38 status half-installed libqt4-xmlpatterns 4.5.0-0ubuntu4.2
2009-11-11 14:04:39 status unpacked libqt4-xmlpatterns 4.5.0-0ubuntu4.3
2009-11-11 14:04:39 status unpacked libqt4-xmlpatterns 4.5.0-0ubuntu4.3
2009-11-11 14:04:39 upgrade libqt4-network 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:39 status half-configured libqt4-network 4.5.0-0ubuntu4.2
2009-11-11 14:04:39 status unpacked libqt4-network 4.5.0-0ubuntu4.2
2009-11-11 14:04:39 status half-installed libqt4-network 4.5.0-0ubuntu4.2
2009-11-11 14:04:40 status half-installed libqt4-network 4.5.0-0ubuntu4.2
2009-11-11 14:04:40 status unpacked libqt4-network 4.5.0-0ubuntu4.3
2009-11-11 14:04:40 status unpacked libqt4-network 4.5.0-0ubuntu4.3
2009-11-11 14:04:40 upgrade libqt4-test 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:40 status half-configured libqt4-test 4.5.0-0ubuntu4.2
2009-11-11 14:04:40 status unpacked libqt4-test 4.5.0-0ubuntu4.2
2009-11-11 14:04:41 status half-installed libqt4-test 4.5.0-0ubuntu4.2
2009-11-11 14:04:41 status half-installed libqt4-test 4.5.0-0ubuntu4.2
2009-11-11 14:04:41 status unpacked libqt4-test 4.5.0-0ubuntu4.3
2009-11-11 14:04:41 status unpacked libqt4-test 4.5.0-0ubuntu4.3
2009-11-11 14:04:41 upgrade libqtcore4 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:41 status half-configured libqtcore4 4.5.0-0ubuntu4.2
2009-11-11 14:04:41 status unpacked libqtcore4 4.5.0-0ubuntu4.2
2009-11-11 14:04:41 status half-installed libqtcore4 4.5.0-0ubuntu4.2
2009-11-11 14:04:42 status half-installed libqtcore4 4.5.0-0ubuntu4.2
2009-11-11 14:04:43 status unpacked libqtcore4 4.5.0-0ubuntu4.3
2009-11-11 14:04:44 status unpacked libqtcore4 4.5.0-0ubuntu4.3
2009-11-11 14:04:44 upgrade qt4-qmake 4.5.0-0ubuntu4.2 4.5.0-0ubuntu4.3
2009-11-11 14:04:44 status half-configured qt4-qmake 4.5.0-0ubuntu4.2
2009-11-11 14:04:44 status unpacked qt4-qmake 4.5.0-0ubuntu4.2
2009-11-11 14:04:44 status half-installed qt4-qmake 4.5.0-0ubuntu4.2
2009-11-11 14:04:45 status half-installed qt4-qmake 4.5.0-0ubuntu4.2
2009-11-11 14:04:46 status half-installed qt4-qmake 4.5.0-0ubuntu4.2
2009-11-11 14:04:47 status unpacked qt4-qmake 4.5.0-0ubuntu4.3
2009-11-11 14:04:47 status unpacked qt4-qmake 4.5.0-0ubuntu4.3
2009-11-11 14:04:47 upgrade libcups2 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:04:47 status half-configured libcups2 1.3.9-17ubuntu3.2
2009-11-11 14:04:47 status unpacked libcups2 1.3.9-17ubuntu3.2
2009-11-11 14:04:47 status half-installed libcups2 1.3.9-17ubuntu3.2
2009-11-11 14:04:47 status half-installed libcups2 1.3.9-17ubuntu3.2
2009-11-11 14:04:48 status unpacked libcups2 1.3.9-17ubuntu3.4
2009-11-11 14:04:48 status unpacked libcups2 1.3.9-17ubuntu3.4
2009-11-11 14:04:48 upgrade libcupsimage2 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:04:48 status half-configured libcupsimage2 1.3.9-17ubuntu3.2
2009-11-11 14:04:48 status unpacked libcupsimage2 1.3.9-17ubuntu3.2
2009-11-11 14:04:48 status half-installed libcupsimage2 1.3.9-17ubuntu3.2
2009-11-11 14:04:48 status half-installed libcupsimage2 1.3.9-17ubuntu3.2
2009-11-11 14:04:49 status unpacked libcupsimage2 1.3.9-17ubuntu3.4
2009-11-11 14:04:49 status unpacked libcupsimage2 1.3.9-17ubuntu3.4
2009-11-11 14:04:49 upgrade cups-common 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:04:49 status half-configured cups-common 1.3.9-17ubuntu3.2
2009-11-11 14:04:49 status unpacked cups-common 1.3.9-17ubuntu3.2
2009-11-11 14:04:49 status half-installed cups-common 1.3.9-17ubuntu3.2
2009-11-11 14:04:50 status half-installed cups-common 1.3.9-17ubuntu3.2
2009-11-11 14:04:51 status unpacked cups-common 1.3.9-17ubuntu3.4
2009-11-11 14:04:51 status unpacked cups-common 1.3.9-17ubuntu3.4
2009-11-11 14:04:51 upgrade cups 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:04:51 status half-configured cups 1.3.9-17ubuntu3.2
2009-11-11 14:04:52 status unpacked cups 1.3.9-17ubuntu3.2
2009-11-11 14:04:52 status half-installed cups 1.3.9-17ubuntu3.2
2009-11-11 14:04:58 status triggers-pending doc-base 0.8.20
2009-11-11 14:04:59 status half-installed cups 1.3.9-17ubuntu3.2
2009-11-11 14:04:59 status half-installed cups 1.3.9-17ubuntu3.2
2009-11-11 14:05:00 status triggers-pending ufw 0.27-0ubuntu2
2009-11-11 14:05:00 status half-installed cups 1.3.9-17ubuntu3.2
2009-11-11 14:05:00 status half-installed cups 1.3.9-17ubuntu3.2
2009-11-11 14:05:01 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:01 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:01 upgrade cups-bsd 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:05:01 status half-configured cups-bsd 1.3.9-17ubuntu3.2
2009-11-11 14:05:03 status unpacked cups-bsd 1.3.9-17ubuntu3.2
2009-11-11 14:05:03 status half-installed cups-bsd 1.3.9-17ubuntu3.2
2009-11-11 14:05:03 status half-installed cups-bsd 1.3.9-17ubuntu3.2
2009-11-11 14:05:03 status half-installed cups-bsd 1.3.9-17ubuntu3.2
2009-11-11 14:05:03 status unpacked cups-bsd 1.3.9-17ubuntu3.4
2009-11-11 14:05:03 status unpacked cups-bsd 1.3.9-17ubuntu3.4
2009-11-11 14:05:03 upgrade cups-client 1.3.9-17ubuntu3.2 1.3.9-17ubuntu3.4
2009-11-11 14:05:03 status half-configured cups-client 1.3.9-17ubuntu3.2
2009-11-11 14:05:04 status unpacked cups-client 1.3.9-17ubuntu3.2
2009-11-11 14:05:04 status half-installed cups-client 1.3.9-17ubuntu3.2
2009-11-11 14:05:04 status half-installed cups-client 1.3.9-17ubuntu3.2
2009-11-11 14:05:04 status half-installed cups-client 1.3.9-17ubuntu3.2
2009-11-11 14:05:04 status unpacked cups-client 1.3.9-17ubuntu3.4
2009-11-11 14:05:04 status unpacked cups-client 1.3.9-17ubuntu3.4
2009-11-11 14:05:05 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-11-11 14:05:05 status half-configured man-db 2.5.5-1build1
2009-11-11 14:05:10 status installed man-db 2.5.5-1build1
2009-11-11 14:05:10 trigproc doc-base 0.8.20 0.8.20
2009-11-11 14:05:10 status half-configured doc-base 0.8.20
2009-11-11 14:05:11 status installed doc-base 0.8.20
2009-11-11 14:05:12 trigproc ufw 0.27-0ubuntu2 0.27-0ubuntu2
2009-11-11 14:05:12 status half-configured ufw 0.27-0ubuntu2
2009-11-11 14:05:14 status installed ufw 0.27-0ubuntu2
2009-11-11 14:05:16 startup packages configure
2009-11-11 14:05:16 configure libqtcore4 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status unpacked libqtcore4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status half-configured libqtcore4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status installed libqtcore4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status triggers-pending libc6 2.9-4ubuntu6.1
2009-11-11 14:05:16 configure libqtgui4 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status unpacked libqtgui4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status half-configured libqtgui4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status installed libqtgui4 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 configure libqt4-opengl 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:16 status unpacked libqt4-opengl 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status half-configured libqt4-opengl 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status installed libqt4-opengl 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 configure libqt4-xml 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status unpacked libqt4-xml 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status half-configured libqt4-xml 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status installed libqt4-xml 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 configure libqt4-dbus 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status unpacked libqt4-dbus 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status half-configured libqt4-dbus 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status installed libqt4-dbus 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 configure libqt4-script 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status unpacked libqt4-script 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status half-configured libqt4-script 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status installed libqt4-script 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 configure libqt4-designer 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status unpacked libqt4-designer 4.5.0-0ubuntu4.3
2009-11-11 14:05:17 status half-configured libqt4-designer 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status installed libqt4-designer 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 configure libqt4-network 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status unpacked libqt4-network 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status half-configured libqt4-network 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status installed libqt4-network 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 configure libqt4-sql 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status unpacked libqt4-sql 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status half-configured libqt4-sql 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status installed libqt4-sql 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 configure libqt4-qt3support 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status unpacked libqt4-qt3support 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status half-configured libqt4-qt3support 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status installed libqt4-qt3support 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 configure libqt4-svg 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status unpacked libqt4-svg 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status half-configured libqt4-svg 4.5.0-0ubuntu4.3
2009-11-11 14:05:18 status installed libqt4-svg 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 configure libqt4-webkit 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status unpacked libqt4-webkit 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status half-configured libqt4-webkit 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status installed libqt4-webkit 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 configure libqt4-scripttools 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status unpacked libqt4-scripttools 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status half-configured libqt4-scripttools 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status installed libqt4-scripttools 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 configure libqt4-xmlpatterns 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status unpacked libqt4-xmlpatterns 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status half-configured libqt4-xmlpatterns 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status installed libqt4-xmlpatterns 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 configure libqt4-help 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status unpacked libqt4-help 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status half-configured libqt4-help 4.5.0-0ubuntu4.3
2009-11-11 14:05:19 status installed libqt4-help 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 configure libqt4-assistant 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status unpacked libqt4-assistant 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status half-configured libqt4-assistant 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status installed libqt4-assistant 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 configure libqt4-test 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status unpacked libqt4-test 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status half-configured libqt4-test 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status installed libqt4-test 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 configure qt4-qmake 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status unpacked qt4-qmake 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status half-configured qt4-qmake 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status installed qt4-qmake 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 configure libqt4-dev 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:20 status unpacked libqt4-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status half-configured libqt4-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status installed libqt4-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 configure libqt4-opengl-dev 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status unpacked libqt4-opengl-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status half-configured libqt4-opengl-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status installed libqt4-opengl-dev 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 configure qt4-qtconfig 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:21 status unpacked qt4-qtconfig 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 status half-configured qt4-qtconfig 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 status installed qt4-qtconfig 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 configure libqt4-sql-mysql 4.5.0-0ubuntu4.3 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 status unpacked libqt4-sql-mysql 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 status half-configured libqt4-sql-mysql 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 status installed libqt4-sql-mysql 4.5.0-0ubuntu4.3
2009-11-11 14:05:22 configure libcups2 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status unpacked libcups2 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status half-configured libcups2 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status installed libcups2 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 configure libcupsimage2 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status unpacked libcupsimage2 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status half-configured libcupsimage2 1.3.9-17ubuntu3.4
2009-11-11 14:05:22 status installed libcupsimage2 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 configure cups-common 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups-common 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status half-configured cups-common 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status installed cups-common 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 configure cups 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:23 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status unpacked cups 1.3.9-17ubuntu3.4
2009-11-11 14:05:24 status half-configured cups 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status installed cups 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 configure cups-client 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status unpacked cups-client 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status half-configured cups-client 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status installed cups-client 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 configure cups-bsd 1.3.9-17ubuntu3.4 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status unpacked cups-bsd 1.3.9-17ubuntu3.4
2009-11-11 14:06:09 status half-configured cups-bsd 1.3.9-17ubuntu3.4
2009-11-11 14:06:11 status installed cups-bsd 1.3.9-17ubuntu3.4
2009-11-11 14:06:11 trigproc libc6 2.9-4ubuntu6.1 2.9-4ubuntu6.1
2009-11-11 14:06:11 status half-configured libc6 2.9-4ubuntu6.1
2009-11-11 14:06:12 status installed libc6 2.9-4ubuntu6.1
2009-11-11 14:59:11 startup archives unpack
2009-11-11 14:59:27 upgrade linux-image-2.6.28-16-generic 2.6.28-16.56 2.6.28-16.57
2009-11-11 14:59:27 status half-configured linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-11 14:59:27 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-11 14:59:27 status half-installed linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:00:20 status half-installed linux-image-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:00:27 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:00:34 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:00:34 upgrade libpulse0 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:34 status half-configured libpulse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:35 status unpacked libpulse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:35 status half-installed libpulse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:35 status half-installed libpulse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:35 status unpacked libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:35 status unpacked libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:35 upgrade libpulse-browse0 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:35 status half-configured libpulse-browse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status unpacked libpulse-browse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status half-installed libpulse-browse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status half-installed libpulse-browse0 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status unpacked libpulse-browse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:36 status unpacked libpulse-browse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:36 upgrade libpulsecore9 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:36 status half-configured libpulsecore9 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status unpacked libpulsecore9 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:36 status half-installed libpulsecore9 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:37 status half-installed libpulsecore9 1:0.9.14-0ubuntu20.2
2009-11-11 15:00:37 status unpacked libpulsecore9 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:37 status unpacked libpulsecore9 1:0.9.14-0ubuntu20.3
2009-11-11 15:00:37 upgrade linux-headers-2.6.28-16 2.6.28-16.56 2.6.28-16.57
2009-11-11 15:00:37 status half-configured linux-headers-2.6.28-16 2.6.28-16.56
2009-11-11 15:00:38 status unpacked linux-headers-2.6.28-16 2.6.28-16.56
2009-11-11 15:00:38 status half-installed linux-headers-2.6.28-16 2.6.28-16.56
2009-11-11 15:01:23 status half-installed linux-headers-2.6.28-16 2.6.28-16.56
2009-11-11 15:01:24 status unpacked linux-headers-2.6.28-16 2.6.28-16.57
2009-11-11 15:01:26 status unpacked linux-headers-2.6.28-16 2.6.28-16.57
2009-11-11 15:01:27 upgrade linux-headers-2.6.28-16-generic 2.6.28-16.56 2.6.28-16.57
2009-11-11 15:01:27 status half-configured linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:01:27 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:01:27 status half-installed linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:01:32 status half-installed linux-headers-2.6.28-16-generic 2.6.28-16.56
2009-11-11 15:01:34 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:01:35 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:01:36 upgrade linux-libc-dev 2.6.28-16.56 2.6.28-16.57
2009-11-11 15:01:36 status half-configured linux-libc-dev 2.6.28-16.56
2009-11-11 15:01:36 status unpacked linux-libc-dev 2.6.28-16.56
2009-11-11 15:01:36 status half-installed linux-libc-dev 2.6.28-16.56
2009-11-11 15:01:37 status half-installed linux-libc-dev 2.6.28-16.56
2009-11-11 15:01:38 status unpacked linux-libc-dev 2.6.28-16.57
2009-11-11 15:01:38 status unpacked linux-libc-dev 2.6.28-16.57
2009-11-11 15:01:38 upgrade pulseaudio 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:38 status half-configured pulseaudio 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:39 status unpacked pulseaudio 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:39 status half-installed pulseaudio 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:39 status triggers-pending man-db 2.5.5-1build1
2009-11-11 15:01:39 status half-installed pulseaudio 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:40 status half-installed pulseaudio 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:41 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:41 upgrade pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:41 status half-configured pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status unpacked pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status half-installed pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status half-installed pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status half-installed pulseaudio-esound-compat 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:41 status unpacked pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:42 status unpacked pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:42 upgrade pulseaudio-module-gconf 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:42 status half-configured pulseaudio-module-gconf 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:42 status unpacked pulseaudio-module-gconf 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:42 status half-installed pulseaudio-module-gconf 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:42 status half-installed pulseaudio-module-gconf 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:42 status unpacked pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:42 status unpacked pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:43 upgrade pulseaudio-module-hal 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:43 status half-configured pulseaudio-module-hal 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status unpacked pulseaudio-module-hal 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status half-installed pulseaudio-module-hal 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status half-installed pulseaudio-module-hal 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status unpacked pulseaudio-module-hal 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:43 status unpacked pulseaudio-module-hal 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:43 upgrade pulseaudio-utils 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:43 status half-configured pulseaudio-utils 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status unpacked pulseaudio-utils 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:43 status half-installed pulseaudio-utils 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:44 status half-installed pulseaudio-utils 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:44 status half-installed pulseaudio-utils 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:44 status unpacked pulseaudio-utils 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:44 status unpacked pulseaudio-utils 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:44 upgrade pulseaudio-module-x11 1:0.9.14-0ubuntu20.2 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:44 status half-configured pulseaudio-module-x11 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:45 status unpacked pulseaudio-module-x11 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:45 status half-installed pulseaudio-module-x11 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:45 status half-installed pulseaudio-module-x11 1:0.9.14-0ubuntu20.2
2009-11-11 15:01:45 status unpacked pulseaudio-module-x11 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:45 status unpacked pulseaudio-module-x11 1:0.9.14-0ubuntu20.3
2009-11-11 15:01:45 upgrade totem-common 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:01:45 status half-configured totem-common 2.26.1-0ubuntu5
2009-11-11 15:01:54 status unpacked totem-common 2.26.1-0ubuntu5
2009-11-11 15:01:54 status half-installed totem-common 2.26.1-0ubuntu5
2009-11-11 15:01:55 status half-installed totem-common 2.26.1-0ubuntu5
2009-11-11 15:01:56 status half-installed totem-common 2.26.1-0ubuntu5
2009-11-11 15:02:00 status unpacked totem-common 2.26.1-0ubuntu5.1
2009-11-11 15:02:01 status unpacked totem-common 2.26.1-0ubuntu5.1
2009-11-11 15:02:01 upgrade totem-plugins-extra 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:01 status half-configured totem-plugins-extra 2.26.1-0ubuntu5
2009-11-11 15:02:01 status unpacked totem-plugins-extra 2.26.1-0ubuntu5
2009-11-11 15:02:01 status half-installed totem-plugins-extra 2.26.1-0ubuntu5
2009-11-11 15:02:02 status half-installed totem-plugins-extra 2.26.1-0ubuntu5
2009-11-11 15:02:02 status unpacked totem-plugins-extra 2.26.1-0ubuntu5.1
2009-11-11 15:02:02 status unpacked totem-plugins-extra 2.26.1-0ubuntu5.1
2009-11-11 15:02:02 upgrade totem-plugins 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:02 status half-configured totem-plugins 2.26.1-0ubuntu5
2009-11-11 15:02:03 status unpacked totem-plugins 2.26.1-0ubuntu5
2009-11-11 15:02:03 status half-installed totem-plugins 2.26.1-0ubuntu5
2009-11-11 15:02:03 status half-installed totem-plugins 2.26.1-0ubuntu5
2009-11-11 15:02:03 status unpacked totem-plugins 2.26.1-0ubuntu5.1
2009-11-11 15:02:03 status unpacked totem-plugins 2.26.1-0ubuntu5.1
2009-11-11 15:02:04 upgrade totem-xine 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:04 status half-configured totem-xine 2.26.1-0ubuntu5
2009-11-11 15:02:04 status unpacked totem-xine 2.26.1-0ubuntu5
2009-11-11 15:02:04 status half-installed totem-xine 2.26.1-0ubuntu5
2009-11-11 15:02:04 status half-installed totem-xine 2.26.1-0ubuntu5
2009-11-11 15:02:05 status unpacked totem-xine 2.26.1-0ubuntu5.1
2009-11-11 15:02:05 status unpacked totem-xine 2.26.1-0ubuntu5.1
2009-11-11 15:02:06 upgrade totem-gstreamer 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:06 status half-configured totem-gstreamer 2.26.1-0ubuntu5
2009-11-11 15:02:06 status unpacked totem-gstreamer 2.26.1-0ubuntu5
2009-11-11 15:02:06 status half-installed totem-gstreamer 2.26.1-0ubuntu5
2009-11-11 15:02:06 status half-installed totem-gstreamer 2.26.1-0ubuntu5
2009-11-11 15:02:07 status unpacked totem-gstreamer 2.26.1-0ubuntu5.1
2009-11-11 15:02:07 status unpacked totem-gstreamer 2.26.1-0ubuntu5.1
2009-11-11 15:02:07 upgrade totem 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:07 status half-configured totem 2.26.1-0ubuntu5
2009-11-11 15:02:07 status unpacked totem 2.26.1-0ubuntu5
2009-11-11 15:02:07 status half-installed totem 2.26.1-0ubuntu5
2009-11-11 15:02:07 status half-installed totem 2.26.1-0ubuntu5
2009-11-11 15:02:08 status unpacked totem 2.26.1-0ubuntu5.1
2009-11-11 15:02:08 status unpacked totem 2.26.1-0ubuntu5.1
2009-11-11 15:02:08 upgrade totem-mozilla 2.26.1-0ubuntu5 2.26.1-0ubuntu5.1
2009-11-11 15:02:08 status half-configured totem-mozilla 2.26.1-0ubuntu5
2009-11-11 15:02:08 status unpacked totem-mozilla 2.26.1-0ubuntu5
2009-11-11 15:02:08 status half-installed totem-mozilla 2.26.1-0ubuntu5
2009-11-11 15:02:08 status half-installed totem-mozilla 2.26.1-0ubuntu5
2009-11-11 15:02:09 status unpacked totem-mozilla 2.26.1-0ubuntu5.1
2009-11-11 15:02:09 status unpacked totem-mozilla 2.26.1-0ubuntu5.1
2009-11-11 15:02:09 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-11-11 15:02:09 status half-configured man-db 2.5.5-1build1
2009-11-11 15:02:11 status installed man-db 2.5.5-1build1
2009-11-11 15:02:12 startup packages configure
2009-11-11 15:02:12 configure linux-image-2.6.28-16-generic 2.6.28-16.57 2.6.28-16.57
2009-11-11 15:02:12 status unpacked linux-image-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:02:13 status half-configured linux-image-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:03:18 status installed linux-image-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:03:19 configure libpulse0 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status unpacked libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status unpacked libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status half-configured libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status installed libpulse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status triggers-pending libc6 2.9-4ubuntu6.1
2009-11-11 15:03:19 configure libpulse-browse0 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status unpacked libpulse-browse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status half-configured libpulse-browse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status installed libpulse-browse0 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 configure libpulsecore9 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status unpacked libpulsecore9 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status half-configured libpulsecore9 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 status installed libpulsecore9 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:19 configure linux-headers-2.6.28-16 2.6.28-16.57 2.6.28-16.57
2009-11-11 15:03:19 status unpacked linux-headers-2.6.28-16 2.6.28-16.57
2009-11-11 15:03:20 status half-configured linux-headers-2.6.28-16 2.6.28-16.57
2009-11-11 15:03:20 status installed linux-headers-2.6.28-16 2.6.28-16.57
2009-11-11 15:03:20 configure linux-headers-2.6.28-16-generic 2.6.28-16.57 2.6.28-16.57
2009-11-11 15:03:20 status unpacked linux-headers-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:03:20 status half-configured linux-headers-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:03:23 status installed linux-headers-2.6.28-16-generic 2.6.28-16.57
2009-11-11 15:03:23 configure linux-libc-dev 2.6.28-16.57 2.6.28-16.57
2009-11-11 15:03:23 status unpacked linux-libc-dev 2.6.28-16.57
2009-11-11 15:03:23 status half-configured linux-libc-dev 2.6.28-16.57
2009-11-11 15:03:23 status installed linux-libc-dev 2.6.28-16.57
2009-11-11 15:03:23 configure pulseaudio 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:23 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:23 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:23 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status unpacked pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status half-configured pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status installed pulseaudio 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 configure pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status unpacked pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status half-configured pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:24 status installed pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 configure pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status unpacked pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status half-configured pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status installed pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 configure pulseaudio-module-hal 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status unpacked pulseaudio-module-hal 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status half-configured pulseaudio-module-hal 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status installed pulseaudio-module-hal 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 configure pulseaudio-utils 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status unpacked pulseaudio-utils 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status half-configured pulseaudio-utils 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status installed pulseaudio-utils 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 configure pulseaudio-module-x11 1:0.9.14-0ubuntu20.3 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status unpacked pulseaudio-module-x11 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status half-configured pulseaudio-module-x11 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 status installed pulseaudio-module-x11 1:0.9.14-0ubuntu20.3
2009-11-11 15:03:25 configure totem-common 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:25 status unpacked totem-common 2.26.1-0ubuntu5.1
2009-11-11 15:03:25 status half-configured totem-common 2.26.1-0ubuntu5.1
2009-11-11 15:03:35 status installed totem-common 2.26.1-0ubuntu5.1
2009-11-11 15:03:35 configure totem-gstreamer 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:35 status unpacked totem-gstreamer 2.26.1-0ubuntu5.1
2009-11-11 15:03:35 status half-configured totem-gstreamer 2.26.1-0ubuntu5.1
2009-11-11 15:03:36 status installed totem-gstreamer 2.26.1-0ubuntu5.1
2009-11-11 15:03:36 configure totem-xine 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:36 status unpacked totem-xine 2.26.1-0ubuntu5.1
2009-11-11 15:03:37 status half-configured totem-xine 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status installed totem-xine 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 configure totem-plugins-extra 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status unpacked totem-plugins-extra 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status half-configured totem-plugins-extra 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status installed totem-plugins-extra 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 configure totem-plugins 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status unpacked totem-plugins 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status half-configured totem-plugins 2.26.1-0ubuntu5.1
2009-11-11 15:03:38 status installed totem-plugins 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 configure totem 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status unpacked totem 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status half-configured totem 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status installed totem 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 configure totem-mozilla 2.26.1-0ubuntu5.1 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status unpacked totem-mozilla 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status half-configured totem-mozilla 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 status installed totem-mozilla 2.26.1-0ubuntu5.1
2009-11-11 15:03:39 trigproc libc6 2.9-4ubuntu6.1 2.9-4ubuntu6.1
2009-11-11 15:03:39 status half-configured libc6 2.9-4ubuntu6.1
2009-11-11 15:03:40 status installed libc6 2.9-4ubuntu6.1
2009-11-13 11:23:53 startup archives unpack
2009-11-13 11:24:11 upgrade openjdk-6-jre-lib 6b14-1.4.1-0ubuntu11 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:11 status half-configured openjdk-6-jre-lib 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:11 status unpacked openjdk-6-jre-lib 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:11 status half-installed openjdk-6-jre-lib 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:15 status half-installed openjdk-6-jre-lib 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:16 status unpacked openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:17 status unpacked openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:17 upgrade icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu11 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:17 status half-configured icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:17 status unpacked icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:17 status half-installed icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:18 status half-installed icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:18 status unpacked icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:18 status unpacked icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:18 upgrade openjdk-6-jre-headless 6b14-1.4.1-0ubuntu11 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:18 status half-configured openjdk-6-jre-headless 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:19 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:19 status half-installed openjdk-6-jre-headless 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:29 status half-installed openjdk-6-jre-headless 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:36 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:36 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:37 upgrade openjdk-6-jre 6b14-1.4.1-0ubuntu11 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:37 status half-configured openjdk-6-jre 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:37 status unpacked openjdk-6-jre 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:37 status half-installed openjdk-6-jre 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:38 status half-installed openjdk-6-jre 6b14-1.4.1-0ubuntu11
2009-11-13 11:24:39 status unpacked openjdk-6-jre 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:39 status unpacked openjdk-6-jre 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:41 startup packages configure
2009-11-13 11:24:41 configure openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:41 status unpacked openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status half-configured openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status installed openjdk-6-jre-lib 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 configure openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:42 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:43 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status unpacked openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:44 status half-configured openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:54 status installed openjdk-6-jre-headless 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:56 configure icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:56 status unpacked icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:56 status half-configured icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:57 status installed icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:57 configure openjdk-6-jre 6b14-1.4.1-0ubuntu12 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:57 status unpacked openjdk-6-jre 6b14-1.4.1-0ubuntu12
2009-11-13 11:24:57 status half-configured openjdk-6-jre 6b14-1.4.1-0ubuntu12
2009-11-13 11:25:01 status installed openjdk-6-jre 6b14-1.4.1-0ubuntu12
2009-11-13 11:25:50 startup archives unpack
2009-11-13 11:27:02 upgrade tzdata-java 2009o+repack-0ubuntu0.9.04.2 2009r~repack-0ubuntu9.04
2009-11-13 11:27:02 status half-configured tzdata-java 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:02 status unpacked tzdata-java 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:02 status half-installed tzdata-java 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:03 status half-installed tzdata-java 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:04 status unpacked tzdata-java 2009r~repack-0ubuntu9.04
2009-11-13 11:27:04 status unpacked tzdata-java 2009r~repack-0ubuntu9.04
2009-11-13 11:27:04 upgrade tzdata 2009o+repack-0ubuntu0.9.04.2 2009r~repack-0ubuntu9.04
2009-11-13 11:27:04 status half-configured tzdata 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:05 status unpacked tzdata 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:05 status half-installed tzdata 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:10 status half-installed tzdata 2009o+repack-0ubuntu0.9.04.2
2009-11-13 11:27:11 status unpacked tzdata 2009r~repack-0ubuntu9.04
2009-11-13 11:27:11 status unpacked tzdata 2009r~repack-0ubuntu9.04
2009-11-13 11:27:13 startup packages configure
2009-11-13 11:27:13 configure tzdata 2009r~repack-0ubuntu9.04 2009r~repack-0ubuntu9.04
2009-11-13 11:27:13 status unpacked tzdata 2009r~repack-0ubuntu9.04
2009-11-13 11:27:14 status half-configured tzdata 2009r~repack-0ubuntu9.04
2009-11-13 11:27:21 status installed tzdata 2009r~repack-0ubuntu9.04
2009-11-13 11:27:21 configure tzdata-java 2009r~repack-0ubuntu9.04 2009r~repack-0ubuntu9.04
2009-11-13 11:27:21 status unpacked tzdata-java 2009r~repack-0ubuntu9.04
2009-11-13 11:27:21 status half-configured tzdata-java 2009r~repack-0ubuntu9.04
2009-11-13 11:27:21 status installed tzdata-java 2009r~repack-0ubuntu9.04
2009-11-19 14:50:28 startup archives unpack
2009-11-19 14:58:48 startup archives unpack
2009-11-19 14:58:49 startup packages configure
2009-11-19 14:59:27 startup archives unpack
2009-11-19 14:59:28 startup packages configure
2009-11-19 15:44:31 startup archives unpack
2009-11-19 15:44:32 startup packages configure
2009-11-19 15:46:40 startup archives unpack
2009-11-19 15:46:41 startup packages configure
2009-11-20 11:55:40 startup archives unpack
2009-11-20 11:55:44 startup packages configure
2009-11-20 12:04:10 startup archives unpack
2009-11-21 12:50:34 startup archives unpack
2009-11-21 12:50:44 startup packages configure
2009-11-21 12:51:58 startup archives unpack
2009-11-21 12:51:59 startup packages configure
2009-11-21 12:54:52 startup archives unpack
2009-11-21 12:54:54 startup packages configure
2009-11-21 12:56:43 startup archives unpack
2009-11-21 12:56:44 startup packages configure
2009-11-21 13:11:48 startup archives unpack
2009-11-22 13:54:36 startup archives unpack
2009-11-22 13:54:40 startup packages configure
2009-11-22 14:19:00 startup archives unpack
2009-11-23 14:57:23 startup archives unpack
2009-11-23 16:11:54 startup archives unpack
2009-11-23 16:11:57 startup packages configure
2009-11-23 16:12:43 startup archives unpack
2009-11-23 16:12:44 startup packages configure
2009-11-23 16:14:02 startup archives unpack
2009-11-23 16:14:04 startup packages configure
2009-11-23 16:18:10 startup archives unpack
2009-11-23 16:18:11 startup packages configure
2009-11-23 16:27:07 startup archives install
2009-11-23 16:28:06 startup archives install
2009-11-23 16:32:08 startup packages configure
2009-11-23 16:32:40 startup archives unpack
2009-11-23 18:57:48 startup archives unpack
2009-11-23 18:57:52 startup packages configure
2009-11-24 14:19:29 startup archives unpack
2009-11-24 14:19:33 startup packages configure
2009-11-24 14:47:09 startup archives unpack
2009-11-25 17:18:47 startup archives unpack
2009-11-25 17:39:54 startup archives unpack
2009-11-25 17:39:55 startup packages configure
2009-11-26 02:24:09 startup archives unpack
2009-11-26 12:08:28 startup archives unpack
2009-11-26 12:08:32 startup packages configure
2009-11-27 11:34:56 startup archives unpack
2009-11-28 12:05:35 startup archives unpack
2009-11-28 12:05:40 startup packages configure
2009-11-28 12:11:57 startup archives unpack
2009-11-28 12:11:58 startup packages configure
2009-11-28 12:40:52 startup archives unpack
2009-11-29 14:14:34 startup archives unpack
2009-11-29 14:14:39 startup packages configure
2009-11-29 14:57:22 startup archives unpack
2009-11-30 14:48:58 startup archives unpack
2009-12-01 15:12:03 startup archives unpack
```


OK... when I try to install any updates I get this error:

debconf  DbDriver  config  /var/cache/config.dat  is locked by a process: resource temporarily unavailable.

the says reading database: dpkg ......... fatal error 

files list file for package lsb-release  is missing final newline
usr/bin/dpkg returned error code 2. 
failed to install trying to recover. 


this is what I can see from the update manager or the package manager.

I can't install anything without fixing this issure.

what should I do?

---

### Post by wilee-nilee on 2009-12-06
If it was me I would back up and do a fresh install. That is a lot of muck to wade through and only assume it is fixed.

---

