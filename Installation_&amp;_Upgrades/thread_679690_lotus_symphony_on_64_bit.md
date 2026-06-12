---
title: "lotus symphony on 64 bit"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by zpon on 2008-01-27
Hi

I am trying to install lotus symphony on ubuntu hardy (64 bit) but i get the following error when i run ./IBM_Lotus_Symphony_linux.bin

```

          Launching InstallShield Wizard........

[...]

Locking assertion failure.  Backtrace:
#0 /usr/lib32/libxcb-xlib.so.0 [0xd7ed4767]
#1 /usr/lib32/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xd7ed48b1]
#2 /usr/lib32/libX11.so.6(_XReply+0xfd) [0xd77d729d]
#3 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/xawt/libmawt.so(XineramaQueryScreens+0x91) [0xd78cdca1]
#4 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/xawt/libmawt.so(xineramaInit+0x58) [0xd78b7cc8]
#5 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/xawt/libmawt.so(awt_init_Display+0xe1) [0xd78b7e01]
#6 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libj9vm23.so [0xf7ced389]
#7 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_J9VMInternals_initializeImpl+0x7e) [0xf7767a3a]
#8 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_Class_forNameImpl+0x2be) [0xf776fe86]
#9 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_J9VMInternals_initializeImpl+0x7e) [0xf7767a3a]
#10 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libjclscar_23.so(java_lang_Class_forNameImpl+0x2be) [0xf776fe86]
#11 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libj9vm23.so [0xf7d1984c]
#12 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libj9prt23.so [0xf7ccbcfa]
#13 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libj9vm23.so [0xf7d18151]
#14 /tmp/istemp18320027150845/_bundledJRE_/jre/bin/libj9thr23.so [0xf7f1cd93]
#15 /lib32/libpthread.so.0 [0xf7f024fb]
#16 /lib32/libc.so.6(clone+0x5e) [0xf7e69b1e]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
JVMDUMP006I Processing Dump Event "abort", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/tmp/symphony.tmp182901201442895/core.20080127.151004.18876.dmp'
JVMDUMP010I System Dump written to /tmp/symphony.tmp182901201442895/core.20080127.151004.18876.dmp
JVMDUMP007I JVM Requesting Snap Dump using '/tmp/symphony.tmp182901201442895/Snap0001.20080127.151004.18876.trc'
JVMDUMP010I Snap Dump written to /tmp/symphony.tmp182901201442895/Snap0001.20080127.151004.18876.trc
JVMDUMP007I JVM Requesting Java Dump using '/tmp/symphony.tmp182901201442895/javacore.20080127.151004.18876.txt'
JVMDUMP010I Java Dump written to /tmp/symphony.tmp182901201442895/javacore.20080127.151004.18876.txt
JVMDUMP013I Processed Dump Event "abort", detail "".
Aborted (core dumped)

```

Anybody know what is wrong?

---

