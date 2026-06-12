---
title: "Gutsy device name: /dev/dvd1 Why not /dev/dvd?"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by manolo on 2007-12-13
I have just installed Gutsy
My drives are correctly identified:
ls -l /dev
	crw-rw---- 1 root   audio    14,  12 2007-12-12 19:48 adsp
	crw-rw---- 1 root   audio    14,   4 2007-12-12 19:48 audio
	drwxr-xr-x 3 root   root          60 2007-12-12 19:48 bus
	lrwxrwxrwx 1 root   root           4 2007-12-12 19:48 cdrom -> scd0
	lrwxrwxrwx 1 root   root           4 2007-12-12 19:48 cdrom1 -> scd1
	lrwxrwxrwx 1 root   root           4 2007-12-12 19:48 cdrw -> scd0
	crw------- 1 root   root      5,   1 2007-12-12 19:49 console
	lrwxrwxrwx 1 root   root          11 2007-12-12 19:48 core -> /proc/kcore
	drwxr-xr-x 6 root   root         120 2007-12-12 19:48 disk
	drwxr-xr-x 2 root   root          60 2007-12-12 19:49 dri
	crw-rw---- 1 root   audio    14,   3 2007-12-12 19:48 dsp
	lrwxrwxrwx 1 root   root           4 2007-12-12 19:48 dvd1 -> scd1
	lrwxrwxrwx 1 root   root          13 2007-12-12 19:48 fd -> /proc/self/fd
	brw-rw---- 1 root   floppy    2,   0 2007-12-12 19:48 fd0

but, as you can see, the link to my Dvd drive is named /dev/dvd1 instead of /dev/dvd
If I make a link named /dev/dvd it is deleted at start up.

Most media applications (mplayer, xine, lsdvd, ...) use /dev/dvd as the default Dvd drive and it is a bother to have to specify /dev/dvd1. Is there a way to have udev change the name to /dev/dvd?

Thanks in advance.



SOLVED: Editing /etc/udev/rules.d/70-persistent-cd.rules

---

### Post by manolo on 2007-12-13
Is it normal, in Gutsy, that the dvd drive is linked to /dev/dvd1 instead of /dev/dvd, or is it only in my system?

Please let me know if it happens to you too.

Thanks.


P.S.
This is th ls -l output for /dev with Ubuntu 5.1 Breezy (Have two Hds: Breezy & Gutsy):
crw-rw----  1 root root     10,  62 2007-12-13 19:28 acpi
crw-rw----  1 root audio    14,  12 2007-12-13 19:28 adsp
crw-rw----  1 root video    10, 175 2007-12-13 19:28 agpgart
crw-rw----  1 root audio    14,   4 2007-12-13 19:28 audio
lrwxrwxrwx  1 root root           3 2007-12-13 19:27 cdrom -> hda
lrwxrwxrwx  1 root root           3 2007-12-13 19:27 cdrom1 -> hdb
lrwxrwxrwx  1 root root           3 2007-12-13 19:27 cdrw -> hda
crw-------  1 root root      5,   1 2007-12-13 19:28 console
lrwxrwxrwx  1 root root          11 2007-12-13 19:27 core -> /proc/kcore
drwxr-xr-x  2 root root           0 2007-12-13 19:28 dri
crw-rw----  1 root audio    14,   3 2007-12-13 19:28 dsp
lrwxrwxrwx  1 root root           3 2007-12-13 19:27 dvd -> hdb
drwxr-xr-x  4 root root           0 2007-12-13 19:27 evms
crw-rw----  1 root video    29,   0 2007-12-13 19:27 fb0
lrwxrwxrwx  1 root root          13 2007-12-13 19:27 fd -> /proc/self/fd
brw-rw----  1 root floppy    2,   0 2007-12-13 19:28 fd0

---

