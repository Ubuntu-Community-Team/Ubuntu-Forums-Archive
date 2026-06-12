---
title: "amaroK Won't Load!"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by adamsbryce1495 on 2010-07-20
I have a fresh install Ubuntu 10.04. I installed amaroK about a week ago, but it had nothing in it so i just quit it. now, it puts the amaroK SplashScreen up and i can see underneath it is the KDE Wallet or something like that. but i can't see it. so i just guessed and just typed my password and hit enter. it went away, but amaroK splash is still there, and always on top of all other windows. i do task killer from panel and it gets rid of splash, but then it wont start again. help please would be much appriciated.

---

### Post by Sonsum on 2010-07-20
Did you try running Amarok from the terminal? That should show any error messages you may be getting.

---

### Post by adamsbryce1495 on 2010-07-20
This is what i got from simply writing "amarok" in terminal. apperently something is wrong. but i dunno how to fix this at all.

kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kbuildsycoca4(1562) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(1562) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(1562) kdemain: Emitting notifyDatabaseChanged ()
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kglobalaccel(1580) GlobalShortcutsRegistry::loadSettings: Loading group  "amarok"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+A" for "amarok" : "playlist_add"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "playlist_add" : Failed to register  "Meta+A"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift++" for "amarok" : "seek_forward"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+-" for "amarok" : "seek_backward"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Media Previous" for "amarok" : "prev"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "prev" : Failed to register  "Media Previous"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Media Next" for "amarok" : "next"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "next" : Failed to register  "Media Next"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta++" for "amarok" : "increaseVolume"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+-" for "amarok" : "decreaseVolume"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+P" for "amarok" : "toggleMainWindow"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+O" for "amarok" : "showNotificationPopup"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+M" for "amarok" : "mute"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "mute" : Failed to register  "Meta+M"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+L" for "amarok" : "loveTrack"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+S" for "amarok" : "skipTrack"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "skipTrack" : Failed to register  "Meta+S"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+1" for "amarok" : "rate1"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+2" for "amarok" : "rate2"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+3" for "amarok" : "rate3"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+4" for "amarok" : "rate4"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+5" for "amarok" : "rate5"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Media Stop" for "amarok" : "stop"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "stop" : Failed to register  "Media Stop"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Meta+Shift+V" for "amarok" : "stop_after_current"
kglobalaccel(1580) GlobalShortcutsRegistry::registerKey: Registering key "Media Play" for "amarok" : "play_pause"
kglobalaccel(1580) KGlobalAccelImpl::grabKey: grab failed!
kglobalaccel(1580) GlobalShortcut::setActive: "play_pause" : Failed to register  "Media Play"
amarok(1551)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(1551)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(1551)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
QGraphicsLinearLayout::removeAt: invalid index 1
amarok(1551)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(1551)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
role  0  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
role  1  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QIcon, ) ,  QVariant(QIcon, ) )  ) 
role  3  : ( QVariantList ) :  QVariant(QVariantList, (QVariant(QString, "Playlist Files on Disk") ,  QVariant(QString, "Internal Database") )  ) 
QMap((0, QMap((0, QVariant(QString, "Playlist Files on Disk") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Playlist Files on Disk") ) )  ) )  
Creating empty group:  "Playlist Files on Disk" 
QMap((0, QMap((0, QVariant(QString, "Internal Database") ) ( 1 ,  QVariant(QIcon, ) ) ( 3 ,  QVariant(QString, "Internal Database") ) )  ) )  
Creating empty group:  "Internal Database" 
QMap() 
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kwalletd.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kwalletd(1585) KWalletD::setupDialog: Application ' "Amarok" ' using kwallet without parent window! 
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
bryce@inspiron600m:~$ QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setCompositionMode: Painter not active
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::save: Painter not active
QPainter::fillPath: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::translate: Painter not active
QPainter::setPen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::fillPath: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::setClipRegion: Painter not active
QPainter::save: Painter not active
QPainter::translate: Painter not active
QPainter::save: Painter not active
QPainter::pen: Painter not active
QPainter::setPen: Painter not active
QPainter::pen: Painter not active
QPainter::setPen: Painter not active
QPainter::setPen: Painter not active
QPainter::setPen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::restore: Unbalanced save/restore
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::save: Painter not active
QPainter::setPen: Painter not active
QPainter::translate: Painter not active
QPainter::pen: Painter not active
QPainter::restore: Unbalanced save/restore
QPainter::end: Painter not active, aborted

---

