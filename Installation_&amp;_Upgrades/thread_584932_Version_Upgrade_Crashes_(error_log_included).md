---
title: "Version Upgrade Crashes (error log included)"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by sveden on 2007-10-21
After having my install break and crash twice and cleaning up and trying again, the last time I tried a version upgrade using Adpet it crashed and gave  me this msg. Any ideas on how to proceed?

I'm upgrading from Kubuntu 7.04 to 7.10,

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1236117296 (LWP 2094)]
[KCrash handler]
#6  0x08144f83 in ?? ()
#7  0x081453bc in ?? ()
#8  0xb718fd68 in QWizard::qt_invoke () from /usr/lib/libqt-mt.so.3
#9  0xb770ff7b in KWizard::qt_invoke () from /usr/lib/libkdeui.so.4
#10 0x0814afba in ?? ()
#11 0x081468b3 in ?? ()
#12 0xb6dd0893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#13 0xb6dd1338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#14 0xb7165907 in QButton::clicked () from /usr/lib/libqt-mt.so.3
#15 0xb6e6ef8c in QButton::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#16 0xb6e07681 in QWidget::event () from /usr/lib/libqt-mt.so.3
#17 0xb6d67af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#18 0xb6d69cae in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0xb752dca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#20 0xb6cfa27d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0xb6cf8ee2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#22 0xb6cf6fcc in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#23 0xb6d0e1a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#24 0xb6d821ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#25 0xb6d81fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#26 0xb6d69699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#27 0x0806f75e in ?? ()
#28 0xb656c050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#29 0x0806f401 in ?? ()
```

---

