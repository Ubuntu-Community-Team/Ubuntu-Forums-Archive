---
title: "Recent update to libglib and libsoup render hardy near unusable"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by NickEvans on 2008-08-10
Hey,
I noticed my computer was extremely sluggish today, and wondered what was going on. I checked /var/log/apt/term.log and looked for the last update. This is what it was.

> Log started: 2008-08-09  10:28:08
(Reading database ... 179460 files and directories currently installed.)

Preparing to replace libglib2.0-dev 2.16.4-0ubuntu2 (using .../libglib2.0-dev_2.16.4-0ubuntu3_i386.deb) ...

Unpacking replacement libglib2.0-dev ...

Preparing to replace libglib2.0-0 2.16.4-0ubuntu2 (using .../libglib2.0-0_2.16.4-0ubuntu3_i386.deb) ...

Unpacking replacement libglib2.0-0 ...

Preparing to replace deskbar-applet 2.22.3-0ubuntu1 (using .../deskbar-applet_2.22.3.1-0ubuntu1_i386.deb) ...

Unpacking replacement deskbar-applet ...

Preparing to replace libsoup2.4-dev 2.4.1-1 (using .../libsoup2.4-dev_2.4.1-1ubuntu1_i386.deb) ...

Unpacking replacement libsoup2.4-dev ...

Preparing to replace libsoup2.4-1 2.4.1-1 (using .../libsoup2.4-1_2.4.1-1ubuntu1_i386.deb) ...

Unpacking replacement libsoup2.4-1 ...

Setting up libglib2.0-0 (2.16.4-0ubuntu3) ...



Setting up libglib2.0-dev (2.16.4-0ubuntu3) ...

Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...



Setting up libsoup2.4-1 (2.4.1-1ubuntu1) ...



Setting up libsoup2.4-dev (2.4.1-1ubuntu1) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Log ended: 2008-08-09  10:28:51

I downgraded them all back to the previous version and it seemed to cure the problem. This is a good temporary fix, but now it's nagging me to update these packages. Hardy was near unusable after it updated. Everything took much longer to open, and the computer would seem to freeze on occasion. Applications would freeze up when they tried to do something big. I'm sort of a newb to bug reporting, so I was wondering if you guys could point me in the right direction. It doesn't seem to be a common problem, as no one else is reporting any sluggishness.

By the way, I didn't downgrade deskbar, only glib and libsoup. I needed to downgrade libsoup with libglib or else it would have uninstalled several important dependent packages. I'm not sure which is the culprit.

Please, tell me if I missed any information. Like I said, I'm new to bug reporting.

---

### Post by mauricebis on 2009-09-23
Hi,
From your post, I could read you downgraded the version of glib to run on hardy. 

I have a problem a bit similar, gnome won't load because it fails to find a reference to g-thread-gettime in the libgio-2.0.so.0.0.0 library. Running ldd, I see that this library references /usr/local/local/libglib-2.0.so.0 which points to /usr/local/lib/libglib-2.0.so.1200.0.

I guess the problem is in this latter library since I installed (stupidly) a new version of glib.

How could I manage to reinstall the good old glib library for Hardy? Which version is it? I could then possibly modify manually the previous links to point to the old library since I understand ldconfig favours the newer version. Just to mention that I have to work at the recovery command prompt since Gnome and synaptic are not running.

If you've time to answer me, I'd be very grateful since I'm not very knowledgeable in Linux administration.

Thanks. Mauricebis.

---

