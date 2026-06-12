---
title: "linux-image-3.13.0-43-generic does not install"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by la.khan on 2014-12-28
Hi all,

I have installed UL14.04LTS on my Dell Inspiron 1525 since Jun 2014 and I have had no issues. I update my OS as and when UL says there are updates available, typically once a month.

Last week, when I tried to update the OS, the update starts fine but then the update process hangs. I have to turn off my machine and turn it back on to continue using it.

Here are my UL installation details:

uname -a
```
Linux MilkyWay 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux
```

df -h
```
df: ‘/run/user/1002/gvfs’: Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       144G  8.0G  129G   6% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           303M  1.3M  301M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  240K  1.5G   1% /run/shm
none            100M   84K  100M   1% /run/user
```

When I searched Google to see if any other UL user has faced a similar issue, I see a bug logged in Ubuntu.
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1405703](https://bugs.launchpad.net/ubuntu/+source/linux-lts-trusty/+bug/1405703)

If you need more information on my hardware and/or software configuration or logs for this installation, please let me know. Thanks for your help!

---

### Post by schragge on 2014-12-28
Error the bug reporter from LP#[lpbug]1405703[/lpbug] got trying to install this kernel on an old IBM Thinkpad T42p running Ubuntu 12.04 LTS was
> This kernel does not support a non-PAE CPU. Your hardware is different, and you said you were successfully running Ubuntu 14.04 LTS on it. AFAIK 14.04 required [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")-enabled processor to run from the very beginning. So I'm pretty sure what you've got is a different issue.

---

### Post by la.khan on 2014-12-28
> **schragge said:**
> You hardware is different, and you said you were successfully running Ubuntu 14.04 LTS on it. AFAIK 14.04 required [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension")-enabled processor to run from the very beginning. So I'm pretty sure what you've got is a different issue.

schragge, thanks for the reply. I thought the issue was generic; I did not go through the issue in detail :( So, is there anthing from my end that you need to figure out what's going on (like log files)?

Also, every time I try to install any other software, my laptop tries to install linux-image-3.13.0-43-generic and then hangs :mad:. Is there a way to roll this back?

---

### Post by Bashing-om on 2014-12-28
la.khan; Hello;

Allow me to push this along a bit.
Show us what the error condition might be by posting the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2014-12-28
Are you trying to run the update as user 1002, and does that user have sudo permissions?

---

### Post by schragge on 2014-12-28
@**ubfan1**: Most probably not as user 1002, otherwise there would be no error message in the output of *df -h* command  that filesystem owned by 1002 cannot be read. But good point nevertheless.

@OP: Yes, please, do what **Bashing-om** asked from you. Also, could you please provide a bit more information.

What exactly *hangs*? Update Manager? At what point? I suppose you get beyond this:

[IMG]http://screenshots.ubuntu.com/screenshots/u/update-manager/9413_large.png[/IMG]

You say
> Also, every time I try to install any other software, my laptop tries to install linux-image-3.13.0-43-generic and then hangs
How did you try to install other software? In Software Center? In Synaptic? With apt-get? Only the package manager hangs and you are able to kill it or the whole desktop freezes? If only > the update process hangs then why > I have to turn off my machine and turn it back on to continue using it. Have you tried to change to a virtual console with Alt+Ctrl+F2 after the desktop got unresponsive on update?

---

### Post by grahammechanical on 2014-12-28
You have

> Linux MilkyWay 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 i686 i686 i686 GNU/Linux
The update tried to install

> [COLOR=#000000]linux-image-3.13.0-43-generic[/COLOR]

and failed and you turned off the machine and that is why every attempt to update software or install software the software updater tries to install linux-image-3.13.0-43. It is trying to complete the earlier update. You could try

```
apt-get -f install
```

which will attempt to fix broken packages.

Regards.

---

### Post by la.khan on 2014-12-28
> **Bashing-om said:**
> la.khan; Hello;

Allow me to push this along a bit.
Show us what the error condition might be by posting the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

Bashing-om,

Thanks for the reply! Below is the output of commands you suggested.
sudo apt-get update
```
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release
Ign http://extras.ubuntu.com trusty InRelease
Hit http://dl.google.com stable/main i386 Packages
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://ubuntu.01link.hk trusty InRelease
Hit http://extras.ubuntu.com trusty Release
Hit http://extras.ubuntu.com trusty/main i386 Packages
Ign http://ubuntu.01link.hk trusty-updates InRelease
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://ubuntu.01link.hk trusty-backports InRelease
Ign http://ubuntu.01link.hk trusty-security InRelease
Hit http://ubuntu.01link.hk trusty Release.gpg
Hit http://ubuntu.01link.hk trusty-updates Release.gpg
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://ubuntu.01link.hk trusty-backports Release.gpg
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://ubuntu.01link.hk trusty-security Release.gpg
Ign http://archive.canonical.com trusty InRelease
Hit http://archive.canonical.com trusty Release.gpg
Hit http://ubuntu.01link.hk trusty Release
Hit http://archive.canonical.com trusty Release
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://ubuntu.01link.hk trusty-updates Release
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://ubuntu.01link.hk trusty-backports Release
Hit http://ubuntu.01link.hk trusty-security Release
Hit http://ubuntu.01link.hk trusty/main Sources
Hit http://ubuntu.01link.hk trusty/restricted Sources
Hit http://ubuntu.01link.hk trusty/universe Sources
Hit http://ubuntu.01link.hk trusty/multiverse Sources
Hit http://ubuntu.01link.hk trusty/main i386 Packages
Hit http://ubuntu.01link.hk trusty/restricted i386 Packages
Hit http://ubuntu.01link.hk trusty/universe i386 Packages
Hit http://ubuntu.01link.hk trusty/multiverse i386 Packages
Hit http://ubuntu.01link.hk trusty/main Translation-en
Hit http://ubuntu.01link.hk trusty/multiverse Translation-en
Hit http://ubuntu.01link.hk trusty/restricted Translation-en
Hit http://ubuntu.01link.hk trusty/universe Translation-en
Hit http://ubuntu.01link.hk trusty-updates/main Sources
Hit http://ubuntu.01link.hk trusty-updates/restricted Sources
Hit http://ubuntu.01link.hk trusty-updates/universe Sources
Hit http://ubuntu.01link.hk trusty-updates/multiverse Sources
Hit http://ubuntu.01link.hk trusty-updates/main i386 Packages
Hit http://ubuntu.01link.hk trusty-updates/restricted i386 Packages
Hit http://ubuntu.01link.hk trusty-updates/universe i386 Packages
Hit http://ubuntu.01link.hk trusty-updates/multiverse i386 Packages
Hit http://ubuntu.01link.hk trusty-updates/main Translation-en
Hit http://ubuntu.01link.hk trusty-updates/multiverse Translation-en
Hit http://ubuntu.01link.hk trusty-updates/restricted Translation-en
Hit http://ubuntu.01link.hk trusty-updates/universe Translation-en
Hit http://ubuntu.01link.hk trusty-backports/main Sources
Hit http://ubuntu.01link.hk trusty-backports/restricted Sources
Hit http://ubuntu.01link.hk trusty-backports/universe Sources
Hit http://ubuntu.01link.hk trusty-backports/multiverse Sources
Hit http://ubuntu.01link.hk trusty-backports/main i386 Packages
Hit http://ubuntu.01link.hk trusty-backports/restricted i386 Packages
Hit http://ubuntu.01link.hk trusty-backports/universe i386 Packages
Hit http://ubuntu.01link.hk trusty-backports/multiverse i386 Packages
Hit http://ubuntu.01link.hk trusty-backports/main Translation-en
Hit http://ubuntu.01link.hk trusty-backports/multiverse Translation-en
Hit http://ubuntu.01link.hk trusty-backports/restricted Translation-en
Hit http://ubuntu.01link.hk trusty-backports/universe Translation-en
Hit http://ubuntu.01link.hk trusty-security/main Sources
Hit http://ubuntu.01link.hk trusty-security/restricted Sources
Hit http://ubuntu.01link.hk trusty-security/universe Sources
Hit http://ubuntu.01link.hk trusty-security/multiverse Sources
Hit http://ubuntu.01link.hk trusty-security/main i386 Packages
Hit http://ubuntu.01link.hk trusty-security/restricted i386 Packages
Hit http://ubuntu.01link.hk trusty-security/universe i386 Packages
Hit http://ubuntu.01link.hk trusty-security/multiverse i386 Packages
Hit http://ubuntu.01link.hk trusty-security/main Translation-en
Hit http://ubuntu.01link.hk trusty-security/multiverse Translation-en
Hit http://ubuntu.01link.hk trusty-security/restricted Translation-en
Hit http://ubuntu.01link.hk trusty-security/universe Translation-en
Ign http://ubuntu.01link.hk trusty/main Translation-en_US
Ign http://ubuntu.01link.hk trusty/multiverse Translation-en_US
Ign http://ubuntu.01link.hk trusty/restricted Translation-en_US
Ign http://ubuntu.01link.hk trusty/universe Translation-en_US
```

sudo apt-get upgrade
```
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk compiz compiz-core compiz-gnome compiz-plugins-default
  fonts-opensymbol gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-webkit-3.0 google-chrome-stable libappindicator1 libcompizconfig0
  libdecoration0 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
  libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 liblightdm-gobject-1-0
  libnux-4.0-0 libnux-4.0-common libplymouth2
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-style-human libreoffice-writer libsepol1 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common lightdm
  nux-tools plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text python3-apport python3-distupgrade
  python3-problem-report python3-uno ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk uno-libs3 ure
62 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 142 MB of archives.
After this operation, 3,044 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 39.0.2171.95-1 [47.4 MB]
Get:2 http://ubuntu.01link.hk/ trusty-updates/main libsepol1 i386 2.2-1ubuntu0.1 [99.6 kB]
Get:3 http://ubuntu.01link.hk/ trusty-updates/main libdrm2 i386 2.4.56-1~ubuntu1 [23.1 kB]
Get:4 http://ubuntu.01link.hk/ trusty-updates/main plymouth-label i386 0.8.8-0ubuntu17.1 [5,180 B]
Get:5 http://ubuntu.01link.hk/ trusty-updates/main plymouth i386 0.8.8-0ubuntu17.1 [98.8 kB]
Get:6 http://ubuntu.01link.hk/ trusty-updates/main libplymouth2 i386 0.8.8-0ubuntu17.1 [76.3 kB]
Get:7 http://ubuntu.01link.hk/ trusty-updates/main libappindicator1 i386 12.10.1+13.10.20130920-0ubuntu4.1 [17.7 kB]
Get:8 http://ubuntu.01link.hk/ trusty-updates/main libdrm-intel1 i386 2.4.56-1~ubuntu1 [54.1 kB]
Get:9 http://ubuntu.01link.hk/ trusty-updates/main libdrm-nouveau2 i386 2.4.56-1~ubuntu1 [14.3 kB]
Get:10 http://ubuntu.01link.hk/ trusty-updates/main libdrm-radeon1 i386 2.4.56-1~ubuntu1 [24.1 kB]
Get:11 http://ubuntu.01link.hk/ trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.3 [167 kB]
Get:12 http://ubuntu.01link.hk/ trusty-updates/main libgail-3-0 i386 3.10.8-0ubuntu1.3 [20.0 kB]
Get:13 http://ubuntu.01link.hk/ trusty-updates/main libgtk-3-0 i386 3.10.8-0ubuntu1.3 [1,926 kB]
Get:14 http://ubuntu.01link.hk/ trusty-updates/main libwebkitgtk-1.0-common all 2.4.7-1~ubuntu1 [107 kB]
Get:15 http://ubuntu.01link.hk/ trusty-updates/main libwebkitgtk-1.0-0 i386 2.4.7-1~ubuntu1 [7,150 kB]
Get:16 http://ubuntu.01link.hk/ trusty-updates/main libjavascriptcoregtk-1.0-0 i386 2.4.7-1~ubuntu1 [1,818 kB]
Get:17 http://ubuntu.01link.hk/ trusty-updates/main libwebkitgtk-3.0-common all 2.4.7-1~ubuntu1 [107 kB]
Get:18 http://ubuntu.01link.hk/ trusty-updates/main libwebkitgtk-3.0-0 i386 2.4.7-1~ubuntu1 [7,155 kB]
Get:19 http://ubuntu.01link.hk/ trusty-updates/main libjavascriptcoregtk-3.0-0 i386 2.4.7-1~ubuntu1 [1,816 kB]
Get:20 http://ubuntu.01link.hk/ trusty-updates/main libnux-4.0-0 i386 4.0.6+14.04.20141107-0ubuntu1 [698 kB]
Get:21 http://ubuntu.01link.hk/ trusty-updates/main libnux-4.0-common i386 4.0.6+14.04.20141107-0ubuntu1 [45.9 kB]
Get:22 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-calc i386 1:4.2.7-0ubuntu2 [5,844 kB]
Get:23 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-gnome i386 1:4.2.7-0ubuntu2 [87.3 kB]
Get:24 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-gtk i386 1:4.2.7-0ubuntu2 [217 kB]
Get:25 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-writer i386 1:4.2.7-0ubuntu2 [9,397 kB]
Get:26 http://ubuntu.01link.hk/ trusty-updates/main uno-libs3 i386 4.2.7-0ubuntu2 [605 kB]
Get:27 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-ogltrans i386 1:4.2.7-0ubuntu2 [74.4 kB]
Get:28 http://ubuntu.01link.hk/ trusty-updates/main ure i386 4.2.7-0ubuntu2 [1,617 kB]
Get:29 http://ubuntu.01link.hk/ trusty-updates/main python3-uno i386 1:4.2.7-0ubuntu2 [119 kB]
Get:30 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-common all 1:4.2.7-0ubuntu2 [19.9 MB]
Get:31 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-pdfimport i386 1:4.2.7-0ubuntu2 [218 kB]
Get:32 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-math i386 1:4.2.7-0ubuntu2 [355 kB]
Get:33 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-base-core i386 1:4.2.7-0ubuntu2 [700 kB]
Get:34 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-draw i386 1:4.2.7-0ubuntu2 [2,374 kB]
Get:35 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-impress i386 1:4.2.7-0ubuntu2 [1,183 kB]
Get:36 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-core i386 1:4.2.7-0ubuntu2 [26.7 MB]
Get:37 http://ubuntu.01link.hk/ trusty-updates/main fonts-opensymbol all 2:102.6+LibO4.2.7-0ubuntu2 [111 kB]
Get:38 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-style-human all 1:4.2.7-0ubuntu2 [1,740 kB]
Get:39 http://ubuntu.01link.hk/ trusty-updates/main lightdm i386 1.10.3-0ubuntu2 [104 kB]
Get:40 http://ubuntu.01link.hk/ trusty-updates/main plymouth-theme-ubuntu-text i386 0.8.8-0ubuntu17.1 [7,900 B]
Get:41 http://ubuntu.01link.hk/ trusty-updates/main gir1.2-gtk-3.0 i386 3.10.8-0ubuntu1.3 [174 kB]
Get:42 http://ubuntu.01link.hk/ trusty-updates/main gir1.2-webkit-3.0 i386 2.4.7-1~ubuntu1 [60.3 kB]
Get:43 http://ubuntu.01link.hk/ trusty-updates/main gir1.2-javascriptcoregtk-3.0 i386 2.4.7-1~ubuntu1 [11.9 kB]
Get:44 http://ubuntu.01link.hk/ trusty-updates/main ubuntu-release-upgrader-gtk all 1:0.220.6 [9,238 B]
Get:45 http://ubuntu.01link.hk/ trusty-updates/main ubuntu-release-upgrader-core all 1:0.220.6 [23.1 kB]
Get:46 http://ubuntu.01link.hk/ trusty-updates/main python3-distupgrade all 1:0.220.6 [104 kB]
Get:47 http://ubuntu.01link.hk/ trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.6 [9,032 B]
Get:48 http://ubuntu.01link.hk/ trusty-updates/main python3-apport all 2.14.1-0ubuntu3.6 [75.0 kB]
Get:49 http://ubuntu.01link.hk/ trusty-updates/main apport all 2.14.1-0ubuntu3.6 [178 kB]
Get:50 http://ubuntu.01link.hk/ trusty-updates/main apport-gtk all 2.14.1-0ubuntu3.6 [9,558 B]
Get:51 http://ubuntu.01link.hk/ trusty-updates/main libcompizconfig0 i386 1:0.9.11.3+14.04.20141104-0ubuntu1 [115 kB]
Get:52 http://ubuntu.01link.hk/ trusty-updates/main compiz-gnome i386 1:0.9.11.3+14.04.20141104-0ubuntu1 [156 kB]
Get:53 http://ubuntu.01link.hk/ trusty-updates/main compiz-plugins-default i386 1:0.9.11.3+14.04.20141104-0ubuntu1 [746 kB]
Get:54 http://ubuntu.01link.hk/ trusty-updates/main libdecoration0 i386 1:0.9.11.3+14.04.20141104-0ubuntu1 [49.0 kB]
Get:55 http://ubuntu.01link.hk/ trusty-updates/main compiz-core i386 1:0.9.11.3+14.04.20141104-0ubuntu1 [297 kB]
Get:56 http://ubuntu.01link.hk/ trusty-updates/main compiz all 1:0.9.11.3+14.04.20141104-0ubuntu1 [4,048 B]
Get:57 http://ubuntu.01link.hk/ trusty-updates/main libgtk-3-bin i386 3.10.8-0ubuntu1.3 [18.1 kB]
Get:58 http://ubuntu.01link.hk/ trusty-updates/main liblightdm-gobject-1-0 i386 1.10.3-0ubuntu2 [33.1 kB]
Get:59 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-avmedia-backend-gstreamer i386 1:4.2.7-0ubuntu2 [36.3 kB]
Get:60 http://ubuntu.01link.hk/ trusty-updates/main libreoffice-presentation-minimizer all 1:4.2.7-0ubuntu2 [26.5 kB]
Get:61 http://ubuntu.01link.hk/ trusty-updates/main nux-tools i386 4.0.6+14.04.20141107-0ubuntu1 [10.2 kB]
Get:62 http://ubuntu.01link.hk/ trusty-updates/main plymouth-theme-ubuntu-logo i386 0.8.8-0ubuntu17.1 [21.2 kB]
Fetched 142 MB in 6min 14s (381 kB/s)
Preconfiguring packages ...
(Reading database ... 232687 files and directories currently installed.)
Preparing to unpack .../libsepol1_2.2-1ubuntu0.1_i386.deb ...
Unpacking libsepol1:i386 (2.2-1ubuntu0.1) over (2.2-1) ...
Setting up libsepol1:i386 (2.2-1ubuntu0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
(Reading database ... 232687 files and directories currently installed.)
Preparing to unpack .../libdrm2_2.4.56-1~ubuntu1_i386.deb ...
Unpacking libdrm2:i386 (2.4.56-1~ubuntu1) over (2.4.52-1) ...
Preparing to unpack .../plymouth-label_0.8.8-0ubuntu17.1_i386.deb ...
Unpacking plymouth-label (0.8.8-0ubuntu17.1) over (0.8.8-0ubuntu17) ...
Preparing to unpack .../plymouth_0.8.8-0ubuntu17.1_i386.deb ...
Unpacking plymouth (0.8.8-0ubuntu17.1) over (0.8.8-0ubuntu17) ...
Preparing to unpack .../libplymouth2_0.8.8-0ubuntu17.1_i386.deb ...
Unpacking libplymouth2:i386 (0.8.8-0ubuntu17.1) over (0.8.8-0ubuntu17) ...
Preparing to unpack .../libappindicator1_12.10.1+13.10.20130920-0ubuntu4.1_i386.deb ...
Unpacking libappindicator1 (12.10.1+13.10.20130920-0ubuntu4.1) over (12.10.1+13.10.20130920-0ubuntu4) ...
Preparing to unpack .../google-chrome-stable_39.0.2171.95-1_i386.deb ...
Unpacking google-chrome-stable (39.0.2171.95-1) over (39.0.2171.65-1) ...
Preparing to unpack .../libdrm-intel1_2.4.56-1~ubuntu1_i386.deb ...
Unpacking libdrm-intel1:i386 (2.4.56-1~ubuntu1) over (2.4.52-1) ...
Preparing to unpack .../libdrm-nouveau2_2.4.56-1~ubuntu1_i386.deb ...
Unpacking libdrm-nouveau2:i386 (2.4.56-1~ubuntu1) over (2.4.52-1) ...
Preparing to unpack .../libdrm-radeon1_2.4.56-1~ubuntu1_i386.deb ...
Unpacking libdrm-radeon1:i386 (2.4.56-1~ubuntu1) over (2.4.52-1) ...
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.3_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.3) over (3.10.8-0ubuntu1.2) ...
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.3_i386.deb ...
Unpacking libgail-3-0:i386 (3.10.8-0ubuntu1.3) over (3.10.8-0ubuntu1.2) ...
Preparing to unpack .../libgtk-3-0_3.10.8-0ubuntu1.3_i386.deb ...
Unpacking libgtk-3-0:i386 (3.10.8-0ubuntu1.3) over (3.10.8-0ubuntu1.2) ...
Preparing to unpack .../libwebkitgtk-1.0-common_2.4.7-1~ubuntu1_all.deb ...
Unpacking libwebkitgtk-1.0-common (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libwebkitgtk-1.0-0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking libwebkitgtk-1.0-0:i386 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libjavascriptcoregtk-1.0-0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking libjavascriptcoregtk-1.0-0:i386 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libwebkitgtk-3.0-common_2.4.7-1~ubuntu1_all.deb ...
Unpacking libwebkitgtk-3.0-common (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libwebkitgtk-3.0-0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking libwebkitgtk-3.0-0:i386 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libjavascriptcoregtk-3.0-0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking libjavascriptcoregtk-3.0-0:i386 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../libnux-4.0-0_4.0.6+14.04.20141107-0ubuntu1_i386.deb ...
Unpacking libnux-4.0-0 (4.0.6+14.04.20141107-0ubuntu1) over (4.0.6+14.04.20140930-0ubuntu1) ...
Preparing to unpack .../libnux-4.0-common_4.0.6+14.04.20141107-0ubuntu1_i386.deb ...
Unpacking libnux-4.0-common (4.0.6+14.04.20141107-0ubuntu1) over (4.0.6+14.04.20140930-0ubuntu1) ...
Preparing to unpack .../libreoffice-calc_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-calc (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-gnome_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-gnome (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-gtk_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-gtk (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-writer_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-writer (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../uno-libs3_4.2.7-0ubuntu2_i386.deb ...
Unpacking uno-libs3 (4.2.7-0ubuntu2) over (4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-ogltrans_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-ogltrans (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../ure_4.2.7-0ubuntu2_i386.deb ...
Unpacking ure (4.2.7-0ubuntu2) over (4.2.7-0ubuntu1) ...
Preparing to unpack .../python3-uno_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking python3-uno (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-common (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-pdfimport_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-pdfimport (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-math_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-math (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-base-core_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-base-core (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-draw_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-draw (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-impress_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-impress (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-core_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-core (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../fonts-opensymbol_2%3a102.6+LibO4.2.7-0ubuntu2_all.deb ...
Unpacking fonts-opensymbol (2:102.6+LibO4.2.7-0ubuntu2) over (2:102.6+LibO4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-style-human_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-style-human (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../lightdm_1.10.3-0ubuntu2_i386.deb ...
Unpacking lightdm (1.10.3-0ubuntu2) over (1.10.1-0ubuntu1) ...
Preparing to unpack .../plymouth-theme-ubuntu-text_0.8.8-0ubuntu17.1_i386.deb ...
Unpacking plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1) over (0.8.8-0ubuntu17) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.3_i386.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.3) over (3.10.8-0ubuntu1.2) ...
Preparing to unpack .../gir1.2-webkit-3.0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking gir1.2-webkit-3.0 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-3.0_2.4.7-1~ubuntu1_i386.deb ...
Unpacking gir1.2-javascriptcoregtk-3.0 (2.4.7-1~ubuntu1) over (2.4.4-1~ubuntu1) ...
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a0.220.6_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a0.220.6_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../python3-distupgrade_1%3a0.220.6_all.deb ...
Unpacking python3-distupgrade (1:0.220.6) over (1:0.220.5) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.6_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.6) over (2.14.1-0ubuntu3.5) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.6_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.6) over (2.14.1-0ubuntu3.5) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.6_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.6) over (2.14.1-0ubuntu3.5) ...
Preparing to unpack .../apport-gtk_2.14.1-0ubuntu3.6_all.deb ...
Unpacking apport-gtk (2.14.1-0ubuntu3.6) over (2.14.1-0ubuntu3.5) ...
Preparing to unpack .../libcompizconfig0_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking libcompizconfig0 (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-gnome_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-gnome (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-plugins-default_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-plugins-default (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../libdecoration0_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking libdecoration0 (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz-core_1%3a0.9.11.3+14.04.20141104-0ubuntu1_i386.deb ...
Unpacking compiz-core (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../compiz_1%3a0.9.11.3+14.04.20141104-0ubuntu1_all.deb ...
Unpacking compiz (1:0.9.11.3+14.04.20141104-0ubuntu1) over (1:0.9.11.2+14.04.20140714-0ubuntu1) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.3_i386.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.3) over (3.10.8-0ubuntu1.2) ...
Preparing to unpack .../liblightdm-gobject-1-0_1.10.3-0ubuntu2_i386.deb ...
Unpacking liblightdm-gobject-1-0 (1.10.3-0ubuntu2) over (1.10.1-0ubuntu1) ...
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a4.2.7-0ubuntu2_i386.deb ...
Unpacking libreoffice-avmedia-backend-gstreamer (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../libreoffice-presentation-minimizer_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-presentation-minimizer (1:4.2.7-0ubuntu2) over (1:4.2.7-0ubuntu1) ...
Preparing to unpack .../nux-tools_4.0.6+14.04.20141107-0ubuntu1_i386.deb ...
Unpacking nux-tools (4.0.6+14.04.20141107-0ubuntu1) over (4.0.6+14.04.20140930-0ubuntu1) ...
Preparing to unpack .../plymouth-theme-ubuntu-logo_0.8.8-0ubuntu17.1_i386.deb ...
Unpacking plymouth-theme-ubuntu-logo (0.8.8-0ubuntu17.1) over (0.8.8-0ubuntu17) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-43-generic
) points to /boot/initrd.img-3.13.0-43-generic
 (/boot/initrd.img-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-43-generic
) points to /boot/vmlinuz-3.13.0-43-generic
 (/boot/vmlinuz-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
[COLOR=#ff0000]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...[/COLOR]

```

It is more than 30+ mins and my system is generating grub file. If I decide to abort now (Cntrl + C), will it affect my system? I see a lot of applications get updated (Google Chrome, Libre Office etc); are these applications dependent on linux-image-3.13.0-43-generic? I hope not; please confirm.

As of now, there are no errors; however, each of the lines highligted in RED ran/running for more than 30+ mins. Should I abort (Cntrl + C)? Please advise.

---

### Post by Bashing-om on 2014-12-28
la.khan; Hey !

Interrupting an update is never a good thing to do .. 
as of this time (02:10:54 UTC) has the upgrade completed ?

Is it hanging on upgrading the kernel ?

[INDENT][INDENT]could be a situation here 
[/INDENT][/INDENT]

---

### Post by la.khan on 2014-12-29
Latest update Mon., 29th Dec @ 6 AM UTC:

The machine wasn't hung but it was running very s*l*o*w*l*y but I let it run at its pace since I am in no hurry (just to illustrate how slow the machine was, as an example, when I wanted to save a log file, the machine would take 3-4 mins to show save as dialog box after I clicked save as).

My wife wanted to use the laptop but she couldn't login as it was not showing her username, but only admin username. After an hour, when I wanted to see the progress of the upgrade, I see only a blank screen and mouse cursor. I waited for a few minutes to see if the laptop would display anything at all; when nothing came up, I switched off the laptop. When I booted it after 30 mins (I had to step away as I had to run some errands), it booted fine and still has the same linux 3.13.0-40-generic, prior to the attempted upgrade.

I think it is hanging/running very slowly when it hits upgrading the kernel to linux-image-3.13.0-43-generic. When the upgrade hits processing the kernel, I am unable to capture the output as my laptop becomes unusably slow at that time :mad:

I am planning to do what user grahammechanical suggested in this thread (apt-get -f install). Is that advisable?

---

### Post by la.khan on 2014-12-29
Just to update further on my issue, I could capture output when my UL installation begins to process linux-image-3.13.0-43-generic. Please read this output as continuation to my earlier post.

```

dpkg: error processing package linux-image-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python3-distupgrade (1:0.220.6) ...
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 dependency problems - leaving unconfigured
Setting up lightdm (1.10.3-0ubuntu2) ...
Installing new version of config file /etc/lightdm/users.conf ...
Setting up fonts-opensymbol (2:102.6+LibO4.2.7-0ubuntu2) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.6) ...
Setting up libdrm-intel1:i386 (2.4.56-1~ubuntu1) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.3) ...
Setting up nux-tools (4.0.6+14.04.20141107-0ubuntu1) ...
Setting up ure (4.2.7-0ubuntu2) ...
Setting up compiz-plugins-default (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up libwebkitgtk-1.0-0:i386 (2.4.7-1~ubuntu1) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.3) ...
Setting up libwebkitgtk-3.0-0:i386 (2.4.7-1~ubuntu1) ...
Setting up gir1.2-webkit-3.0 (2.4.7-1~ubuntu1) ...
Setting up libreoffice-common (1:4.2.7-0ubuntu2) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1) ...
update-initramfs: deferring update (trigger activated)
Setting up ubuntu-release-upgrader-core (1:0.220.6) ...
Setting up plymouth-label (0.8.8-0ubuntu17.1) ...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up python3-apport (2.14.1-0ubuntu3.6) ...
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up compiz-gnome (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up apport (2.14.1-0ubuntu3.6) ...
Installing new version of config file /etc/init.d/apport ...
Setting up libreoffice-core (1:4.2.7-0ubuntu2) ...
Setting up ubuntu-release-upgrader-gtk (1:0.220.6) ...
Setting up python3-uno (1:4.2.7-0ubuntu2) ...
Setting up compiz (1:0.9.11.3+14.04.20141104-0ubuntu1) ...
Setting up libreoffice-math (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-base-core (1:4.2.7-0ubuntu2) ...
Setting up plymouth-theme-ubuntu-logo (0.8.8-0ubuntu17.1) ...
update-initramfs: deferring update (trigger activated)
Setting up libreoffice-pdfimport (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-gtk (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-draw (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-calc (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-impress (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-writer (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-gnome (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-presentation-minimizer (1:4.2.7-0ubuntu2) ...
Setting up libreoffice-ogltrans (1:4.2.7-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up apport-gtk (2.14.1-0ubuntu3.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.4) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
Processing triggers for libreoffice-common (1:4.2.7-0ubuntu2) ...
Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic

```

Looks like some dependency issue. Any idea how to resolve this?

---

### Post by schragge on 2014-12-29
The kernel update process hangs trying  to update GRUB:
```

run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...

```

Try to invoke update-grub manually:
```

sudo update-grub

```
and report any errors. If this hangs without any error messages, abort it and try again this way:
```

sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg

```
and post back the last part of the output (30 or so lines).

---

### Post by Bashing-om on 2014-12-29
la.khan; schragge; Hey ;

This has gotten interesting, and has my full attention. I am in a learning mode here also .

Depending on that last :
There are times when you have to be able to see where things in Grub are coming from and you can do that by looking at the output of sudo grub-mkconfig but, sometimes the output is too long to show in terminal. 
To see what is going on one can enter into the terminal:
```

sudo grub-mkconfig > mkconfig-output

```
to produce an output that can then be opened with gedit to view - transfer. It saves to the /home directory.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]try'n to find out -> what is going on here 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by schragge on 2014-12-29
@**Bashing-om**:
Actually, first I was going to suggest something like
```
sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg 2>&1 | pastebinit
```
but then I thought: what would end up on pastebin if grub-mkconfig hangs halfway through the update? I experimented a bit and found out that
```
sh -c 'echo This is just test;line' | pastebinit
``` doesn't print the link to paste.ubuntu.com if interrupted with Ctrl+C. But saving the output in a file as you suggested should work, obviously. Good point.

 However, I'd like to see the output to stderror, too. Actually, even more so than the output to stdout.

@OP: Let's do it by conflating mine and **Bashing-om**'s suggestions into this one:
```

sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg 2>&1 >mkconfig-output
pastebinit -i mkconfig-output

```
Then post the link pastebinit will give you.

---

### Post by Bashing-om on 2014-12-29
@schragge ....

OHH, do I ever appreciate that great mind that you have. 

Seeking to know what is bogging the system down - why updating grub is hanging .


[INDENT][INDENT]no substitute for experience[/INDENT][/INDENT]

---

### Post by schragge on 2014-12-29
You're flattering me too much :oops:

---

### Post by MAFoElffen on 2014-12-29
Yes, that would try to take care of the 4 broken packages... that it says 
> 
[COLOR=#ff0000]4 not fully installed or removed.[/COLOR]

which hanging or user interuption would have caused those broken packages...

To sooth what some have asked about, please post the results of 
```

cat /proc/cpuinfo

```
which would answer if your cpu and that kernel update would be compatible...

EDIT-- I just did updates on some of my KVM guests this morning. That kernel upgrade takes a while, 5 mins, just to upgrade that Kernel. Albiet in KVM... but that host is two fast 4-core cpu's, 48GB RAM and SAS6 disks. I can imagine that on an i686 that it may tke a while to complete... Sure you are waiting long enough for it to finish? Popping up another virt TTY session and checking the process in top may shed some light if it were really hung, or just taking a while to work on that.

---

### Post by la.khan on 2014-12-29
**MAFoElffen**,

Here is the output for cat /proc/cpuinfo
```

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
stepping    : 13
microcode    : 0xa3
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
bogomips    : 3990.31
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
stepping    : 13
microcode    : 0xa3
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
bogomips    : 3990.31
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

**schragge**/**Bashing-om**: Can I get you the output of 

```

sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg 2>&1 >mkconfig-output
pastebinit -i mkconfig-output

```

in a day? Thanks for your patience!

---

### Post by MAFoElffen on 2014-12-29
That cpu is PAE and is compatible with that kernel... But it is the kernel not installing-- Not because of just the update-initramfs porcess hanging... Well that's not all true. It is thankfully hanging on that process because it has already errored out before that process. That is a script problem where it should have caught that Error 2 code... Look for error level 0 (good) to ensure that is installed "before" coming back to that... Meaning, it should have skipped over that update-initrafs process. It was a problem before that...

Okay? Understand? Because those are broken--> Forcing Grub is not going help = It is just recreating the error. The 4 broken packages I see there are:
```

 linux-image-3.13.0-43-generic
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic

```
Where it said the error's on those were:
```

dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured

```
Several question arise from that. Usually you have a same version kernel header file that goes with those deb files, but many that is now inside one of those deb files (searching on the launchpad repo details file list, I get 404 not found) 

What launchpad does say is the depends list for that version I didn't see the header file for that(?) and I didn't see linux-firmware downloaded and installed for the OP, but I just glanced over that list... What launchpad says are the depends for linux-image-generic (3.13.0.43.50) [security] is:
```

linux-firmware
linux-image-3.13.0-43-generic
linux-image-extra-3.13.0-43-generic

```
BUT... I didn't see mention from the OP of him doing
```

sudo apt-get install -f
# which is shorthand for 
sudo apt-get install --fix-broken

```
Which to fix a broken package tries to get a depends to solve the issue.

To see what would be pending on a dependency, you could query with 
```

sudo apt-get install -s  linux-image-3.13.0-43-generic

```
Which would do a dry-run simulation to test that. During a test run, it is more verbose on the output to the screen. It will list all broken packages and missing dependent packages for that process to complete... without actually doing it. Very good for diagnostics.

One thing to try, is to remove/purge those 4 broken packages... and then reinstall them fresh. Possible that it got corruption on it's initial download... then trying to install on those corrupted packages... (You never know sometimes) To do that, you would
```


```
In those 2 lines, it should purge all, then download new copies of the deb packages and try to install them
```

sudo apt-get remove --purge linux-image-3.13.0-43-generic
sudo apt-get install linux-image-3.13.0-43-generic

```

Having gone through this a few times in Dev Testing and in LTS'es on various equipment, what I was told by others at Launchpad, was to try that... if still a problem, then install the same version from the Mainline Kernel Repo (untouched upstream kernel in deb package form)... If that is still a problem, then the problem is upstream of Ubuntu. I've had a few upstream bugs over the years.

---

### Post by la.khan on 2014-12-30
Hello **schragge/Bashing-om**,

I ran the command [COLOR=#0000cd]sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg 2>&1 >mkconfig-output[/COLOR] and it ran for 6+ hrs. When I look for file mkconfig-output, I see it has 0 bytes :mad: Secondly, I don't have package pastebinit installed; when I try to install it, I see a msg that dpkg was interrupted. Do I run command [COLOR=#ff0000]sudo dpkg --configure -a[/COLOR]? 

```

root@MilkyWay:~# ls -l
total 4
-rw-r--r-- 1 root root    0 Dec 30 05:43 mkconfig-output
-rw-r--r-- 1 root root 1478 Dec 29 05:21 upgrade.txt
root@MilkyWay:~# pastebinit -i mkconfig-output
The program 'pastebinit' is currently not installed. You can install it by typing:
apt-get install pastebinit
root@MilkyWay:~# apt-get install pastebinit
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

I have saved the screen output of the above command (in blue) to a text file (200 lines, 6.7 kB). Will contents of mkconfig-output (from above command in blue) be same as output to screen? Can I attach the file to one of my posts? Will that help?

Please let me know.

---

### Post by schragge on 2014-12-30
Yes, please. Attach the saved screen output.

Now I see the command I gave you was wrong, sorry, that's why mkconfig-output is empty. Actually, it supposed to have the contents that you've got on screen.

Just for reference, the right command should have been
```
sudo sh -x /usr/sbin/grub-mkconfig -o /boot/grub/grub.cfg [COLOR=red]>mkconfig-output 2>&1[/COLOR]
``` Note the order of the last two operands. But if you saved the screen output anyway no need to re-run it. And sorry again, I should have said you could interrupt the command after 5 minutes or so.

Yes, you can run *sudo dpkg --configure -a*. It won't do any harm, but may help with installation of unrelated packages that otherwise held back by this problem.

[highlight]Update[/highlight]
After thinking about it a bit, I've got an idea. The most fragile and error-prone part of the GRUB update process is known to be *os-prober* -- the script that checks what other operating systems are present on computer and adds entries for them to GRUB menu. Try to disable it with
```
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
``` and re-run *update-grub*:
```
sudo update-grub
```
 If it hangs again, wait just a couple of minutes and interrupt it. That would mean that my guess was wrong, and your woes have other causes. In this case you can remove the line that was added by above command from */etc/default/grub*:
```

sudo sed -i '/^GRUB_DISABLE_OS_PROBER=/d' /etc/default/grub
```

 **BUT** if *update-grub* finishes successfully without *os-prober* then we're after something.

---

### Post by la.khan on 2014-12-30
Hi schragge,

Attached is the screen output of the command I ran previously; please go through it and see if there are any issues that are causing me grief.

Also, I am unavailable till next week as I am busy with other stuff. I will run the following commands and get back to you next week (earliest Tue., 6th Jan). Is that okay?

1. [COLOR=#0000ff]sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub[/COLOR]
2. [COLOR=#0000ff]apt-get update-grub[/COLOR]
3. If above hangs again, [COLOR=#0000ff]run sed -i '/^GRUB_DISABLE_OS_PROBER=/d' /etc/default/grub[/COLOR]
4. Finally, [COLOR=#0000ff]sudo dpkg --configure -a[/COLOR]

My concern  with either step 2 and 4 is that my machine may take hours to complete. In the last few days, I have run step 4 and it was struck again where the installation processes linux-image-3.13.0-43-generic. In this thread, User **MAFoElffen** had suggested that I purge.

```

sudo apt-get remove --purge linux-image-3.13.0-43-generic
sudo apt-get install linux-image-3.13.0-43-generic

```

Early next week, I will get back to you on the four steps listed above, if they is no difference/progress, I will take your advise on purge.

Happy New Year!!!

---

### Post by schragge on 2014-12-31
I've just looked through the output of *grub-mkconfig*. Weird, but it looks like the GRUB update process went successful including the *os-prober* step, so disabling it probably won't bring us any further.

The only interesting line in the output was
```

Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

```
but it is harmless. Still, to get rid of this warning, comment the line *GRUB_HIDDEN_TIMEOUT=0* in file */etc/default/grub* by putting the # character in front of it:
```

sudo sed -i 's/^GRUB_HIDDEN_TIMEOUT=/#&/' /etc/default/grub

```

 The next debugging step would be to run
```
sudo grub-mkconfig
``` and watch the last line it outputs. It should be "done". If it gets stuck for more than one minute, just abort it, and report the last line it wrote onto screen.

But regardless of its results, and even before that check if you're already running the new kernel:
```
uname -r
``` It should give back
```
3.13.0-43-generic
```
If this is the case, please run
```
sudo dpkg --force-depends --configure linux-image-extra-3.13.0-43-generic
```
Mind you, it appears as though *update-grub* managed to configure the new kernel and add it to the boot menu even if dpkg still thinks it's broken and refuses to install packages that depend on it. If you're already booted into this kernel, it makes sense to ignore dpkg and forcibly configure *linux-image-extra-3.13.0-43-generic*, thus installing the kernel drivers that come with this package and may be needed to run your system properly. If left unconfigured, you may end up without network access and with broken video, among other things.

 As the last step in its configuration however, *linux-image-extra-3.13.0-43-generic* will run post-installation scripts in */etc/kernel/postinst.d* once again, including *update-grub*. If it again hangs, just interrupt it.

Happy New Year!

---

### Post by la.khan on 2015-01-06
Hello schragge,

I have run your all of your suggestions; please find below the screen output. My comments are included between [COLOR=#ff0000]/* */. [/COLOR]I abort a command using Cntrl + C; I hope that's fine. Is there a better way to abort/kill a command? Kill?

```

root@MilkyWay:~# sudo grub-mkconfig  [COLOR=#ff0000]/* Aborted after 3-4 mins. */[/COLOR]
^Croot@MilkyWay:~# uname -r
3.13.0-43-generic
root@MilkyWay:~# sudo dpkg --force-depends --configure linux-image-extra-3.13.0-43-generic
dpkg: linux-image-extra-3.13.0-43-generic: dependency problems, but configuring anyway as you requested:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic[COLOR=#ff0000] /*Takes more than 30 mins */[/COLOR]
Generating grub configuration file ... [COLOR=#ff0000]/*Takes more than 1 hr. */[/COLOR]
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. [COLOR=#ff0000]/*Aborted as soon as I saw the warning */[/COLOR]
^Cdpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
root@MilkyWay:~# sudo sed -i 's/^GRUB_HIDDEN_TIMEOUT=/#&/' /etc/default/grub
root@MilkyWay:~# uname -r
3.13.0-43-generic
root@MilkyWay:~# sudo grub-mkconfig
^Croot@MilkyWay:~# sudo dpkg --force-depends --configure linux-image-extra-3.13.0-43-generic
dpkg: linux-image-extra-3.13.0-43-generic: dependency problems, but configuring anyway as you requested:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic; however:
  Package linux-image-3.13.0-43-generic is not configured yet.

Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic [COLOR=#ff0000]/*Takes more than 30 mins */[/COLOR]
Generating grub configuration file ... [COLOR=#ff0000]/*Takes more than 1 hr. */[/COLOR]
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic [COLOR=#ff0000]/* At this point, I had to step out for an hour. The machine went into suspend and when I logged back in, I wasn't sure if anything was running. So, I aborted the process */[/COLOR]
^Cdpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic

```

So, from the above, my machine has 3.13.0-43-generic installed. Last week, when I checked it was 3.13.0-40-generic; it is upgraded to 3.13.0-43-generic. That is the good news.

Whenever I apply patches to my UL installation, I finish up by running the following commands:
```

sudo apt-get autoclean
sudo apt-get autoremove

```

Since my UL is installed with latest kernel, I ran above commands; here is the screen out.
```

root@MilkyWay:~# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@MilkyWay:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-43-generic
) points to /boot/initrd.img-3.13.0-43-generic
 (/boot/initrd.img-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-43-generic
) points to /boot/vmlinuz-3.13.0-43-generic
 (/boot/vmlinuz-3.13.0-43-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-43-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic

```

For reasons I don't understand, my OS still tries to run linux-image-3.13.0-43-generic. How do I get my machine out of this loop? Purge?

---

### Post by schragge on 2015-01-06
The problem is the low-level package manager (dpkg) still thinks the linux-image-3.13.0-43-generic is broken/not properly installed even if it isn't. From the output above I see that *update-grub* does its job, but does it *unbelievably* slow. All the assumed breakage is only because it always gets aborted and never gets the chance to run to the end. The process probably freezes when the computer goes into suspend mode. Actually, the */etc/kernel/postinst.d/pm-utils* is called during kernel install just to prevent computer from going into hibernate mode. Did it freeze again at the last run shown above (i.e. *sudo apt-get autoremove*)? I presume it did?

It seems like an old, long ago fixed Debian bug #[508834]("https://bugs.debian.org/508834") may shed some light on this. The discussion there outlines possible troubleshooting procedures.

Anyway, first let's do one dirty trick. We'll run grub-mkconfig by hand again, then disable the kernel hook that is supposed to do this, then configure everything. Just to be sure, we'll also disable both hibernate and suspend till the next reboot.
```

sudo -i
grub-mkconfig -o /boot/grub/grub.cfg
chmod -x /etc/kernel/postinst.d/zz-update-grub
touch /var/run/do-not-hibernate-or-suspend
dpkg --configure -a
chmod +x /etc/kernel/postinst.d/zz-update-grub
exit

```
This time don't abort, let dpkg run its job to the end.

[highlight]Update[/highlight]
Doing it from a virtual console (e.g. **Ctrl+Alt+F2**) rather than from a terminal window inside X session may speed up things quite a bit.

---

### Post by MAFoElffen on 2015-01-06
> **schragge said:**
> 
This time don't abort, let dpkg run its job to the end.

I confirm that the error about GRUB_TIMEOUT being set to a zero value will not cause a problem. This is a warning of what used to be a work-around to force the menu to appear and stay there until the user interacted with the menu. GNU change some of the underlying logic behind that, but even with that value and warning, it ignores the "forever" behavior of that previous work-around... It will not cause any problem or crash it. That is a just a warning.

I would be curous to see the syslog for that period (during that lag during the os_probe and grub config.

---

### Post by la.khan on 2015-01-07
> **schragge said:**
> 
```

sudo -i
mkconfig-grub -o /boot/grub/grub.cfg
chmod -x /etc/kernel/postinst.d/zz-update-grub
touch /var/run/do-not-hibernate-or-suspend
dpkg --configure -a
chmod +x /etc/kernel/postinst.d/zz-update-grub
exit

```

Do I put the above commands in a script file and run it? When I manually ran in a terminal window, I see:
```

root@MilkyWay:~# mkconfig-grub -o /boot/grub/grub.cfg
mkconfig-grub: command not found

```

> **schragge said:**
> 
[highlight]Update[/highlight]
Doing it from a virtual console (e.g. **Ctrl+Alt+F2**) rather than from a terminal window inside X session may speed up things quite a bit.

I prefer to run the commands in a terminal window so that I can capture the screen output using gedit. When I use a virtual login, I can't copy paste into gedit. I am still new to UL :redface:

---

### Post by ubfan1 on 2015-01-07
That should be grub-mkconfig

---

### Post by la.khan on 2015-01-07
Hi MAFoElffen,

> **MAFoElffen said:**
> I would be curous to see the syslog for that period (during that lag during the os_probe and grub config.

May I know where can I find that file? Folder & file name please.

---

### Post by Bashing-om on 2015-01-07
la.khan; Hey ;

> **la.khan said:**
> Hi MAFoElffen,



May I know where can I find that file? Folder & file name please.

That file be at " /var/log/syslog "

to display it :
```

cat /var/log/syslog

```
copy and paste the relevant entries - as the complete file would likely be too large to directly post to the forum.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by schragge on 2015-01-07
> **ubfan1 said:**
> That should be grub-mkconfig
Yep. Sorry. Edited the post.

---

### Post by schragge on 2015-01-07
> **la.khan said:**
> Do I put the above commands in a script file and run it?
Sure.

---

### Post by la.khan on 2015-01-07
> **Bashing-om said:**
> 
That file be at " /var/log/syslog "
to display it :
```

cat /var/log/syslog

```
copy and paste the relevant entries - as the complete file would likely be too large to directly post to the forum.[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Hi **MAFoElffen/Bashing-om**,

When I lookup syslog file, I see it is 685 kb and it has only entries of today (8th Jan 2015) :( So, I will watch the syslog file as I run commands suggested by **schragge**
```

sudo -i
grub-mkconfig -o /boot/grub/grub.cfg
chmod -x /etc/kernel/postinst.d/zz-update-grub
touch /var/run/do-not-hibernate-or-suspend
dpkg --configure -a
chmod +x /etc/kernel/postinst.d/zz-update-grub
exit

```

Will that work?

---

### Post by Dennis N on 2015-01-07
> When I lookup syslog file, I see it is 685 kb and it has only entries of today (8th Jan 2015)
If you need earlier data, it would be in syslog.1
Data before that is archived in .gz files - such as syslog.2.gz and so on.

---

### Post by la.khan on 2015-01-07
I ran the command manually, not as part of any script file.

```
grub-mkconfig -o /boot/grub/grub.cfg
```

I let this run for an hour before I killed the command and looked at the log file. Here is the output from var/log/syslog file:
```

Jan  8 07:05:08 MilkyWay kernel: [ 5867.896648] ata3: EH complete
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204885] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204894] ata3.00: BMDMA stat 0x24
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204900] ata3.00: failed command: READ DMA EXT
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204911] ata3.00: cmd 25/00:08:d0:f7:41/00:00:12:00:00/e0 tag 0 dma 4096 in
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204911]          res 51/01:00:d6:f7:41/01:00:12:00:00/e0 Emask 0x1 (device error)
Jan  8 07:05:11 MilkyWay kernel: [ 5871.204917] ata3.00: status: { DRDY ERR }
Jan  8 07:05:11 MilkyWay kernel: [ 5871.228795] ata3.00: configured for UDMA/33
Jan  8 07:05:11 MilkyWay kernel: [ 5871.228815] ata3: EH complete
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406721] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406729] ata3.00: BMDMA stat 0x24
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406736] ata3.00: failed command: READ DMA EXT
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406747] ata3.00: cmd 25/00:08:d0:f7:41/00:00:12:00:00/e0 tag 0 dma 4096 in
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406747]          res 51/01:00:d6:f7:41/01:00:12:00:00/e0 Emask 0x1 (device error)
Jan  8 07:05:15 MilkyWay kernel: [ 5874.406753] ata3.00: status: { DRDY ERR }
Jan  8 07:05:15 MilkyWay kernel: [ 5874.428698] ata3.00: configured for UDMA/33

```
Looks like a hard drive problem 8-[ :sad: Attached is a screenshot that mentions a bad sector. Please let me know if you need any other file/information from my end.

Any diagnostic utilities that are native to UL 14.04 that can help me here? I don't want to install anything new as my installation will first try to run an update for linux-image-3.13.0-43-generic :confused:

Just to add more information about my system: it is 6+ years since I bought the machine; it has served me well. Last month, I was thinking of buying a new one in 2015. Now, I want to continue using it as long as the machine lasts. Currently, it needs to have its battery replaced, and may be, the processor fan. Unless, I ask my UL installation to update with the latest patches, it runs fine for my daily use. I can attach the output of lshw, if that would help to resolve the device error.

---

### Post by schragge on 2015-01-08
Your hard drive is dropping down to [UDMA/33](http://en.wikipedia.org/wiki/UDMA) speed as result of failed [DMA](http://en.wikipedia.org/wiki/Direct_memory_access) reads. Unfortunately, this really looks like a failing hard drive. Another possibilities are a loose connector, or a bad [SATA](http://en.wikipedia.org/wiki/Serial_ATA) controller, or even a faulty PSU. Actually, a loose/defect SATA cable would be the most probable cause for this sort of DMA errors on a desktop system. But you've got a laptop. And a bad sector is being reported as well. If you can, check that the hard drive is firmly seated in its socket, better just re-seat it. Check power cables and connectors. Make a backup of any important data you have on the drive, then, and only then, boot from Ubuntu Live CD/DVD/USB, and run Disk Utility Tool, look there for SMART data, it should make full assessment of your hard drive's health. 

The commands I gave above could be run without *grub-mkconfig*, too.  But dpkg errors should not be your primary concern right now. There's a real possibility of your hard drive being in the process of dying.

---

### Post by la.khan on 2015-01-10
Hi schragge,

As you suggested, I backed all important files and used the UL Live DVD to perform SMART Data & self tests. The self test has failed; attached are screenshots of the same.

From the screenshots, can you conclude if the cause of failure is:
1. HDD not firmly seated in its socket 
2. power cables & connectors
3. bad SATA controller
4. faulty PSU
5. HDD gone bad and needs to be replaced

I plan to take the laptop to a nearby store and have it looked at to see if it no. 1-4 listed above. If it is no. 5 above, I can buy a new HDD (I see 500 GB WDC/Seagate retail for USD50). I plan to repair and continue to use this laptop. I think it makes sense to repair and use the laptop rather than throw it away.

Please let me know if you need more info from my end.

---

### Post by MAFoElffen on 2015-01-10
I realize you are having HDD problems... and that should be your primary concern. 

Aside from that, you are "also" having troubles w/ removing that kernel. You are not alone in that problem. The behavior of what is happening matches this user and you should add yourself to this bug:
[Can not remove old kernels & upgrade system; Bug #1404700]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1404700")

---

### Post by schragge on 2015-01-11
The SMART data don't look *very* bad on itself (for good account of SMART attributes, see [the Wikipedia article on it]("http://en.wikipedia.org/wiki/S.M.A.R.T.")). The normalized read error rate of 200 is well above the threshold value of 51, and there's only one sector in Current Pending Sector Count (but I'm still uncomfortable with this one, see [this answer]("http://askubuntu.com/a/159888") for why). OTOH, the failed self-test probably means the bad sector shown in Current Pending Sector Count isn't accounted for by the disk firmware yet. Try to run the commands described in [this FAQ]("http://www.smartmontools.org/wiki/FAQ#ATAdriveisfailingself-testsbutSMARThealthstatusisPASSED.Whatsgoingon")):
```

sudo smartctl -t long /dev/sda
sudo smartctl -l selftest /dev/sda

```
See [this HOWTO]("http://smartmontools.sourceforge.net/badblockhowto.html") for how to deal with bad blocks discovered by SMART. The HOWTO assumes your disk is formatted with ext2/ext3/ext4 filesystem. To see what filesystem is actually in use, run *df -T*.

If your filesystem is one of ext2/ext3/ext4 there's also a simpler procedure than what described in the HOWTO above to try first. From Live DVD, start a terminal, find out what device your hard drive is with
```

lsblk -S

```
Then, assuming it is */dev/sda*, run
```

sudo e2fsck -ccfp /dev/sda1

```
Hopefully, this will detect the bad block and mark it as unusable by filesystem.

Among the DMA read errors in the syslog output you gave above, I didn't see anything like
 ```
ata3.00: error: { UNC }
``` that would mean there were UNCorrectable disk errors. The DMA read errors per se only mean there's a problem with communicating data *towards* hard disk, but the hard drive *itself* may be OK. Is there a possibility you overlooked real disk I/O errors in the syslog? Try
```
grep 'ata.*error:' /var/log/syslog
```

If you happen to have a SATA-to-USB adapter handy, another thing to try would be to hook up the hard drive on a USB port through the adapter to see if the DMA errors go away.

I still think the commands I gave above to bring the package management system back into controllable state may be worth a try, but without the *grub-mkconfig* step, i.e.
```

sudo -i
chmod -x /etc/kernel/postinst.d/zz-update-grub
touch /var/run/do-not-hibernate-or-suspend
dpkg --configure -a
chmod +x /etc/kernel/postinst.d/zz-update-grub
exit

```
They won't address your hard drive problems obviously, but at least you'll be able to install other pending software updates.

---

### Post by MAFoElffen on 2015-01-11
I agree with putting on a USB converter to check... Must of the time errors show up in the log like those in Post #24, it's suspect that it either has a bad SATA cable of that the PSU power is at fault for that drive. 


 To put on a SATA/USB converter would isolate the drive completely from the existing SATA controller completely.

But while inside the box, you could do some other quick checks:
-Put another cable on it. (Or swap from a different drive)
-- check to see if it still has errors.
- Plug into a different power source.
-- Put on another physical branch coming from the PSU. (Or another physical PSU)

If you do have a SATA/USB converter, use one that has it's own external power source. 2-1/2 form factor drives will work fine without one, But 3-1/2 form factor drives need additional power thna just from USB... Otherwise your may get a false positive on DMA errors. (because of insufficient power.)

Just a few tips from volunteer work testing equipment for a non-profit computer recycler. There's more info, but I have to tell you, that recylcer has some stringent spec's that they test for, before they will resell a drive. I've gotten many free drives from them, that have not passed certain tests-- and have lasted me years (after I re-prepped them).

---

### Post by la.khan on 2015-01-15
Hi schragge/MAFoElffen,

Just an update from my end on some of the suggestions you made.

> 
Among the DMA read errors in the syslog output you gave above, I didn't see anything like
  ```
ata3.00: error: { UNC }
```
that would mean there were UNCorrectable disk errors. The DMA read errors per se only mean there's a problem with communicating data [I]
towards[/I] hard disk, but the hard drive *itself* may be OK. Is there a possibility you overlooked real disk I/O errors in the syslog? Try
```
grep 'ata.*error:' /var/log/syslog
```


When I looked up syslog file, I couldn't find any of these errors. However, when I look up older syslog files, one older syslog file had 10+ instances of of this error (may be from 11th January).

> 
If you happen to have a SATA-to-USB adapter handy, another thing to try  would be to hook up the hard drive on a USB port through the adapter to  see if the DMA errors go away.


Unfortunately, I do not have this with me :( and neither does the computer store I visited to have the laptop hardware looked at.

I ran command ```
sudo e2fsck -ccfp /dev/sda1
``` and this ran for more than 4.5 hours before this was interuppted by power failure (my laptop needs a new battery as the current one offers 2 mins back up :redface:). Is it usual for this command to run this long on a 160 GB HDD? I did not see any updates on screen while this was running. I ran the command, for a few mintues with -v (verbose option) but no updates on screen about progress of the command.

I ran the rest of the commands you suggested.
```

sudo -i
chmod -x /etc/kernel/postinst.d/zz-update-grub
touch /var/run/do-not-hibernate-or-suspend
dpkg --configure -a
chmod +x /etc/kernel/postinst.d/zz-update-grub
exit

```

Please refer to attached text file as it contains screen output for the commands I ran. Since my UL installation slows down during kernel update, for all future updates, I plan to turn off hibernate/suspend before I apply patches. [COLOR=#ff0000]May I know how do I turn hibernate/suspend back on after I apply updates?[/COLOR]

Lastly, when I query UL about the current version, I see
```
$ uname -a
Linux MilkyWay 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686 i686 i686 GNU/Linux

```

So, it looks as though that my Linux instance got updated but I prefer I didn't have to jump through so may hoops for the same. That may be due to my HDD that I need to replace in the near future. I plan to get a 500GB SATA WDC/Seagate that retails for USD50.

Thanks for your help & assitance in this regard!

---

### Post by schragge on 2015-01-16
> **la.khan said:**
> However, when I look up older syslog files, one older syslog file had 10+ instances of of this error (may be from 11th January).
Could you please post corresponding parts of the syslog?

> Is it usual for this command to run this long on a 160 GB HDD?
Well, it depends on the scope of repair and maintenance work *e2fsck* performs and may vary from drive to drive. While it taking a very long time to complete is [not unheard of]("http://gparted-forum.surf4.info/viewtopic.php?id=13613"), that's definitely not usual. It may be connected to your hard drive dropping down to UDMA/33 speed, however.

> May I know how do I turn hibernate/suspend back on after I apply updates? Just remove the file */var/run/do-not-hibernate-or-suspend*. It will also go away by itself after reboot.

> That may be due to my HDD that I need to replace in the near future. May be. Or may be not. Unfortunately, it's hard to tell without troubleshooting your hard drive in depth with tools like [smartctl]("http://manpages.ubuntu.com/manpages/trusty/en/man8/smartctl.8.html"), [hdparm]("http://manpages.ubuntu.com/manpages/trusty/en/man8/hdparm.8.html"), [hddtemp](http://manpages.ubuntu.com/manpages/trusty/en/man8/hddtemp.8.html), [debugfs]("http://manpages.ubuntu.com/manpages/trusty/en/man8/debugfs.8.html"), and diagnostic tools from Dell and/or your hard drive manufacturer. E.g. there was [an old report]("http://thread.gmane.org/gmane.linux.ide/32981") of hard drive in Dell Inspiron 1525 performing too frequent head unloads that may shorten its lifespan. But I assume this issue should be fixed by now. If not, see [uwiki]AsusUL/HddCycles[/uwiki].

The upgrade log you posted looks OK. For now, don't forget to backup your data frequently.

---

### Post by la.khan on 2015-01-17
Hello schragge,

> Could you please post corresponding parts of the syslog?

Here is a sample of what I see in syslog from 13th January.
```

Jan 13 18:46:09 MilkyWay kernel: [ 1117.564727] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 13 18:46:09 MilkyWay kernel: [ 1117.564736] ata3.00: BMDMA stat 0x24
Jan 13 18:46:09 MilkyWay kernel: [ 1117.564742] ata3.00: failed command: READ DMA EXT
Jan 13 18:46:09 MilkyWay kernel: [ 1117.564753] ata3.00: cmd 25/00:08:d0:f7:41/00:00:12:00:00/e0 tag 0 dma 4096 in
Jan 13 18:46:09 MilkyWay kernel: [ 1117.564753]          res 51/01:00:d6:f7:41/01:00:12:00:00/e0 Emask 0x1 (device error)
Jan 13 18:46:09 MilkyWay kernel: [ 1117.564759] ata3.00: status: { DRDY ERR }
Jan 13 18:46:10 MilkyWay kernel: [ 1117.588675] ata3.00: configured for UDMA/33
Jan 13 18:46:10 MilkyWay kernel: [ 1117.588691] ata3: EH complete
Jan 13 18:46:13 MilkyWay kernel: [ 1120.899993] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900000] ata3.00: BMDMA stat 0x24
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900027] ata3.00: failed command: READ DMA EXT
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900039] ata3.00: cmd 25/00:08:d0:f7:41/00:00:12:00:00/e0 tag 0 dma 4096 in
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900039]          res 51/40:00:d6:f7:41/40:00:12:00:00/e0 Emask 0x9 (media error)
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900055] ata3.00: status: { DRDY ERR }
Jan 13 18:46:13 MilkyWay kernel: [ 1120.900061] **ata3.00: error: { UNC }**
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924952] ata3.00: configured for UDMA/33
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924971] sd 2:0:0:0: [sda] Unhandled sense code
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924976] sd 2:0:0:0: [sda]  
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924979] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924984] sd 2:0:0:0: [sda]  
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924987] Sense Key : Medium Error [current] [descriptor]
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924993] Descriptor sense data with sense descriptors (in hex):
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924996]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925017]         12 41 f7 d6 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925027] sd 2:0:0:0: [sda]  
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925033] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925038] sd 2:0:0:0: [sda] CDB: 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925041] Read(10): 28 00 12 41 f7 d0 00 00 08 00
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925057] end_request: I/O error, dev sda, sector 306313174
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925063] Buffer I/O error on device sda, logical block 38289146
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925083] ata3: EH complete

```

> Unfortunately, it's hard to tell without troubleshooting your hard drive in depth with tools like [smartctl]("http://manpages.ubuntu.com/manpages/trusty/en/man8/smartctl.8.html"), [hdparm]("http://manpages.ubuntu.com/manpages/trusty/en/man8/hdparm.8.html"), [hddtemp]("http://manpages.ubuntu.com/manpages/trusty/en/man8/hddtemp.8.html"), [debugfs]("http://manpages.ubuntu.com/manpages/trusty/en/man8/debugfs.8.html"), and diagnostic tools from Dell and/or your hard drive manufacturer.

I don't have any diagnostic tools from Dell or my device manufacturer (WDC) but I have installed smartctl, hdparm, hddtemp, debugfs. Will these tools help?

---

### Post by schragge on 2015-01-17
```

Jan 13 18:46:13 MilkyWay kernel: [ 1120.924987] Sense Key : Medium Error [current] [descriptor]
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924993] Descriptor sense data with sense descriptors (in hex):
Jan 13 18:46:13 MilkyWay kernel: [ 1120.924996]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925017]         12 41 f7 d6 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925027] sd 2:0:0:0: [sda]  
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925033] Add. Sense: [COLOR=red]Unrecovered read error - auto reallocate failed[/COLOR]
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925038] sd 2:0:0:0: [sda] CDB: 
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925041] Read(10): 28 00 12 41 f7 d0 00 00 08 00
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925057] end_request: [COLOR=red]I/O error, dev sda, sector 306313174[/COLOR]
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925063] [COLOR=red]Buffer I/O error on device sda, logical block 38289146[/COLOR]
Jan 13 18:46:13 MilkyWay kernel: [ 1120.925083] ata3: EH complete

```
Well, [COLOR=red]this[/COLOR] definitely looks like an I/O disk error. If there's only a handful of bad sectors then try to locate them manually one by one and mark as unusable to filesystem as described in [this HOWTO]("http://smartmontools.sourceforge.net/badblockhowto.html").

> **la.khan said:**
> I don't have any diagnostic tools from Dell or my device manufacturer (WDC)
WD diagnostic tool may be downloaded from [here]("http://support.wdc.com/product/download.asp?groupid=702&sid=2&lang=en"). To create a bootable USB with FreeDOS you can use [unetbootin]("http://manpages.ubuntu.com/manpages/trusty/en/man1/unetbootin.1.html") instead of Rufus suggested in WD documentation.

> but I have installed smartctl, hdparm, hddtemp, debugfs. Will these tools help?
They may help you dealing with bad blocks. So may other tools like [ddrescue]("http://manpages.ubuntu.com/manpages/trusty/en/man1/ddrescue.1.html"), or even plain old [dd]("http://manpages.ubuntu.com/manpages/trusty/en/man1/dd.1.html"). If you feel uncomfortable using command-line tools there's also a GUI wrapper for *smartctl*: [gsmartcontrol]("http://manpages.ubuntu.com/manpages/trusty/en/man1/gsmartcontrol.1.html").

---

### Post by la.khan on 2015-01-20
Hi schragge/MAFoElffen/bashing-om,

I will use the HDD tools that schragge mentioned in the post above to monitor my HDD and try to fix the error(s).

Thanks for your help and insights in resolving the issue!

I will mark this thread resolved.

---

