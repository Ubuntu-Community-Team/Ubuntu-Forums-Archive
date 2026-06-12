---
title: "X wont start"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by infornography on 2007-04-22
I just downloaded new Ubuntu. Just like the previous two versions, it wont install on either of my machines. It's a fine distro when it installs, but I seem to have no end of problems installing it.

The machine I want it on is a Dell inspiron E1505 laptop. It has an ATI Mobility Radeon 1400 graphics card. Anyway when GDM tries to start, X fails and it asks me if I would like to see a log to diagnose the problem. The log says nothing I can understand, so hopefully someone here can...

Backtrace:

0: /usr/X11R6/bin/X(xf86SigHand ler+0x81) [x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main+0x27b) [0x7456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7db8ebc]
5: /usr/X11R6/bin/X(FrontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11. Server aborting

---

### Post by 4ebees on 2007-04-22
Hi there,

This may or may not be of assistance :)

When you are thrown back to the terminal, try:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original

then enter your root user password. 

This will create a copy of your existing xorg.conf file.

Then run:

sudo dpkg-reconfigure xserver-xorg

then enter your root user password and follow the prompts provided.

This will allow you to manually set up xorg. I would stay clear of modifying the vertical and horizontal frequencies unless you have the manual for your monitor.

I've been able to get some machines up and running this way.

I hope this helps.

Regards,
4ebees

> **infornography said:**
> I just downloaded new Ubuntu. Just like the previous two versions, it wont install on either of my machines. It's a fine distro when it installs, but I seem to have no end of problems installing it.

The machine I want it on is a Dell inspiron E1505 laptop. It has an ATI Mobility Radeon 1400 graphics card. Anyway when GDM tries to start, X fails and it asks me if I would like to see a log to diagnose the problem. The log says nothing I can understand, so hopefully someone here can...

Backtrace:

0: /usr/X11R6/bin/X(xf86SigHand ler+0x81) [x80c5d91]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X(main+0x27b) [0x7456b]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7db8ebc]
5: /usr/X11R6/bin/X(FrontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11. Server aborting

---

