---
title: "Ubuntu server 16.04 apt errors"
date: 2017-10-14
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2017-10-14
Hello,
I installed Ubuntu server on a Intel processor. On top I installed Ubuntu desktop with command

```
sudo apt install ubuntu-desktop.   
``` There was no problem and the desktop came nicely. But later installing or removing packages is giving problem.

```
 printer-driver-foo2zjs-common printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix pulseaudio-module-bluetooth pyotherside python3-blinker
  python3-brlapi python3-bs4 python3-cairo python3-cffi-backend
  python3-checkbox-support python3-cryptography python3-cups
  python3-cupshelpers python3-feedparser python3-gi-cairo python3-guacamole
  python3-html5lib python3-httplib2 python3-idna python3-jinja2 python3-jwt
  python3-louis python3-lxml python3-mako python3-markupsafe python3-oauthlib
  python3-padme python3-plainbox python3-pyatspi python3-pyparsing
  python3-speechd python3-uno python3-xlsxwriter qdbus
  qml-module-io-thp-pyotherside qml-module-qt-labs-folderlistmodel
  qml-module-qt-labs-settings qml-module-qtfeedback
  qml-module-qtgraphicaleffects qml-module-qtquick-layouts
  qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qttest
  qml-module-ubuntu-components qml-module-ubuntu-layouts
  qml-module-ubuntu-onlineaccounts qml-module-ubuntu-performancemetrics
  qml-module-ubuntu-test qml-module-ubuntu-web qmlscene qt-at-spi qtchooser
  qtcore4-l10n qtdeclarative5-accounts-plugin qtdeclarative5-dev-tools
  qtdeclarative5-qtquick2-plugin qtdeclarative5-test-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qttranslations5-l10n remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc rfkill rhythmbox rhythmbox-data
  rhythmbox-plugin-zeitgeist rhythmbox-plugins sbsigntool seahorse
  secureboot-db session-shortcuts shotwell shotwell-common
  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password
  signon-ui signon-ui-service signon-ui-x11 signond simple-scan
  snapd-login-service sni-qt speech-dispatcher speech-dispatcher-audio-plugins
  suru-icon-theme syslinux syslinux-common syslinux-legacy
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev tcl tcl8.6 thunderbird thunderbird-gnome-support
  tk tk8.6 toshset transmission-common transmission-gtk
  ttf-ancient-fonts-symbola ubuntu-artwork ubuntu-docs ubuntu-mobile-icons
  ubuntu-session ubuntu-settings ubuntu-software ubuntu-sounds
  ubuntu-system-service ubuntu-touch-sounds ubuntu-ui-toolkit-theme
  ubuntu-wallpapers ubuntu-wallpapers-xenial unity
  unity-accessibility-profiles unity-asset-pool unity-control-center
  unity-control-center-faces unity-control-center-signon unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-lens-applications unity-lens-files unity-lens-music unity-lens-photos
  unity-lens-video unity-schemas unity-scope-calculator
  unity-scope-chromiumbookmarks unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gdrive unity-scope-home
  unity-scope-manpages unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-video-remote unity-scope-virtualbox
  unity-scope-yelp unity-scope-zotero unity-scopes-master-default
  unity-scopes-runner unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-qml unity-webapps-service uno-libs3 unzip
  upower ure usb-creator-common usb-creator-gtk usb-modeswitch
  usb-modeswitch-data vbetool vino webapp-container webbrowser-app whoopsie
  whoopsie-preferences wpasupplicant x11-apps x11-session-utils x11-xkb-utils
  xbrlapi xcursor-themes xdg-user-dirs-gtk xdiagnose xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xinit xinput xorg
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  zenity zenity-common zip
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mate-menus (1.12.0-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package mate-menus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-cairo (1.8.8-2) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-cairo (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-dbus (1.2.0-3) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-decorator (4.0.6-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-decorator (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up python-gi (3.20.0-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-gi (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up python-gobject-2 (2.28.6-12ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-gobject-2 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-cairo (>= 1.0.2-1.1); however:
  Package python-cairo is not configured yet.
 python-gtk2 depends on python-gobject-2 (>= 2.21.3); however:
  Package python-gobject-2 is not configured yet.

dpkg: error processing package python-gtk2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up python-numpy (1:1.11.0-1ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up python-ptyprocess (0.5-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-ptyprocess (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-pexpect:
 python-pexpect depends on python-ptyprocess; however:
  Package python-ptyprocess is not configured yet.

dpkg: error processing package python-pexpect (--configure):
 dependency problems - leaving unconfigured
Setting up python-pip (8.1.1-2) ...
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-pip (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up python-pkg-resources (20.7.0-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-pkg-resources (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up python-pyinotify (0.9.6-0fakesync1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-pyinotify (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-setuptools:No apport report written because MaxReports is reached already

 python-setuptools depends on python-pkg-resources (= 20.7.0-1); however:
  Package python-pkg-resources is not configured yet.

dpkg: error processing package python-setuptools (--configure):
 dependency problems - leaving unconfigured
Setting up python-wheel (0.29.0-1) ...No apport report written because MaxReports is reached already

Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error processing package python-wheel (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-scipy:
 python-scipy depends on python-decorator; however:
  Package python-decorator is not configured yet.
 python-scipy depends on python-numpy (>= 1:1.10.0~b1); however:
  Package python-numpy is not configured yet.
 python-scipy depends on python-numpy-abi9; however:
  Package python-numpy-abi9 is not installed.
  Package python-numpy which provides python-numpy-abi9 is not configured yet.

dpkg: error processing package python-scipy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 mate-menus
 python-cairo
 python-dbus
 python-decorator
 python-gi
 python-gobject-2
 python-gtk2
 python-numpy
 python-ptyprocess
 python-pexpect
 python-pip
 python-pkg-resources
 python-pyinotify
 python-setuptools
 python-wheel
 python-scipy
E: Sub-process /usr/bin/dpkg returned an error code (1)  
```
Kindly help. Any help is welcome.

---

### Post by ian-weisser on 2017-10-15
Did you alter or replace your system's original version of Python?

---

