---
title: "cockatrice... linux compile error in zoneviewwidget.cpp"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by joshcanfield on 2011-11-21
I am trying to Install cockatrice and have run in to this problem can any body tell me what I should do?

here Is what I have Done so far...

joshua@joshua-laptop:~$ cd Downloads/cockatrice*
joshua@joshua-laptop:~/Downloads/cockatrice$ cd cockatrice
joshua@joshua-laptop:~/Downloads/cockatrice/cockatrice$ lrelease translations/*.ts && qmake && make
Updating 'translations/cockatrice_cs.qm'...
    Generated 639 translation(s) (504 finished and 135 unfinished)

    Ignored 93 untranslated source text(s)
Updating 'translations/cockatrice_de.qm'...
    Generated 722 translation(s) (721 finished and 1 unfinished)

    Ignored 10 untranslated source text(s)
Updating 'translations/cockatrice_en.qm'...
    Generated 7 translation(s) (1 finished and 6 unfinished)

    Ignored 725 untranslated source text(s)
Updating 'translations/cockatrice_es.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_fr.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_it.qm'...
    Generated 721 translation(s) (720 finished and 1 unfinished)

    Ignored 11 untranslated source text(s)
Updating 'translations/cockatrice_ja.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_pl.qm'...
    Generated 0 translation(s) (0 finished and 0 unfinished)

    Ignored 732 untranslated source text(s)
Updating 'translations/cockatrice_pt-br.qm'...
    Generated 629 translation(s) (487 finished and 142 unfinished)

    Ignored 103 untranslated source text(s)
Updating 'translations/cockatrice_pt.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_ru.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_sk.qm'...
    Generated 0 translation(s) (0 finished and 0 unfinished)

    Ignored 732 untranslated source text(s)
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/abstractcounter.o src/abstractcounter.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/counter_general.o src/counter_general.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/dlg_creategame.o src/dlg_creategame.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/dlg_connect.o src/dlg_connect.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/dlg_create_token.o src/dlg_create_token.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/abstractclient.o src/abstractclient.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/remoteclient.o src/remoteclient.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/main.o src/main.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/window_main.o src/window_main.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/gamesmodel.o src/gamesmodel.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/player.o src/player.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/playertarget.o src/playertarget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/cardzone.o src/cardzone.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/selectzone.o src/selectzone.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/cardlist.o src/cardlist.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/abstractcarditem.o src/abstractcarditem.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/carditem.o src/carditem.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/tablezone.o src/tablezone.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/handzone.o src/handzone.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/handcounter.o src/handcounter.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/carddatabase.o src/carddatabase.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/gameview.o src/gameview.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/gameselector.o src/gameselector.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/decklistmodel.o src/decklistmodel.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/dlg_load_deck_from_clipboard.o src/dlg_load_deck_from_clipboard.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/dlg_load_remote_deck.o src/dlg_load_remote_deck.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/cardinfowidget.o src/cardinfowidget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/messagelogwidget.o src/messagelogwidget.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/zoneviewzone.o src/zoneviewzone.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/zoneviewwidget.o src/zoneviewwidget.cpp
src/zoneviewwidget.cpp: In constructor ‘ZoneViewWidget::ZoneViewWidget(Player*, CardZone*, int, bool, const QList<ServerInfo_Card*>&)’:
src/zoneviewwidget.cpp:63: error: ‘setAutoFillBackground’ was not declared in this scope
make: *** [build/zoneviewwidget.o] Error 1
joshua@joshua-laptop:~/Downloads/cockatrice/cockatrice$ 


well any suggestions?

---

