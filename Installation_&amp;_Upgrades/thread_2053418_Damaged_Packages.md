---
title: "Damaged Packages"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by auraithx on 2012-09-05
I installed 12.04 a few weeks ago, all seemed to be working fine until this morning when my site when down. I restarted my VPS to try and kick it back into action. There is something wrong with my MySQL installation. I've spent all morning on forums/IRC trying to sort it to no avail. 

Here's what happens when I try and run sudo apt-get -f install
```
 libpoppler19 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libpoppler19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgs9:
 libgs9 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libgs9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-filters:
 cups-filters depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 cups-filters depends oNo apport report written because the error message indicates it's a follow-up error from a previous failure.
   No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                               No apport report written because MaxReports has already been reached
                                                   No apport report written because MaxReports has already been reached
                                                                                                                       No apport report written because MaxReports has already been reached
                                                           No apport report written because MaxReports has already been reached
                                                                                                                               No apport report written because MaxReports has already been reached
                                                                   No apport report written because MaxReports has already been reached
       No apport report written because MaxReports has already been reached
                                                                           No apport report written because MaxReports has already been reached
               No apport report written because MaxReports has already been reached
                                                                                   No apport report written because MaxReports has already been reached
                       No apport report written because MaxReports has already been reached
                                                                                           No apport report written because MaxReports has already been reached
                               n libpoppler19; however:
  Package libpoppler19 is not configured yet.
dpkg: error processing cups-filters (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libcairo2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of poppler-utils:
 poppler-utils depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
 poppler-utils depends on libpoppler19; however:
  Package libpoppler19 is not configured yet.
dpkg: error processing poppler-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on poppler-utils (>= 0.12); however:
  Package poppler-utils is not configured yet.
 cups depends on cups-filters; however:
  Package cups-filters isNo apport report written because MaxReports has already been reached
                                                                                             No apport report written because MaxReports has already been reached
                                 No apport report written because MaxReports has already been reached
                                                                                                     No apport report written because MaxReports has already been reached
                                         No apport report written because MaxReports has already been reached
                                                                                                             No apport report written because MaxReports has already been reached
                                                 No apport report written because MaxReports has already been reached
                                                                                                                     No apport report written because MaxReports has already been reached
                                                         No apport report written because MaxReports has already been reached
                                                                                                                             No apport report written because MaxReports has already been reached
                                                                 No apport report written because MaxReports has already been reached
     No apport report written because MaxReports has already been reached
                                                                         No apport report written because MaxReports has already been reached
              not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo-gobject2:
 libcairo-gobject2 depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
dpkg: error processing libcairo-gobject2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft2:
 libxft2 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libxft2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fontconfig:
 fontconfig depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 fontconfig depends on fontconfig-config; however:
  Package fontconfig-config is not configured yet.
dpkg: error processing fontconfig (--configure):
 dependency problems - leaving unconfigured
dpNo apport report written because MaxReports has already been reached
                                                                      No apport report written because MaxReports has already been reached
          No apport report written because MaxReports has already been reached
                                                                              kg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libcairo2 (>= 1.8.10-3); however:
  Package libcairo2 is not configured yet.
 libpango1.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libpango1.0-0 depends on libxft2 (>> 2.1.1); however:
  Package libxft2 is not configured yet.
 libpango1.0-0 depends on fontconfig (>= 2.1.91); however:
  Package fontconfig is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-2:
 librsvg2-2 depends on libcairo2 (>= 1.2.4); however:
  Package libcairo2 is not configured yet.
 librsvg2-2 depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing librsvg2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libcairo2 (>= 1.6.4-6.1); however:
  Package libcairo2 is not configured yet.
 libgtk2.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libgtk2.0-0 depends on libpango1.0-0 (>= 1.28.3); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-common:
 librsvg2-common depends on libgtk2.0-0 (>= 2.21.5); however:
  Package libgtk2.0-0 is not configured yet.
 librsvg2-common depends on librsvg2-2 (= 2.36.1-0ubuntu1); however:
  Package librsvg2-2 is not configured yet.
dpkg: error processing librsvg2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-gtk0:
 libcanberra-gtk0 depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libcanberra-gtk0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on libcairo-gobject2 (>= 1.10.0); however:
  Package libcairo-gobject2 is not configured yet.
 libgtk-3-0 depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
 libgtk-3-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libgtk-3-0 depends on libpango1.0-0 (>= 1.30.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-gtk3-0:
 libcanberra-gtk3-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libcanberra-gtk3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-gtk3-4:
 libdbusmenu-gtk3-4 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libdbusmenu-gtk3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on fontconfig; however:
  Package fontconfig is not configured yet.
 libqtgui4 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-qt2:
 libdbusmenu-qt2 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libdbusmenu-qt2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:
 libgail-3-0 depends on libgtk-3-0 (= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
 libgail-3-0 depends on libpango1.0-0 (>= 1.30.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgail-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgd2-xpm:
 libgd2-xpm depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libgd2-xpm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
 libwebkitgtk-3.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgail-3-0 (>= 3.0.0); however:
  Package libgail-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
 libwebkitgtk-3.0-0 depends on libpango1.0-0 (>= 1.22.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgoa-1.0-0:
 libgoa-1.0-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libgoa-1.0-0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
 libgoa-1.0-0 depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
dpkg: error processing libgoa-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libcairo2 (>= 1.2.4); however:
  Package libcairo2 is not configured yet.
 libgtksourceview-3.0-0 depends on libgtk-3-0 (>= 3.4.0); however:
  Package libgtk-3-0 is not configured yet.
 libgtksourceview-3.0-0 depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libphonon4:
 libphonon4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libphonon4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-qt3support:
 libqt4-qt3support depends on libqt4-designer (= 4:4.8.1-0ubuntu4.2); however:
  Package libqt4-designer is not configured yet.
 libqt4-qt3support depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-qt3support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtwebkit4:
 libqtwebkit4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqtwebkit4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration-3.0-1:
 liblaunchpad-integration-3.0-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing liblaunchpad-integration-3.0-1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libpeas-1.0-0:
 libpeas-1.0-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libpeas-1.0-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gir1.2-pango-1.0:
 gir1.2-pango-1.0 depends on libpango1.0-0 (>= 1.29.4); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing gir1.2-pango-1.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on gir1.2-pango-1.0; however:
  Package gir1.2-pango-1.0 is not configured yet.
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.3.18); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: dependency problems prevent configuration of gir1.2-gtksource-3.0:
 gir1.2-gtksource-3.0 depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-gtksource-3.0 depends on gir1.2-pango-1.0; however:
  Package gir1.2-pango-1.0 is not configured yet.
 gir1.2-gtksource-3.0 depends on libgtksourceview-3.0-0 (>= 3.3.4); however:
  Package libgtksourceview-3.0-0 is not configured yet.
dpkg: error processing gir1.2-gtksource-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-peas-1.0:
 gir1.2-peas-1.0 depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-peas-1.0 depends on gir1.2-pango-1.0; however:
  Package gir1.2-pango-1.0 is not configured yet.
 gir1.2-peas-1.0 depends on libpeas-1.0-0 (>= 1.1.0); however:
  Package libpeas-1.0-0 is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: error processing gir1.2-peas-1.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on libcairo2 (>= 1.2.4); however:
  Package libcairo2 is not configured yet.
 gedit depends on libgtk-3-0 (>= 3.3.15); however:
  Package libgtk-3-0 is not configured yet.
 gedit depends on libgtksourceview-3.0-0 (>= 3.0.0); however:
  Package libgtksourceview-3.0-0 is not configured yet.
 gedit depends on liblaunchpad-integration-3.0-1 (>= 0.1.17); however:
  Package liblaunchpad-integration-3.0-1 is not configured yet.
 gedit depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
 gedit depends on libpeas-1.0-0 (>= 1.1.0); however:
  Package libpeas-1.0-0 is not configured yet.
 gedit depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gedit depends on gir1.2-gtksource-3.0; however:
  Package gir1.2-gtksource-3.0 is not configured yet.
 gedit depends on gir1.2-pango-1.0; however:
  Package gir1.2-pango-1.0 is not configured yet.
 gedit depends on gir1.2-peas-1.0; however:
  Package gir1.2-peas-1.0 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libindicator3-7:
 libindicator3-7 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libindicator3-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libappindicator3-1:
 libappindicator3-1 depends on libdbusmenu-gtk3-4 (>= 0.4.2); however:
  Package libdbusmenu-gtk3-4 is not configured yet.
 libappindicator3-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libappindicator3-1 depends on libindicator3-7; however:
  Package libindicator3-7 is not configured yet.
dpkg: error processing libappindicator3-1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: dependency problems prevent configuration of libgnome-desktop-3-2:
 libgnome-desktop-3-2 depends on libcairo2 (>= 1.2.4); however:
  Package libcairo2 is not configured yet.
 libgnome-desktop-3-2 depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgnome-desktop-3-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomekbd7:
 libgnomekbd7 depends on libcairo2 (>= 1.2.4); however:
  Package libcairo2 is not configured yet.
 libgnomekbd7 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libgnomekbd7 depends on libpango1.0-0 (>= 1.22.0); however:
  Package libpango1.0-0 is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: error processing libgnomekbd7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libappindicator3-1 (>= 0.4.90); however:
  Package libappindicator3-1 is not configured yet.
 gnome-settings-daemon depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
 gnome-settings-daemon depends on libcanberra-gtk3-0 (>= 0.25); however:
  Package libcanberra-gtk3-0 is not configured yet.
 gnome-settings-daemon depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 gnome-settings-daemon depends on libgnome-desktop-3-2 (>= 3.3.4); however:
  Package libgnome-desktop-3-2 is not configured yet.
 gnome-settings-daemon depends on libgnomekbd7 (>= 2.91.90); however:
  Package libgnomekbd7 is not configured yet.
 gnome-settings-daemon depends on libgtk-3-0 (>= 3.3.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-control-center1:
 libgnome-control-center1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libgnome-control-center1 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libgnome-control-center1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: dependency problems prevent configuration of policykit-1-gnome:
 policykit-1-gnome depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing policykit-1-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnm-gtk0:
 libnm-gtk0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libnm-gtk0 depends on policykit-1-gnome; however:
  Package policykit-1-gnome is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
        dpkg: error processing libnm-gtk0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-icon-theme:
 gnome-icon-theme depends on libgtk-3-bin; however:
  Package libgtk-3-bin is not configured yet.
 gnome-icon-theme depends on librsvg2-common; however:
  Package librsvg2-common is not configured yet.
dpkg: error processing gnome-icon-theme (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-icon-theme-symbolic:
 gnome-icon-theme-symbolic depends on gnome-icon-theme (>= 3.4); however:
  Package gnome-icon-theme is not configured yet.
 gnome-icon-theme-symbolic depends on gnome-icon-theme (<< 3.5); however:
  Package gnome-icon-theme is not configured yet.
dpkg: error processing gnome-icon-theme-symbolic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libcairo2 (>= 1.10.0); however:
  Package libcairo2 is not configured yet.
 gnome-control-center depends on libcanberra-gtk3-0 (>= 0.25); however:
  Package libcanberra-gtk3-0 is not configured yet.
 gnome-control-center depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 gnome-control-center depends on libgnome-control-center1 (>= 1:3.3.5); however:
  Package libgnome-control-center1 is not configured yet.
 gnome-control-center depends on libgnome-desktop-3-2 (>= 3.2.0); however:
  Package libgnome-desktop-3-2 is not configured yet.
 gnome-control-center depends on libgnomekbd7 (>= 2.91.91); however:
  Package libgnomekbd7 is not configured yet.
 gnome-control-center depends on libgoa-1.0-0 (>= 3.1.1); however:
  Package libgoa-1.0-0 is not configured yet.
 gnome-control-center depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
 gnome-control-center depends on libnm-gtk0; however:
  Package libnm-gtk0 is not configured yet.
 gnome-control-center depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
 gnome-control-center depends on gnome-icon-theme (>= 2.24); however:
  Package gnome-icon-theme is not configured yet.
 gnome-control-center depends on gnome-icon-theme-symbolic; however:
  Package gnome-icon-theme-symbolic is not configured yet.
 gnome-control-center depends on gnome-settings-daemon (>= 3.3.91); however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1a:
 libnautilus-extension1a depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libnautilus-extension1a (--configure):
 dependency problems - leaving unconfigurNo apport report written because MaxReports has already been reached
                                                                                                             No apport report written because MaxReports has already been reached
                                                 ed
dpkg: too many errors, stopping
Errors were encountered while processing:
 fontconfig-config
 libfontconfig1
 libpoppler19
 libgs9
 cups-filters
 libcairo2
 poppler-utils
 cups
 libcairo-gobject2
 libxft2
 fontconfig
 libpango1.0-0
 librsvg2-2
 libgtk2.0-0
 librsvg2-common
 libcanberra-gtk0
 libgtk-3-0
 libcanberra-gtk3-0
 libdbusmenu-gtk3-4
 libqtgui4
 libdbusmenu-qt2
 libgail-3-0
 libgd2-xpm
 libwebkitgtk-3.0-0
 libgoa-1.0-0
 libgtksourceview-3.0-0
 libphonon4
 libqt4-designer
 libqt4-qt3support
 libqt4-svg
 libqtwebkit4
 liblaunchpad-integration-3.0-1
 libpeas-1.0-0
 gir1.2-pango-1.0
 gir1.2-gtk-3.0
 gir1.2-gtksource-3.0
 gir1.2-peas-1.0
 gedit
 libindicator3-7
 libappindicator3-1
 libgnome-desktop-3-2
 libgnomekbd7
 gnome-settings-daemon
 libgnome-control-center1
 policykit-1-gnome
 libnm-gtk0
 libgtk-3-bin
 gnome-icon-theme
 gnome-icon-theme-symbolic
 gnome-control-center
 libnautilus-extension1a
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server1:~# 

```

---

### Post by drmrgd on 2012-09-05
What happens if you run:

```
sudo dpkg --config -a
```

Seems that the installation can't continue because one of the packages in that meta package is not configured.  This may configure that one and allow the rest to behave.  Post back any errors you get.

---

### Post by auraithx on 2012-09-05
> **drmrgd said:**
> What happens if you run:
```
sudo dpkg --config -a
```

Seems that the installation can't continue because one of the packages in that meta package is not configured.  This may configure that one and allow the rest to behave.  Post back any errors you get.
Seems its not a valid command.

```
root@server1:~# sudo dpkg --config -a
dpkg: error: unknown option -o

Type dpkg --help for help about installing and un-installing packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by SlugSlug on 2012-09-05
its --config not -config :)

---

### Post by auraithx on 2012-09-05
> **SlugSlug said:**
> its --config not -config :)

I'm not writing -config, I'm copy/pasting from here. I tried -config as well after --config didn't work and accidently pasted it into my post (I ninja-edited it out though so unless you seen my post before then)

```
root@server1:~# sudo dpkg --config -a
dpkg: error: unknown option --config

Type dpkg --help for help about installing and un-installing packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Using --configure works though, this is the error I get.

```
root@server1:~# sudo dpkg --configure -a
Setting up fontconfig-config (2.8.0-3ubuntu9) ...
rmdir: failed to remove `/var/lib/defoma/fontconfig.d/': Directory not empty
dpkg: error processing fontconfig-config (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of fontconfig:
 fontconfig depends on fontconfig-config; however:
  Package fontconfig-config is not configured yet.
dpkg: error processing fontconfig (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtgui4:
 libqtgui4 depends on fontconfig; however:
  Package fontconfig is not configured yet.
dpkg: error processing libqtgui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdeui5:
 libkdeui5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkdeui5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdnssd4:
 libkdnssd4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
dpkg: error processing libkdnssd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrossui4:
 libkrossui4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkrossui4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkrossui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:
 libqt4-declarative depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-declarative (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfontconfig1:
 libfontconfig1 depends on fontconfig-config (= 2.8.0-3ubuntu9); however:
  Package fontconfig-config is not configured yet.
dpkg: error processing libfontconfig1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnepomukutils4:
 libnepomukutils4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libnepomukutils4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libnepomukutils4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-svg:
 libqt4-svg depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-svg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnepomuk4:
 libnepomuk4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libnepomuk4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libnepomuk4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsolid4:
 libsolid4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libsolid4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of katepart:
 katepart depends on libkdeui5 (>= 4:4.8.1); however:
  Package libkdeui5 is not configured yet.
 katepart depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing katepart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-0:
 libgtk-3-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libgtk-3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkde3support4:
 libkde3support4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkde3support4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkde3support4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-gtk3-0:
 libcanberra-gtk3-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libcanberra-gtk3-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkio5:
 libkio5 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkio5 depends on libnepomuk4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomuk4 is not configured yet.
 libkio5 depends on libqt4-svg (>= 4:4.7.0); however:
  Package libqt4-svg is not configured yet.
 libkio5 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
 libkio5 depends on libsolid4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libsolid4 is not configured yet.
dpkg: error processing libkio5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff2-4:
 libknewstuff2-4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libknewstuff2-4 depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libknewstuff2-4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libknewstuff2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnepomukquery4a:
 libnepomukquery4a depends on libnepomuk4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomuk4 is not configured yet.
dpkg: error processing libnepomukquery4a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnepomuksync4:
 libnepomuksync4 depends on libnepomuk4 (>= 4:4.8.1); however:
  Package libnepomuk4 is not configured yet.
dpkg: error processing libnepomuksync4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libcanberra-gtk3-0 (>= 0.25); however:
  Package libcanberra-gtk3-0 is not configured yet.
 gnome-control-center depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 gnome-control-center depends on libgtk-3-0 (>= 3.3.6); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing synaptic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-filters:
 cups-filters depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing cups-filters (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
 libpango1.0-0 depends on fontconfig (>= 2.1.91); however:
  Package fontconfig is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknotifyconfig4:
 libknotifyconfig4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libknotifyconfig4 depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libknotifyconfig4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libknotifyconfig4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgs9:
 libgs9 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libgs9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-pango-1.0:
 gir1.2-pango-1.0 depends on libpango1.0-0 (>= 1.29.4); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing gir1.2-pango-1.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x11-utils:
 x11-utils depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing x11-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 kdelibs-bin depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 kdelibs-bin depends on libnepomuk4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomuk4 is not configured yet.
 kdelibs-bin depends on libnepomukutils4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomukutils4 is not configured yet.
 kdelibs-bin depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-gtk3-4:
 libdbusmenu-gtk3-4 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libdbusmenu-gtk3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-2:
 librsvg2-2 depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing librsvg2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libknewstuff3-4:
 libknewstuff3-4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libknewstuff3-4 depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libknewstuff3-4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libknewstuff3-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkparts4:
 libkparts4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkparts4 depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkparts4 depends on libnepomuk4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomuk4 is not configured yet.
 libkparts4 depends on libnepomukutils4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libnepomukutils4 is not configured yet.
 libkparts4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkparts4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkcmutils4:
 libkcmutils4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkcmutils4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkcmutils4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdoctools:
 kdoctools depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 kdoctools depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing kdoctools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libindicator3-7:
 libindicator3-7 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libindicator3-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1a:
 libnautilus-extension1a depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libnautilus-extension1a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqtwebkit4:
 libqtwebkit4 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqtwebkit4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrosscore4:
 libkrosscore4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkrosscore4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkrosscore4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libappindicator3-1:
 libappindicator3-1 depends on libdbusmenu-gtk3-4 (>= 0.4.2); however:
  Package libdbusmenu-gtk3-4 is not configured yet.
 libappindicator3-1 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
 libappindicator3-1 depends on libindicator3-7; however:
  Package libindicator3-7 is not configured yet.
dpkg: error processing libappindicator3-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-designer:
 libqt4-designer depends on libqtgui4 (= 4:4.8.1-0ubuntu4.2); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libqt4-designer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libphonon4:
 libphonon4 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libphonon4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktexteditor4:
 libktexteditor4 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libktexteditor4 depends on libkparts4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
 libktexteditor4 depends on libqtgui4 (>= 4:4.7.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libktexteditor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-common:
 librsvg2-common depends on libgtk2.0-0 (>= 2.21.5); however:
  Package libgtk2.0-0 is not configured yet.
 librsvg2-common depends on librsvg2-2 (= 2.36.1-0ubuntu1); however:
  Package librsvg2-2 is not configured yet.
dpkg: error processing librsvg2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtksource-3.0:
 gir1.2-gtksource-3.0 depends on gir1.2-pango-1.0; however:
  Package gir1.2-pango-1.0 is not configured yet.
dpkg: error processing gir1.2-gtksource-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxft2:
 libxft2 depends on libfontconfig1 (>= 2.8.0); however:
  Package libfontconfig1 is not configured yet.
dpkg: error processing libxft2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkhtml5:
 libkhtml5 depends on libkdeui5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkdeui5 is not configured yet.
 libkhtml5 depends on libkio5 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkio5 is not configured yet.
 libkhtml5 depends on libkparts4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libkparts4 is not configured yet.
 libkhtml5 depends on libktexteditor4 (= 4:4.8.4a-0ubuntu0.2); however:
  Package libktexteditor4 is not configured yet.
 libkhtml5 depends on libphonon4 (>= 4:4.7.0really4.4.3); however:
  Package libphonon4 is not configured yet.
 libkhtml5 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4 is not configured yet.
dpkg: error processing libkhtml5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.4.2-0ubuntu0.4); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0 is not configured yet.
 python-gtk2 depends on libpango1.0-0 (>= 1.22.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnm-gtk0:
 libnm-gtk0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0 is not configured yet.
dpkg: error processing libnm-gtk0 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 fontconfig-config
 fontconfig
 libqtgui4
 libkdeui5
 libkdnssd4
 libkrossui4
 libqt4-declarative
 libfontconfig1
 libnepomukutils4
 libqt4-svg
 libgtk2.0-0
 libnepomuk4
 libsolid4
 katepart
 libgtk-3-0
 libkde3support4
 libcanberra-gtk3-0
 libkio5
 libknewstuff2-4
 libnepomukquery4a
 libnepomuksync4
 gnome-control-center
 synaptic
 cups-filters
 libpango1.0-0
 libknotifyconfig4
 libgs9
 gir1.2-pango-1.0
 x11-utils
 kdelibs-bin
 libdbusmenu-gtk3-4
 librsvg2-2
 libknewstuff3-4
 libkparts4
 libkcmutils4
 kdoctools
 libindicator3-7
 libnautilus-extension1a
 libqtwebkit4
 libkrosscore4
 libappindicator3-1
 libqt4-designer
 libphonon4
 libktexteditor4
 librsvg2-common
 gir1.2-gtksource-3.0
 libxft2
 libkhtml5
 libgtk-3-bin
 python-gtk2
 libnm-gtk0
Processing was halted because there were too many errors.
root@server1:~# 

```

---

### Post by drmrgd on 2012-09-05
Yikes!  Sorry about that!  I guess the coffee has not yet kicked in.  The command should have been:

```
sudo dpkg --configure -a
```

Glad you figured it out!

It has left us with a clue, though.  Looks like there's an issue with the fontconfig package and the directory 'fontconfig.d' not being empty.  I'm not 100% sure about this package.  However, it looks like it should be updated by the new package (hence the package wanting to remove it).  So, I would venture a guess that you could safely remove that directory that it's stuck on manually, and then try the dpkg reconfigure command again.  

Had a quick look for that folder, and it seems that one other has agreed with that strategy as well:

[http://askubuntu.com/questions/130679/upgrade-failed-kinda-now-cannot-install-some-packages](http://askubuntu.com/questions/130679/upgrade-failed-kinda-now-cannot-install-some-packages)

---

### Post by auraithx on 2012-09-05
> **drmrgd said:**
> Yikes!  Sorry about that!  I guess the coffee has not yet kicked in.  The command should have been:

```
sudo dpkg --configure -a
```

Glad you figured it out!

It has left us with a clue, though.  Looks like there's an issue with the fontconfig package and the directory 'fontconfig.d' not being empty.  I'm not 100% sure about this package.  However, it looks like it should be updated by the new package (hence the package wanting to remove it).  So, I would venture a guess that you could safely remove that directory that it's stuck on manually, and then try the dpkg reconfigure command again.  

Had a quick look for that folder, and it seems that one other has agreed with that strategy as well:

[http://askubuntu.com/questions/130679/upgrade-failed-kinda-now-cannot-install-some-packages](http://askubuntu.com/questions/130679/upgrade-failed-kinda-now-cannot-install-some-packages)

Woohoo!

```
rm /var/lib/defoma/fontconfig.d/*
```

Fixed the issue I was having. No more installation errors :). Now I just need to get MySQL working again

---

