---
title: "DVD problem"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by antennae on 2005-05-18
hi there
i installed ubuntu hoary hedgehog on my laptop earlier today, now i'm trying to get dvd playback. have followed the steps [here](http://www.ubuntuguide.org/#dvdplayback). the dvd playback wont work in either totem or xine.

---

### Post by defkewl on 2005-05-18
Install libdvdcss2 first.
If it is not in the repository you could find it at apt-get.org

---

### Post by antennae on 2005-05-19
[QUOTE=defkewl]Install libdvdcss2 first.
If it is not in the repository you could find it at apt-get.org[/QUOTE]

libdvdcss2 is already the newest version.

this is terminal utput when i run xine:

~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

---

### Post by antennae on 2005-05-19
the drive is a combined cd/dvd drive

---

### Post by antennae on 2005-05-19
these packages wont upgrade:

~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer0.8-lame libxvidcore4 mplayer-386
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by @jens on 2005-05-19
[QUOTE=antennae]libdvdcss2 is already the newest version.

this is terminal utput when i run xine:

~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.

Are you sure that "dev/dvd" is the correct device? It's by xine-defaults but doesn't match the reality. Look at /etc/fstab. I guess /dev/cdrom or /dev/cdrom1 is the correct one. Open xine->setup->become "master of the known universe" -> change the devices in "audio" and "video" (scroll down because there is one of the entries) -> apply->ok->close start again->watch dvd.
hth
@jens

---

### Post by antennae on 2005-05-19
anyways this is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


i get these messages after trying to load the dvd:

there is no input plugin available to handle 'dvd:/'. maybe mrl syntax is wrong or file/stream source doesn't exist

the source can't be read. maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). (/media/cdrom0)

ti get his message in the title bar when i start up: xine: there is no mrl

this is the terminal output:
~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.

---

### Post by @jens on 2005-05-19
[QUOTE=antennae]anyways this is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


i get these messages after trying to load the dvd:

there is no input plugin available to handle 'dvd:/'. maybe mrl syntax is wrong or file/stream source doesn't exist

the source can't be read. maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). (/media/cdrom0)

ti get his message in the title bar when i start up: xine: there is no mrl

this is the terminal output:
~$ xine
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.[/QUOTE]
 Okay your dvd-drive is master on IDE2=hdc and the device (fstab) is /dev/cdrom0. Please open xine, go to setup (right click->setup), become "master of the known universe" (default is "beginner" or so, you can see that on the front page). Then open "audio" and "video" and change the devices to /dev/cdrom0->apply->close->start xine->watch dvd movie
Regards

---

### Post by chele on 2007-06-28
> **antennae said:**
> hi there
i installed ubuntu hoary hedgehog on my laptop earlier today, now i'm trying to get dvd playback. have followed the steps [here]("http://www.ubuntuguide.org/#dvdplayback"). the dvd playback wont work in either totem or xine.Check the permissions on the mounted DVD. There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550") about some DVD's being mounted with restrictive permissions, resulting in no playback.

---

