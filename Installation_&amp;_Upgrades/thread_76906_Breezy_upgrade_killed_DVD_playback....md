---
title: "Breezy upgrade killed DVD playback?..."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by raggamuffin on 2005-10-15
After apt-get dist-upgrade'ing to breezy (Kubuntu), all the sudden VLC or other media players cannot play any DVD's...

this is what comes up in the terminal window...

> VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat
No such file or directory
libdvdnav: vm: faild to open/read the DVD
libdvdread: Can't stat
No such file or directory
[00000271] dvdread demuxer error: DVDRead cannot open source:
[00000270] main input error: no suitable access module for `dvd://'
[00000261] main playlist: nothing to play


How do I go about fixing this...(or downgrading VLC to the previous, **working** version)?...

Thanks in advance...

---

### Post by raggamuffin on 2005-10-16
OK...I tried compiling VLC from source...after an hour of waiting for shit to compile and searching down obscure -devel packages...is still the same problem?...

Is anybody else having a similar problem?...

---

### Post by dtfinch on 2005-10-16
This is just a guess, since I don't use VLC and DVD playback has worked for me, but in VLC go into settings->preferences->input/codecs->advanced and make sure the DVD device option is correct. Maybe /dev/dvd, /dev/cdrom, or /dev/hdc.

---

### Post by v-gudmk on 2005-12-19
Try installing libdvdread3 and then read this:
    /usr/share/doc/libdvdread3/README.Debian

---

### Post by jsaacmk on 2006-02-26
Yes! That worked for me. Awesome. Thank you very much.

---

