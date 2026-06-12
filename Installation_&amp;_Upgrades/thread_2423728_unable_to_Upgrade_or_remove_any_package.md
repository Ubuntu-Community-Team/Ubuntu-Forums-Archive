---
title: "unable to Upgrade or remove any package"
date: 2019-07-28
forum: Installation &amp; Upgrades
---

### Post by shakir-mengrani on 2019-07-28
```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
62 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dictionaries-common (1.28.1) ...
Setting up python3 (3.7.3-1) ...
running python rtupdate hooks for python3.7...
dpkg-query: package 'gedit' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: package 'hplip-data' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of hplip-data
error running python rtupdate hook hplip-data
dpkg-query: package 'ibus-table' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ibus-table
error running python rtupdate hook ibus-table
dpkg-query: package 'python3-uno' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of python3-uno
error running python rtupdate hook python3-uno
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugin-alternative-toolbar
error running python rtupdate hook rhythmbox-plugin-alternative-toolbar
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of rhythmbox-plugins
error running python rtupdate hook rhythmbox-plugins
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of ubuntu-drivers-common
error running python rtupdate hook ubuntu-drivers-common
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.


dpkg: error processing package apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-tz:
 python3-tz depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-tz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.0~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cupshelpers:
 python3-cupshelpers depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: errorNo apport report written because the error message indicates its a followup error from a previous failure.
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
                                                                                                                                      processing package python3-cupshelpers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests-unixsocket:
 python3-requests-unixsocket depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-requests-unixsocket (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-six:
 python3-six depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-six (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent No apport report written because MaxReports is reached already
                                                                                                No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              configuration of python3-cups:
 python3-cups depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-cups depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer:
 system-config-printer depends on python3-cups (>= 1.9.60); however:
  Package python3-cups is not configured yet.
 system-config-printer depends on python3-cupshelpers (= 1.5.11-2ubuntu2); however:
  Package python3-cupshelpers is not configured yet.
 system-config-printer depends on python3:any; however:
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                                                                                                              Package python3 is not configured yet.


dpkg: error processing package system-config-printer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-certifi:
 python3-certifi depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-certifi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-gi depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests:
 python3-requests depends on python3-certifi; however:
  Package python3-certifi is not configured yet.
 python3-requests depends on python3-chardet (<< 3.1.0); however:
  Package python3-chardet is not configured yet.
 python3-requests depends on python3:any; however:
  Package python3 is not configured yet.
 python3-requests depends on python3-chardet (>= 3.0.2); however:
  Package python3-chardet is not configured yet.


dpkg: error processing package python3-requests (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-idna:
 python3-idna depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-idna (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-urllib3:
 python3-urllib3 depends on python3:any; however:
  Package python3 is not configured yet.
 python3-urllib3 depends on pythNo apport report written because MaxReports is reached already
                                                                                              on3-six; however:
  Package python3-six is not configured yet.


dpkg: error processing package python3-urllib3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on python3; however:
  Package python3 is not configured yet.


dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-session:
 ubuntu-session depends on gnome-shell (>= 3.24.3-0ubuntu2); however:
  Package gnome-shell is not configured yet.


dpkg: error processing package ubuntu-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on python3-gi; however:
  Package python3-gi is not configured yet.
 ibus depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm3:
 gdm3 depends on gnome-shell (>= 3.19.92); however:
  Package gnome-shell is not configured yet.


dpkg: error processing package gdm3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-defer:
 python3-defer depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.No apport report written because MaxReports is reached already




dpkg: error processing package python3-defer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-httplib2:
 python3-httplib2 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-httplib2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 virtualbox depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 virtualbox depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package virtualbox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-protobuf:
 python3-protobuf depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-protobuf depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-protobuf depends on python3-six (>= 1.9); however:
  Package python3-six is not configured yet.
 python3-protobuf depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-protobuf (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-rfc3339:
 python3-rfc3339 depends on python3-tz; however:
  Package python3-tz is not configured yet.
 python3-rfc3339 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-rfc3339 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-macaroonbakery:
 python3-macaroonbakery depends on python3-protobuf (>= 3.0.0); however:
  Package python3-protobuf is not configured yet.
 python3-macaroonbakery depends on python3-requests (>= 2.18.1); however:
  Package python3-requests is not configured yet.
 python3-macaroonbakery depends on python3-rfc3339 (>= 1.0); however:
  Package python3-rfc3339 is not configured yet.
 python3-macaroonbakery depends on python3-six (<< 2.0); however:
  Package python3-six is not configured yet.
 python3-macaroonbakery depends on python3-six (>= 1.11.0); however:
  Package python3-six is not configured yet.
 python3-macaroonbakery depends on python3:any (>= 3.5~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-macaroonbakery (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon.gtk3widgets depends on python3-gi; however:
  Package python3-gi is not configured yet.


dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-nacl:
 python3-nacl depends on python3 (>= 3~); however:
  Package python3 is not configured yet.
 python3-nacl depends on python3-six; however:
  Package python3-six is not configured yet.
 python3-nacl depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-nacl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-systemd:
 python3-systemd depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-systemd depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-systemd depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-systemd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-cffi-backend:
 python3-cffi-backend depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-cffi-backend depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-cffi-backend (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-system-service:
 ubuntu-system-service depends on python3-gi; however:
  Package python3-gi is not configured yet.
 ubuntu-system-service depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package ubuntu-system-service (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of snapd:
 snapd depends on apparmor (>= 2.10.95-0ubuntu2.2); however:
  Package apparmor is not configured yet.


dpkg: error processing package snapd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on language-selector-common (= 0.194.1); however:
  Package language-selector-common is not configured yet.
 language-selector-gnome depends on python3:any; however:
  Package python3 is not configured yet.
 language-selector-gnome depends on python3-gi; however:
  Package python3-gi is not configured yet.
 language-selector-gnome depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.


dpkg: error processing package language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-dbus (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python3-cups (>= 1.9.60); however:
  Package python3-cups is not configured yet.
 system-config-printer-common depends on python3-cupshelpers (= 1.5.11-2ubuntu2); however:
  Package python3-cupshelpers is not configured yet.
 system-config-printer-common depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 system-config-printer-common depends on python3-gi; however:
  Package python3-gi is not configured yet.
 system-config-printer-common depends on python3-requests; however:
  Package python3-requests is not configured yet.
 system-config-printer-common depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on language-selector-gnome (>= 0.179~); however:
  Package language-selector-gnome is not configured yet.
 gnome-control-center depends on system-config-printer (>= 1.4); however:
  Package system-config-printer is not configured yet.


dpkg: error processing package gnome-control-center (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-cairo:amd64:
 python3-cairo:amd64 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-cairo:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-distro:
 python3-distro depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python3-distro depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-distro (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.


dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-pymacaroons:
 python3-pymacaroons depends on python3-nacl (>= 1.1.2); however:
  Package python3-nacl is not configured yet.
 python3-pymacaroons depends on python3-six (>= 1.8.0); however:
  Package python3-six is not configured yet.
 python3-pymacaroons depends on python3:any; however:
  Package python3 is not configured yet.


dpkg: error processing package python3-pymacaroons (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on gnome-shell | policykit-1-gnome | polkit-1-auth-agent; however:
  Package gnome-shell is not configured yet.
  Package policykit-1-gnome is not installed.
  Package polkit-1-auth-agent is not installed.
  Package gnome-shell which provides polkit-1-auth-agent is not configured yet.


dpkg: error processing package network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-talloc:
 python3-talloc depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-talloc depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-talloc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gnome-online-accounts:
 gnome-online-accounts depends on python3; however:
  Package python3 is not configured yet.
 gnome-online-accounts depends on python3-macaroonbakery; however:
  Package python3-macaroonbakery is not configured yet.


dpkg: error processing package gnome-online-accounts (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3:any (>= 3.0~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-problem-report (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.7~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3:any (>= 3.3~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on aptdaemon; however:
  Package aptdaemon is not configured yet.
 python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however:
  Package python3-apt is not configured yet.
 python3-aptdaemon depends on python3-defer (>= 1.0.6); however:
  Package python3-defer is not configured yet.
 python3-aptdaemon depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 python3-aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.


dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on python3-apport; however:
  Package python3-apport is not configured yet.


dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 system-config-printer-udev depends on python3-cups (>= 1.9.42); however:
  Package python3-cups is not configured yet.
 system-config-printer-udev depends on python3-cupshelpers (>= 1.5.11-2ubuntu2); however:
  Package python3-cupshelpers is not configured yet.
 system-config-printer-udev depends on python3-dbus; however:
  Package python3-dbus is not configured yet.


dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: too many errors, stopping
Processing triggers for dictionaries-common (1.28.1) ...
update-default-wordlist:
  Could not make the default symlink to "/usr/share/dict/american-english".
  This may be a temporary problem due to installation ordering. If that
  file is not present after installation, please file a bugreport
  against wordlist package owning that file.
  
dpkg: error processing package dictionaries-common (--configure):
 installed dictionaries-common package post-installation script subprocess returned error exit status 2
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python3
 apport
 python3-tz
 python3-apport
 python3-cupshelpers
 python3-requests-unixsocket
 python3-six
 apparmor
 python3-cups
 python3-chardet
 system-config-printer
 python3-certifi
 python3-gi
 python3-requests
 python3-idna
 python3-urllib3
 gnome-shell
 ubuntu-session
 ibus
 gdm3
 python3-defer
 python3-httplib2
 language-selector-common
 virtualbox
 lsb-release
 python3-protobuf
 python3-rfc3339
 python3-macaroonbakery
 python3-aptdaemon.gtk3widgets
 python3-nacl
 python3-systemd
 python3-cffi-backend
 ubuntu-system-service
 python3-pkg-resources
 snapd
 language-selector-gnome
 python3-dbus
 system-config-printer-common
 gnome-control-center
 python3-cairo:amd64
 python3-distro
 aptdaemon
 python3-pymacaroons
 network-manager-gnome
 python3-talloc
 gnome-online-accounts
 python3-problem-report
 python3-apt
 python3-aptdaemon
 xserver-xorg
 system-config-printer-udev
 dictionaries-common
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Impavidus on 2019-07-28
Which release of Ubuntu? Do you have any idea what could have caused this issue? Can you show the output from these commands:```
sudo apt update
dpkg --list | egrep -v ^ii\|^rc
dpkg --list gedit hplip-data ibus-table python3-uno rhythmbox-plugin-alternative-toolbar rhythmbox-plugins ubuntu-drivers-common
```

---

### Post by rsteinmetz70112 on 2019-07-29
It looks like something interrupted an upgrade or install and the package database is not sure what to do. You may have missing dependencies or they may not be installed and configured. 

The clue is:
> 62 not fully installed or removed.
and 
> dpkg-query: package 'gedit' is not installed

I suggest:

```
# sudo dpkg --configure -a
# sudo apt install -f
```

You may have to run them more than once. If those run clean then:

```
# sudo apt update
# sudo apt upgrade
```

If they don't run clean post the output. You may have to manually download and install some packages, depending on how badly messed up the dpkg data is.

---

### Post by DuckHook on 2019-07-29
It is stingy of you to post the bare output without the slightest further comment on the context, background or goals you are trying to achieve.

[LIST=1]
[*]Is this a new install?
[*]Have you backed up your critical data?
[*]Are you prepared to re-install from scratch if necessary?
[*]What did you do prior to the dpkg breakage? Did you do something to cause your predicament? Please describe in detail.
[/LIST]
When asking for help, it is only common courtesy and standard netiquette to provide context and appropriate info.

---

