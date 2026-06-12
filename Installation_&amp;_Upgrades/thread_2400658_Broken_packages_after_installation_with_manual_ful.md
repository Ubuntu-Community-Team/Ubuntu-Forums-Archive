---
title: "Broken packages after installation with manual full system encryption"
date: 2018-09-08
forum: Installation &amp; Upgrades
---

### Post by jharai on 2018-09-08
I'm using Dell XPS 13 (9370) by replacing pre-installed Windows with Ubuntu.

Since I need both volume encryption and hibernation, I installed Ubuntu 18.04 by reading [ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"). The install seemed to have been finished successfully, but I found a problem after that. Some packages are broken. I found this when I tried to install easystroke:

```
$ sudo apt install easystroke 
[sudo] password for harai: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libboost-serialization1.65.1 libgtkmm-3.0-1v5
Suggested packages:
  cellwriter
The following NEW packages will be installed:
  easystroke libboost-serialization1.65.1 libgtkmm-3.0-1v5
0 upgraded, 3 newly installed, 0 to remove and 104 not upgraded.
Need to get 1,248 kB of archives.
After this operation, 7,877 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) bionic/main amd64 libboost-serialization1.65.1 amd64 1.65.1+dfsg-0ubuntu5 [99.3 kB]
Get:2 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) bionic/main amd64 libgtkmm-3.0-1v5 amd64 3.22.2-2 [850 kB]
Get:3 [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) bionic/universe amd64 easystroke amd64 0.6.0-0ubuntu11 [298 kB]
Fetched 1,248 kB in 1s (859 kB/s)   
Selecting previously unselected package libboost-serialization1.65.1:amd64.
(Reading database ... 179995 files and directories currently installed.)
Preparing to unpack .../libboost-serialization1.65.1_1.65.1+dfsg-0ubuntu5_amd64.deb ...
Unpacking libboost-serialization1.65.1:amd64 (1.65.1+dfsg-0ubuntu5) ...
Selecting previously unselected package libgtkmm-3.0-1v5:amd64.
Preparing to unpack .../libgtkmm-3.0-1v5_3.22.2-2_amd64.deb ...
Unpacking libgtkmm-3.0-1v5:amd64 (3.22.2-2) ...
Selecting previously unselected package easystroke.
Preparing to unpack .../easystroke_0.6.0-0ubuntu11_amd64.deb ...
Unpacking easystroke (0.6.0-0ubuntu11) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.1) .........] 
Setting up libgtkmm-3.0-1v5:amd64 (3.22.2-2) ...
Setting up libboost-serialization1.65.1:amd64 (1.65.1+dfsg-0ubuntu5) ...
Setting up easystroke (0.6.0-0ubuntu11) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...

$ easystroke 
easystroke: error while loading shared libraries: libatkmm-1.6.so.1: cannot open shared object file: No such file or directory
```

After reinstalling its dependencies, easystroke started to run normally.

What's happening? I also tried (automated) normal full system encryption, and in that case, easystroke ran without any problems.

One possibility might be a minor difference between instructions in [ManualFullSystemEncryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption") and the behavior on my XPS 13 (9370). During installation, a dialog box titled "Installer crashed" popped up as the document said. The difference was that I couldn't close it because both "Close" button and "x" sign were unresponsive. Is this related to the broken packages?

[ATTACH=CONFIG]281015[/ATTACH]

---

