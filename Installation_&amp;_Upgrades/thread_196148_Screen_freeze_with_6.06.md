---
title: "Screen freeze with 6.06"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by ekici on 2006-06-13
Hi all,
After the upgrade to 6.06, I can not use dapper because of the freeze. GDM or KDM does not matter keep freezing and only exit is the hard shut down. If I try use the old version 5.10, fortunately I can use GDM. However KDM crashes repeatedly giving the following signal: SIGABRT Signal 6. Tried to get the backtrace for the KDM repeated crash (could not get any info about the freeze bug, as the name implies...:)):

--------------------------------------------------------------------------------
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231456576 (LWP 13417)]
[New Thread -1245094992 (LWP 13424)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e1f0c1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6e76a25 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#3  0xb6eea8b7 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#4  0xb6eea7da in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#5  0xb6ed08d5 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#6  0xb7f9b450 in kdemain () from /usr/lib/libkdeinit_kded.so
#7  0xb7d71ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#8  0x080483b1 in ?? ()

---

