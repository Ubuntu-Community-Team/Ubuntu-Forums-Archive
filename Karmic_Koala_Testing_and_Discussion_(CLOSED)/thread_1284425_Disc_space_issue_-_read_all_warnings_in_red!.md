---
title: "Disc space issue - read all warnings in red!"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-10-06
I noticed today that recent updates left some of us "crunched" for space:

> lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
**/dev/sda3              6.3G   4.9G   1.1G  82% /**
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


Not so much in my case, but a problem for some.

So I ran:

> lance@lance-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-11 linux-headers-2.6.31-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              6.3G   4.9G   1.1G  82% /
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home
lance@lance-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree        
Reading state information... Done
[COLOR="Red"]The following packages will be REMOVED:
  linux-headers-2.6.31-11 linux-headers-2.6.31-11-generic[/COLOR]
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, [COLOR="Red"]82.0MB[/COLOR] disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148821 files and directories currently installed.)
Removing linux-headers-2.6.31-11-generic ...
Removing linux-headers-2.6.31-11 ...
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              6.3G   4.8G   1.2G  81% /
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


[COLOR="Red"]Do NOT run the autoremove command until you are certain that the new kernel boots OK![/COLOR] It only gains you 82MB anyway!

**[COLOR="Red"]Remember, if you break it you own it![/COLOR]**

However, read on:

> lance@lance-desktop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-libc-dev 2.6.31-11.38 [733kB]
Del hplip-gui 3.9.8-0ubuntu6 [58.8kB]
Del libqt4-dbus 4.5.2-0ubuntu5 [174kB]
Del python2.6 2.6.3-0ubuntu1 [2,501kB]
Del dmraid 1.0.0.rc15-11build1 [36.1kB]
Del libqt4-script 4.5.2-0ubuntu5 [350kB]
Del python-aptdaemon 0.10+bzr242-0ubuntu3 [40.6kB]
Del hpijs 3.9.8-0ubuntu7 [416kB]
Del linux-firmware 1.20 [4,047kB]
Del libqt4-scripttools 4.5.2-0ubuntu5 [222kB]
Del libqt4-network 4.5.2-0ubuntu5 [386kB]
Del evolution 2.28.0-0ubuntu3 [2,605kB]
Del evolution-common 2.28.0-0ubuntu3 [4,077kB]
Del gcc-4.4 4.4.1-4ubuntu5 [3,078kB]
Del gstreamer0.10-ffmpeg 0.10.8.2-1 [123kB]
Del dmraid 1.0.0.rc15-11ubuntu1 [36.2kB]
Del libgomp1 4.4.1-4ubuntu5 [27.3kB]
Del ubuntu-xsplash-artwork 0.8.2-0ubuntu1 [573kB]
Del libgail-common 2.18.1-1 [345kB]
Del libapparmor-perl 2.3.1+1403-0ubuntu24 [38.2kB]
Del grub 0.97-29ubuntu56 [427kB]
Del libdmraid1.0.0.rc15 1.0.0.rc15-11build1 [111kB]
Del libgtk2.0-bin 2.18.1-1ubuntu1 [212kB]
Del totem-xine 2.28.0-0ubuntu1 [51.3kB]
Del ubuntu-docs 9.10.8 [465kB]
Del libgail18 2.18.1-1ubuntu1 [216kB]
Del libpython2.6 2.6.3-0ubuntu1 [1,017kB]
Del libgtk2.0-bin 2.18.1-1 [212kB]
Del libgstreamer0.10-0 0.10.24.4-1 [708kB]
Del libboost-python1.38.0 1.38.0-6ubuntu4 [239kB]
Del libgtk2.0-0 2.18.1-1 [2,515kB]
Del libdvdread4 4.1.3-5ubuntu1 [64.0kB]
Del f-spot 0.6.1.3-1ubuntu1 [1,437kB]
Del gtk2-engines-pixbuf 2.18.1-1 [484kB]
Del libqt4-xmlpatterns 4.5.2-0ubuntu5 [641kB]
Del libgtk2.0-common 2.18.1-1ubuntu1 [471kB]
Del apparmor 2.3.1+1403-0ubuntu24 [340kB]
Del libqt4-assistant 4.5.2-0ubuntu5 [11.5kB]
Del libgail18 2.18.1-1 [216kB]
Del libqtgui4 4.5.2-0ubuntu5 [3,620kB]
Del libgdu0 2.28.0-1 [61.5kB]
Del evolution-documentation-en 2.28.0-0ubuntu3 [123kB]
Del libdevkit-power-gobject1 010+git20090913-0ubuntu2 [25.1kB]
Del gstreamer0.10-tools 0.10.24.4-1 [56.4kB]
Del libqt4-test 4.5.2-0ubuntu5 [41.2kB]
Del libbonoboui2-0 2.24.2-1ubuntu1 [175kB]
Del libapparmor1 2.3.1+1403-0ubuntu24 [35.3kB]
Del python-twisted-conch 1:8.2.0-2 [242kB]
Del hplip-gui 3.9.8-0ubuntu7 [59.6kB]
Del gcc-4.4-base 4.4.1-4ubuntu5 [112kB]
Del python-aptdaemon-gtk 0.10+bzr242-0ubuntu3 [188kB]
Del libdmraid1.0.0.rc15 1.0.0.rc15-11ubuntu1 [111kB]
Del libqt4-xml 4.5.2-0ubuntu5 [85.1kB]
Del xsplash 0.8.2-0ubuntu1 [17.3kB]
Del software-center 0.4.5 [241kB]
Del devicekit-power 010+git20090913-0ubuntu2 [68.8kB]
Del telepathy-gabble 0.8.4-1 [356kB]
Del libffi5 3.0.7-2 [15.9kB]
Del binutils 2.19.91.20091005-0ubuntu2 [1,657kB]
Del libqt4-help 4.5.2-0ubuntu5 [177kB]
Del software-center 0.4.4 [195kB]
Del libqt4-webkit 4.5.2-0ubuntu5 [3,771kB]
Del ntfs-3g 1:2009.4.4-1ubuntu2 [27.5kB]
Del totem-plugins-extra 2.28.0-0ubuntu1 [113kB]
Del libklibc 1.5.15-1ubuntu1 [49.4kB]
Del libqtcore4 4.5.2-0ubuntu5 [1,507kB]
Del libgtk2.0-0 2.18.1-1ubuntu1 [2,515kB]
Del klibc-utils 1.5.15-1ubuntu1 [162kB]
Del libgtk2.0-common 2.18.1-1 [470kB]
Del libqt4-phonon 4.5.2-0ubuntu5 [92.6kB]
Del libstdc++6 4.4.1-4ubuntu5 [347kB]
Del libgdu-gtk0 2.28.0-1 [63.3kB]
Del byobu 2.36-0ubuntu1 [54.0kB]
Del ubuntu-xsplash-artwork 0.8.1-0ubuntu2 [573kB]
Del libntfs-3g54 1:2009.4.4-1ubuntu2 [117kB]
Del python2.6-minimal 2.6.3-0ubuntu1 [1,373kB]
Del hplip 3.9.8-0ubuntu7 [313kB]
Del libmp4v2-0 1:1.6dfsg-0.2ubuntu4 [295kB]
Del hplip-cups 3.9.8-0ubuntu7 [400kB]
Del libqt4-svg 4.5.2-0ubuntu5 [127kB]
Del evolution-plugins 2.28.0-0ubuntu3 [237kB]
Del binutils 2.19.91.20091001-0ubuntu2 [1,656kB]
Del devicekit-disks 007-1 [172kB]
Del libqt4-sql 4.5.2-0ubuntu5 [86.6kB]
Del gdm 2.28.0-0ubuntu11 [721kB]
Del libqt4-designer 4.5.2-0ubuntu5 [1,811kB]
Del binutils 2.19.91.20091001-0ubuntu1 [1,656kB]
Del gnome-disk-utility 2.28.0-1 [436kB]
Del libgcc1 1:4.4.1-4ubuntu5 [73.3kB]
Del gtk2-engines-pixbuf 2.18.1-1ubuntu1 [484kB]
Del gparted 0.4.5-2build1 [907kB]
Del cpp-4.4 4.4.1-4ubuntu5 [3,814kB]
Del apparmor-utils 2.3.1+1403-0ubuntu24 [99.5kB]
Del xsplash 0.8.1-0ubuntu2 [17.3kB]
Del libgail-common 2.18.1-1ubuntu1 [345kB]
Del aptdaemon 0.10+bzr242-0ubuntu3 [4,078B]
Del libbonoboui2-common 2.24.2-1ubuntu1 [15.5kB]
Del hplip-data 3.9.8-0ubuntu7 [8,847kB]
Del libqt4-sql-mysql 4.5.2-0ubuntu5 [24.6kB]
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
**/dev/sda3              6.3G   4.8G   1.3G  80% /**
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


[COLOR="Red"]Some gain there, a tenth of a GB.[/COLOR]

Then:

> lance@lance-desktop:~$ sudo apt-get clean
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
**/dev/sda3              6.3G   4.3G   1.7G  72% /**
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   201k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


So apt-get clean gained me a half a GB, [COLOR="Red"]but while I see no ill effects, **you could!**[/COLOR][COLOR="Red"][/COLOR]

You must decide for yourselves what to do, just know that "autoclean" only removes .deb archives from packages which are no longer installed, whereas "clean" [COLOR="Red"]is more radical, and will remove .deb files even for packages currently installed. But most of the time you probably don't need the .debs any more, so it might be worth it if you're strapped for megabytes.[/COLOR]

It's up to you!

---

### Post by emarkay on 2009-10-06
Might this be related to this whole "Partial Upgrade" issue?

---

### Post by kansasnoob on 2009-10-06
> **emarkay said:**
> Might this be related to this whole "Partial Upgrade" issue?

I was never warned of a Partial Upgrade.

---

### Post by emarkay on 2009-10-06
Another one! 

The warning is buried in the first "Sticky", "...Please read before testing", along with a LOT of other info.  I knew this would bite more than just me a few days ago and have asked for this issue alone to be a separate "Sticky". 

Sorry, I can't do anything more.  :(

---

### Post by jpeddicord on 2009-10-06
linux-headers-* packages have nothing to do with boot. They are only used if you want to do some kernel/module/etc development. You can remove all of them if you want, your boot will not be affected.

linux-image-* is what matters.

---

### Post by kansasnoob on 2009-10-07
> **jacobmp92 said:**
> linux-headers-* packages have nothing to do with boot. They are only used if you want to do some kernel/module/etc development. You can remove all of them if you want, your boot will not be affected.

linux-image-* is what matters.

Thanks for the info. I'd always been reluctant to remove those packages until I knew for sure that the new kernel worked alright with my hardware.

---

