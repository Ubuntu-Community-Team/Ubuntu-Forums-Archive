---
title: "64bit Karmic beta - PolicyKit-KDE crashing...endlessly"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by punchdrunkgrunt on 2009-10-26
This is driving me up the wall. Every 5 minutes, without fail, it launches two instances of polkit-kde-manager which immediately crash and popup two identical crash reports on my desktop. I left my computer alone for about an hour and a half and when I came back I had to close 24 crash reports.
FYI the report looks like this:

> Application: PolicyKit-KDE (polkit-kde-manager), signal: Aborted
[KCrash Handler]
#5  0x00007f021e4324b5 in *__GI_raise (sig=<value optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
#6  0x00007f021e435f50 in *__GI_abort () at abort.c:92
#7  0x00007f021e46ac97 in __libc_message (do_abort=<value optimized out>, fmt=<value optimized out>) at ../sysdeps/unix/sysv/linux/libc_fatal.c:189
#8  0x00007f021e474dd6 in malloc_printerr (action=3, str=0x7f021e5366a8 "double free or corruption (fasttop)", ptr=<value optimized out>) at malloc.c:6217
#9  0x00007f021e47970c in *__GI___libc_free (mem=<value optimized out>) at malloc.c:3716
#10 0x00007f0220170056 in PolkitQt::Context::Private::init() () from /usr/lib/libpolkit-qt-core.so.0
#11 0x00007f0220171b2d in PolkitQt::Context::hasError() const () from /usr/lib/libpolkit-qt-core.so.0
#12 0x000000000040ffce in _start ()

Karmic beta has been OK up until an update a couple of days back when this started happening. I've filed a bug report which has been merged with an older bug that doesn't exactly fit the circumstances of this problem (
[https://bugs.kde.org/show_bug.cgi?id=200953]("https://bugs.kde.org/show_bug.cgi?id=200953")).

Can somebody please tell me if there's a way to
a) stop it crashing OR
b) stop it launching in the first place OR
c) stop these annoying popups from telling me about it crashing

TIA

---

