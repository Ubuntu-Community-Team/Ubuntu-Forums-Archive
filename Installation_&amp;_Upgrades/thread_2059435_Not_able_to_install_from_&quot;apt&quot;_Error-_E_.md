---
title: "Not able to install from &quot;apt&quot; Error:- E: Sub-process /usr/bin/dpkg returned an error"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by amolredhat on 2012-09-18
While installing packages in the Server, i Found that "apt" is not working properly, i have to manually download .deb package and then, i have to install in the servers, From command line are not working properly. 

I have tried to fix this with following commands:-


[HTML]sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
[/HTML] Below is the Error :-

administrator@xyz:~$ sudo apt-get install pidgin
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
32 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up shared-mime-info (0.71-1ubuntu2) ...
/var/lib/dpkg/info/shared-mime-info.postinst: line 13:  1214 Segmentation fault      update-mime-database.real /usr/share/mime
dpkg: error processing shared-mime-info (--configure):
 subprocess installed post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libgtk2.0-0:
 libgtk2.0-0 depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing libgtk2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser:
 chromium-browser depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing chromium-browser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-codecs-ffmpeg:
 chromium-codecs-ffmpeg depends on chromium-browser (>= 4.0.203.0~); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-codecs-ffmpeg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (= 18.0.1025.151~r130497-0ubuntu0.10.04.No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         1); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevdocument2:
 libevdocument2 depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libevdocument2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevview2:
 libevview2 depends on libevdocument2 (>= 2.29.5); however:
  Package libevdocument2 is not configured yet.
 libevview2 depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libevview2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevdocument2 (>= 2.29.5); however:
  Package libevdocument2 is not configured yet.
 evince depends on libevview2 (>= 2.29.No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       5); however:
  Package libevview2 is not configured yet.
 evince depends on libgtk2.0-0 (>= 2.16.0); however:
  Package libgtk2.0-0 is not configured yet.
 evince depends on shared-mime-info; however:
  Package shared-mime-info is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libgtk2.0-0 (>= 2.20.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcalctool:
 gcalctool depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdict-1.0-6:
 libgdict-1.0-6 depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgdict-1.0-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libgdict-1.0-6 (>= 2.23.90); however:
  Package libgdict-1.0-6 is not configured yet.
 gnome-utils depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:
 gtk2-engines-pixbuf depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is not configured yet.
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing gtk2-engines-pixbuf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail18:
 libgail18 depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgail18 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-bin:
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing libgtk2.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnotify-dev:
 libnotify-dev depends on libgtk2.0-dev (>= 2.10); however:
  Package libgtk2.0-dev is not configured yet.
dpkg: error processing libnotify-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libgtk2.0-0 (>= 2.16.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on libgtk2.0-0 (>= 2.10); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.2.0-7ubuntu4.4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up update-manager (1:0.134.12.1) ...
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on libgtk2.0-0 (>= 2.14.0); however:
  Package libgtk2.0-0 is not configured yet.
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xulrunner-1.9.2:
 xulrunner-1.9.2 depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing xulrunner-1.9.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xulrunner-1.9.2-dev:
 xulrunner-1.9.2-dev depends on xulrunner-1.9.2 (= 1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package xulrunner-1.9.2 is not configured yet.
 xulrunner-1.9.2-dev depends on libnotify-dev; however:
  Package libnotify-dev is not configured yet.
dpkg: error processing xulrunner-1.9.2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on xulrunner-1.9.2; however:
  Package xulrunner-1.9.2 is not configured yet.
 icedtea6-plugin depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
Setting up libgweather-common (2.30.0-0ubuntu1.1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing libgweather-common (--configure):
 subprocess installed post-installation script returned error exit status 245
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgtk2.0-0 (>= 2.11.0); however:
  Package libgtk2.0-0 is not configured yet.
 libgweather1 depends on libgweather-common (>= 2.24.0); however:
  Package libgweather-common is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-galaxy:
 openoffice.org-style-galaxy depends on openoffice.org-core (>= 1:3.2.0~beta); however:
  Package openoffice.org-core is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing openoffice.org-style-galaxy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-style-default | openoffice.org-style; however:
  Package openoffice.org-style-default is not installed.
  Package openoffice.org-style-galaxy which provides openoffice.org-style-default is not configured yet.
  Package openoffice.org-style is not installed.
  Package openoffice.org-style-galaxy which provides openoffice.org-style is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 shared-mime-info
 libgtk2.0-0
 chromium-browser
 chromium-codecs-ffmpeg
 chromium-browser-l10n
 libevdocument2
 libevview2
 evince
 firefox
 gcalctool
 libgdict-1.0-6
 gnome-utils
 gtk2-engines-pixbuf
 libedataserverui1.2-8
 libgail18
 libgtk2.0-bin
 libgtk2.0-dev
 libnotify-dev
 network-manager-gnome
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-impress
 pidgin
 update-manager
 update-notifier
 xulrunner-1.9.2
 xulrunner-1.9.2-dev
 icedtea6-plugin
 libgweather-common
 libgweather1
 openoffice.org-style-galaxy
 openoffice.org-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
administrator@xyz:~$

 Ubuntu Guru's i appreciate, if some help me to resolve this issue.


Thanks in advance :)

---

### Post by drmrgd on 2012-09-18
Looks like the package shared-mime-info is causing a problem that's cascading through the whole package installation process (i.e. other packages can't configure themselves until shared-mime-info is configured).  I found this thread where there was a solution posted at the bottom:

[http://askubuntu.com/questions/102480/sudo-apt-get-upgrade-fails-due-to-shared-mime-info-postinst-error](http://askubuntu.com/questions/102480/sudo-apt-get-upgrade-fails-due-to-shared-mime-info-postinst-error)

Instead of using the maverick package, though, be sure to grab the correct one for your system (Precise?) and your architecture.  Once you've installed that package manually, give the full update and upgrade another shot.

---

