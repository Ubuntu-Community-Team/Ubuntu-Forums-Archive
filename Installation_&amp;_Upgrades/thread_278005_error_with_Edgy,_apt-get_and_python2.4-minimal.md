---
title: "error with Edgy, apt-get and python2.4-minimal"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by BobFolkerts on 2006-10-15
*I have upgraded successfully to Edgy, but now I find that neither aptitude nor apt-get is able to upgrade my system.  Under a variety of command (upgrade,install or remove) and with a variety of options ( -f --ignore-missing) I always end up with the same error.  Here is an example:*

$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gdk-imlib1 hpijs ipython kde-guidance kdevelop3 python-adns python-cheetah
  python-ctypes python-egenix-mxdatetime python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-gadfly python-htmlgen python-htmltmpl python-imaging
  python-imaging-sane python-jabber python-kde3 python-kjbuckets python-ldap
  python-lxml python-opengl python-osd python-pam python-pexpect python-psyco
  python-pychart python-pylibacl python-pyopenssl python-pyorbit python-pyrex
  python-pyxattr python-qt3 python-reportlab python-scipy-core
  python-simpletal python-soappy python-sqlite python-syck python-xml
  python-xmpp ubuntu-minimal
The following packages will be upgraded:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater akregator app-install-data ark bluez-cups bluez-pcmcia-support
  bluez-utils brltty bsdutils console-setup dmsetup example-content fetchmail
  firefox firefox-dom-inspector flashplugin-nonfree gcj-4.1-base gettext
  gettext-base gij-4.1 hal hplip hplip-data idle-python2.4 iproute iptables
  kaddressbook kaffeine kaffeine-xine kamera karm kate kcontrol
  kdeartwork-emoticons kdeartwork-misc kdeartwork-theme-icon kdebase-bin
  kdebase-data kdebase-kio-plugins kdebluetooth kdegames-card-data
  kdegraphics-kfile-plugins kdelibs kdelibs-data kdelibs4-dev kdelibs4c2a
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins
  kdepim-kresources kdepim-wizards kdeprint kdesdk-doc-html kdesdk-scripts
  kdesktop kdewallpapers kdewebdev kdm kdnssd kdvi kenolaba kfax kfaxview
  kfilereplace kfind kfouleggs kgamma kghostview kgoldrunner khelpcenter
  kicker kicker-applets kiconedit kimagemapeditor kjumpingcube klaptopdaemon
  klibc-utils klickety klines klinkstatus klipper kmahjongg kmail kmailcvt
  kmenuedit kmilo kmines kmoon kmrml knewsticker-scripts knode knotes kodo
  kolf kolourpaint kommander kompare konq-plugins konqueror
  konqueror-nsplugins konquest konsole kontact konversation kooka korganizer
  kpager kpat kpdf kpersonalizer kpf kpoker kpovmodeler kppp krdc kreversi
  krfb kruler ksame kscreensaver kscreensaver-xsavers kshisen ksig ksirtet
  ksmiletris ksmserver ksnake ksnapshot ksokoban kspaceduel ksplash ksvg
  ksysguard ksysguardd kteatime ktip ktorrent ktron ktuberling ktux
  kubuntu-artwork-usplash kubuntu-default-settings kview kviewshell
  kwalletmanager kweather kwifimanager kwin kwin4 kworldclock kxsldbg
  language-pack-en language-pack-en-base language-pack-kde-en
  language-pack-kde-en-base launchpad-integration libbluetooth2 libbrlapi1
  libcamel1.2-8 libcvsservice0 libdevmapper1.02 libdirectfb-0.9-24
  libebook1.2-9 libedata-book1.2-2 libedataserver1.2-7 libgcj-common libgcj7-0
  libgcj7-awt libgcj7-jar libgd2-noxpm libgl1-mesa-dev libgl1-mesa-dri
  libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev libgmp3c2 libhal-storage1
  libhal1 libkcal2b libkdegames1 libkdepim1a libkleopatra1 libklibc libkmime2
  libkonq4 libkpathsea4 libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 liblaunchpad-integration0 liblockfile1 liblpint-bonobo0
  liblrdf0 libmimelib1c2a libmusicbrainz4c2a libmysqlclient15off libnspr4
  libnss3 libopenobex-1.0-0 libpoppler1 libpoppler1-qt libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql libsasl2 libsasl2-dev libsasl2-modules
  libselinux1 libxml2 libxml2-dev libxml2-utils linux-image-2.6.17-10-386
  linux-libc-dev lskat mesa-common-dev mount netkit-inetd openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us
  openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-industrial openoffice.org-writer pgadmin3 pgadmin3-data
  poppler-utils popularity-contest pychecker python-apt python-eunuchs
  python-uno python2.4-doc python2.4-examples qobex quanta quanta-data
  reiserfsprogs strace tasksel tasksel-data tetex-bin ttf-opensymbol tzdata
  ubuntu-standard umbrello util-linux util-linux-locales wine xmms
  xserver-xorg-input-wacom zlib-bin
269 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
11 not fully installed or removed.
Need to get 0B/343MB of archives.
After unpacking 15.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up python2.4-minimal (2.4.4~c1-0ubuntu1) ...
Linking and byte-compiling packages for runtime python2.4...
INFO: using old version '/usr/bin/python2.3'
pycentral: pycentral rtinstall: package python-logilab-common: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
pycentral rtinstall: package python-logilab-common: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


*If I try with ignore missing, I get a different error, *
$ sudo apt-get --ignore-missing -f upgrade
Reading package lists... Done
...
269 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
11 not fully installed or removed.
Need to get 0B/343MB of archives.
After unpacking 15.2MB of additional disk space will be used.
Do you want to continue [Y/n]?  Y
Abort.

*Any ideas how I can get my packaging fixed?  I have both an onboard Intel video and an nVidia card, so I have been having trouble getting the install CD to work.  I wouldn't mind reinstalling, but even that is problematic*.

---

### Post by BobFolkerts on 2006-10-15
*Perhaps this will help.  There seem to be issues with my python 2.4 packages:*

$ sudo dpkg --audit
Password:
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 python2.4-dev        Header files and a static library for Python (v2.4)
 python2.4            An interactive high-level object-oriented language (versi
 python-glade2        GTK+ bindings: Glade support
 python-gtk2          Python bindings for the GTK+ widget set
 streamtuner          A GUI audio stream directory browser
 python-glade-1.2     Put a bit of python code behind interfaces built with GLA
 python-logilab-astng extend python's abstract syntax tree

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 python-logilab-common useful miscellaneous modules used by Logilab projects
 python-gtk-1.2       GTK support module for Python
 python-gobject       Python bindings for the GObject
 python2.4-minimal    A minimal subset of the Python language (version 2.4)

---

### Post by NeoLithium on 2006-10-15
try running 
```

sudo dpkg --configure -a

then 

sudo apt-get clean

and finally

sudo apt-get dist-upgrade


```

Everything went good for me after that.

---

### Post by BobFolkerts on 2006-10-15
Thanks for the quick reply, I'm getting an error on the first command:
```
$ sudo dpkg --configure -a
Setting up python-logilab-common (0.16.1-2) ...
INFO: using old version '/usr/bin/python2.3'
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
dpkg: error processing python-logilab-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gtk-1.2 (0.6.12-5) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gobject
dpkg: error processing python-gtk-1.2 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gobject (2.12.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gtk
dpkg: error processing python-gobject (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-glade-1.2:
 python-glade-1.2 depends on python-gtk-1.2 (= 0.6.12-5); however:
  Package python-gtk-1.2 is not configured yet.
dpkg: error processing python-glade-1.2 (--configure):
 dependency problems - leaving unconfigured
Setting up python2.4-minimal (2.4.4~c1-0ubuntu1) ...
Linking and byte-compiling packages for runtime python2.4...
INFO: using old version '/usr/bin/python2.3'
pycentral: pycentral rtinstall: package python-logilab-common: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
pycentral rtinstall: package python-logilab-common: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-logilab-astng:
 python-logilab-astng depends on python-logilab-common (>= 0.16.1-2); however:
  Package python-logilab-common is not configured yet.
dpkg: error processing python-logilab-astng (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4~c1-0ubuntu1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.12.1); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of streamtuner:
 streamtuner depends on python-gtk2 (>= 2.6.0); however:
  Package python-gtk2 is not configured yet.
 streamtuner depends on python2.4 (>= 2.3.90); however:
  Package python2.4 is not configured yet.
dpkg: error processing streamtuner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dev:
 python2.4-dev depends on python2.4 (= 2.4.4~c1-0ubuntu1); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python-gtk2 (= 2.10.3-0ubuntu3); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-logilab-common
 python-gtk-1.2
 python-gobject
 python-glade-1.2
 python2.4-minimal
 python-logilab-astng
 python2.4
 python-gtk2
 streamtuner
 python2.4-dev
 python-glade2

```

The lines 
> INFO: using old version '/usr/bin/python2.3'
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/logilab/common/ureports/__init__.py
make me think I will remove the ureports package in python2.4 and try again.  I'm a little worried that python2.3 is giving me errors in a python-2.4 package.

---

### Post by BobFolkerts on 2006-10-15
After removing the logilab python 2.4 package, aptitude & apt-get are running, so I should be off and running.  There are a bunch of Zope related packages that now have unmet dependancies, so I will remove them, do the dist-upgrade and then reinstall the latest Zope packages.  I'll report back with my successes and/or failures.  Thanks again Neo:)

---

### Post by BobFolkerts on 2006-10-15
I managed to get through an upgrade & almost everything is working well again.  There are still issues with some of the gtk packages.  I should probably have said that I am running Kubuntu, so Gnome support isn't a huge issue with me.  After a successful upgrade, I reran the command to show what isn't working:

```
$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up python-gtk-1.2 (0.6.12-5) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gobject
dpkg: error processing python-gtk-1.2 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-glade-1.2:
 python-glade-1.2 depends on python-gtk-1.2 (= 0.6.12-5); however:
  Package python-gtk-1.2 is not configured yet.
dpkg: error processing python-glade-1.2 (--configure):
 dependency problems - leaving unconfigured
Setting up python-gobject (2.12.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gtk
dpkg: error processing python-gobject (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.12.1); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python-gtk2 (= 2.10.3-0ubuntu3); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of streamtuner:
 streamtuner depends on python-gtk2 (>= 2.6.0); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing streamtuner (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gtk-1.2
 python-glade-1.2
 python-gobject
 python-gtk2
 python-glade2
 streamtuner
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-gtk-1.2 (0.6.12-5) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gobject
dpkg: error processing python-gtk-1.2 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-gobject (2.12.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 281, in ?
    process(basedir,install_modules(py_installed))
  File "/usr/sbin/update-python-modules", line 154, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 121, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite pygtk.py which is already provided by /usr/share/python-support/python-gtk
dpkg: error processing python-gobject (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-glade-1.2:
 python-glade-1.2 depends on python-gtk-1.2 (= 0.6.12-5); however:
  Package python-gtk-1.2 is not configured yet.
dpkg: error processing python-glade-1.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.12.1); however:
  Package python-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of streamtuner:
 streamtuner depends on python-gtk2 (>= 2.6.0); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing streamtuner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python-gtk2 (= 2.10.3-0ubuntu3); however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-gtk-1.2
 python-gobject
 python-glade-1.2
 python-gtk2
 streamtuner
 python-glade2

```
This is a huge improvement over no aptitude working.  I then removed the broken packages & it seems all is well.

---

### Post by NeoLithium on 2006-10-15
I'm glad that worked out for you. The first time I installed edgy, I just reinstalled the whole thing and was careful with the repositories...*shrug*  Seems a little easier the way you did it; but I'm a sucker for punishment ;)

---

