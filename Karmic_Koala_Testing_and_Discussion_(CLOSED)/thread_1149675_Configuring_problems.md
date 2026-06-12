---
title: "Configuring problems"
date: 2009-05-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-05-05
Basically, I accidentally knocked my external hard drive whilst I was running karmic on it, and whilst synaptic was installing updates. I have got my system up and running again after a hard restart, but now when trying to install updates again I get this message:

```
E: libdatrie1: subprocess post-installation script returned error exit status 2
E: libthai0: dependency problems - leaving unconfigured
E: libpango1.0-0: dependency problems - leaving unconfigured
E: libpango1.0-dev: dependency problems - leaving unconfigured
E: libatspi1.0-0: dependency problems - leaving unconfigured
E: at-spi: dependency problems - leaving unconfigured
E: python-pyatspi: dependency problems - leaving unconfigured
E: libatspi-dbg: dependency problems - leaving unconfigured
E: compiz-gnome: dependency problems - leaving unconfigured
E: compiz-fusion-plugins-extra: dependency problems - leaving unconfigured
E: compiz-fusion-plugins-main: dependency problems - leaving unconfigured
E: compiz: dependency problems - leaving unconfigured
E: libcryptui0: dependency problems - leaving unconfigured
E: mousetweaks: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
E: nautilus-dbg: dependency problems - leaving unconfigured
E: seahorse: dependency problems - leaving unconfigured
E: seahorse-plugins: dependency problems - leaving unconfigured
```

Does anyone know how I can resolve these dependency problems, and then configure the packages?

All help appreciated :D

David

---

### Post by taavikko on 2009-05-05
```
sudo dpkg --configure -a
sudo apt-get -f install
```

Keep running those until no errors

---

### Post by davideotape on 2009-05-05
Unfortuantly I seem to be getting the same over and over again:

```
david@ExternalHarddrive:~$ sudo dpkg --configure -a
Setting up libdatrie1 (0.2.2-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libdatrie1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libthai0:
 libthai0 depends on libdatrie1 (>= 0.2.0); however:
  Package libdatrie1 is not configured yet.
dpkg: error processing libthai0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libthai0 (>= 0.1.9); however:
  Package libthai0 is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcryptui0:
 libcryptui0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libcryptui0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-main:
 compiz-fusion-plugins-main depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-fusion-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of at-spi:
 at-spi depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing at-spi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libpango1.0-0 (>= 1.20.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pyatspi:
 python-pyatspi depends on at-spi (>= 1.26.0-1ubuntu1); however:
  Package at-spi is not configured yet.
 python-pyatspi depends on at-spi (<< 1.26.0-1ubuntu1.1~); however:
  Package at-spi is not configured yet.
dpkg: error processing python-pyatspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse-plugins:
 seahorse-plugins depends on libcryptui0 (>= 2.25.4); however:
  Package libcryptui0 is not configured yet.
 seahorse-plugins depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing seahorse-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.
 compiz depends on compiz-fusion-plugins-main (>= 0.8.2-0); however:
  Package compiz-fusion-plugins-main is not configured yet.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on libcryptui0 (>= 2.25.4); however:
  Package libcryptui0 is not configured yet.
 seahorse depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing seahorse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatspi1.0-0:
 libatspi1.0-0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libatspi1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libpango1.0-0 (= 1.24.1-0ubuntu2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-dbg:
 nautilus-dbg depends on nautilus (= 1:2.26.2-3ubuntu1); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-extra:
 compiz-fusion-plugins-extra depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-fusion-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mousetweaks:
 mousetweaks depends on libatspi1.0-0 (>= 1.26.0); however:
  Package libatspi1.0-0 is not configured yet.
 mousetweaks depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing mousetweaks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatspi-dbg:
 libatspi-dbg depends on libatspi1.0-0 (= 1.26.0-1ubuntu1); however:
  Package libatspi1.0-0 is not configured yet.
dpkg: error processing libatspi-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdatrie1
 libthai0
 libpango1.0-0
 libcryptui0
 compiz-fusion-plugins-main
 at-spi
 nautilus
 python-pyatspi
 compiz-gnome
 seahorse-plugins
 compiz
 seahorse
 libatspi1.0-0
 libpango1.0-dev
 nautilus-dbg
 compiz-fusion-plugins-extra
 mousetweaks
 libatspi-dbg
david@ExternalHarddrive:~$ 

```

and

```
david@ExternalHarddrive:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-qt3support python-libsmbios smbios-utils libqt4-script libqt4-designer libqt4-network libqt4-dbus libsmbios2 libqtcore4
  seahorse-plugins qt4-qtconfig libqt4-sql libqt4-xml libqtgui4 libqt4-sql-mysql
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
18 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libdatrie1 (0.2.2-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libdatrie1 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libthai0:
 libthai0 depends on libdatrie1 (>= 0.2.0); however:
  Package libdatrie1 is not configured yet.
dpkg: error processing libthai0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libthai0 (>= 0.1.9); however:
  Package libthai0 is not configured yet.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatspi1.0-0:
 libatspi1.0-0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libatspi1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevNo apport report written because the error message indicates its a followup error from a previous failure.
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
                                                          ent configuration of at-spi:
 at-spi depends on libatspi1.0-0 (>= 1.26.0); however:
  Package libatspi1.0-0 is not configured yet.
 at-spi depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing at-spi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-main:
 compiz-fusion-plugins-main depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-fusion-plugins-main (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-fusion-plugins-extra:
 compiz-fusion-plugins-extra depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing compiz-fusion-plugins-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome; however:
  Package compiz-gnome is not configured yet.
 compiz depends on compiz-fusion-plugins-main (>= 0.8.2-0); however:
  Package compiz-fusion-plugins-main is not configured yet.
 compiz depends on compiz-fusion-plugins-extra (>= 0.8.2); however:
  Package compiz-fusion-plugins-extra is not configured yet.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcryptui0:
 libcryptui0 depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libcryptui0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-dev:
 libpango1.0-dev depends on libpango1.0-0 (= 1.24.1-0ubuntu2); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing libpango1.0-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mousetweaks:
 mousetweaks depends on libatspi1.0-0 (>= 1.26.0); however:
  Package libatspi1.0-0 is not configured yet.
 mousetweaks depends on libpango1.0-0 (>= 1.18.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing mousetweaks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libpango1.0-0 (>= 1.20.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pyatspi:
 python-pyatspi depends on at-spi (>= 1.26.0-1ubuntu1); however:
  Package at-spi is not configured yet.
 python-pyatspi depends on at-spi (<< 1.26.0-1ubuntu1.1~); however:
  Package at-spi is not configured yet.
dpkg: error processing python-pyatspi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse:
 seahorse depends on libcryptui0 (>= 2.25.4); however:
  Package libcryptui0 is not configured yet.
 seahorse depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing seahorse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of seahorse-plugins:
 seahorse-plugins depends on libcryptui0 (>= 2.25.4); however:
  Package libcryptui0 is not configured yet.
 seahorse-plugins depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing seahorse-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependenNo apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                                        cy problems prevent configuration of libatspi-dbg:
 libatspi-dbg depends on libatspi1.0-0 (= 1.26.0-1ubuntu1); however:
  Package libatspi1.0-0 is not configured yet.
dpkg: error processing libatspi-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-dbg:
 nautilus-dbg depends on nautilus (= 1:2.26.2-3ubuntu1); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdatrie1
 libthai0
 libpango1.0-0
 libatspi1.0-0
 at-spi
 compiz-gnome
 compiz-fusion-plugins-main
 compiz-fusion-plugins-extra
 compiz
 libcryptui0
 libpango1.0-dev
 mousetweaks
 nautilus
 python-pyatspi
 seahorse
 seahorse-plugins
 libatspi-dbg
 nautilus-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@ExternalHarddrive:~$ 

```

---

### Post by dinxter on 2009-05-05
try moving the file "/var/lib/dpkg/info/libdatrie1.postinst"  out of the way (its a simple enough script)
and running,
"dpkg --configure -a" again. 
you may want to reinstall libdatrie1 again after that after that

---

### Post by davideotape on 2009-05-06
Thank you, that seemed to work fine :D

---

