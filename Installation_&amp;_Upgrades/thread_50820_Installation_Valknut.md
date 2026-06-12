---
title: "Installation Valknut"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by Bunz on 2005-07-21
Hi,

I tried to install Valknut on my Ubuntu installation but i keep getting errors while i'm installing.
./configure
make (here it goes wrong) 
make[3]: Entering directory `/home/jan/valknut-0.3.7/valknut'
/bin/sh ../libtool --silent --mode=link --tag=CXX g++ -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -I/usr/local/include -I/usr/include/libxml2  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o valknut -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/local/lib -ldc   -L/usr/lib -lxml2 -lz -lpthread -lm -ldl -lpthread  dciconloader.o dcdebug.o dceditserver.o dcapplicationevents.o dcevent.o dcedittransfer.o dcpluginmanager.o dcfilebrowser.o dcuserslist.o dctranslator.o dcspy.o dchubfilter.o dchubprofile.o dcfiletransferinfo.o dcmenuhandler.o dcsplash.o dcchat.o dcfiletool.o dchubsearch.o dcconfig.o dcoptions.o main.o dctransferview.o dchublistmanager.o dcconnectionmanager.o dcgui.o dcgeturl.o dcclient.o dcupdatemanager.o dcedittransfer.moc.o dchubprofile.moc.o dcapplicationevents.moc.o dcfiletransferinfo.moc.o dcchat.moc.o dcfiletool.moc.o dcclient.moc.o dcupdatemanager.moc.o dchublistmanager.moc.o dcspy.moc.o dcconnectionmanager.moc.o dceditserver.moc.o dcuserslist.moc.o dchubsearch.moc.o dctransferview.moc.o dcdebug.moc.o dcgui.moc.o dctranslator.moc.o dcgeturl.moc.o dchubfilter.moc.o dcfilebrowser.moc.o dcoptions.moc.o dcsplash.moc.o  ui/libui.la -L/usr/lib -lxml2 -lz -lpthread -lm -lqt-mt  -lz -lpng -lz -lm -lXext -lX11  -lSM -lICE -lpthread    -lbz2
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status
make[3]: *** [valknut] Error 1
make[3]: Leaving directory `/home/jan/valknut-0.3.7/valknut'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jan/valknut-0.3.7/valknut'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jan/valknut-0.3.7'
make: *** [all] Error 2

I searched on google and the only thing i found was that i needed to install opensll libraries, so i did. Same error still occur.

thx in advance

Bunz

---

