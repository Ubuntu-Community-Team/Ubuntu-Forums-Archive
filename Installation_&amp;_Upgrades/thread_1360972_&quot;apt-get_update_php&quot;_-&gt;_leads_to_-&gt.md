---
title: "&quot;apt-get update php&quot; -&gt; leads to -&gt; &quot;/lib/libc.so.6: file too short&quot;"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by yixing on 2009-12-21
Hi everybody,

I tried to upgrade PHP on a 9.10 server with the "apt-get upgrade php" command. However, I got into big problems. Here is a part of the log outputed by apt-get where the issues started:

============
Fetched 82.8MB in 25s (3267kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 28351 files and directories currently installed.)
Preparing to replace dash 0.5.4-8ubuntu1 (using
.../dash_0.5.4-8ubuntu1.1_i386.deb) ...
Unpacking replacement dash ...
Setting up dash (0.5.4-8ubuntu1.1) ...
(Reading database ... 28351 files and directories currently installed.)
Preparing to replace login 1:4.0.18.2-1ubuntu2.1 (using
.../login_1%3a4.0.18.2-1ubuntu2.2_i386.deb) ...
Unpacking replacement login ...
Setting up login (1:4.0.18.2-1ubuntu2.2) ...
(Reading database ... 28351 files and directories currently installed.)
Preparing to replace mount 2.13.1-5ubuntu2 (using
.../mount_2.13.1-5ubuntu3_i386.deb) ...
Unpacking replacement mount ...
Setting up mount (2.13.1-5ubuntu3) ...
(Reading database ... 28351 files and directories currently installed.)
Preparing to replace perl-modules 5.8.8-12 (using
.../perl-modules_5.8.8-12ubuntu0.4_all.deb) ...
Unpacking replacement perl-modules ...
Preparing to replace libc6-dev 2.7-10ubuntu4 (using
.../libc6-dev_2.7-10ubuntu5_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.7-10ubuntu4 (using
.../libc6_2.7-10ubuntu5_i386.deb) ...
head: error while loading shared libraries: /lib/libc.so.6: file too short
od: error while loading shared libraries: /lib/libc.so.6: file too short
dpkg: error processing /var/cache/apt/archives/libc6_2.7-10ubuntu5_i386.deb
(--unpack):
 subprocess pre-installation script returned error exit status 127
/bin/sh: error while loading shared libraries: /lib/libc.so.6: file too short
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
rm: error while loading shared libraries: /lib/libc.so.6: file too short
dpkg: error while cleaning up:
 subprocess rm cleanup returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.7-10ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@domU-12-31-39-03-44-13:/usr/local/virtuoso-opensource/var/lib/virtuoso/vsp/ws/scripts#
apt-get upgrade php
apt-get: error while loading shared libraries: /lib/libc.so.6: file too short
root@domU-12-31-39-03-44-13:/usr/local/virtuoso-opensource/var/lib/virtuoso/vsp/ws/scripts#
apt-get upgrade php
apt-get: error while loading shared libraries: /lib/libc.so.6: file too short
============


Now, nearly no commands work on my connected shells, and I can't initiate any new SCP connections to this server. I am a running SCP connection where I can download/upload files, but that is it. The shell terminal is nearly useless since nearly all programs uses this library.

I am wondering about a couple of things:


[LIST=1]
[*]How can I fix that issues !?!?!
[*]What caused it?
[/LIST]
I did search on the web, and these forums, without any luck. I also asked on some IRC channels without much luck neither.

Does anyone already experienced this?


Thanks!


Take care,


Fred

---

