---
title: "[SOLVED] Update manager not working: python errors."
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by mattydee on 2008-05-12
I am running 7.10 and the update manager doesn't work. Nothing happens when I select it from the menu, and when I run it from the command line, I get the following error:
```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 59, in <module>
    import dbus
  File "/var/lib/python-support/python2.5/dbus/__init__.py", line 96, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 45, in <module>
    from dbus.bus import BusConnection
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 22, in <module>
    import logging
  File "logging/__init__.py", line 29, in <module>
ImportError: /usr/lib/python2.5/lib-dynload/cStringIO.so: invalid ELF header
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 36, in apport_excepthook
    from cStringIO import StringIO
ImportError: /usr/lib/python2.5/lib-dynload/cStringIO.so: invalid ELF header

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 59, in <module>
    import dbus
  File "/var/lib/python-support/python2.5/dbus/__init__.py", line 96, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 45, in <module>
    from dbus.bus import BusConnection
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 22, in <module>
    import logging
  File "logging/__init__.py", line 29, in <module>
ImportError: /usr/lib/python2.5/lib-dynload/cStringIO.so: invalid ELF header
```

Something seems wrong with python...

---

### Post by zenwalker on 2008-05-12
Seems like a problem with Python or Update manager. 

Just update that package by first updating u r local cahche to the correct repo of ubuntu

---

### Post by iaculallad on 2008-05-12
Execute sudo apt-get update if it prompts you an error

---

### Post by mattydee on 2008-05-12
> **zenwalker said:**
> Seems like a problem with Python or Update manager. 

I'm pretty sure the problem is with python since the printers settings module gives me a similar error. 
> Just update that package by first updating u r local cahche to the correct repo of ubuntu
I'm not sure how to do that, but I can update fine using apt-get or synaptic. I would just like to solve this python(2.5) problem though and get everything working. 

Thanks

---

### Post by zenwalker on 2008-05-12
Launch syanptic, update the cache using Reload. After things completed, update ur python package.

Make sure u r using correct repo links to u r Ubuntu ver. Check in /etc/apt/source.lst file i guess.

---

### Post by iaculallad on 2008-05-12
Could you try this one:

sudo apt-get update
sudo apt-cache search python | grep 2.5

does it show you any error?

---

### Post by mattydee on 2008-05-12
> **iaculallad said:**
> Could you try this one:

sudo apt-get update
sudo apt-cache search python | grep 2.5

does it show you any error?

Doesn't seem to show any errors: 
```
python-dbg - Debug Build of the Python Interpreter (version 2.5)
idle-python2.5 - An IDE for Python (v2.5) using Tkinter
python2.5 - An interactive high-level object-oriented language (version 2.5)
python2.5-dbg - Debug Build of the Python Interpreter (version 2.5)
python2.5-dev - Header files and a static library for Python (v2.5)
python2.5-doc - Documentation for the high-level object-oriented language Python (v2.5)
python2.5-examples - Examples for the Python language (v2.5)
python2.5-minimal - A minimal subset of the Python language (version 2.5)

```

---

### Post by iaculallad on 2008-05-12
Could you post the message this gives you:

sudo apt-cache search python

---

### Post by mattydee on 2008-05-12
```
bicyclerepair - A refactoring tool for python
bittornado - bittorrent client with enhanced curses interface
dbus - simple interprocess messaging system
diveintopython - free Python book for experienced programmers
diveintopython-zh - free Python book for experienced programmers (zh translation)
doxygen - Documentation system for C, C++, Java, Python and other languages
doxygen-doc - Documentation for doxygen
epydoc-doc - official documentation for the Epydoc package
exuberant-ctags - build tag file indexes of source code definitions
idle - An IDE for Python using Tkinter (default version)
inkscape - vector-based drawing program
jython - Python seamlessly integrated with Java
jython-doc - Jython documentation including API docs
kate-plugins - plugins for Kate, the KDE Advanced Text Editor
libapache2-mod-python - Apache 2 module that embeds Python within the server
libapache2-mod-python-doc - Apache 2 module that embeds Python within the server
libbsf-java - Bean Scripting Framework to support scripting languages in Java
libdbus-1-3 - simple interprocess messaging system
libgtksourceview-common - common files for the GTK+ syntax highlighting widget
libidl0 - library for parsing CORBA IDL files
libnettle-dev - low level cryptographic library (development files)
libnettle2 - low level cryptographic library
libpythonize0 - Python packages to support KDE applications (library)
libpythonize0-dev - Python packages to support KDE applications (development)
libxslt1-dbg - XSLT processing library - debugging symbols
linda - Debian package checker, not unlike lintian
moinmoin-common - Python clone of WikiWiki - common data
pychecker - Finds common bugs in python source code
pykdeextensions - Python packages to support KDE applications (scripts)
pymacs - interface between Emacs Lisp and Python
pyqt-tools - pyuic and pylupdate for Qt3
python - An interactive high-level object-oriented language (default version)
python-adns - Python bindings to the asynchronous DNS resolver library
python-all - Package depending on all supported Python runtime versions
python-all-dbg - Package depending on all supported Python debugging packages
python-all-dev - Package depending on all supported Python development packages
python-apport - apport crash report handling library
python-apt - Python interface to libapt-pkg
python-apt-dbg - Python interface to libapt-pkg (debug extension)
python-at-spi - Assistive Technology Service Provider Interface - Python bindings
python-at-spi-dbg - Assistive Technology Service Provider Interface - Python bindings (debug extension)
python-cairo - Python bindings for the Cairo vector graphics library
python-cairo-dbg - Python bindings for the Cairo vector graphics library (debug extension)
python-cairo-dev - Python cairo bindings: development files
python-cddb - Python interface to CD-IDs and FreeDB
python-central - register and build utility for Python packages
python-clientcookie - Python module for automating HTTP Cookie management
python-clientform - module for handling HTML forms on the client side
python-crypto - cryptographic algorithms and protocols for Python
python-crypto-dbg - cryptographic algorithms and protocols for Python (debug extension)
python-cups - Python bindings for CUPS
python-dbg - Debug Build of the Python Interpreter (version 2.5)
python-dbus - simple interprocess messaging system (Python interface)
python-dbus-dbg - simple interprocess messaging system (Python interface, debug extension)
python-dev - Header files and a static library for Python (default)
python-dictclient - Python client library for DICT (RFC2229) protocol
python-dictdlib - Python library for generating dictd dictionaries
python-distutils-extra - enhancements to the Python build system
python-doc - Documentation for the high-level object-oriented language Python
python-docutils - Utilities for the documentation of Python modules
python-egenix-mx-base-dbg - extension files for the egenix-mx-base distribution (debug build)
python-egenix-mx-base-dev - development files for the egenix-mx-base distribution
python-egenix-mxbeebase - on-disk B+Tree based database kit for Python
python-egenix-mxdatetime - date and time handling routines for Python
python-egenix-mxproxy - generic proxy wrapper type for Python
python-egenix-mxqueue - fast and memory-efficient queue for Python
python-egenix-mxstack - fast and memory-efficient stack for Python
python-egenix-mxtexttools - fast text processing tools for Python
python-egenix-mxtools - collection of additional builtins for Python
python-egenix-mxuid - unique identifiers for Python
python-egenix-mxurl - flexible URL datatype for Python
python-epydoc - tool for generating Python API documentation
python-examples - Examples for the Python language (default version)
python-exo - Library with extensions for Xfce (python bindings)
python-exo-dbg - Library with extensions for Xfce (python debug bindings)
python-eyed3 - Python module for id3-tags manipulation
python-gamin - Python binding for the gamin client library
python-gamin-dbg - Python binding for the gamin client library (debug extension)
python-gconf - Python bindings for GConf2
python-gconf-dbg - Python bindings for GConf2 (debug extension)
python-gd - Python module wrapper for libgd
python-gd-dbg - Python module wrapper for libgd (debug extension)
python-gdbm - GNU dbm database support for Python
python-genetic - genetic algorithms in Python
python-geoip - python bindings for the GeoIP IP-to-country resolver library
python-geoip-dbg - python bindings for the GeoIP IP-to-country resolver library (debug extension)
python-glade2 - GTK+ bindings: Glade support
python-glade2-dbg - GTK+ bindings: Glade support (debug extension)
python-gnome2 - Python bindings for the GNOME desktop environment
python-gnome2-dbg - Python bindings for the GNOME desktop environment (debug extension)
python-gnome2-desktop - Python bindings for the GNOME desktop environment
python-gnome2-desktop-dbg - Python bindings for the GNOME desktop environment (extension module)
python-gnome2-desktop-dev - Python bindings for the GNOME desktop environment
python-gnome2-desktop-doc - Python bindings for the GNOME desktop environment - documentation
python-gnome2-dev - Python bindings for the GNOME desktop environment
python-gnome2-extras - Python bindings for the GNOME desktop environment
python-gnome2-extras-dbg - Python bindings for the GNOME desktop environment (debug extensions)
python-gnome2-extras-dev - Python bindings for the GNOME desktop environment
python-gnome2-extras-doc - Python bindings for the GNOME desktop environment - documentation
python-gnomecanvas - Python bindings for gnomecanvas (debug extension)
python-gnomecanvas-dbg - Python bindings for gnomecanvas (debug extension)
python-gnupginterface - Python interface to GnuPG (GPG)
python-gobject - Python bindings for the GObject library
python-gobject-dbg - Python bindings for the GObject library (debug extension)
python-gobject-dev - Development headers for the GObject python bindings
python-gobject-doc - Python bindings for the GObject - documentation
python-gpod - a library to read and write songs and artwork to an iPod
python-gst0.10 - generic media-playing framework (Python bindings)
python-gst0.10-dbg - generic media-playing framework (Python debug bindings)
python-gtk2 - Python bindings for the GTK+ widget set
python-gtk2-dbg - Python bindings for the GTK+ widget set (debug extension)
python-gtk2-dev - GTK+ bindings: devel files
python-gtk2-doc - Python bindings for the GTK+ widget set - documentation
python-gtk2-tutorial - tutorial for the GTK2 python library
python-gtkhtml2 - Python bindings for the GtkHTML2 library
python-gtkhtml2-dbg - Python bindings for the GtkHTML2 library (debug extension)
python-htmlgen - Python library for the generation of HTML
python-imaging - Python Imaging Library
python-imaging-dbg - Python Imaging Library (debug extension)
python-imaging-doc - Examples for the Python Imaging Library
python-imaging-sane - Python Imaging Library - SANE interface
python-imaging-sane-dbg - Python Imaging Library - SANE interface (debug extension)
python-imaging-tk - Python Imaging Library - ImageTk Module
python-imaging-tk-dbg - Python Imaging Library - ImageTk Module (debug extension)
python-jabber - Python module for the Jabber instant messaging platform
python-kde3 - KDE3 bindings for Python
python-kde3-dbg - KDE3 bindings for Python (debug extensions)
python-kde3-dev - KDE3 bindings for Python - Development files and scripts
python-kde3-doc - Documentation and examples for PyKDE
python-launchpad-bugs - simple Python Interface to Bugs in Launchpad
python-launchpad-integration - library for launchpad integration
python-launchpad-integration-dbg - library for launchpad integration (debug extension)
python-ldap - An LDAP interface module for Python
python-ldap-dbg - An LDAP interface module for Python (debug extension)
python-librdf - Python language bindings for the Redland RDF library
python-libxslt1 - Python bindings for libxslt1
python-libxslt1-dbg - Python bindings for libxslt1 (debug extension)
python-ltsp - provides ltsp related functions
python-magic - File type determination library using "magic" numbers (python bindings)
python-magic-dbg - File type determination library using "magic" numbers (python bindings/debug)
python-mechanize - stateful programmatic web browsing
python-minimal - A minimal subset of the Python language (default version)
python-moinmoin - Python clone of WikiWiki - library
python-mutagen - audio metadata editing library
python-mysqldb - A Python interface to MySQL
python-mysqldb-dbg - A Python interface to MySQL (debug extension)
python-nevow - Web application templating system for Python and Twisted
python-newt - A NEWT module for Python
python-newt-dbg - A NEWT module for Python (debug extension)
python-notify - Python bindings for libnotify
python-numarray - An array processing package modelled after Python-Numeric
python-numarray-dbg - An array processing package modelled after Python-Numeric (debug extension)
python-numarray-doc - An array processing package for Python (documentation)
python-numeric - Numerical (matrix-oriented) Mathematics for Python
python-numeric-dbg - Numerical (matrix-oriented) Mathematics for Python (debug extension)
python-numeric-ext - Extension modules for Numeric Python
python-numeric-ext-dbg - Extension modules for Numeric Python
python-orca-brlapi - python bindings for braille display access via BRLTTY
python-orca-brlapi-dbg - python debug bindings for braille display access via BRLTTY
python-pam - A Python interface to the PAM library
python-pam-dbg - A Python interface to the PAM library (debug extension)
python-paramiko - make SSH2 connections with python
python-pexpect - Python module for automating interactive applications
python-pisock - Python module to communicate with PalmOS PDA
python-pisock-dbg - Python module to communicate with PalmOS PDA (debug extension)
python-pqueue - a priority queue extension for Python
python-problem-report - python library to handle problem reports
python-pullparser - simple "pull API" for HTML parsing
python-pyao - A Python interface to the Audio Output library
python-pyao-dbg - A Python interface to the Audio Output library (debug extension)
python-pycurl - Python bindings to libcurl
python-pycurl-dbg - Python bindings to libcurl (debug extension)
python-pygresql - PostgreSQL module for Python
python-pygresql-dbg - PostgreSQL module for Python (debug extension)
python-pygtksourceview - python bindings for the version 2 of the GtkSourceView library
python-pylibacl - module for manipulating POSIX.1e ACLs
python-pylibacl-dbg - module for manipulating POSIX.1e ACLs (debug extension)
python-pyogg - A Python interface to the Ogg library
python-pyogg-dbg - A Python interface to the Ogg library (debug extension)
python-pyopenssl - Python wrapper around the OpenSSL library
python-pyopenssl-dbg - Python wrapper around the OpenSSL library (debug extension)
python-pyorbit - A Python language binding for the ORBit2 CORBA implementation
python-pyorbit-dbg - Python bindings for ORBit2 CORBA (debug extension)
python-pyorbit-dev - PyORBit: development files
python-pyrex - compile native-code modules for python from python-like syntax
python-pysqlite2 - python interface to SQLite 3
python-pysqlite2-dbg - python interface to SQLite 3 (debug extension)
python-pyvorbis - A Python interface to the Ogg Vorbis library
python-pyvorbis-dbg - A Python interface to the Ogg Vorbis library (debug extension)
python-pyxattr - module for manipulating filesystem extended attributes
python-pyxattr-dbg - module for manipulating filesystem extended attributes (debug extension)
python-qt-dev - Qt bindings for Python - Development files
python-qt3 - Qt3 bindings for Python
python-qt3-dbg - Qt3 bindings for Python (debug extension)
python-qt3-doc - Qt bindings for Python - Documentation and examples
python-qtext - Qt extensions for PyQt
python-qtext-dbg - Qt debug extensions for PyQt
python-reportlab - ReportLab library to create PDF documents using Python
python-reportlab-doc - Documentation for the ReportLab Python library (PDF format)
python-roman - A module for generating/analyzing Roman numerals
python-selinux - Python bindings to SELinux shared libraries
python-selinux-dbg - Python bindings to SELinux shared libraries (debug extension)
python-setuptools - Python Distutils Enhancements
python-sexy - python language bindings for libsexy
python-simpletal - Simple TAL, TALES and METAL implementation
python-sip4 - Python/C++ bindings generator runtime library
python-sip4-dbg - Python/C++ bindings generator runtime library (debug extension)
python-sip4-dev - Python/C++ bindings generator development files
python-software-properties - manage the repositories that you install software from
python-subversion - Python bindings for Subversion
python-subversion-dbg - Python bindings for Subversion (debug extension)
python-support - automated rebuilding support for python modules
python-tcm - control ubuntu LTSP connections
python-tk - Tkinter - Writing Tk applications with Python
python-twisted - Event-based framework for internet applications (transitional package)
python-twisted-bin - Event-based framework for internet applications
python-twisted-bin-dbg - Event-based framework for internet applications (debug extension)
python-twisted-conch - The Twisted SSH Implementation
python-twisted-core - Event-based framework for internet applications
python-twisted-lore - Documentation generator with HTML and LaTeX support
python-twisted-mail - An SMTP, IMAP and POP protocol implementation
python-twisted-names - A DNS protocol implementation with client and server
python-twisted-news - An NNTP protocol implementation with client and server
python-twisted-runner - Process management, including an inetd server
python-twisted-runner-dbg - Process management, including an inetd server (debug extension)
python-twisted-web - An HTTP protocol implementation together with clients and servers
python-twisted-web2 - An HTTP/1.1 Server Framework
python-twisted-words - Chat and Instant Messaging
python-tz - Python version of the Olson timezone database
python-unit - unit test framework for Python
python-virtkey - Library to emulate keyboard keypresses.
python-vte - Python bindings for the VTE widget set
python-vte-dbg - Python bindings for the VTE widget set (debug extension)
python-xdg - A python library to access freedesktop.org standards
python-xml - XML tools for Python
python-xml-dbg - XML tools for Python (debug extension)
python-xml-doc - XML tools for Python (documentation and examples)
python-xmpp - Python library for communication with XMPP (Jabber) servers
python-zopeinterface - The implementation of interface definitions for Zope 3
python-zopeinterface-dbg - The implementation of interface definitions for Zope 3 (debug extension)
scons - A replacement for Make
sip4 - Python/C++ bindings generator
swig - Generate scripting interfaces to C/C++ code
system-config-printer - Printer configuration GUI
yapps2 - Yet Another Python Parser System
yapps2-runtime - Yet Another Python Parser System
zope3 - Open Source Web Application Server (Libraries)
zope3-dbg - Open Source Web Application Server (debug extensions)
aap - make-like "expert system" for building software
aap-doc - make-like "expert system" for building software (documentation)
accerciser - an interactive Python accessibility explorer for the GNOME desktop
ajaxterm - Web based terminal written in python
anydbm-doc - Generic DBM-type interface for Haskell, Documentation
apoo - An Assembly course aid
bake - yet another Make replacement (python)
bayonne - Telephony server of the GNU project
blender - Very fast and versatile 3D modeller/renderer
boa-constructor - RAD tool for Python and WxWindows application
boo - a python-like language and compiler for the CLI
burn - Command line Data-CD, Audio-CD, ISO-CD, Copy-CD writing tool
cableswig - Generate wrappers for Python and Tcl from C++ code
cedar-backup2 - local and remote backups to CD-R/CD-RW media
cedar-backup2-doc - local and remote backups to CD-R/CD-RW media (documentation)
chatplus - a simple graphical LAN chat programme with unicode
chatplus-server - a simple LAN chat programme with unicode (server)
childsplay - Suite of educational games for young children
childsplay-plugins - Additional games for childsplay
codeville - a distributed version control system
comix - GTK Comic Book Viewer
configfile-doc - Parser and writer for handling sectioned config files in Haskell, Documentation
curator - Turn directories of images into static web content
cvs-syncmail - Notification program for CVS checkins
darcsweb - web interface for browsing darcs repositories
dballe - Database for punctual meteorological data (Command line tools)
ddd - The Data Display Debugger, a graphical debugger frontend
decompyle - a Python byte-code decompiler
deluge-torrent - A Bittorrent client written in Python/PyGTK
dia2code - a dia-UML code generator
dir2ogg - audio file converter into ogg-vorbis format
directoryassistant - small LDAP address book manager
dissy - graphical frontend for objdump
ditrack - lightweight distributed issue tracking system
doxygen-gui - GUI configuration tool for doxygen
driconf - DRI configuration applet
drpython - simple and customizable editor for the Python language
eclipse-pydev - Python development plug-in for Eclipse
eclipse-pydev-gcj - Python development plug-in for Eclipse (GCJ version)
eikazo - graphical frontend for SANE designed for mass-scanning
ekg - console Gadu Gadu client for UNIX systems
entity - XML-based GUI builder for GTK+
entity-c - XML-based GUI builder for GTK+ (C bindings)
entity-doc - XML-based GUI builder for GTK+
entity-gl - XML-based GUI builder for GTK+ (OpenGL bindings)
entity-javascript - XML-based GUI builder for GTK+ (JavaScript bindings)
entity-python - XML-based GUI builder for GTK+ (Python bindings)
entity-tcl - XML-based GUI builder for GTK+ (TCL bindings)
eric - full featured Python IDE
eric-api-files - API description files for use with eric
exaile - flexible audio player, similar to Amarok, but written in GTK+
exfalso - audio tag editor for GTK+
flow-tools - collects and processes NetFlow data
flow-tools-dev - development files for flow-tools
fnorb - a pure Python ORB
fnorb-doc - a pure Python ORB - programming examples
foff - X/GTK+ FTP client - Free Open FTP Face
fonttools - Converts OpenType and TrueType fonts to and from XML
fontypython - Manage your ttf fonts on Gnu/Linux
forg - Graphical Gopher Browser
freeloader - A nice GNOME download manager supporting torrents
gadfly - Server and interactive shell for Gadfly SQL database
gajim - Jabber client written in PyGTK
geany - A fast and lightweight IDE
gizmod - allows scripting of input events through Python scripts
glade - GTK+ 2 User Interface Builder
glade-gnome - GTK+ 2 User Interface Builder (with GNOME 2 support)
gmail-notify - A Gmail Notifier
gmailfs - Use your GMail account as a filesystem
gnuradio-examples - Example programs to test and use GNU Radio
gozerbot - An IRC and Jabber bot written in Python
gpib-modules-source - kernel modules for various GPIB boards
gpsd - GPS (Global Positioning System) daemon
gramps - Genealogical Research and Analysis Management Program
gvr-lessons - Interactive, introductory programming language lessons
gvrng - Interactive, introductory programming language
haskell-hsql-doc - Multi-Database Interface System for Haskell
hellanzb - Newzbin (nzb) & BinNews (bns) files downloader and post-processor
hgsvn - Scripts to work locally on Subversion checkouts using Mercurial
hslogger-doc - The Haskell Logging Framework, API Documentation
ipcheck - Dyndns.org client to register your dynamic IP address
ipython - enhanced interactive Python shell
ironpython - A Python implementation targeting the .NET and Mono platforms
jabber-irc - IRC transport for jabber
jed - editor for programmers (textmode version)
jython-gcj - Python seamlessly integrated with Java (native support for gij)
k3d - 3D modeling and animation system
karrigell - python web server application framework
karrigell-demo - Demo for karrigell
karrigell-doc - documentation for karrigell web application framework
khmerconverter - converts between legacy Khmer encodings and Unicode
kiki - tool for python regular expression testing
klone - web application development framework
klone-doc - web application development framework
klone-source - KLone development framework source code
knoda - graphical database frontend for KDE
kodos - A visual regular expression editor
labyrinth - lightweight mind-mapping tool
lampython - MPI-enhanced Python interpreter (LAM based version)
lastfmsubmitd - submission daemon for the Last.fm social music network
ldaptor-common - Pure-Python library for LDAP (common files)
libalgorithm-c3-perl - A module for merging hierarchies using the C3 algorithm
libclass-c3-perl - A pragma to use the C3 method resolution order algortihm
libclass-spiffy-perl - Spiffy Perl interface framework
libcmd-ruby - library for building line-oriented command interpreters in Ruby
libcmd-ruby1.8 - library for building line-oriented command interpreters in Ruby 1.8
libentity-dev - XML-based GUI builder for GTK+ (core library development files)
libentity0 - XML-based GUI builder for GTK+ (core library)
libfann1-dev - Fast Artificial Neural Network Library, Development files
libghc6-anydbm-dev - Generic DBM-type interface for Haskell, GHC package
libghc6-configfile-dev - Parser and writer for handling sectioned config files in Haskell, GHC package
libghc6-hdbc-dev - Haskell Database Connectivity, GHC6 package
libghc6-hslogger-dev - The Haskell Logging Framework, GHC package
libghc6-hsql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-mysql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-odbc-dev - Multi-Database Interface System for Haskell
libghc6-hsql-postgresql-dev - Multi-Database Interface System for Haskell
libghc6-hsql-sqlite-dev - Multi-Database Interface System for Haskell
libghc6-hsql-sqlite3-dev - Multi-Database Interface System for Haskell
libghc6-missingpy-dev - Python interface and utility library for Haskell
libgpib-bin - libgpib support applications and configuration
libgpib-perl - libgpib perl bindings
libgpib0 - C bindings for GPIB (IEEE 488) kernel driver -- headers
libgpib0-dev - C bindings for GPIB (IEEE 488) kernel driver -- headers
libgv-python - Python bindings for graphviz
libhdate-python - A library that help use hebrew dates
libhocr-python - Hebrew OCR library Python bindings
libhtml-parser-ruby1.8 - HTML parser library for Ruby 1.8
libhugs-hdbc - Haskell Database Connectivity, Hugs package
libhugs-hslogger - The Haskell Logging Framework, Hugs package
libicessl32 - Ice for C++ SSL plug-in
libiceutil32 - Ice for C++ misc utility library
liblangscan-ruby - Ruby module of scanners for programming languages
libming-dev - Library to generate SWF (Flash) Files (development files)
libming-util - Library to generate SWF (Flash) Files - Utilities
libming0 - Library to generate SWF (Flash) Files
libnet-z3950-perl - Perl interface to the Z39.50 information retrieval protocol
libpigment0.3-1 - User interfaces with embedded multimedia - shared library
libpigment0.3-dev - User interfaces with embedded multimedia - development files
libplplot-dev - Scientific plotting library (development files)
librfxswf-dev - RFXSWF library for SWF (Flash) generation
libsmokeqt4-1 - Smoke library for Qt4
libsmokeqt4-dev - Smoke library for Qt4
libspiffy-perl - Spiffy Perl Interface Framework For You
libswf-perl - Ming (SWF) module for Perl
libsyck0-dev - YAML parser kit -- development files
libsynopsis8 - The runtime library for Synopsis
libsynopsis8-dev - The runtime library for Synopsis (development files)
libvtk5 - Visualization Toolkit - A high level 3D visualization library
libxul0d-dbg - Development files for the Gecko engine library
libyaml-ruby - YAML for Ruby
libzeroc-ice32 - Ice for C++ runtime library
libzorp2-dev - Development files needed to compile Zorp modules
libzorpll-dev - Low level library functions for Zorp, development files
libzorpll3.0.6 - Low level library functions for Zorp
libzorpll3.0.6-dbg - Low level library functions for Zorp, debug version
luma - gui utility for accessing and managing LDAP database
lybniz - mathematical function graph plotter
mascyma - A user-friendly frontend for MAXIMA
mayavi - A scientific data visualization system
mbot - A multi purpose mail robot
medit - A useful programming and around-programming text editor
megahal - conversation simulator that can learn as you talk to it
mercurial - Scalable distributed version control system
mftrace - Converts Metafont fonts into Type1 fonts
ming-fonts-dejavu - Ming format DejaVue Fonts
ming-fonts-opensymbol - Ming format Opensymbol Fonts
mped - Minimum Profit, a programmer's text editor
mpichpython - MPI-enhanced Python interpreter (MPICH based version)
mucous - Python/curses client for museekd
musetup-gtk - Gtk based museekd configuration utility
nettle-bin - low level cryptographic library (binary tools)
nicotine - graphical client for the SoulSeek peer-to-peer system
ntlmaps - NTLM Authorization Proxy Server
nuauth-utils - Set of tools useful to nuauth admin
ocempgui-doc - documentation and examples for ocempgui
octaviz - 3D visualization system for Octave
omniidl4-python - omniORBpy2 - idl to python compiler
ontv - applet to monitor current and upcoming TV programs
oo-browser - Object Oriented Class Browser (for emacsen)
ooo2dbk - converts OpenOffice.org SXW documents to DocBook XML
papercut - simple and extensible NNTP server
paste-common - common files for paste modules
photon - a static HTML gallery generator
php5-syck - YAML parser kit -- PHP5 bindings
phpunit - Unit testing suite for PHP5
pida - Python Integrated Development Application, a Python IDE
postgresql-plpython-8.1 - PL/Python procedural language for PostgreSQL 8.1
postnews - Post Usenet articles via NNTP from the command line
pubtal - A template driven web site builder for small sites
pybaz - python bindings for the bazaar revision control system
pyblosxom - simple weblog (blog) written in Python
pyca - Certification Authority written in python
pycaml - OCaml bindings to embed Python interpreter and objects
pychess - chess graphical user interface for several chess engines
pyching - A Python program to cast and interpret I Ching hexagrams
pycmail - mail sorter written in python
pycocuma - Pythonic Contact and Customer Management
pydb - An enhanced Python command-line debugger Pydb is a command-line
pydf - colourised df(1)-clone
pydict - an English/Chinese Dictionary written with python/gtk
pyecm - Integer factorization with the Elliptic Curve Method (ECM)
pyflakes - simple python source checker
pyftpd - ftp daemon with advanced features
pyg - Python Mail <-> News Gateway
pygopherd - Modular Multiprotocol Gopher/HTTP/WAP Server in Python
pylint - python code static checker
pylize - On-Screen presentation generation tool
pymol - An OpenGL Molecular Graphics System written in Python
pympd - Frontend for mpd in the style of rhythmbox and itunes
pyneighborhood - An SMB network browser for Linux and X11 written in Python
pyntor - flexible and componentized presentation program
pypanel - lightweight panel/taskbar for X11 window managers
pype - python programmers editor
pyqonsole - X Window terminal emulation written in Python
pyragua - Pythonic editor for python coding
pyrex-mode - emacs-lisp pyrex-mode for pyrex
pyro - distributed object system for Python
pyro-doc - documentation for Pyro
pyro-examples - examples for Pyro
pyro-gui - graphicals tool for Pyro
pyroman - Firewall configuration tool for complex networks
pyslide - Tiny but powerful program to make animated presentations
pysol - X11 solitaire game written in Python
python-2play - peer-to-peer network game engine
python-4suite-doc - Documentation for 4Suite
python-4suite-rdf - An open-source platform for XML and RDF processing
python-4suite-server - 4Suite RDF Controller (Server)
python-4suite-xml - An open-source platform for XML and RDF processing
python-adodb - A database abstraction library for python
python-advas - algorithms for high-level search and information retrieval
python-albatross - Toolkit for Stateful Web Applications
python-albatross-common - Toolkit for Stateful Web Applications (common files)
python-albatross-doc - documentation for the Albatross Web Toolkit
python-alsaaudio - Alsa bindings for Python
python-annodex - Python bindings for Annodex
python-apsw - another Python SQLite 3 wrapper
python-aptsources - abstraction of the sources.list for use in python applications
python-asterisk - Asterisk Manager API interface module for Python
python-aubio - python interface for aubio, a library for audio segmentation
python-audit - Python bindings for security auditing
python-authkit - authentication and authorisation framework for Python WSGI applications
python-axiom - a Python object database
python-beagle - python bindings for beagle
python-beaker - Simple WSGI middleware that uses the Myghty Container API
python-beautifulsoup - error-tolerant HTML parser for Python
python-bibtex - Python interfaces to BibTeX and the GNU Recode library
python-biggles - Scientific plotting package for Python
python-biopython - Python library for bioinformatics
python-biopython-doc - Documentation for the Biopython library
python-biopython-martel - Flat file parser for the Biopython library
python-biopython-sql - SQL support for the Biopython library
python-bluez - Python wrappers around BlueZ for rapid bluetooth development
python-bsdiff - generate/apply a patch between two binary files (python module)
python-bughelper - Python utility classes of bughelper
python-cdd - library to make easier to build CDD related applications
python-celementtree - Light-weight toolkit for XML processing
python-celementtree-dbg - Light-weight toolkit for XML processing (debug extension)
python-cerealizer - secure pickle-like module for Python
python-chardet - universal character encoding detector
python-cheetah - text-based template engine and Python code generator
python-chm - Python binding for CHMLIB
python-clamav - Python bindings to ClamAV
python-clearsilver - python bindings for clearsilver
python-clutter - Open GL based interactive canvas library - Python bindings
python-codespeak-lib - The pylib library containing py.test, greenlets and other niceties
python-comedilib - Python wrapper for Comedilib
python-compizconfig - Compiz configuration system bindings
python-configobj - a simple but powerful config file reader and writer for Python
python-constraint - constraints satisfaction solver in Python
python-coverage - module to measure code coverage during Python execution
python-crack - Python bindings for cracklib
python-ctypes - Python package to create and manipulate C data types
python-cubictemp - small, elegant, Python-specific HTML templating system
python-cvxopt - python package for convex optimization
python-cxx - A Set of facilities to extend Python with C++
python-cxx-dev - A Set of facilities to extend Python with C++
python-daap - DAAP client implemented in Python
python-dateutil - powerful extensions to the standard datetime module
python-davlib - WebDAV client library for Python
python-dballe - Database for punctual meteorological data (Python bindings)
python-dcop - DCOP bindings for Python
python-deb822 - Read and manipulate RFC822-like files (e.g. .dsc and .changes)
python-debian - python modules to work with Debian-related data formats
python-decorator - simplify usage of python decorators by programmers
python-dhm - Collection of Python utilities
python-diacanvas2 - DiaCanvas2 library support for Python (default version)
python-dialog - Python module for making simple Text/Console-mode user interfaces
python-dispatch - Rule-based Dispatching and Generic Functions
python-dns - pydns - DNS client module for Python
python-dnspython - DNS toolkit for Python
python-dogtail - GUI test tool and automation framework
python-dsv - Python module for delimiter-separated-value files
python-ecasound2.2 - python binding files for ecasound 2.2
python-editobj - Python object editor
python-elementtidy - An HTML tree builder for ElementTree based on Tidy
python-elementtree - Light-weight toolkit for XML processing
python-elementtree-doc - Documentation for ElementTree
python-elixir - Declarative Mapper for SQLAlchemy
python-empathy - High-level library and user-interface for Telepathy
python-empy - A templating system for Python
python-empy-doc - Documentation for python-empy
python-enchant - spellchecking library for Python
python-epsilon - utility Python modules commonly used by Divmod.org project
python-eunuchs - Missing manly parts of UNIX API for Python
python-evolution - python bindings for libebook and libecal
python-excelerator - module for reading/writing Excel spreadsheet files
python-extclass - Improves integration between Python and C++ classes
python-extractor - Python bindings for GNU libextractor
python-fam - Python interface to FAM
python-feedparser - Universal Feed Parser for Python
python-fibranet - cooperative threading and event driven framework
python-flup - Implements Python Web Server Gateway Interface (WSGI)
python-foomatic - Python interface to the Foomatic printer database
python-forgethtml - Python module for easy HTML-writing
python-forgetsql - Python module for easy SQL-database access
python-formencode - validation and form generation python package
python-fpconst - Utilities for handling IEEE 754 floating point special values
python-fuse - Python bindings for FUSE (Filesystems in USErland)
python-gadfly - SQL database and parser generator for Python
python-galago - Galago presence library (Python interface)
python-galago-dev - Galago presence library (Python interface)
python-galago-gtk - GTK+ widgets for the Galago presence library (Python interface)
python-galago-gtk-dev - Galago presence library (Python interface)
python-gammu - Python module to communicate with mobile phones
python-gammu-dbg - Python module to communicate with mobile phones
python-gammu-doc - Documentation for Python module to communicate with mobile phones
python-gaphas - diagramming widget
python-gastables - compressible flow gas table modules for python
python-gdal - Python bindings to the Geospatial Data Abstraction Library
python-gdata - Google Data Python client library
python-gdchart - Python interface to GDChart
python-gdchart2 - Python OO interface to GDChart
python-gdchart2-doc - Python OO interface to GDChart - docs
python-gdk-imlib-1.2 - GTK gdk_imlib support module for Python
python-gendoc - Documentation generation from Python source files
python-genshi - python XML-based template engine
python-glade-1.2 - Put a bit of python code behind interfaces built with GLADE
python-gmpy - Interfaces GMP to Python for fast, unbound-precision computations
python-gnuplot - A Python interface to the gnuplot plotting program
python-gnuradio - Python bindings for GNU Radio
python-goopy - A small collection of handy routines for functional programming
python-gpib - libgpib python bindings (default package)
python-gtk-1.2 - GTK support module for Python
python-gtkglext1 - GtkGLext python bindings
python-gtkmvc - model-view-controller (MVC) implementation for pygtk
python-hachoir-core - Core of Hachoir framework: parse and edit binary files
python-hachoir-metadata - Program to extract metadata using Hachoir library
python-hachoir-parser - Package of Hachoir parsers used to open binary files
python-hachoir-urwid - Binary file explorer using Hachoir and urwid libraries
python-hachoir-wx - wxWidgets GUI for the hachoir binary parser
python-happydoc - Python Documentation Extraction Tool
python-happydoc-doc - Python Documentation Extraction Tool Documentation
python-hid - Python wrapper for USB HID access library
python-hildon - Python bindings for Hildon Framework
python-hildon-dev - Examples and development files Python Hildon
python-hippocanvas - Python bindings to hippo-canvas
python-hk-classes - Python scripting module for database applications library
python-html5lib - Library for working with HTML5 documents
python-htmltmpl - Templating engine for separation of code and HTML
python-httplib2 - A comprehensive HTTP client library written in python
python-id3 - Python module for id3-tags manipulation
python-ieee1284 - Python bindings to libieee1284
python-imaging-doc-html - Documentation for the Python Imaging Library.
python-imaging-doc-pdf - Documentation for the Python Imaging Library.
python-imdbpy - Python package to access the IMDb's movie database
python-impacket - Python module to easily build and dissect network protocols
python-impacket-doc - Python module to easily build and dissect network protocols
python-iplib - Python library to convert amongst many different IPv4 notations
python-ipod - ipod library
python-iptcdata - Python bindings for the iptcdata library
python-ipy - Python module for handling IPv4 and IPv6 addresses and networks
python-irclib - IRC client library for Python
python-jaxml - Python module for generating XML documents
python-jinja - small but fast and easy to use stand-alone template engine
python-json - a JSON (http://json.org) reader and writer in Python
python-jtoolkit - Web application framework
python-kerberos - A GSSAPI interface module for python
python-kid - simple Pythonic template language for XML based vocabularies
python-kinterbasdb - InterBase/Firebird support for Python
python-kiwi - a graphical framework to construct simple UI
python-kjbuckets - Set and graph data types for Python
python-lasso - Liberty ID-FF library - Python bindings
python-ldaptor - Pure-Python library for LDAP
python-ldtp - Python bindings for GNU/Linux Desktop Testing Project
python-libavg - libavg Ain't Vector Graphics
python-libbtctl - Python bindings for libbtctl Bluetooth library
python-libgmail - Python bindings to access Gmail accounts
python-libhamlib2 - Run-time library to control radio transceivers and receivers
python-liblcms - Python bindings for liblcms color management library
python-libsvm - The LIBSVM shared library Python bindings
python-libuser - user and group account administration library (development files)
python-libvirt - libvirt python bindings
python-ll-core - Python modules for colors, make, cron, daemons, URLs, templating
python-logilab-astng - extend python's abstract syntax tree
python-logilab-common - useful miscellaneous modules used by Logilab projects
python-louie - Python signal dispatching mechanism
python-lxml - pythonic binding for the libxml2 and libxslt libraries
python-lxml-dbg - pythonic binding for the libxml2 and libxslt libraries (debug extension)
python-m2crypto - a crypto and SSL toolkit for Python
python-mako - hyperfast and lightweight templating for the Python platform
python-mapscript - Python library for MapServer
python-markdown - text-to-HTML conversion library/tool
python-matplotlib - python based plotting system in a style similar to Matlab
python-matplotlib-data - python based plotting system (data package)
python-matplotlib-doc - python based plotting system (documentation package)
python-maxdb - Python bindings for MaxDB (default version)
python-maxdb-loader - Python bindings for MaxDB loader server (default version)
python-medusa - Framework for implementing asynchronous servers
python-medusa-doc - Framework for implementing asynchronous servers
python-metakit - Metakit bindings for python
python-migrate - Database schema migration for SQLAlchemy
python-milter - Python extensions for Sendmail Milter Protocol
python-ming - Ming (SWF) module for Python
python-mlmmjadmd - a daemon for remotely administrating an mlmmj installation
python-mmpython - Media Metadata for Python
python-mode - Emacs-lisp python-mode and doctest-mode for the Python language
python-mpdclient - Python interface to MPD
python-mpi - MPI module for Python
python-msn - Python client library for the MSN protocol
python-museek - Python bindings for museek+
python-musicbrainz - Second generation incarnation of the CD Index - python bindings
python-musicbrainz2 - An interface to the MusicBrainz XML web service
python-musicbrainz2-doc - An interface to the MusicBrainz XML web service (documentation)
python-myghty - Python based templating framework originally based on HTML::Mason
python-myghtyutils - Set of utility classes used by Myghty templating
python-nautilus - Python binding for Nautilus components
python-ncrypt - python wrapper for OpenSSL
python-necpp - Python module for using NEC2++
python-netcdf - A netCDF interface for Python
python-networkx - tool to manipulate and study more than complex networks
python-nifti - Python interface to the NIfTI I/O libraries
python-nose - test discovery and running for Python's unittest
python-numarray-ext - Extension modules for Python array processing (transitional package)
python-numeric-tutorial - Tutorial for the Numerical Python Library
python-numpy - Numerical Python adds a fast array facility to the Python language
python-numpy-dbg - Numerical Python adds a fast array facility to the Python language (debug extension)
python-numpy-dev - Numerical Python adds a fast array facility to the Python language
python-numpy-doc - Numpy documentation
python-numpy-ext - Numerical Python adds a fast array facility to the Python language
python-ocempgui - graphical user interface toolkit providing widgets for PyGame
python-omniorb2 - omniORBpy2 - dependency package
python-omniorb2-omg - omniORBpy2 - python 2.3 CORBA OMG standard files
python-ooolib - Python module for creating OpenDocument documents (sp.sheet/text)
python-openal - port for Python of the OpenAL library
python-opencv - Python bindings for the computer vision library
python-opengl - Python bindings to OpenGL
python-opengl-doc - Documentation for PyOpenGL
python-openid - OpenID support for servers and consumers
python-opensync - Python bindings to the opensync synchronisation engine
python-optcomplete - provide bash-completion for Python programs
python-osd - Python bindings for X On-Screen Display library
python-oss - Open Sound System (OSS) interface for Python
python-parallel - Module encapsulating access for the parallel port
python-paste - Tools for using a Web Server Gateway Interface stack
python-pastedeploy - Load, configure, and compose WSGI applications and servers
python-pastescript - serving web applications, creating file layouts for python packages
python-pastewebkit - port/reimplementation of Webware WebKit in WSGI and Paste
python-pcapy - Python interface to the libpcap packet capture library
python-petsc - Python bindings for PETSc libraries
python-pgsql - A Python DB-API 2.0 interface to PostgreSQL v7.x
python-phidgets - Phidgets access library
python-pigment - User interfaces with embedded multimedia - Python bindings
python-playerc - Networked server for robots and sensors - python wrapper
python-plplot - Python support for PLplot, a plotting library
python-ply - Lex and Yacc implementation for Python
python-ply-doc - Lex and Yacc implementation for Python
python-pmock - Python module for unit testing using mock objects
python-pmw - Pmw -- Python MegaWidgets
python-pmw-doc - Pmw -- Python MegaWidgets
python-poker-engine - multiplayer poker engine with abstract variants specifications
python-poker-network - multiplayer poker server and client library
python-poker2d - GTK poker client to play on a poker-network server
python-policyd-spf - pure-Python Postfix policy daemon for SPF checking
python-prelude - Hybrid Intrusion Detection System [ Base library ]
python-preludedb - Hybrid Intrusion Detection System [ Base library ]
python-protocols - Open Protocols and Component Adaptation for Python
python-psyco - python specializing compiler
python-psycopg - Python module for PostgreSQL
python-psycopg-dbg - Python module for PostgreSQL (debug extension)
python-psycopg2 - Python module for PostgreSQL
python-psycopg2-dbg - Python module for PostgreSQL (debug extension)
python-psycopg2da - Zope database adapter based on python-psycopg2 -- zope3 version
python-psycopgda - Zope database adapter based on python-psycopg -- zope3 version
python-pudge - documentation generator for Python projects
python-pyasn1 - ASN.1 library for Python
python-pyatspi - Assistive Technology Service Provider Interface - Python bindings
python-pychart - Python library for creating high quality charts
python-pydds - bridge double dummy solver - python extension
python-pydot - Python interface to Graphviz's dot
python-pyepl - library for coding psychology experiments in Python
python-pyepl-common - library for coding psychology experiments in Python
python-pyfits - Python module for reading, writing, and manipulating FITS files
python-pyfits-doc - Documentation for PyFITS
python-pyfribidi - FriBidi Python bindings
python-pygame - SDL bindings for games development in Python
python-pygments - syntax highlighting package written in Python
python-pygoocanvas - GooCanvas python bindings
python-pygraphviz - Python interface to the Graphviz graph layout and visualization package
python-pyinotify - Simple Linux inotify Python bindings
python-pyinotify-doc - Simple Linux inotify Python bindings
python-pyip - Python modules for raw ip packet assembling/disassembling
python-pyisomd5sum - ISO9660 checksum Python module
python-pykaraoke - free CDG/MIDI/MPEG karaoke player
python-pylons - Python web framework emphasizing flexibility and rapid development
python-pymad - Python wrapper to the MPEG Audio Decoder library
python-pyme - Python interface to the GPGME GnuPG encryption library
python-pyme-doc - Python interface to the GPGME GnuPG encryption library
python-pymetar - Python interface to METAR reports
python-pynetsnmp - Python ctypes bindings for NET-SNMP with Twisted integration
python-pynjb - python wrapper for libnjb
python-pyode - open-source Python bindings for The Open Dynamics Engine
python-pyode-doc - open-source Python bindings for The Open Dynamics Engine
python-pyorbit-omg - PyORBit - python CORBA OMG standard files
python-pyparsing - Python parsing module
python-pypoker-eval - python interface to poker hand evaluator library development files
python-pyrad - python module for creating and decoding RADIUS packets
python-pyrss2gen - A Python interface for generating RSS 2.0 feeds
python-pyscript - Python module for producing postscript graphics
python-pyscript-doc - Python module for producing postscript graphics
python-pysnmp-common - Python SNMP library for agents and managers (version selection module)
python-pysnmp-se - speed enhanced Python SNMP library for agents and managers
python-pysnmp2 - Python SNMP library for agents and managers (stable branch)
python-pysnmp4 - Python SNMP library for agents and managers (unstable branch)
python-pysnmp4-doc - Python SNMP library for agents and managers (unstable branch)
python-pysnmp4-mibs - MIBs for the Python SNMP library
python-pysqlite1.1 - python interface to SQLite 3
python-pythoncard - wxPython-based GUI construction framework (underlying Python libraries)
python-pytils - Python library for processing strings in Russian
python-pyusb - USB interface for python
python-pyvtk - module for manipulating VTK files
python-pyx - Python module for generating PostScript graphics
python-pyx-doc - Python module for generating PostScript graphics (documentation)
python-pyxine - interface to the xine media player for Python
python-pyxmpp - XMPP and Jabber implementation for Python
python-pyxmpp-doc - XMPP and Jabber implementation for Python (documentation)
python-qt3-gl - Qt3 OpenGL bindings for Python
python-qt3-gl-dbg - Qt3 OpenGL bindings for Python (debug extension)
python-quixote - A highly Pythonic Web application framework
python-quixote-doc - Quixote web application framework documentation
python-quixote1 - A highly Pythonic Web application framework
python-qwt4 - Python version of the Qwt technical widget library
python-qwt4-doc - Documentation for the Python-qwt library
python-rdflib - RDF library containing an RDF triple store and RDF/XML parser/serializer
python-renpy - framework for developing visual-novel type games
python-reportlab-accel - C coded extension accelerator for the ReportLab Toolkit
python-reportlab-accel-dbg - C coded extension accelerator for the ReportLab Toolkit (debug build)
python-reverend - general purpose Bayesian classifier for Python
python-rfxswf - Python wrapper for the rfxswf library
python-routes - Routing Recognition and Generation Tools
python-rpm - Python bindings for RPM
python-rpy - Python interface to the GNU R language and environment
python-rpy-doc - Python interface to the GNU R language (documentation package)
python-rrd - Time-series data storage and display system (Python interface)
python-scapy - Packet generator/sniffer and network scanner/discovery
python-scgi - Server-side implementation of the SCGI protocol
python-scientific - Python modules useful for scientific computing
python-scientific-doc - Python modules useful for scientific computing
python-scipy - scientific tools for Python
python-semanage - Python bindings  for SELinux policy manipulation tools
python-serial - Module encapsulating access for the serial port
python-sigmask - module for saving and restoring the signal mask.
python-simplejson - Simple, fast, extensible JSON encoder/decoder for Python
python-simpleparse - A simple parser generator for Python
python-simpy - python-based simulation package
python-simpy-doc - python-based simulation package, Documentation and examples
python-simpy-gui - python-based simulation package, GUI
python-slides - Python-based Slide Maker
python-smbpasswd - This module can generate both LANMAN and NT password hashes
python-snpp - SNPP library for Python
python-soappy - SOAP Support for Python (SOAP.py)
python-soya - high level 3D engine for Python
python-soya-doc - high level 3D engine for Python
python-sparse - Sparse linear algebra extension for Python
python-sparse-examples - Sparse linear algebra extension for Python: documentation
python-speechd - Python interface to Speech Dispatcher
python-speex - python bindings for Speex
python-spf - sender policy framework (SPF) module for Python
python-sqlalchemy - SQL toolkit and Object Relational Mapper for Python
python-sqlalchemy-doc - Documentation for the SQLAlchemy Python library
python-sqlite - python interface to SQLite 2
python-sqlite-dbg - python interface to SQLite 2 (debug extension)
python-sqlobject - python module for SQLObject
python-sqlrelay - SQL Relay Python (default version) API
python-statgrab - interface to the libstatgrab library for Python
python-stats - A collection of statistical functions for Python
python-stfl - Python bindings for the structured terminal forms language/library
python-storm - object-relational mapper (ORM) for Python
python-svn - A(nother) Python interface to Subversion
python-svn-dbg - A(nother) Python interface to Subversion (debug extension)
python-sympy - Computer Algebra System (CAS) in Python
python-tables - hierarchical database for Python based on HDF5
python-tables-doc - hierarchical database for Python based on HDF5 - documentation
python-tagpy - Python module for manipulating tags in music files
python-tau - Tuning and Analysis Utilities - support for python bindings
python-tclink - TrustCommerce credit card processing for Python
python-tcpwrap - python interface for libwrap0 (TCP wrappers)
python-telepathy - python language bindings for telepathy
python-templayer - layered template library for Python
python-testresources - testresources, a PyUnit extension for managing expensive test fixtures.
python-textile - Python parser for the Textile markup
python-tickcount - a python module to access the python interpreter tickcount.
python-tmda - TMDA Python libraries
python-tofu - high-level network game engine for Python
python-tunepimp - Python bindings for MusicBrainz tagging library
python-turbogears - Python-based web framework
python-turbojson - TurboGears template plugin that supports Json templates
python-turbokid - TurboGears template plugin that supports Kid templates
python-turbomail - multi-threaded mail queue manager for TurboGears applications
python-turbomail-doc - multi-threaded mail queue manager for TurboGears applications
python-twisted-snmp - SNMP implementation for the Twisted networking framework
python-uncertainities - Python module for working with uncertain numbers
python-urlgrabber - A high-level cross-protocol url-grabber
python-urljr - Common interface to urllib2 and curl for making HTTP requests
python-urwid - curses-based UI/widget library for Python
python-usrp - Python binding for the USRP client side library
python-utidylib - Python wrapper for TidyLib
python-utmp - python module for working with utmp
python-vipscc - image processing system good for very large images (tools)
python-visual - VPython 3D scientific visualization library
python-vobject - parse iCalendar and VCards in python
python-vtk - Python bindings for VTK
python-wavelets - python extension implementing of wavelet transformations
python-webhelpers - Library of helper functions to make writing web application templates easier
python-weblib - Yet another web programming framework for Python - library
python-weblib-doc - Yet another web programming framework for Python - docs
python-webpy - Web API for Python applications
python-webut - Miscellaneous utilities for nevow and twisted.web{,2} programming
python-wmi - DCOM/WMI client implementation, Python bindings
python-wxaddons - wxWidgets Cross-platform C++ GUI toolkit (wxPython add-on packages base)
python-wxglade - GUI designer written in Python with wxPython
python-wxgtk2.4 - wxWindows Cross-platform C++ GUI toolkit (wxPython binding)
python-wxgtk2.6 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
python-wxgtk2.6-dbg - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
python-wxgtk2.8 - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
python-wxgtk2.8-dbg - wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
python-wxtools - wxWidgets Cross-platform C++ GUI toolkit (wxPython common files)
python-wxversion - wxWidgets Cross-platform C++ GUI toolkit (wxPython version selector)
python-xapian - Xapian search engine interface for Python
python-xattr - module for manipulating filesystem extended attributes
python-xen-3.1 - python bindings for Xen, a Virtual Machine Monitor
python-xfce - Python bindings for Xfce
python-xlib - Interface for Python to the X11 Protocol
python-xmms - Python interface to XMMS
python-xmms-doc - Python interface to XMMS (documentation)
python-xmmsclient - XMMS2 - Python bindings
python-xpcom - XPCOM bindings for Python
python-yadis - Yadis service discovery library
python-yaml - PyYAML is a YAML parser and emitter for Python
python-yapgvb - Python bindings for Graphviz, using Boost.Python
python-yappy - Yet Another Parser Generator fo Python
python-yappy-doc - Documentation for yappy
python-yenc - yEnc encoding/decoding extension for Python
python-zeroc-ice - Ice for Python libraries
python-zodb - set of tools for using the Zope Object Database (ZODB)
python-zsi - Zolera Soap Infrastructure
python2.4-rfxswf - Python wrapper for the rfxswf library
python2.4-schooltool - common platform for school administration
pythoncad - Computer Aided Drafting (CAD) program
pythoncard - wxPython-based GUI construction framework (meta-package)
pythoncard-doc - wxPython-based GUI construction framework (documentation and samples)
pythoncard-tools - wxPython-based GUI construction framework (optional development tools)
pytris - two-player networked console tetris clone
pyxmms-remote - command-line interface to XMMS
pyzor - spam-catcher using a collaborative filtering network
qemulator - a solution for easy setup and management of qemu
quantlib-python - Python bindings for the Quantlib Quantitative Finance library
rats - Rough Auditing Tool for Security
regina-normal - 3-manifold topology software with normal surface support
regina-normal-doc - API docs for Regina, the 3-manifold topology software
rekall - graphical database front-end
renpy - framework for developing visual-novel type games
scalemail - Scalable virtual mail domain system built on Postfix and LDAP
scapy - dummy upgrade package for scapy -> python-scapy
sepolgen - A Python module used in SELinux policy generation
serpento - DICT server with full Unicode support
shogun-octave - Large Scale Machine Learning Toolbox
shogun-python - Large Scale Machine Learning Toolbox
shogun-python-modular - Large Scale Machine Learning Toolbox
shogun-r - Large Scale Machine Learning Toolbox
shogun-readline - Large Scale Machine Learning Toolbox
sitemap - Makes an HTML site map from meta tags from other HTML pages
skencil - Interactive vector drawing program for X11
slice2py - Slice to Python translator
slides-doc - The official documentation of slides
sloccount - Programs for counting physical source lines of code (SLOC)
snappea - a program for creating and studying hyperbolic 3-manifolds
solarwolf - Collect the boxes and don't become mad
solfege - Ear training program for GNOME2
source-highlight - convert source code to syntax highlighted document
spambayes - Python-based spam filter using statistical analysis
sql-editor - editor of SQL databases, with 'join' capability
sqlrelay - Database connection pooling, proxying and load balancing
sqlrelay-dev - SQL Relay C and C++ APIs
sqlrelay-doc - SQL Relay Documentation
streamtuner - A GUI audio stream directory browser
superkaramba - a program based on karamba improving the eyecandy of KDE
supybot - robust and user friendly Python IRC bot
svn-workbench - A Workbench for Subversion
swaml - Semantic Web Archive of Mailing Lists
swig1.3 - Generate scripting interfaces to C/C++ code
syncropated - An application for syncing music player playlists with mass storage devices
synopsis - A Source-code Introspection Tool
synopsis-doc - Documentation for synopsis
tepache - A code sketcher for python that uses pygtk and glade
texify - Beautify source code for use with LaTeX
tinywm - tiny window manager
toursst - RSS channel news items where you want them
treeline - versatile tree-like structured custom data manager
txt2regex - A Regular Expression "wizard", all written with bash2 builtins
txt2tags - a conversion tool generating HTML/SGML/LaTeX/man/MoinMoin/mgp/PageMaker files
utf8script - binfmt_misc plugin for UTF-8 scripts
vim-full - Vi IMproved - enhanced vi editor - full fledged version
vim-python - Vi IMproved - enhanced vi editor - with Python support
vtk-examples - C++, Tcl and Python example programs/scripts for VTK
vtkdata - Example data for VTK
webcpp - configurable utility to convert source code to HTML
weechat-plugins - Plugins for WeeChat
wx2.4-examples - wxWindows Cross-platform C++ GUI toolkit (examples)
wx2.6-examples - wxWidgets Cross-platform C++ GUI toolkit (examples)
wx2.8-examples - wxWidgets Cross-platform C++ GUI toolkit (examples)
xjed - editor for programmers (x11 version)
xtalk - BSD talk compatible X Window System client
zope-mysqlda - A Database Adapter for connecting Zope and MySQL
zope-portaltransforms - mimetypes based transformations for the CMF
zope-psycopgda - Zope database adapter based on python-psycopg
zope-psycopgda2 - Zope database adapter based on python-psycopg2
zope-replacesupport - Add search and replace functionality to TTW Zope objects
zope-scriptablefields - Zope tool bundle for working with component Logic
zope-securemailhost - secure MailHost reimplementation for zope
zope2.10 - Open Source Web Application Server
zope2.9 - Open Source Web Application Server
zorp - An advanced protocol analyzing firewall
zorp-modules - Default proxy modules for Zorp
ifeffit - An interactive program for XAFS analysis
mytharchive - create and burn DVD's from MythTV - binary file
mytharchive-data - create and burn DVD's from MythTV - data files
python-cdb - Python CDB (constant database) library
python-ifeffit - Python GUI interface and extensions for IFEFFIT
python-lame - Python bindings for LAME
python-profiler - deterministic profiling of any Python programs
python-psyco-doc - python specializing compiler documentation
idle-python2.4 - An IDE for Python (v2.4) using Tkinter
idle-python2.5 - An IDE for Python (v2.5) using Tkinter
pyste - Boost.Python code generator
python-cherrypy - Python web development framework
python-cherrypy3 - Python web development framework - version 3
python-django - A high-level Python Web framework
gnumeric-plugins-extra - additional plugins for the GNOME spreadsheet
libboost-dev - Boost C++ Libraries development files
libboost-python-dev - Boost.Python Library development files
libboost-python1.34.1 - Boost.Python Library
libxml2-dbg - Debugging symbols for the GNOME XML library
python-libxml2 - Python bindings for the GNOME XML library
python-libxml2-dbg - Python bindings for the GNOME XML library (debug extension)
python-uno - Python interface for OpenOffice.org
python2.4 - An interactive high-level object-oriented language (version 2.4)
python2.4-dbg - Debug Build of the Python Interpreter (version 2.4)
python2.4-dev - Header files and a static library for Python (v2.4)
python2.4-doc - Documentation for the high-level object-oriented language Python (v2.4)
python2.4-examples - Examples for the Python language (v2.4)
python2.4-minimal - A minimal subset of the Python language (version 2.4)
python2.5 - An interactive high-level object-oriented language (version 2.5)
python2.5-dbg - Debug Build of the Python Interpreter (version 2.5)
python2.5-dev - Header files and a static library for Python (v2.5)
python2.5-doc - Documentation for the high-level object-oriented language Python (v2.5)
python2.5-examples - Examples for the Python language (v2.5)
python2.5-minimal - A minimal subset of the Python language (version 2.5)
gnumed-client - [Med] Medical practice management - Client
python-avahi - Python utility package for Avahi
python-qt4-gl - Python bindings for Qt4's OpenGL module
python-qt4-gl-dbg - Python bindings for Qt4's OpenGL module (debug extension)
python-twill - A simple scripting language for Web browsing
spe - Stani's Python Editor
deskbar-applet-dbg - keyword-driven navigational bar for GNOME (python debug build)
epiphany-extensions - Extensions for Epiphany web browser
gimp-python - Python support and plugins for The GIMP
libgtksourceview2.0-common - common files for the GTK+ syntax highlighting widget
php5-cli - command-line interpreter for the php5 scripting language
postgresql-plpython-8.2 - PL/Python procedural language for PostgreSQL 8.2
python-bittorrent - Scatter-gather network file transfer
python-gmenu - an implementation of the freedesktop menu specification for GNOME
python-gmenu-dbg - Python bindings for the freedesktop menu specification for GNOME (debug extension)
python-qt4 - Python bindings for Qt4
python-qt4-dbg - Python bindings for Qt4 (debug extensions)
python-qt4-dbus - DBus Support for PyQt4
python-qt4-dbus-dbg - DBus Support for PyQt4 (debug extensions)
python-qt4-dev - Development files for PyQt4
python-qt4-doc - Documentation and examples for PyQt4
python-qt4-sql - Python bindings for Qt4's SQL module
python-qt4-sql-dbg - Python bindings for Qt4's SQL module (debug extension)
```

---

### Post by iaculallad on 2008-05-12
I see no error in here. Try reinstalling python.

---

### Post by mattydee on 2008-05-12
I did that already... no joy :(
I reinstalled the python2.5 package since the python package is a meta-package (I think) and reinstalling it wouldn't really do anything. 

Anyways, it didn't work... same error

---

### Post by mattydee on 2008-05-13
I don't get it... Invalid ELF header?

---

### Post by mattydee on 2008-05-13
I had to reinstall python2.5-minimal. I did 
sudo apt-get clean
and then did a reinstall of python2.5-minimal from synaptic.

---

