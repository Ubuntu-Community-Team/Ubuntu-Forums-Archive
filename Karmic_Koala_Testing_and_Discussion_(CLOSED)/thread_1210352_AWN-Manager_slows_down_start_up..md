---
title: "AWN-Manager slows down start up."
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-07-11
Anyone else having this problem since the recent update? If you have the AWN dock and have it start up at "start-up", it slows the desktop, X session down like a snail. Nothing loads and the only way to access anything, to continue, is to close the dock.

---

### Post by wayne_cat on 2009-07-11
[https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008](https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008)

---

### Post by tjeremiah on 2009-07-11
> **wayne_cat said:**
> [https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008](https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008)

I swear i need to remember to first search for a bug report :(

---

### Post by wayne_cat on 2009-07-11
It started after these updates ... Seems to have a problem with one of the new gtk packages
```

2009-07-10 16:33:36 status installed man-db 2.5.5-2
2009-07-10 16:33:36 status installed menu 2.1.41ubuntu1
2009-07-10 16:33:38 status installed hicolor-icon-theme 0.10-2
2009-07-10 16:33:39 status installed desktop-file-utils 0.15-2ubuntu1
2009-07-10 16:33:39 status installed upstart 0.6.0-3
2009-07-10 16:33:39 status installed command-not-found-data 0.2.37ubuntu1
2009-07-10 16:33:40 status installed command-not-found 0.2.37ubuntu1
2009-07-10 16:33:40 status installed apt-xapian-index 0.21ubuntu1
2009-07-10 16:33:40 status installed libgtk2.0-common 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libgtk2.0-0 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libgtk2.0-dev 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libgail18 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libgail-common 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed gtk2-engines-pixbuf 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libgtk2.0-bin 2.17.3-0ubuntu1
2009-07-10 16:33:40 status installed libpq5 8.4.0-1
2009-07-10 16:33:40 status installed libpq-dev 8.4.0-1
2009-07-10 16:33:41 status installed rhythmbox 0.12.3-1ubuntu1
2009-07-10 16:33:42 status installed unattended-upgrades 0.51ubuntu1
2009-07-10 16:33:42 status installed xserver-xorg-video-intel 2:2.7.99.901+git20090702.74227141-0ubuntu1
2009-07-10 16:33:42 status installed gjs 0.3-0ubuntu1
2009-07-10 16:33:42 status installed libc6 2.9-9ubuntu2
2009-07-10 16:33:42 status installed menu 2.1.41ubuntu1
```

---

### Post by afv on 2009-07-11
Workaround: downgrade libgtk2.0-0 from 2.17.3-0ubuntu1 to [2.16.1-0ubuntu2]("http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.16.1-0ubuntu2_i386.deb"). ;)

---

### Post by TerminX on 2009-07-11
Why downgrade all the way to 2.16.1-0ubuntu2?  2.17.2-0ubuntu2 works as well.

---

### Post by wayne_cat on 2009-07-11
> **afv said:**
> Workaround: downgrade libgtk2.0-0 from 2.17.3-0ubuntu1 to [2.16.1-0ubuntu2]("http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.16.1-0ubuntu2_i386.deb"). ;)

tested ... it works.

afv .. I saw the update in the bug report #398008 ... thank you!

---

### Post by wayne_cat on 2009-07-11
> **TerminX said:**
> Why downgrade all the way to 2.16.1-0ubuntu2?  2.17.2-0ubuntu2 works as well.

Where can I find this version?

Can't find it here:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/](http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/)

---

### Post by afv on 2009-07-11
> **wayne_cat said:**
> tested ... it works.

afv .. I saw the update in the bug report #398008 ... thank you!

You're welcome. :)


> **TerminX said:**
> Why downgrade all the way to 2.16.1-0ubuntu2?  2.17.2-0ubuntu2 works as well.

Because I looked at [http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/](http://mirrors.kernel.org/ubuntu/pool/main/g/gtk+2.0/) and the 2.17.3-0ubuntu1 version was the only before 2.16.1-0ubuntu2 that I found there. :)

Thanks for the information about that. Will add that to the bug page.

---

