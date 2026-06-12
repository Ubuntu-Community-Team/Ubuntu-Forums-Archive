---
title: "Errors with updating after upgrading to 13.04 from 12.10"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by tuxpenguin42 on 2013-07-04
When I upgraded to 13.04, it kept showing messages about a package "python3.3-minimal" not being configured yet. After the upgrade was complete, and I tried to update the software, I got this: 

```

adam@adam-Satellite-P855:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-gnomebluetooth-1.0 : Breaks: gnome-bluetooth (< 3.8) but 3.6.1-0ubuntu3 is installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3) but 3.8.1-2ubuntu1~ubuntu13.04.1 is installed
 python-gi : Breaks: software-center (< 5.6.0-0ubuntu3) but 5.6.0-0ubuntu2 is installed
 yelp : Depends: libyelp0 (= 3.6.2-0ubuntu1) but 3.8.1-0ubuntu1~raring1 is installed
E: Unmet dependencies. Try using -f.

```

Running "apt-get -f install" gives: (Some of it at the top is cut off, I don't know how to do anything about that, sorry.)

```

s reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     figure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-tk:
 python3-tk depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-tk depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle-python3.3:
 idle-python3.3 depends on python3.3; however:
  Package python3.3 is not configured yet.
 idle-python3.3 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle-python3.3 depends on python3.3-tk; however:
  Package python3.3-tk is not installed.
  Package python3-tk which provides python3.3-tk is not configured yet.

dpkg: error processing idle-python3.3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle3:
 idle3 depends on python3 (>= 3.3.1-0ubuntNo apport report written because MaxReports is reached already
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
                                                                  No apport report written because MaxReports is reached already
                                                u1); however:
  Package python3 is not configured yet.
 idle3 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle3 depends on idle-python3.3; however:
  Package idle-python3.3 is not configured yet.

dpkg: error processing idle3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-dbus (--configure):
 dependency problems - leaving unconNo apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            figured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 language-selector-common depends on python3.3; however:
  Package python3.3 is not configured yet.
 language-selector-common depends on python3-apt (>= 0.7.12.0); however:
  Package python3-apt is not configured yet.
 language-selector-common depends on python3-dbus; however:
  Package python3-dbus is not configured yet.

dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on python3-dbus; however:
  Package python3-dbus is not configured yet.

dpkg: error processing bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python3 (>= 3.1); however:
  Package python3 is not configured yet.

dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-menus (>= 3.1.4); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-fallback:
 gnome-session-fallback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.

dpkg: error processing gnome-session-fallback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager-common:
 kde-window-manager-common depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager-common depends on kde-style-oxygen; however:
  Package kde-style-oxygen is not configured yet.

dpkg: error processing kde-window-manager-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager depends on kde-window-manager-common (= 4:4.10.4-0ubuntu0.1); however:
  Package kde-window-manager-common is not configured yet.

dpkg: error processing kde-window-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3); however:
  Version of gir1.2-gnomebluetooth-1.0 on system is 3.8.1-2ubuntu1~ubuntu13.04.1.
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 gir1.2-gnomebluetooth-1.0 (3.8.1-2ubuntu1~ubuntu13.04.1) breaks gnome-bluetooth (<< 3.8) and is installed.
  Version of gnome-bluetooth to be configured is 3.6.1-0ubuntu3.

dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-bluetooth (>= 3.0.0); however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-menus (>= 2.12.0); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xkit:
 python3-xkit depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-xkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 ubuntu-drivers-common depends on python3-xkit; however:
  Package python3-xkit is not configured yet.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-crypto:
 python3-crypto depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-crypto depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-oauthlib depends on python3-crypto; however:
  Package python3-crypto is not configured yet.

dpkg: error processing python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of friends-dispatcher:
 friends-dispatcher depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.
 friends-dispatcher depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 friends-dispatcher depends on python3-gi; however:
  Package python3-gi is not configured yet.
 friends-dispatcher depends on python3-oauthlib; however:
  Package python3-oauthlib is not configured yet.
 friends-dispatcher depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing friends-dispatcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfriends0:
 libfriends0 depends on friends-dispatcher; however:
  Package friends-dispatcher is not configured yet.

dpkg: error processing libfriends0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkgapi0:amd64:
 libkgapi0:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkgapi0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on lsb-release; however:
  Package lsb-release is not configured yet.
 ubuntu-minimal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency No apport report written because MaxReports is reached already
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
                                                           problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuNo apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         ration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.192.11); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:0.186.1); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-apport depends on python3-apt (>= 0.7.9); however:
  Package python3-apt is not configured yet.
 python3-apport depends on python3-problem-report (>= 0.94); however:
  Package python3-problem-report is not configured yet.
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.
 apport depends on python3-apport (>= 2.9.2-0ubuntu8.1); however:
  Package python3-apport is not configured yet.
 apport depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3; however:
  Package python3 is not configured yet.
 apport-gtk depends on python3-apport (>= 2.9.2-0ubuntu8.1); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on python3-gi; however:
  Package python3-gi is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 python3.3-minimal
 python3-minimal
 python3.3
 python3
 python3-tk
 idle-python3.3
 idle3
 python3-apt
 python3-dbus
 language-selector-common
 python3-gi
 bluez
 gnome-menus
 gnome-panel
 gnome-session-fallback
 kde-runtime
 kde-style-oxygen
 kde-window-manager-common
 kde-window-manager
 konsole
 gnome-bluetooth
 gnome-shell
 gnome-control-center
 indicator-bluetooth
 kinfocenter
 python3-xkit
 ubuntu-drivers-common
 python3-pkg-resources
 python3-crypto
 python3-oauthlib
 friends-dispatcher
 libfriends0
 kdepim-runtime
 libkgapi0:amd64
 libkdepimdbusinterfaces4
 libkdepim4
 lsb-release
 ubuntu-minimal
 python3-gdbm:amd64
 python3-commandnotfound
 command-not-found
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 ubuntu-standard
 ufw
 update-manager-core
 python3-problem-report
 python3-apport
 apport
 apport-gtk
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
adam@adam-Satellite-P855:~$ 


```

This leads me to believe it's a problem with the "python3.3-minimal" package that the upgrade had problems with. However, trying to install this package gives me this:

```

adam@adam-Satellite-P855:~$ sudo apt-get install python3.3-minimal
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3.3-minimal is already the newest version.
python3.3-minimal set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gir1.2-gnomebluetooth-1.0 : Breaks: gnome-bluetooth (< 3.8) but 3.6.1-0ubuntu3 is to be installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3) but 3.8.1-2ubuntu1~ubuntu13.04.1 is to be installed
 python-gi : Breaks: software-center (< 5.6.0-0ubuntu3) but 5.6.0-0ubuntu2 is to be installed
 yelp : Depends: libyelp0 (= 3.6.2-0ubuntu1) but 3.8.1-0ubuntu1~raring1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

This is also preventing me from updating via the GUI, as I get this:

[IMG]http://i.imgur.com/1IE8MW3.png[/IMG]

Clicking on Continue then shows:

[IMG]http://i.imgur.com/X6smiav.png[/IMG]

...Which then takes me back to where I already was.

Any help on this would be greatly appreciated.

EDIT: In case it matters, I've already tried installing the dependencies that "python3.3-minimal" needs, and they're all there. In addition, typing "python3.3" into the terminal starts the python prompt (with version 3.3.0), and typing "python3" starts version 3.2.3.

---

### Post by Bucky Ball on 2013-07-04
When you get to the 'Not all upgrades can be installed' try hitting 'Partial Upgrade' instead of 'Continue'. Let us know what happens then. ;)

(PS: Nice post; descriptive, plenty of info, and good thread title.)

---

### Post by tuxpenguin42 on 2013-07-04
Clicking on that takes me to the upgrade window, instead of the normal update window. Is this normal? (I don't know if something changed between 12.10 and 13.04.)

And thanks, I (unfortunately) have a lot of experience. :p

EDIT: I went ahead with it, seems to be installing everything correctly so far (not done yet, lets hope this works :p).

---

### Post by tuxpenguin42 on 2013-07-04
Nope, getting the same error:

[IMG]http://i.imgur.com/jpk9KJb.png[/IMG]

After that it shows an error about there being too many errors, so it cancels.

---

### Post by tuxpenguin42 on 2013-07-04
Running "sudo apt-get upgrade" now shows this: (again, it's cut off at the top, sorry)

```

 bluez depends on python3-dbus; however:
  Package python3-dbus is not configured yet.

dpkg: error processing bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libmetacity-private0a (= 1:2.34.13-0ubuntu1); however:
  Version of libmetacity-private0a on system is 1:2.34.13-0ubuntu2~raring1.
 metacity depends on metacity-common (= 1:2.34.13-0ubuntu1); however:
  Version of metacity-common on system is 1:2.34.13-0ubuntu2~raring1.

dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python3 (>= 3.1); however:
  Package python3 is not configured yet.

dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:3.6.2-0ubuntu3); however:
  Version of gnome-panel-data on system is 1:3.6.2-0ubuntu11~ubuntu13.04.1.
 gnome-panel depends on gnome-menus (>= 3.1.4); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-flashback:
 gnome-session-flashback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.
 gnome-session-flashback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.

dpkg: error processing gnome-session-flashback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager-common:
 kde-window-manager-common depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager-common depends on kde-style-oxygen; however:
  Package kde-style-oxygen is not configured yet.

dpkg: error processing kde-window-manager-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager depends on kde-window-manager-common (= 4:4.10.4-0ubuntu0.1); however:
  Package kde-window-manager-common is not configured yet.

dpkg: error processing kde-window-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on metacity (>= 1:2.34.2); however:
  Package metacity is not configured yet.

dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3); however:
  Version of gir1.2-gnomebluetooth-1.0 on system is 3.8.1-2ubuntu1~ubuntu13.04.1.
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 gir1.2-gnomebluetooth-1.0 (3.8.1-2ubuntu1~ubuntu13.04.1) breaks gnome-bluetooth (<< 3.8) and is installed.
  Version of gnome-bluetooth to be configured is 3.6.1-0ubuntu3.

dpkg: error processing gnome-bluNo apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              etooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-bluetooth (>= 3.0.0); however:
  Package gnome-bluetooth is not configured yet.
 gnome-shell depends on libgjs0-libmozjs185-1.0; however:
  Package libgjs0-libmozjs185-1.0 is not installed.
 gnome-shell depends on libmutter0a; however:
  Package libmutter0a is not installed.
 gnome-shell depends on gdm (>= 3.5.90); however:
  Package gdm is not configured yet.
 gnome-shell depends on gnome-shell-common (= 3.6.3.1-0ubuntu6); however:
  Version of gnome-shell-common on system is 3.8.2-1ubuntu2~raring2.

dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-menus (>= 2.12.0); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-fallback:
 gnome-session-fallback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.
 gnome-session-fallback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.
 gnome-session-fallback depends on gnome-session-bin (<< 3.7); however:
  Version of gnome-session-bin on system is 3.8.2.1-1ubuntu4~ubuntu13.04.0.
 gnome-session-fallback depends on gnome-session-common (= 3.6.2-0ubuntu5); however:
  Version of gnome-session-common on system is 3.8.2.1-1ubuntu4~ubuntu13.04.0.
 gnome-session-flashback (1:3.6.2-0ubuntu11~ubuntu13.04.1) breaks gnome-session-fallback (<< 1:3.6.2-0ubuntu10) and is unpacked but not configured.
  Version of gnome-session-fallback to be configured is 3.6.2-0ubuntu5.

dpkg: error processing gnome-session-fallback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
Setting up libfolks-eds25:amd64 (0.9.2-1~raring1) ...
Setting up libgtkmm-3.0-1:amd64 (3.8.1-1~raring1) ...
Setting up libgtksourceview-3.0-1:amd64 (3.8.1-0ubuntu1~raring1) ...
Setting up libvala-0.20-0:amd64 (0.20.1-0ubuntu1) ...
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xkit:
 python3-xkit depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-xkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 ubuntu-drivers-common depends on python3-xkit; however:
  Package python3-xkit is not configured yet.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
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
                                                    No apport report written because MaxReports is reached already
                        dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-crypto:
 python3-crypto depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-crypto depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-oauthlib depends on python3-crypto; however:
  Package python3-crypto is not configureNo apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
                                                                                       No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                               d yet.

dpkg: error processing python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of friends-dispatcher:
 friends-dispatcher depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.
 friends-dispatcher depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 friends-dispatcher depends on python3-gi; however:
  Package python3-gi is not configured yet.
 friends-dispatcher depends on python3-oauthlib; however:
  Package python3-oauthlib is not configured yet.
 friends-dispatcher depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing friends-dispatcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfriends0:
 libfriends0 depends on friends-dispatcher; however:
  Package friends-dispatcher is not configured yet.

dpkg: error processing libfriends0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkgapi0:amd64:
 libkgapi0:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkgapi0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on lsb-release; however:
  Package lsb-release is not configured yet.
 ubuntu-minimal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.192.11); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:0.186.1); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on empathy-common (= 3.6.4-0ubuntu4.1); however:
  Version of empathy-common on system is 3.8.3-0ubuntu1~raring1.

dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python3.3-minimal
 python3-minimal
 python3.3
 python3
 python3-tk
 idle-python3.3
 idle3
 python3-apt
 python3-dbus
 language-selector-common
 bluez
 metacity
 gnome-menus
 gnome-panel
 gnome-session-flashback
 kde-runtime
 kde-style-oxygen
 kde-window-manager-common
 kde-window-manager
 konsole
 gdm
 gnome-bluetooth
 gnome-shell
 gnome-control-center
 indicator-bluetooth
 gnome-session-fallback
 kinfocenter
 python3-gi
 python3-xkit
 ubuntu-drivers-common
 python3-pkg-resources
 python3-crypto
 python3-oauthlib
 friends-dispatcher
 libfriends0
 kdepim-runtime
 libkgapi0:amd64
 libkdepimdbusinterfaces4
 libkdepim4
 lsb-release
 ubuntu-minimal
 python3-gdbm:amd64
 python3-commandnotfound
 command-not-found
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 ubuntu-standard
 ufw
 update-manager-core
 empathy
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
adam@adam-Satellite-P855:~$ clear

adam@adam-Satellite-P855:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 account-plugin-facebook : Depends: account-plugin-generic-oauth but it is not installed
 account-plugin-flickr : Depends: account-plugin-generic-oauth but it is not installed
 account-plugin-identica : Depends: account-plugin-generic-oauth but it is not installed
 account-plugin-twitter : Depends: account-plugin-generic-oauth but it is not installed
 account-plugin-windows-live : Depends: account-plugin-generic-oauth but it is not installed
 brasero : Depends: libbrasero-media3-1 (= 3.6.1-0ubuntu2) but 3.8.0-1ubuntu2~raring1 is installed
           Depends: brasero-common (= 3.6.1-0ubuntu2) but 3.8.0-1ubuntu2~raring1 is installed
 empathy : Depends: empathy-common (= 3.6.4-0ubuntu4.1) but 3.8.3-0ubuntu1~raring1 is installed
           Recommends: gnome-contacts but it is not installed
 evince : Depends: libevdocument3-4 (= 3.6.1-1ubuntu3) but 3.8.2-0ubuntu4~raring1 is installed
          Depends: libevview3-3 (= 3.6.1-1ubuntu3) but 3.8.2-0ubuntu4~raring1 is installed
          Depends: evince-common (< 3.7) but 3.8.2-0ubuntu4~raring1 is installed
 gedit : Depends: gedit-common (< 3.7) but 3.8.2-0ubuntu1~raring2 is installed
 gir1.2-gnomebluetooth-1.0 : Breaks: gnome-bluetooth (< 3.8) but 3.6.1-0ubuntu3 is installed
 gir1.2-totem-1.0 : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3) but 3.8.1-2ubuntu1~ubuntu13.04.1 is installed
 gnome-panel : Depends: gnome-panel-data (= 1:3.6.2-0ubuntu3) but 1:3.6.2-0ubuntu11~ubuntu13.04.1 is installed
 gnome-session-fallback : Depends: gnome-session-bin (< 3.7) but 3.8.2.1-1ubuntu4~ubuntu13.04.0 is installed
                          Depends: gnome-session-common (= 3.6.2-0ubuntu5) but 3.8.2.1-1ubuntu4~ubuntu13.04.0 is installed
 gnome-session-flashback : Breaks: gnome-session-fallback (< 1:3.6.2-0ubuntu10) but 3.6.2-0ubuntu5 is installed
 gnome-shell : Depends: libgjs0-libmozjs185-1.0
               Depends: libmutter0a but it is not installed
               Depends: gnome-shell-common (= 3.6.3.1-0ubuntu6) but 3.8.2-1ubuntu2~raring2 is installed
               Recommends: gnome-contacts but it is not installed
 libdevhelp-3-2 : Depends: devhelp-common (>= 3.8.2-0ubuntu1~raring1) but 3.6.1-0ubuntu1 is installed
 metacity : Depends: libmetacity-private0a (= 1:2.34.13-0ubuntu1) but 1:2.34.13-0ubuntu2~raring1 is installed
            Depends: metacity-common (= 1:2.34.13-0ubuntu1) but 1:2.34.13-0ubuntu2~raring1 is installed
 python-gi : Breaks: software-center (< 5.6.0-0ubuntu3) but 5.6.0-0ubuntu2 is installed
 rhythmbox : Depends: rhythmbox-data (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is installed
             Depends: gir1.2-rb-3.0 (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is installed
 rhythmbox-plugins : Depends: gir1.2-rb-3.0 (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is installed
 totem : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is installed
         Depends: totem-common (= 3.6.3-0ubuntu6) but 3.8.2-0ubuntu2~raring1 is installed
 totem-plugins : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is installed
 yelp : Depends: libyelp0 (= 3.6.2-0ubuntu1) but 3.8.1-0ubuntu1~raring1 is installed
E: Unmet dependencies. Try using -f.


```

Following the suggestion of using the "-f" flag results in this:

```

 python3-tk depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-tk depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle-python3.3:
 idle-python3.3 depends on python3.3; however:
  Package python3.3 is not configured yet.
 idle-python3.3 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle-python3.3 depends on python3.3-tk; however:
  Package python3.3-tk is not installed.
  Package python3-tk which provides python3.3-tk is not configured yet.

dpkg: error processing idle-python3.3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of idle3:
 idle3 depends on python3 (>= 3.3.1-0ubuntNo apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                      u1); however:
  Package python3 is not configured yet.
 idle3 depends on python3-tk; however:
  Package python3-tk is not configured yet.
 idle3 depends on idle-python3.3; however:
  Package idle-python3.3 is not configured yet.

dpkg: error processing idle3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 language-selector-common depends on python3.3; however:
  Package python3.3 is not configured yet.
 language-selector-common depends on python3-apt (>= 0.7.12.0); however:
  Package python3-apt is not configured yet.
 language-selector-common depends on python3-dbus; however:
  Package python3-dbus is not configured yet.

dpkg: error processing language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on python3-dbus; however:
  Package python3-dbus is not configured yet.

dpkg: error processing bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libmetacity-private0a (= 1:2.34.13-0ubuntu1); however:
  Version of libmetacity-private0a on system is 1:2.34.13-0ubuntu2~raring1.
 metacity depends on metacity-common (= 1:2.34.13-0ubuntu1); however:
  Version of metacity-common on system is 1:2.34.13-0ubuntu2~raring1.

dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python3 (>= 3.1); however:
  Package python3 is not configured yet.

dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:3.6.2-0ubuntu3); however:
  Version of gnome-panel-data on system is 1:3.6.2-0ubuntu11~ubuntu13.04.1.
 gnome-panel depends on gnome-menus (>= 3.1.4); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-flashback:
 gnome-session-flashback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.
 gnome-session-flashback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.

dpkg: error processing gnome-session-flashback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-runtime:
 kde-runtime depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing kde-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-style-oxygen:
 kde-style-oxygen depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kde-style-oxygen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager-common:
 kde-window-manager-common depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager-common depends on kde-style-oxygen; however:
  Package kde-style-oxygen is not configured yet.

dpkg: error processing kde-window-manager-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kde-runtime; however:
  Package kde-runtime is not configured yet.
 kde-window-manager depends on kde-window-manager-common (= 4:4.10.4-0ubuntu0.1); however:
  Package kde-window-manager-common is not configured yet.

dpkg: error processing kde-window-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on metacity (>= 1:2.34.2); however:
  Package metacity is not configured yet.

dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3); however:
  Version of gir1.2-gnomebluetooth-1.0 on system is 3.8.1-2ubuntu1~ubuntu13.04.1.
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 gir1.2-gnomebluetooth-1.0 (3.8.1-2ubuntu1~ubuntu13.04.1) breaks gnome-bluetooth (<< 3.8) and is installed.
  Version of gnome-bluetooth to be configured is 3.6.1-0ubuntu3.

dpkg: error processing gnome-bluNo apport report written because MaxReports is reached already
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
                                                        No apport report written because MaxReports is reached already
                            etooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-bluetooth (>= 3.0.0); however:
  Package gnome-bluetooth is not configured yet.
 gnome-shell depends on libgjs0-libmozjs185-1.0; however:
  Package libgjs0-libmozjs185-1.0 is not installed.
 gnome-shell depends on libmutter0a; however:
  Package libmutter0a is not installed.
 gnome-shell depends on gdm (>= 3.5.90); however:
  Package gdm is not configured yet.
 gnome-shell depends on gnome-shell-common (= 3.6.3.1-0ubuntu6); however:
  Version of gnome-shell-common on system is 3.8.2-1ubuntu2~raring2.

dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-menus (>= 2.12.0); however:
  Package gnome-menus is not configured yet.

dpkg: error processing gnome-control-center (--configure)No apport report written because MaxReports is reached already
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
                   :
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-bluetooth:
 indicator-bluetooth depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.

dpkg: error processing indicator-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session-fallback:
 gnome-session-fallback depends on gnome-panel (>= 3.0); however:
  Package gnome-panel is not configured yet.
 gnome-session-fallback depends on metacity (>= 2.30); however:
  Package metacity is not configured yet.
 gnome-session-fallback depends on gnome-session-bin (<< 3.7); however:
  Version of gnome-session-bin on system is 3.8.2.1-1ubuntu4~ubuntu13.04.0.
 gnome-session-fallback depends on gnome-session-common (= 3.6.2-0ubuntu5); however:
  Version of gnome-session-common on system is 3.8.2.1-1ubuntu4~ubuntu13.04.0.
 gnome-session-flashback (1:3.6.2-0ubuntu11~ubuntu13.04.1) breaks gnome-sesNo apport report written because MaxReports is reached already
                                               sion-fallback (<< 1:3.6.2-0ubuntu10) and is unpacked but not configured.
  Version of gnome-session-fallback to be configured is 3.6.2-0ubuntu5.

dpkg: error processing gnome-session-fallback (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kinfocenter:
 kinfocenter depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kinfocenter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xkit:
 python3-xkit depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-xkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 ubuntu-drivers-common depends on python3-xkit; however:
  Package python3-xkit is not configured yet.

dpkg: error processing ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 python3-pkg-resources depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-crypto:
 python3-crypto depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-crypto depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-oauthlib depends on python3-crypto; however:
  Package python3-crypto is not configured yet.

dpkg: error processing python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of friends-dispatcher:
 friends-dispatcher depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.
 friends-dispatcher depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 friends-dispatcher depends on python3-gi; however:
  Package python3-gi is not configured yet.
 friends-dispatcher depends on python3-oauthlib; however:
  Package python3-oauthlib is not configured yet.
 friends-dispatcher depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing friends-dispatcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfriends0:
 libfriends0 depends on friends-dispatcher; however:
  Package friends-dispatcher is not configured yet.

dpkg: error processing libfriends0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kde-runtime; however:
  Package kde-runtime is not configured yet.

dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkgapi0:amd64:
 libkgapi0:amd64 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkgapi0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepimdbusinterfaces4:
 libkdepimdbusinterfaces4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepimdbusinterfaces4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdepim4:
 libkdepim4 depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.

dpkg: error processing libkdepim4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on lsb-release; however:
  Package lsb-release is not configured yet.
 ubuntu-minimal depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.3); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of command-not-found:
 command-not-found depends on python3-commandnotfound (>= 0.3ubuntu7); however:
  Package python3-commandnotfound is not configured yet.

dpkg: error processing command-not-found (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.192.11); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on language-selector-common; however:
  Package language-selector-common is not configured yet.

dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3 (>= 3.2.3-3~); however:
  Package python3 is not configured yet.

dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3 (>= 3.2); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:0.186.1); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of empathy:
 empathy depends on empathy-common (= 3.6.4-0ubuntu4.1); however:
  Version of empathy-common on system is 3.8.3-0ubuntu1~raring1.

dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python3.3-minimal
 python3-minimal
 python3.3
 python3
 python3-tk
 idle-python3.3
 idle3
 python3-apt
 python3-dbus
 language-selector-common
 bluez
 metacity
 gnome-menus
 gnome-panel
 gnome-session-flashback
 kde-runtime
 kde-style-oxygen
 kde-window-manager-common
 kde-window-manager
 konsole
 gdm
 gnome-bluetooth
 gnome-shell
 gnome-control-center
 indicator-bluetooth
 gnome-session-fallback
 kinfocenter
 python3-gi
 python3-xkit
 ubuntu-drivers-common
 python3-pkg-resources
 python3-crypto
 python3-oauthlib
 friends-dispatcher
 libfriends0
 kdepim-runtime
 libkgapi0:amd64
 libkdepimdbusinterfaces4
 libkdepim4
 lsb-release
 ubuntu-minimal
 python3-gdbm:amd64
 python3-commandnotfound
 command-not-found
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 ubuntu-standard
 ufw
 update-manager-core
 empathy
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Not shown at the top is where it presents a list of packages to be updated, and I enter "y".

---

### Post by tuxpenguin42 on 2013-07-04
double post, sorry about that

---

### Post by tuxpenguin42 on 2013-07-04
I'm now getting an error of "BrokenCount > 0", which I think just confirms that it's a problem with the python package that the others rely on.

Attempting to reinstall this package gives me this:

```

adam@adam-Satellite-P855:~$ sudo apt-get install --reinstall python3.3-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 account-plugin-facebook : Depends: account-plugin-generic-oauth but it is not going to be installed
 account-plugin-flickr : Depends: account-plugin-generic-oauth but it is not going to be installed
 account-plugin-identica : Depends: account-plugin-generic-oauth but it is not going to be installed
 account-plugin-twitter : Depends: account-plugin-generic-oauth but it is not going to be installed
 account-plugin-windows-live : Depends: account-plugin-generic-oauth but it is not going to be installed
 brasero : Depends: libbrasero-media3-1 (= 3.6.1-0ubuntu2) but 3.8.0-1ubuntu2~raring1 is to be installed
           Depends: brasero-common (= 3.6.1-0ubuntu2) but 3.8.0-1ubuntu2~raring1 is to be installed
 empathy : Depends: empathy-common (= 3.6.4-0ubuntu4.1) but 3.8.3-0ubuntu1~raring1 is to be installed
           Recommends: gnome-contacts but it is not going to be installed
 evince : Depends: libevdocument3-4 (= 3.6.1-1ubuntu3) but 3.8.2-0ubuntu4~raring1 is to be installed
          Depends: libevview3-3 (= 3.6.1-1ubuntu3) but 3.8.2-0ubuntu4~raring1 is to be installed
          Depends: evince-common (< 3.7) but 3.8.2-0ubuntu4~raring1 is to be installed
 gedit : Depends: gedit-common (< 3.7) but 3.8.2-0ubuntu1~raring2 is to be installed
 gir1.2-gnomebluetooth-1.0 : Breaks: gnome-bluetooth (< 3.8) but 3.6.1-0ubuntu3 is to be installed
 gir1.2-totem-1.0 : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is to be installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.6.1-0ubuntu3) but 3.8.1-2ubuntu1~ubuntu13.04.1 is to be installed
 gnome-panel : Depends: gnome-panel-data (= 1:3.6.2-0ubuntu3) but 1:3.6.2-0ubuntu11~ubuntu13.04.1 is to be installed
 gnome-session-fallback : Depends: gnome-session-bin (< 3.7) but 3.8.2.1-1ubuntu4~ubuntu13.04.0 is to be installed
                          Depends: gnome-session-common (= 3.6.2-0ubuntu5) but 3.8.2.1-1ubuntu4~ubuntu13.04.0 is to be installed
 gnome-session-flashback : Breaks: gnome-session-fallback (< 1:3.6.2-0ubuntu10) but 3.6.2-0ubuntu5 is to be installed
 gnome-shell : Depends: libgjs0-libmozjs185-1.0
               Depends: libmutter0a but it is not going to be installed
               Depends: gnome-shell-common (= 3.6.3.1-0ubuntu6) but 3.8.2-1ubuntu2~raring2 is to be installed
               Recommends: gnome-contacts but it is not going to be installed
 libdevhelp-3-2 : Depends: devhelp-common (>= 3.8.2-0ubuntu1~raring1) but 3.6.1-0ubuntu1 is to be installed
 metacity : Depends: libmetacity-private0a (= 1:2.34.13-0ubuntu1) but 1:2.34.13-0ubuntu2~raring1 is to be installed
            Depends: metacity-common (= 1:2.34.13-0ubuntu1) but 1:2.34.13-0ubuntu2~raring1 is to be installed
 python-gi : Breaks: software-center (< 5.6.0-0ubuntu3) but 5.6.0-0ubuntu2 is to be installed
 rhythmbox : Depends: rhythmbox-data (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is to be installed
             Depends: gir1.2-rb-3.0 (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is to be installed
 rhythmbox-plugins : Depends: gir1.2-rb-3.0 (= 2.98-0ubuntu5) but 2.99.1-0ubuntu1~raring1 is to be installed
 totem : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is to be installed
         Depends: totem-common (= 3.6.3-0ubuntu6) but 3.8.2-0ubuntu2~raring1 is to be installed
 totem-plugins : Depends: libtotem0 (< 3.7) but 3.8.2-0ubuntu2~raring1 is to be installed
 yelp : Depends: libyelp0 (= 3.6.2-0ubuntu1) but 3.8.1-0ubuntu1~raring1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

----

Another update:

I checked to see where "python3.3" was installed at, and it was in /usr/local/bin. Is this correct, or should it be in /usr/bin with the main "python" command? There is, however, another "python3.3" command in /usr/bin. I'm getting really confused here...

---

