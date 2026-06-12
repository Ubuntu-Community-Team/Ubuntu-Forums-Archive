---
title: "fix broken feisty install"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by cliowa on 2007-05-28
I recently resized my system partition using the GParted LiveCD, where everything worked well (no errors whatsoever). Then I did a dist-upgrade in kubuntu using adept, upgrading from 6.10 to 7.04. In the middle of the process (downloading and installing), there appeared an error message window without any text. Then I had to shut it down, as there was no reaction from the upgrading programme.

Now I cannot boot with any kernel, not even the old ones, not even in recovery mode. I then started ubuntu 6.10 with a live cd, reconfigured everything, tried doing apt-get -f install and also tried following this tutorial on fixing a broken os: [Fix a broken Ubuntu Feisty]("http://onlyubuntu.blogspot.com/2007/03/how-to-fix-broken-ubuntu-feisty-fawn.html").
None of the operations in involving apt-get work: It always tells me there are unmet dependencies, then there comes a huge list of errors and it says it terminated because of too many errors.

Can somebody help? Thank you in advance...Cliowa

Here is an extract of the text I get when doing apt-get dist-upgrade:
>  libpanel-applet2-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-menu2:
 libgnome-menu2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-menu2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gmenu:
 python-gmenu depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
dpkg: error processing python-gmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-menus depends on python-gmenu (= 2.18.0-0ubuntu3); however:
  Package python-gmenu is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-10:
 libcamel1.2-10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libcamel1.2-10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libcamel1.2-10 (>= 1.10.1); however:
  Package libcamel1.2-10 is not configured yet.
 libebook1.2-9 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-9 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 1.9.2); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslab0:
 libslab0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libslab0 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libslab0 depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 libslab0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libslab0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libslab0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libslab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libgnome-window-settings1 depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome-window-settings1 depends on libpanel-applet2-0 (>= 1:2.18.1); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-control-center depends on libebook1.2-9 (>= 1.10.1); however:
  Package libebook1.2-9 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 gnome-control-center depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-control-center depends on libgnomekbdui1; however:
  Package libgnomekbdui1 is not configured yet.
 gnome-control-center depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-control-center depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-control-center depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
 gnome-control-center depends on libpanel-applet2-0 (>= 1:2.18.1); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-control-center depends on libslab0; however:
  Package libslab0 is not configured yet.
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.18.1-0ubuntu2.1); however:
  Package libgnome-window-settings1 is not configured yet.
 gnome-control-center depends on gnome-menus (>= 2.17.5); however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-about depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libebook1.2-9 (>= 1.10.1); however:
  Package libebook1.2-9 is not configured yet.
 gnome-panel depends on libecal1.2-7 (>= 1.10.1); however:
  Package libecal1.2-7 is not configured yet.
 gnome-panel depends on libedataserverui1.2-8 (>= 1.10.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 gnome-panel depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-panel depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
 gnome-panel depends on libpanel-applet2-0 (>= 1:2.18.1); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on gnome-menus (>= 2.11.1-1); however:
  Package gnome-menus is not configured yet.
 gnome-panel depends on gnome-about (>= 2.10.0-1); however:
  Package gnome-about is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-applets depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-applets depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-applets depends on libgnomekbdui1; however:
  Package libgnomekbdui1 is not configured yet.
 gnome-applets depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-applets depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-applets depends on libgucharmap6; however:
  Package libgucharmap6 is not configured yet.
 gnome-applets depends on libpanel-applet2-0 (>= 2.17.92); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 yelp depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 yelp depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
Setting up at (3.1.10ubuntu4) ...
invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on python-gnome2 (>= 2.6); however:
  Package python-gnome2 is not configured yet.
 alacarte depends on gnome-menus (>= 2.15.4.1); however:
  Package gnome-menus is not configured yet.
 alacarte depends on python-gmenu (>= 2.15.4.1); however:
  Package python-gmenu is not configured yet.
 alacarte depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing bluez-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-pcmcia-support:
 bluez-pcmcia-support depends on bluez-utils (= 3.9-0ubuntu4); however:
  Package bluez-utils is not configured yet.
dpkg: error processing bluez-pcmcia-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on libebook1.2-9 (>= 1.10.0); however:
  Package libebook1.2-9 is not configured yet.
 bug-buddy depends on libgnome-menu2 (>= 2.15.4); however:
  Package libgnome-menu2 is not configured yet.
 bug-buddy depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 bug-buddy depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 bug-buddy depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of contact-lookup-applet:
 contact-lookup-applet depends on libebook1.2-9 (>= 1.9.92); however:
  Package libebook1.2-9 is not configured yet.
 contact-lookup-applet depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 contact-lookup-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 contact-lookup-applet depends on libpanel-applet2-0 (>= 2.17.92); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing contact-lookup-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-1-utils:
 dbus-1-utils depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-1-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser1:
 libtotem-plparser1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.18.0); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser1 (>= 2.17.5); however:
  Package libtotem-plparser1 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-extras depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-extras depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-9 (>= 1.10.1); however:
  Package libebook1.2-9 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
 deskbar-applet depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dhcdbd:
 dhcdbd depends on dbus (>= 0.60); however:
  Package dbus is not configured yet.
dpkg: error processing dhcdbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-9 (>= 1.9.2); however:
  Package libebook1.2-9 is not configured yet.
 libedata-book1.2-2 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libecal1.2-7 (>= 1.9.2); however:
  Package libecal1.2-7 is not configured yet.
 libedata-cal1.2-6 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libcamel1.2-10 (>= 1.10.1); however:
  Package libcamel1.2-10 is not configured yet.
 evolution-data-server depends on libebook1.2-9 (>= 1.9.2); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 1.9.2); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 1.9.2); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 1.9.2); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 ekiga depends on libebook1.2-9 (>= 1.10.0); however:
  Package libebook1.2-9 is not configured yet.
 ekiga depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 ekiga depends on evolution-data-server; however:
  Package evolution-data-server is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 eog depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.17.90); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.14.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome-desktop-2
 libgnomekbdui1
 libgucharmap6
 libpanel-applet2-0
 libgnome-menu2
 python-gmenu
 gnome-menus
 libcamel1.2-10
 libebook1.2-9
 libecal1.2-7
 libedataserverui1.2-8
 liblpint-bonobo0
 libnautilus-extension1
 libslab0
 libgnome-window-settings1
 gnome-control-center
 gnome-about
 gnome-panel
 gnome-applets
 yelp
 gnome-user-guide
 ubuntu-docs
 at
 ubuntu-standard
 python-gnome2
 alacarte
 avahi-daemon
 bluez-utils
 bluez-pcmcia-support
 bug-buddy
 contact-lookup-applet
 dbus-1-utils
 libtotem-plparser1
 python-gnome2-desktop
 python-gnome2-extras
 deskbar-applet
 dhcdbd
 libedata-book1.2-2
 libedata-cal1.2-6
 evolution-data-server
 ekiga
 eog
 evince
 libexchange-storage1.2-3
 libgtkhtml3.14-19
 gtkhtml3.14
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

