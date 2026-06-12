---
title: "Kamefu"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Sprocket_dk on 2008-02-24
Hi when i try to load my collection of games, kamefu crashes. Does anyone know how to fix it? It leaves me following backtrace:
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
[Thread debugging using libthread_db enabled]
[New Thread -1239329088 (LWP 7222)]
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
[KCrash handler]
#6  0xb77a785c in KFileMetaInfo::preferredGroups () from /usr/lib/libkio.so.4
#7  0xb77a7e79 in KFileMetaInfo::item () from /usr/lib/libkio.so.4
#8  0xb7f3693a in Kamefu::DefaultRomMetaData::extractMetaInformation ()
   from /usr/lib/libkamefu.so.0
#9  0xb6038240 in NesRomMetaData::extractMetaInformation ()
   from /usr/lib/kde3/kamefu_nes.so
#10 0xb7f24029 in Kamefu::CollectionBuilder::slotInsertItems ()
   from /usr/lib/libkamefu.so.0
#11 0xb7f24105 in Kamefu::CollectionBuilder::slotListingComplete ()
   from /usr/lib/libkamefu.so.0
#12 0xb7f2474a in Kamefu::CollectionBuilder::qt_invoke ()
   from /usr/lib/libkamefu.so.0
#13 0xb6ac1893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#14 0xb6ac2338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb77766fc in KDirLister::completed () from /usr/lib/libkio.so.4
#16 0xb77946c4 in KDirListerCache::slotResult () from /usr/lib/libkio.so.4
#17 0xb77c6e37 in KDirListerCache::qt_invoke () from /usr/lib/libkio.so.4
#18 0xb6ac1893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#19 0xb76f1021 in KIO::Job::result () from /usr/lib/libkio.so.4
#20 0xb77498cd in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#21 0xb7749d2e in KIO::SimpleJob::slotFinished () from /usr/lib/libkio.so.4
#22 0xb774a0ad in KIO::ListJob::slotFinished () from /usr/lib/libkio.so.4
#23 0xb7755a7e in KIO::ListJob::qt_invoke () from /usr/lib/libkio.so.4
#24 0xb6ac1893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#25 0xb6ac2338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#26 0xb76ecd2c in KIO::SlaveInterface::finished () from /usr/lib/libkio.so.4
#27 0xb774cb60 in KIO::SlaveInterface::dispatch () from /usr/lib/libkio.so.4
#28 0xb773b44a in KIO::SlaveInterface::dispatch () from /usr/lib/libkio.so.4
#29 0xb770266c in KIO::Slave::gotInput () from /usr/lib/libkio.so.4
#30 0xb7733f60 in KIO::Slave::qt_invoke () from /usr/lib/libkio.so.4
#31 0xb6ac1893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#32 0xb6ac21aa in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#33 0xb6e4e683 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#34 0xb6ae446e in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#35 0xb6a58af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#36 0xb6a5a91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#37 0xb721ecd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#38 0xb69eb209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#39 0xb6a4aee9 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#40 0xb69ffd2b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#41 0xb6a731ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#42 0xb6a72fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#43 0xb6a5a699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#44 0x0805cc6c in ?? ()
#45 0xbfd8ff90 in ?? ()
#46 0x00000000 in ?? ()

---

