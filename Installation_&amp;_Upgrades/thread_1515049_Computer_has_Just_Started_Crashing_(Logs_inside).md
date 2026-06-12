---
title: "Computer has Just Started Crashing (Logs inside)"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by Ashocka on 2010-06-21
I was going to post this in 'x86 64-bit Users' but I don't get a "New Thread' button there.

I have had Ubuntu 10.4 running on a new install on new hard disk for a few weeks.  Just this morning it is crashing a lot.  I have msg logs at pastebin; [http://pastebin.com/NkxsCCyy](http://pastebin.com/NkxsCCyy)

I would appreciate help in detecting what is wrong.  There seems to be a number of possibilities to me, maybe they are all valid.  I'm just an average Ubuntu user with not much indepth knowledge.  

below is a dpkg listing

```
gdeering@ubuntuLTS-desktop:~$ dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  acpi-support   0.136          scripts for handling many ACPI events
ii  acpid          1.0.10-5ubuntu Advanced Configuration and Power Interface e
ii  adduser        3.112ubuntu1   add and remove users and groups
ii  adium-theme-ub 0.1-0ubuntu1   Adium message style for Ubuntu
ii  aisleriot      1:2.30.0-0ubun Solitaire card games
ii  akonadi-server 1.3.1-0ubuntu3 Akonadi PIM storage service
ii  alacarte       0.13.1-0ubuntu easy GNOME menu editing tool
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
ii  alsa-oss       1.0.17-3       ALSA wrapper for OSS applications
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities
ii  amule          2.2.6+debian0- client for the eD2k and Kad networks, like e
ii  amule-common   2.2.6+debian0- common files for the rest of aMule packages
ii  amule-utils    2.2.6+debian0- utilities for aMule (command-line version)
ii  anacron        2.3-13.1ubuntu cron-like program that doesn't go by time
ii  apache2        2.2.14-5ubuntu Apache HTTP Server metapackage
ii  apache2-mpm-pr 2.2.14-5ubuntu Apache HTTP Server - traditional non-threade
ii  apache2-utils  2.2.14-5ubuntu utility programs for webservers
ii  apache2.2-bin  2.2.14-5ubuntu Apache HTTP Server common binary files
ii  apache2.2-comm 2.2.14-5ubuntu Apache HTTP Server common files
ii  app-install-da 0.10.04.7      Ubuntu applications (data files)
ii  app-install-da 0.2ubuntu1     Medibuntu applications (data files)
ii  app-install-da 12.10.04       Application Installer (data files for partne
ii  apparmor       2.5-0ubuntu3   User-space parser utility for AppArmor
ii  apparmor-utils 2.5-0ubuntu3   Utilities for controlling AppArmor
ii  apport         1.13.3-0ubuntu automatically generate crash reports for deb
ii  apport-gtk     1.13.3-0ubuntu GTK+ frontend for the apport crash report sy
ii  apport-hooks-m 1medibuntu1    Apport hooks for Medibuntu
ii  apport-symptom 0.9            symptom scripts for apport
ii  apt            0.7.25.3ubuntu Advanced front-end for dpkg
ii  apt-show-versi 0.16           lists available package versions with distri
ii  apt-transport- 0.7.25.3ubuntu APT https transport
ii  apt-utils      0.7.25.3ubuntu APT utility programs
ii  apt-xapian-ind 0.25ubuntu2    maintenance tools for a Xapian index of Debi
ii  aptdaemon      0.11+bzr345-0u transaction based package management service
ii  aptitude       0.4.11.11-1ubu terminal-based package manager
ii  apturl         0.4.1ubuntu4   install packages using the apt protocol - GT
ii  apturl-common  0.4.1ubuntu4   install packages using the apt protocol - co
ii  aspell         0.60.6-3ubuntu GNU Aspell spell-checker
ii  aspell-en      6.0-0-5.1ubunt English dictionary for GNU Aspell
ii  at             3.1.11-1ubuntu Delayed job execution and batch processing
ii  at-spi         1.30.0-0ubuntu Assistive Technology Service Provider Interf
ii  avahi-autoipd  0.6.25-1ubuntu Avahi IPv4LL network address configuration d
ii  avahi-daemon   0.6.25-1ubuntu Avahi mDNS/DNS-SD daemon
ii  avahi-utils    0.6.25-1ubuntu Avahi browsing, publishing and discovery uti
ii  avidemux       1:2.5.2-0ubunt a free video editor - GTK version
ii  avidemux-commo 1:2.5.2-0ubunt a free video editor - Internationalization f
ii  avidemux-plugi 1:2.5.2-0ubunt a free video editor - common files for plugi
ii  avidemux-plugi 1:2.5.2-0ubunt a free video editor - GTK plugins
ii  base-files     5.0.0ubuntu20  Debian base system miscellaneous files
ii  base-passwd    3.5.22         Debian base system master password and group
ii  bash           4.1-2ubuntu3   The GNU Bourne Again SHell
ii  bash-completio 1:1.1-3ubuntu2 programmable completion for the bash shell
ii  bc             1.06.95-2      The GNU bc arbitrary precision calculator la
ii  bcmwl-modalias 5.60.48.36+bdc Modaliases for the Broadcom 802.11 Linux STA
ii  bind9-host     1:9.7.0.dfsg.P Version of 'host' bundled with BIND 9.X
ii  binfmt-support 1.2.18         Support for extra binary formats
ii  binutils       2.20.1-3ubuntu The GNU assembler, linker and binary utiliti
ii  bluez          4.60-0ubuntu8  Bluetooth tools and daemons
ii  bluez-alsa     4.60-0ubuntu8  Bluetooth audio support
ii  bluez-cups     4.60-0ubuntu8  Bluetooth printer driver for CUPS
ii  bluez-gstreame 4.60-0ubuntu8  Bluetooth GStreamer support
ii  bogofilter     1.2.1-0ubuntu1 a fast Bayesian spam filter (dummy package)
ii  bogofilter-bdb 1.2.1-0ubuntu1 a fast Bayesian spam filter (Berkeley DB)
ii  bogofilter-com 1.2.1-0ubuntu1 a fast Bayesian spam filter (common files)
ii  branding-ubunt 0.4-0ubuntu1   Replacement artwork with Ubuntu branding
ii  brasero        2.30.1-0ubuntu CD/DVD burning application for GNOME
ii  brasero-common 2.30.1-0ubuntu Common files for the Brasero CD burning appl
ii  brltty         4.1-2ubuntu6   Access software for a blind person using a b
ii  brltty-x11     4.1-2ubuntu6   Access software for a blind person using a b
ii  bsdmainutils   8.0.1ubuntu1   collection of more utilities from FreeBSD
ii  bsdutils       1:2.17.2-0ubun Basic utilities from 4.4BSD-Lite
ii  busybox-initra 1:1.13.3-1ubun Standalone shell setup for initramfs
ii  busybox-static 1:1.13.3-1ubun Standalone rescue shell with tons of builtin
ii  byobu          2.68-0ubuntu1  a set of useful profiles and a profile-switc
ii  bzip2          1.0.5-4        high-quality block-sorting file compressor -
ii  bzr            2.1.1-1        easy to use distributed version control syst
ii  bzr-explorer   1.0.1-0ubuntu1 GUI application for using Bazaar
ii  bzrtools       2.1.0-1        Collection of tools for bzr
ii  ca-certificate 20090814       Common CA certificates
ii  ca-certificate 20100406ubuntu Common CA certificates (JKS keystore)
ii  cabextract     1.2-3          a program to extract Microsoft Cabinet files
ii  capplets-data  1:2.30.1-0ubun configuration applets for GNOME - data files
ii  cdparanoia     3.10.2+debian- audio extraction tool for sampling CDs
ii  cervisia       4:4.4.2-0ubunt CVS client for KDE 4
ii  checkbox       0.9.1          Checkbox System Testing
ii  checkbox-gtk   0.9.1          Checkbox GTK Interface
ii  chmsee         1.0.7-1.2ubunt A chm file viewer written in GTK+
ii  clamav         0.96.1+dfsg-0u anti-virus utility for Unix - command-line i
ii  clamav-base    0.96.1+dfsg-0u anti-virus utility for Unix - base package
ii  clamav-freshcl 0.96.1+dfsg-0u anti-virus utility for Unix - virus database
ii  clamtk         4.25-1         graphical front-end for ClamAV
ii  cli-common     0.7            common files between all CLI packages
ii  command-not-fo 0.2.40ubuntu5  Suggest installation of packages in interact
ii  command-not-fo 0.2.40ubuntu5  Set of data files for command-not-found.
ii  compiz         1:0.8.4-0ubunt OpenGL window and compositing manager
ii  compiz-core    1:0.8.4-0ubunt OpenGL window and compositing manager
ii  compiz-fusion- 0.8.4-0ubuntu3 Collection of plugins from OpenCompositing f
ii  compiz-gnome   1:0.8.4-0ubunt OpenGL window and compositing manager - GNOM
ii  compiz-plugins 1:0.8.4-0ubunt OpenGL window and compositing manager - plug
ii  compizconfig-b 0.8.4-0ubuntu2 Settings library for plugins - OpenCompositi
ii  computer-janit 1.14.1-0ubuntu clean up a system so it's more like a freshl
ii  computer-janit 1.14.1-0ubuntu clean up a system so it's more like a freshl
ii  console-setup  1.34ubuntu15   console font and keymap setup program
ii  console-termin 4.30-2         Fixed-width fonts for fast reading on the Li
ii  consolekit     0.4.1-3ubuntu1 framework for defining and tracking users, s
ii  convertall     0.4.2-1        very flexible unit converter
ii  coreutils      7.4-2ubuntu2   The GNU core utilities
ii  couchdb-bin    0.10.0-1ubuntu RESTful document oriented database, programs
ii  cpio           2.10-1ubuntu2  GNU cpio -- a program to manage archives of 
ii  cpp            4:4.4.3-1ubunt The GNU C preprocessor (cpp)
ii  cpp-4.4        4.4.3-4ubuntu5 The GNU C preprocessor
ii  cpu-checker    0.1-0ubuntu2   tools to help evaluate certain CPU (or BIOS)
ii  cron           3.0pl1-106ubun process scheduling daemon
ii  cssed          0.4.0-3ubuntu2 graphical CSS editor
ii  cups           1.4.3-1ubuntu1 Common UNIX Printing System(tm) - server
ii  cups-bsd       1.4.3-1ubuntu1 Common UNIX Printing System(tm) - BSD comman
ii  cups-client    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - client pro
ii  cups-common    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - common fil
ii  cups-driver-gu 5.2.5-0ubuntu1 printer drivers for CUPS
ii  cvs            1:1.12.13-12ub Concurrent Versions System
ii  cvsservice     4:4.4.2-0ubunt D-Bus service for accessing CVS repositories
ii  dash           0.5.5.1-3ubunt POSIX-compliant shell
ii  dbus           1.2.16-2ubuntu simple interprocess messaging system
ii  dbus-x11       1.2.16-2ubuntu simple interprocess messaging system (X11 de
ii  dc             1.06.95-2      The GNU dc arbitrary precision reverse-polis
ii  dcraw          8.86-1build1   decode raw digital camera images
ii  debconf        1.5.28ubuntu4  Debian configuration management system
ii  debconf-i18n   1.5.28ubuntu4  full internationalization support for debcon
ii  debianutils    3.2.2          Miscellaneous utilities specific to Debian
ii  defoma         0.11.10-4ubunt Debian Font Manager -- automatic font config
ii  desktop-file-u 0.16-0ubuntu2  Utilities for .desktop files
ii  desktopcouch   0.6.4-0ubuntu3 A Desktop CouchDB instance
ii  devede         3.16.8-0ubuntu simple application to create Video DVDs
ii  dhcp3-client   3.1.3-2ubuntu3 DHCP client
ii  dhcp3-common   3.1.3-2ubuntu3 common files used by all the dhcp3* packages
ii  dictionaries-c 1.4.0ubuntu2   Common utilities for spelling dictionary too
ii  diffutils      1:2.8.1-18     File comparison utilities
ii  disksearch     1.2.1-4        Removable media search tool
ii  dkms           2.1.1.2-2fakes Dynamic Kernel Module Support Framework
ii  dmidecode      2.9-1.2        Dump Desktop Management Interface data
ii  dmsetup        2:1.02.39-1ubu The Linux Kernel Device Mapper userspace lib
ii  dmz-cursor-the 0.4.1          Style neutral, scalable cursor theme
ii  dnsmasq-base   2.52-1         A small caching DNS proxy and DHCP/TFTP serv
ii  dnsutils       1:9.7.0.dfsg.P Clients provided with BIND
ii  doc-base       0.9.5          utilities to manage online documentation
ii  docbook-defgui 2.0.17+svn7549 DocBook: The Definitive Guide - HTML version
ii  docbook-xml    4.5-7          standard XML documentation system for softwa
ii  dosfstools     3.0.7-1        utilities for making and checking MS-DOS FAT
ii  dpkg           1.15.5.6ubuntu Debian package management system
ii  dvd+rw-tools   7.1-6          DVD+-RW/R tools
ii  dvdauthor      0.6.14-3ubuntu create DVD-Video file system
ii  dvdrip         1:0.98.11-0ubu perl front end for transcode and ffmpeg
ii  dvdrip-doc     2:0.98.11-0ubu Documentation for dvd::rip
ii  dvdrip-utils   1:0.98.11-0ubu perl front end for transcode and ffmpeg (too
ii  e2fslibs       1.41.11-1ubunt ext2/ext3/ext4 file system libraries
ii  e2fsprogs      1.41.11-1ubunt ext2/ext3/ext4 file system utilities
ii  ed             1.4-1build1    The classic UNIX line editor
ii  editmoin       1.10.1-3       edit MoinMoin wiki pages with your favourite
ii  eject          2.1.5+deb1+cvs ejects CDs and operates CD-Changers under Li
ii  empathy        2.30.1-0ubuntu GNOME multi-protocol chat and call client
ii  empathy-common 2.30.1-0ubuntu GNOME multi-protocol chat and call client (c
ii  eog            2.30.0-0ubuntu Eye of GNOME graphics viewer program
ii  erlang-base    1:13.b.3-dfsg- Erlang/OTP virtual machine and base applicat
ii  erlang-crypto  1:13.b.3-dfsg- Erlang/OTP cryprographic modules
ii  erlang-inets   1:13.b.3-dfsg- Erlang/OTP Internet clients and servers
ii  erlang-mnesia  1:13.b.3-dfsg- Erlang/OTP distributed relational/object hyb
ii  erlang-public- 1:13.b.3-dfsg- Erlang/OTP public key infrastructure
ii  erlang-runtime 1:13.b.3-dfsg- Erlang/OTP runtime tracing/debugging tools
ii  erlang-ssl     1:13.b.3-dfsg- Erlang/OTP implementation of SSL
ii  erlang-syntax- 1:13.b.3-dfsg- Erlang/OTP modules for handling abstract Erl
ii  erlang-xmerl   1:13.b.3-dfsg- Erlang/OTP XML tools
ii  esound-clients 0.2.41-6ubuntu Enlightened Sound Daemon - clients
ii  esound-common  0.2.41-6ubuntu Enlightened Sound Daemon - Common files
ii  espeak         1.43.03-0ubunt A multi-lingual software speech synthesizer
ii  espeak-data    1.43.03-0ubunt A multi-lingual software speech synthesizer:
ii  evince         2.30.1-0ubuntu Document (postscript, pdf) viewer
ii  evolution      2.28.3-0ubuntu groupware suite with mail client and organiz
ii  evolution-comm 2.28.3-0ubuntu architecture independent files for Evolution
ii  evolution-couc 0.4.5-0ubuntu1 Evolution support for CouchDB databases
ii  evolution-data 2.28.3.1-0ubun evolution database backend server
ii  evolution-data 2.28.3.1-0ubun architecture independent files for Evolution
ii  evolution-exch 2.28.3-0ubuntu Exchange plugin for the Evolution groupware 
ii  evolution-indi 0.2.8-0ubuntu1 GNOME panel indicator applet for Evolution
ii  evolution-plug 2.28.3-0ubuntu standard plugins for Evolution
ii  evolution-webc 2.28.0-1       webcal: URL handler for GNOME and Evolution
ii  example-conten 41             Ubuntu example content
ii  exiv2          0.19-1         EXIF/IPTC metadata manipulation tool
ii  f-spot         0.6.1.5-2ubunt personal photo management application
ii  fakeroot       1.14.4-1ubuntu Gives a fake root environment
ii  fancontrol     1:3.1.2-2      utilities to read temperature/voltage/fan se
ii  ffmpeg         4:0.5.1-1ubunt multimedia player, server and encoder
ii  fglrx-modalias 2:8.723.1-0ubu Identifiers supported by the ATI graphics dr
ii  file           5.03-5ubuntu1  Determines file type using "magic" numbers
ii  file-roller    2.30.1.1-0ubun an archive manager for GNOME
ii  filezilla      3.3.1-1ubuntu1 Full-featured graphical FTP/FTPS/SFTP client
ii  filezilla-comm 3.3.1-1ubuntu1 Architecture independent files for filezilla
ii  findutils      4.4.2-1ubuntu1 utilities for finding files--find, xargs
ii  finger         0.17-13build1  user information lookup program
ii  firefox        3.6.3+nobinonl safe and easy web browser from Mozilla
ii  firefox-brandi 3.6.3+nobinonl Package that ships the firefox branding
ii  firefox-gnome- 3.6.3+nobinonl Support for GNOME in Mozilla Firefox
ii  firestarter    1.0.3-7ubuntu5 gtk program for managing and observing your 
ii  flashplugin-in 10.1.53.64ubun Adobe Flash Player plugin installer
ii  fontconfig     2.8.0-2ubuntu1 generic font configuration library - support
ii  fontconfig-con 2.8.0-2ubuntu1 generic font configuration library - configu
ii  foo2zjs        20100210-0ubun Support for printing to ZjStream-based print
ii  foomatic-db    20100216-0ubun OpenPrinting printer support - database
ii  foomatic-db-en 4.0.4-0ubuntu1 OpenPrinting printer support - programs
ii  foomatic-filte 4.0.4-0ubuntu1 OpenPrinting printer support - filters
ii  fping          2.4b2-to-ipv6- sends ICMP ECHO_REQUEST packets to network h
ii  freepats       20060219-1     Free patch set for MIDI audio synthesis
ii  friendly-recov 0.2.10         Make recovery more user-friendly
ii  ftp            0.17-19build1  The FTP client
ii  fuse-utils     2.8.1-1.1ubunt Filesystem in USErspace (utilities)
ii  gamin          0.1.10-1ubuntu File and directory monitoring system
ii  gawk           1:3.1.6.dfsg-4 GNU awk, a pattern scanning and processing l
ii  gbrainy        1.41-1ubuntu1  brain teaser game and trainer to have fun an
ii  gcalctool      5.30.0.is.5.28 GNOME desktop calculator
ii  gcc            4:4.4.3-1ubunt The GNU C compiler
ii  gcc-4.4        4.4.3-4ubuntu5 The GNU C compiler
ii  gcc-4.4-base   4.4.3-4ubuntu5 The GNU Compiler Collection (base package)
ii  gconf-defaults 2.28.1-0ubuntu GNOME configuration database system (system 
ii  gconf-editor   2.30.0-0ubuntu An editor for the GConf configuration system
ii  gconf2         2.28.1-0ubuntu GNOME configuration database system (support
ii  gconf2-common  2.28.1-0ubuntu GNOME configuration database system (common 
ii  gdb            7.1-1ubuntu2   The GNU Debugger
ii  gdebi          0.6.0ubuntu1   Simple tool to install deb files - GNOME GUI
ii  gdebi-core     0.6.0ubuntu1   Simple tool to install deb files
ii  gdebi-kde      0.6.0ubuntu1   Simple tool to install deb files - KDE GUI
ii  gdm            2.30.0-0ubuntu GNOME Display Manager
ii  gdm-guest-sess 0.15           gdm extension for guest session
ii  geany          0.18-1         A fast and lightweight IDE
ii  gedit          2.30.2-0ubuntu official text editor of the GNOME desktop en
ii  gedit-common   2.30.2-0ubuntu official text editor of the GNOME desktop en
ii  genisoimage    9:1.1.10-1ubun Creates ISO-9660 CD-ROM filesystem images
ii  geoip-database 1.4.6.dfsg-17  IP lookup command line tools that use the Ge
ii  gettext        0.17-8ubuntu3  GNU Internationalization utilities
ii  gettext-base   0.17-8ubuntu3  GNU Internationalization utilities for the b
ii  ghostscript    8.71.dfsg.1-0u The GPL Ghostscript PostScript/PDF interpret
ii  ghostscript-cu 8.71.dfsg.1-0u The GPL Ghostscript PostScript/PDF interpret
ii  ghostscript-x  8.71.dfsg.1-0u The GPL Ghostscript PostScript/PDF interpret
ii  gimp           2.6.8-2ubuntu1 The GNU Image Manipulation Program
ii  gimp-data      2.6.8-2ubuntu1 Data files for GIMP
ii  gimp-help-comm 2.4.1-2        Data files for the GIMP documentation
ii  gimp-help-en   2.4.1-2        Documentation for the GIMP (English)
ii  gksu           2.0.2-2ubuntu2 graphical frontend to su
ii  gnome-about    1:2.30.0-0ubun The GNOME about box
ii  gnome-accessib 2.30.0-0ubuntu accessibility themes for the GNOME desktop
ii  gnome-applets  2.30.0-0ubuntu Various applets for the GNOME panel - binary
ii  gnome-applets- 2.30.0-0ubuntu Various applets for the GNOME panel - data f
ii  gnome-bluetoot 2.30.0-0ubuntu GNOME Bluetooth tools
ii  gnome-codec-in 0.4.2ubuntu2   GStreamer codec installer
ii  gnome-commande 1.2.8.5-0ubunt nice and fast file manager for the GNOME des
ii  gnome-control- 1:2.30.1-0ubun utilities to configure the GNOME desktop
ii  gnome-desktop- 1:2.30.0-0ubun Common files for GNOME desktop apps
ii  gnome-disk-uti 2.30.1-1       manage and configure disk drives and media
ii  gnome-doc-util 0.20.0-0ubuntu a collection of documentation utilities for 
ii  gnome-games-co 1:2.30.0-0ubun Common files for GNOME Games
ii  gnome-icon-the 2.28.0-1ubuntu GNOME Desktop icon theme
ii  gnome-keyring  2.92.92.is.2.3 GNOME keyring services (daemon and tools)
ii  gnome-mag      1:0.16.1-0ubun a screen magnifier for the GNOME desktop
ii  gnome-mahjongg 1:2.30.0-0ubun Mahjongg tile solitaire game
ii  gnome-media    2.30.0-0ubuntu GNOME media utilities
ii  gnome-media-co 2.30.0-0ubuntu GNOME media utilities - common files
ii  gnome-menus    2.30.0-0ubuntu an implementation of the freedesktop menu sp
ii  gnome-mime-dat 2.18.0-1       base MIME and Application database for GNOME
ii  gnome-nettool  2.30.0-0ubuntu network information tool for GNOME
ii  gnome-orca     2.30.0-0ubuntu Scriptable screen reader
ii  gnome-panel    1:2.30.0-0ubun launcher and docking facility for GNOME
ii  gnome-panel-da 1:2.30.0-0ubun common files for the GNOME Panel
ii  gnome-power-ma 2.30.0-0ubuntu power management tool for the GNOME desktop
ii  gnome-screensa 2.30.0-0ubuntu GNOME screen saver and locker
ii  gnome-session  2.30.0-0ubuntu The GNOME Session Manager
ii  gnome-session- 2.30.0-0ubuntu The GNOME Session Manager - Minimal runtime
ii  gnome-session- 0.22-1ubuntu2  GNOME session log in and log out sound event
ii  gnome-settings 2.30.1-0ubuntu daemon handling the GNOME session settings
ii  gnome-sudoku   1:2.30.0-0ubun Sudoku number puzzle
ii  gnome-system-m 2.28.0-1ubuntu Process viewer and system resource monitor f
ii  gnome-system-t 2.30.0-0ubuntu Cross-platform configuration utilities for G
ii  gnome-terminal 2.29.6-0ubuntu The GNOME terminal emulator application
ii  gnome-terminal 2.29.6-0ubuntu Data files for the GNOME terminal emulator
ii  gnome-themes-s 2.30.0-0ubuntu selected official themes for the GNOME 2 des
ii  gnome-themes-u 0.6.1          Ubuntu community themes
ii  gnome-user-gui 2.30.0+git2010 GNOME user's guide
ii  gnome-user-gui 2.30.0+git2010 GNOME user's guide ()
ii  gnome-user-gui 2.30.0+git2010 GNOME user's guide ()
ii  gnome-user-sha 2.30.0-0ubuntu User level public file sharing via WebDAV or
ii  gnome-utils    2.30.0-0ubuntu GNOME desktop utilities
ii  gnomine        1:2.30.0-0ubun Minesweeper logic puzzle game
ii  gnupg          1.4.10-2ubuntu GNU privacy guard - a free PGP replacement
ii  gnupg-curl     1.4.10-2ubuntu GNU privacy guard - a free PGP replacement (
ii  gocr           0.46-2.1       A command line OCR
ii  gparted        0.5.1-1ubuntu2 GNOME partition editor
ii  gpgv           1.4.10-2ubuntu GNU privacy guard - signature verification t
ii  grep           2.5.4-4build1  GNU grep, egrep and fgrep
ii  groff-base     1.20.1-7       GNU troff text-formatting system (base syste
ii  grub-common    1.98-1ubuntu6  GRand Unified Bootloader, version 2 (common 
ii  grub-pc        1.98-1ubuntu6  GRand Unified Bootloader, version 2 (PC/BIOS
ii  gsfonts        1:8.11+urwcyr1 Fonts for the Ghostscript interpreter(s)
ii  gstreamer0.10- 0.10.28-1      GStreamer plugin for ALSA
ii  gstreamer0.10- 0.10.10-1      FFmpeg plugin for GStreamer
ii  gstreamer0.10- 0.10.12.debian Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10- 0.10.15-1      non-linear editing module for GStreamer
ii  gstreamer0.10- 0.0.10-2build1 ICE library (GStreamer plugin)
ii  gstreamer0.10- 0.10.18-1ubunt GStreamer plugins from the "bad" set
ii  gstreamer0.10- 0.10.18-0ubunt GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10- 0.10.28-1      GStreamer plugins from the "base" set
ii  gstreamer0.10- 0.10.28-1      GStreamer helper programs from the "base" se
ii  gstreamer0.10- 0.10.21-1ubunt GStreamer plugins from the "good" set
ii  gstreamer0.10- 0.10.14-1      GStreamer plugins from the "ugly" set
ii  gstreamer0.10- 0.10.14-0ubunt GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10- 0.10.21-1ubunt GStreamer plugin for PulseAudio
ii  gstreamer0.10- 0.10.28-1      Tools for use with GStreamer
ii  gstreamer0.10- 0.10.28-1      GStreamer plugins for X11 and Pango
ii  gtk2-engines   1:2.20.0-0ubun theme engines for GTK+ 2.x
ii  gtk2-engines-m 0.90.3+git2010 cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-p 2.20.1-0ubuntu Pixbuf-based theme for GTK+ 2.x
ii  gucharmap      1:2.30.0-0ubun Unicode character picker and font browser
ii  guile-1.8-libs 1.8.7+1-3ubunt Main Guile libraries
ii  gvfs           1.6.1-0ubuntu1 userspace virtual filesystem - server
ii  gvfs-backends  1.6.1-0ubuntu1 userspace virtual filesystem - backends
ii  gvfs-bin       1.6.1-0ubuntu1 userspace virtual filesystem - binaries
ii  gvfs-fuse      1.6.1-0ubuntu1 userspace virtual filesystem - fuse server
ii  gwibber        2.30.0.1-0ubun Open source social networking client for GNO
ii  gwibber-servic 2.30.0.1-0ubun Open source social networking client for GNO
ii  gzip           1.3.12-9ubuntu GNU compression utilities
ii  hal            0.5.14-0ubuntu Hardware Abstraction Layer
ii  hal-info       20091130-1     Hardware Abstraction Layer - fdi files
ii  hdparm         9.15-1ubuntu9  tune hard disk parameters for high performan
ii  hicolor-icon-t 0.11-1         default fallback theme for FreeDesktop.org i
ii  hostname       3.03ubuntu1    utility to set/show the host name or domain 
ii  hotssh         0.2.6-2        graphical interface to secure shell
ii  hpijs          3.10.2-2ubuntu HP Linux Printing and Imaging - gs IJS drive
ii  hplip          3.10.2-2ubuntu HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data     3.10.2-2ubuntu HP Linux Printing and Imaging - data files
ii  humanity-icon- 0.5.2          Humanity Icon theme
ii  hunspell-en-ca 1:3.2.0-3ubunt English_canadian dictionary for hunspell
ii  hunspell-en-us 20070829-4ubun English_american dictionary for hunspell
ii  ia32-libs      2.7ubuntu25    ia32 shared libraries for use on amd64 and i
ii  ibus           1.2.0.20091215 New input method framework using dbus
ii  ibus-chewing   1.2.0.20091211 chewing input engine for IBus
ii  ibus-gtk       1.2.0.20091215 New input method framework using dbus
ii  ibus-m17n      1.2.0.20091217 m17n engine for IBus
ii  ibus-pinyin    1.2.99.2009121 pinyin engine for ibus
ii  ibus-pinyin-db 1.2.99.2009121 pinyin engine for ibus, open-phrase database
ii  ibus-table     1.2.0.20100111 table engine for IBus
ii  ibus-table-can 1.2.0.20090717 Cangjie input method based on table engine o
ii  ibus-table-wub 1.2.0.20090715 Wubi input method based on table engine of i
ii  icedtea-6-jre- 6b18-1.8-0ubun Alternative JVM for OpenJDK, using Cacao
ii  icedtea6-plugi 6b18-1.8-0ubun web browser plugin based on OpenJDK and Iced
ii  icoutils       0.26.0-4ubuntu Create and extract MS Windows icons and curs
ii  ifupdown       0.6.8ubuntu29  high level tools to configure network interf
ii  im-switch      1.19           Input method switch framework
ii  imagemagick    7:6.5.7.8-1ubu image manipulation programs
ii  indicator-appl 0.3.7-0ubuntu1 GNOME panel indicator applet
ii  indicator-appl 0.3.7-0ubuntu1 Clone of the GNOME panel indicator applet
ii  indicator-appl 0.0.19-0ubuntu Application Indicators
ii  indicator-me   0.2.6-0ubuntu1 indicator showing user information and statu
ii  indicator-mess 0.3.6-0ubuntu2 GNOME panel indicator applet for messages
ii  indicator-sess 0.2.8-0ubuntu2 An indicator showing session management, sta
ii  indicator-soun 0.2.3-0ubuntu1 A system sound indicator.
ii  info           4.13a.dfsg.1-5 Standalone GNU Info documentation browser
ii  initramfs-tool 0.92bubuntu78  tools for generating an initramfs
ii  initramfs-tool 0.92bubuntu78  binaries used by initramfs-tools
ii  initscripts    2.87dsf-4ubunt scripts for initializing and shutting down t
ii  inputattach    20051019-9     utility to connect serial-attached periphera
ii  insserv        1.12.0-14      Tool to organize boot sequence using LSB ini
ii  install-info   4.13a.dfsg.1-5 Manage installed documentation in info forma
ii  install-packag 0.5.2          Install a package GUI
ii  intel-gpu-tool 1.0.2+git20100 tools for debugging the Intel graphics drive
ii  iproute        20091226-1     networking and traffic control tools
ii  iptables       1.4.4-2ubuntu2 administration tools for packet filtering an
ii  iputils-arping 3:20071127-2ub Tool to send ARP Requests for an IP address
ii  iputils-ping   3:20071127-2ub Tools to test the reachability of network ho
ii  iputils-tracep 3:20071127-2ub Tools to trace the network path to a remote 
ii  irqbalance     0.55+20091017- Daemon to balance interrupts for SMP systems
ii  iso-codes      3.12.1-1       ISO language, territory, currency, script co
ii  java-common    0.34           Base of all Java packages
ii  jockey-common  0.5.8-0ubuntu8 user interface and desktop integration for d
ii  jockey-gtk     0.5.8-0ubuntu8 GNOME user interface and desktop integration
ii  kbd            1.15-1ubuntu3  Linux console font and keytable utilities
ii  kde-l10n-engb  4:4.4.2-0ubunt British English (engb) localization for KDE
ii  kde-l10n-zhcn  4:4.4.2-0ubunt Simplified Chinese (zhcn) localization for K
ii  kde-l10n-zhtw  4:4.4.2-0ubunt Traditional Chinese (zhtw) localization for 
ii  kdebase-runtim 4:4.4.2-0ubunt runtime components from the official KDE 4 r
ii  kdebase-runtim 4:4.4.2-0ubunt shared data files for the KDE 4 base runtime
ii  kdebase-worksp 4:4.4.2-0ubunt core binaries for the KDE 4 base workspace m
ii  kdebase-worksp 4:4.4.2-0ubunt shared scripts and data files for the KDE 4 
ii  kdebase-worksp 4:4.4.2-0ubunt KDE greet libraries for authentication
ii  kdelibs-bin    4:4.4.2-0ubunt executables for all KDE 4 core applications
ii  kdelibs-data   4:3.5.10.dfsg. core shared data for all KDE applications
ii  kdelibs4c2a    4:3.5.10.dfsg. core libraries and binaries for all KDE appl
ii  kdelibs5       4:4.4.2-0ubunt core libraries for all KDE 4 applications
ii  kdelibs5-data  4:4.4.2-0ubunt core shared data for all KDE 4 applications
ii  kdepim-runtime 4:4.4.2-0ubunt Runtime components for akonadi-kde
ii  kdepimlibs-dat 4:4.4.2-0ubunt core shared data for KDE PIM 4 applications
ii  kdepimlibs5    4:4.4.2-0ubunt core libraries for KDE PIM 4 applications
ii  kdesudo        3.4.2.3-0ubunt sudo frontend for KDE4
ii  kerneloops-dae 0.12+git200902 kernel oops tracker
ii  kfilereplace-k 4:3.5.10-0ubun batch search-and-replace component for KDE
ii  kiki           0.5.6-3.1ubunt tool for python regular expression testing
ii  klibc-utils    1.5.17-4ubuntu small utilities built with klibc for early b
ii  klinkstatus-kd 4:3.5.10-0ubun web link validity checker for KDE
ii  klipper        4:4.4.2-0ubunt clipboard utility for KDE 4
ii  kommander-kde3 4:3.5.10-0ubun visual dialog builder and executor tool
ii  kompare        4:4.4.2-0ubunt file difference viewer for KDE 4
ii  kpackagekit    0.5.4-0ubuntu4 KDE package management tool using PackageKit
ii  ksysguardd     4:4.4.2-0ubunt System Guard Daemon for KDE 4
ii  kubuntu-debug- 10.04ubuntu4   Debug package installer for Kubuntu
ii  lame           3.98.2+debian- An MP3 encoding library (frontend)
ii  language-pack- 1:10.04+201004 translation updates for language English
ii  language-pack- 1:10.04+201004 translations for language English
ii  language-pack- 1:10.04+201004 GNOME translation updates for language Engli
ii  language-pack- 1:10.04+201004 GNOME translations for language English
ii  language-pack- 1:10.04+201004 GNOME translation updates for language Simpl
ii  language-pack- 1:10.04+201004 GNOME translations for language Simplified C
ii  language-pack- 1:10.04+201004 GNOME translation updates for language Tradi
ii  language-pack- 1:10.04+201004 GNOME translations for language Traditional 
ii  language-pack- 1:10.04+201004 KDE translation updates for language English
ii  language-pack- 1:10.04+201004 KDE translations for language English
ii  language-pack- 1:10.04+201004 KDE translation updates for language Simplif
ii  language-pack- 1:10.04+201004 KDE translations for language Simplified Chi
ii  language-pack- 1:10.04+201004 KDE translation updates for language Traditi
ii  language-pack- 1:10.04+201004 KDE translations for language Traditional Ch
ii  language-pack- 1:10.04+201004 translation updates for language Simplified 
ii  language-pack- 1:10.04+201004 translations for language Simplified Chinese
ii  language-pack- 1:10.04+201004 translation updates for language Traditional
ii  language-pack- 1:10.04+201004 translations for language Traditional Chines
ii  language-selec 0.5.7          Language selector for Ubuntu Linux
ii  language-selec 0.5.7          Language selector for Ubuntu Linux
ii  language-suppo 1:9.10+2009090 metapackage for English language support
ii  language-suppo 1:10.04+200912 Additional fonts metapackage for Simplified 
ii  language-suppo 1:10.04+200912 Additional fonts metapackage for Traditional
ii  language-suppo 1:10.04+200912 Input methods metapackage for Simplified Chi
ii  language-suppo 1:10.04+200912 Input methods metapackage for Traditional Ch
ii  language-suppo 1:10.04+201003 Writing aids metapackage for English
ii  laptop-detect  0.13.7ubuntu2  attempt to detect a laptop
ii  launchpad-inte 0.1.35         launchpad integration
ii  less           436-1          pager program similar to more
ii  lftp           4.0.2-1        Sophisticated command-line FTP/HTTP client p
ii  lib32asound2   1.0.22-0ubuntu shared library for ALSA applications (32 bit
ii  lib32bz2-1.0   1.0.5-4        high-quality block-sorting file compressor l
ii  lib32gcc1      1:4.4.3-4ubunt GCC support library (32 bit Version)
ii  lib32ncurses5  5.7+20090803-2 shared libraries for terminal handling (32-b
ii  lib32nss-mdns  0.10-3ubuntu4  NSS module for Multicast DNS name resolution
ii  lib32stdc++6   4.4.3-4ubuntu5 The GNU Standard C++ Library v3 (32 bit Vers
ii  lib32v4l-0     0.6.4-1ubuntu1 Collection of video4linux support libraries 
ii  lib32z1        1:1.2.3.3.dfsg compression library - 32 bit runtime
ii  liba52-0.7.4   0.7.4-13ubuntu library for decoding ATSC A/52 streams
ii  libaa1         1.4p5-38build1 ascii art library
ii  libaccess-brid 1.26.2-3       Java Access Bridge for GNOME
ii  libaccess-brid 1.26.2-3       Java Access Bridge for GNOME (jni bindings)
ii  libacl1        2.2.49-2       Access control list shared library
ii  libakonadipriv 1.3.1-0ubuntu3 libraries for the Akonadi PIM storage servic
ii  libanthy0      9100h-0ubuntu2 input method for Japanese - runtime library
ii  libanyevent-pe 5.240-1        Perl framework to handle multiple event loop
ii  libapache2-mod 2.4.6-1        Apache 2 FastCGI module for long-running CGI
ii  libapache2-mod 5.3.2-1ubuntu4 server-side, HTML-embedded scripting languag
ii  libapache2-mod 2.8-2ubuntu1   Python WSGI adapter module for Apache
ii  libapparmor-pe 2.5-0ubuntu3   AppArmor library Perl bindings
ii  libapparmor1   2.5-0ubuntu3   changehat AppArmor library
ii  libappindicato 0.0.19-0ubuntu Application Indicators
ii  libapr1        1.3.8-1build1  The Apache Portable Runtime Library
ii  libaprutil1    1.3.9+dfsg-3bu The Apache Portable Runtime Utility Library
ii  libaprutil1-db 1.3.9+dfsg-3bu The Apache Portable Runtime Utility Library 
ii  libaprutil1-ld 1.3.9+dfsg-3bu The Apache Portable Runtime Utility Library 
ii  libapt-pkg-per 0.1.24         Perl interface to libapt-pkg
ii  libarchive1    2.8.0-2        Single library to read/write tar, cpio, pax,
ii  libart-2.0-2   2.3.20-2build1 Library of functions for 2D graphics - runti
ii  libart2.0-cil  2.24.1-6ubuntu CLI binding for libart 2.3
ii  libasound2     1.0.22-0ubuntu shared library for ALSA applications
ii  libasound2-plu 1.0.22-0ubuntu ALSA library additional plugins
ii  libaspell15    0.60.6-3ubuntu GNU Aspell spell-checker runtime library
ii  libass4        0.9.9-0ubuntu1 library for SSA/*** subtitles rendering
ii  libasync-inter 1.02-1         Perl module to allow C/XS libraries to inter
ii  libatasmart4   0.17+git201002 ATA S.M.A.R.T. reading and parsing library
ii  libatk1.0-0    1.30.0-0ubuntu The ATK accessibility toolkit
ii  libatk1.0-data 1.30.0-0ubuntu Common files for the ATK accessibility toolk
ii  libatm1        1:2.5.1-1.2    shared library for ATM (Asynchronous Transfe
ii  libatspi1.0-0  1.30.0-0ubuntu C binding libraries of at-spi for GNOME Acce
ii  libattica0     0.1.3-0ubuntu1 a Qt library that implements the Open Collab
ii  libattr1       1:2.4.44-1     Extended attribute shared library
ii  libaudio2      1.9.2-3        Network Audio System - shared libraries
ii  libaudiofile0  0.2.6-8ubuntu1 Open-source version of SGI's audiofile libra
ii  libauthen-pam- 0.16-2         Perl interface to PAM library
ii  libavahi-clien 0.6.25-1ubuntu Avahi client library
ii  libavahi-commo 0.6.25-1ubuntu Avahi common data files
ii  libavahi-commo 0.6.25-1ubuntu Avahi common library
ii  libavahi-core6 0.6.25-1ubuntu Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1 0.6.25-1ubuntu Avahi glib integration library
ii  libavahi-gobje 0.6.25-1ubuntu Avahi GObject library
ii  libavahi-qt3-1 0.6.25-1ubuntu Avahi Qt 3 integration library
ii  libavahi-ui0   0.6.25-1ubuntu Avahi GTK+ User interface library
ii  libavc1394-0   0.5.3-1build4  control IEEE 1394 audio/video devices
ii  libavcodec-ext 4:0.5.1-1ubunt ffmpeg codec library
rc  libavcodec52   4:0.5.1-1ubunt ffmpeg codec library
ii  libavdevice52  4:0.5.1-1ubunt ffmpeg device handling library
ii  libavfilter0   4:0.5.1-1ubunt ffmpeg video filtering library
ii  libavformat-ex 4:0.5.1-1ubunt ffmpeg file format library
rc  libavformat52  4:0.5.1-1ubunt ffmpeg file format library
ii  libavidemux0   1:2.5.2-0ubunt a free video editor - shared libraries
ii  libavutil-extr 4:0.5.1-1ubunt ffmpeg utility library
rc  libavutil49    4:0.5.1-1ubunt ffmpeg utility library
ii  libbabl-0.0-0  0.0.22-1build1 Dynamic, any to any, pixel format conversion
ii  libbeagle1     0.3.9-1build1  library for accessing beagle using C
ii  libbind9-60    1:9.7.0.dfsg.P BIND9 Shared Library used by BIND
ii  libbit-vector- 7.1-1          Perl module for bit vectors and more
ii  libblkid1      2.17.2-0ubuntu block device id library
ii  libbluetooth3  4.60-0ubuntu8  Library to use the BlueZ Linux Bluetooth sta
ii  libbonobo2-0   2.24.3-0ubuntu Bonobo CORBA interfaces library
ii  libbonobo2-com 2.24.3-0ubuntu Bonobo CORBA interfaces library -- support f
ii  libbonoboui2-0 2.24.3-0ubuntu The Bonobo UI library
ii  libbonoboui2-c 2.24.3-0ubuntu The Bonobo UI library -- common files
ii  libboost-progr 1.40.0-4ubuntu program options library for C++
ii  libbrasero-med 2.30.1-0ubuntu CD/DVD burning library for GNOME - runtime
ii  libbrlapi0.5   4.1-2ubuntu6   braille display access via BRLTTY - shared l
ii  libbsd0        0.2.0-1        utility functions from BSD systems - shared 
ii  libbz2-1.0     1.0.5-4        high-quality block-sorting file compressor l
ii  libc-bin       2.11.1-0ubuntu Embedded GNU C Library: Binaries
ii  libc-dev-bin   2.11.1-0ubuntu Embedded GNU C Library: Development binaries
ii  libc6          2.11.1-0ubuntu Embedded GNU C Library: Shared libraries
ii  libc6-dev      2.11.1-0ubuntu Embedded GNU C Library: Development Librarie
ii  libc6-i386     2.11.1-0ubuntu GNU C Library: 32-bit shared libraries for A
ii  libcaca0       0.99.beta16-3  colour ASCII art library
ii  libcairo-perl  1.061-1build1  Perl interface to the Cairo graphics library
ii  libcairo2      1.8.10-2ubuntu The Cairo 2D vector graphics library
ii  libcairomm-1.0 1.8.4-0ubuntu1 C++ wrappers for Cairo (shared libraries)
ii  libcamel1.2-14 2.28.3.1-0ubun The Evolution MIME message handling library
ii  libcanberra-gt 0.22-1ubuntu2  translates Gtk+ widgets signals to event sou
ii  libcanberra-gt 0.22-1ubuntu2  Gtk+ helper for playing widget event sounds 
ii  libcanberra-pu 0.22-1ubuntu2  PulseAudio backend for libcanberra
ii  libcanberra0   0.22-1ubuntu2  a simple abstract interface for playing even
ii  libcap-ng0     0.6.2-4        An alternate posix capabilities library
ii  libcap2        1:2.17-2ubuntu support for getting/setting POSIX.1e capabil
ii  libcarp-clan-p 6.02-1         Perl enhancement to Carp error logging facil
ii  libcdaudio1    0.99.12p2-9    library for controlling a CD-ROM when playin
ii  libcddb2       1.3.2-0ubuntu1 library to access CDDB data - runtime files
ii  libcdio-cdda0  0.81-4         library to read and control digital audio CD
ii  libcdio-parano 0.81-4         library to read digital audio CDs with error
ii  libcdio10      0.81-4         library to read and control CD-ROM
ii  libcdparanoia0 3.10.2+debian- audio extraction tool for sampling CDs (libr
ii  libcelt0-0     0.7.1-1        The CELT codec runtime library
ii  libchewing3    0.3.2-2        intelligent phonetic input method library
ii  libchewing3-da 0.3.2-2        intelligent phonetic input method library - 
ii  libchm1        2:0.40-2       library for dealing with Microsoft CHM files
ii  libck-connecto 0.4.1-3ubuntu1 ConsoleKit libraries
ii  libclamav6     0.96.1+dfsg-0u anti-virus utility for Unix - library
ii  libclass-acces 0.34-1         Perl module that automatically generates acc
ii  libclucene0ldb 0.9.21b-2      library for full-featured text search engine
ii  libclutter-1.0 1.2.4-0ubuntu1 Open GL based interactive canvas library
ii  libclutter-gtk 0.10.4-0ubuntu Open GL based interactive canvas library GTK
ii  libcolamd2.7.1 1:3.4.0-1ubunt column approximate minimum degree ordering l
ii  libcomerr2     1.41.11-1ubunt common error description library
ii  libcommon-sens 3.00-1         module that implements some sane defaults fo
ii  libcompizconfi 0.8.4-0ubuntu2 Settings library for plugins - OpenCompositi
ii  libcouchdb-gli 0.6.3-0ubuntu1 GLib-based API for CouchDB
ii  libcroco3      0.6.2-1        a generic Cascading Style Sheet (CSS) parsin
ii  libcrypto++8   5.6.0-5        General purpose cryptographic library - shar
ii  libcryptui0    2.30.0-0ubuntu the UI library for DBUS functions exported b
ii  libcups2       1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Core libra
ii  libcupscgi1    1.4.3-1ubuntu1 Common UNIX Printing System(tm) - CGI librar
ii  libcupsdriver1 1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Driver lib
ii  libcupsimage2  1.4.3-1ubuntu1 Common UNIX Printing System(tm) - Raster ima
ii  libcupsmime1   1.4.3-1ubuntu1 Common UNIX Printing System(tm) - MIME libra
ii  libcupsppdc1   1.4.3-1ubuntu1 Common UNIX Printing System(tm) - PPD manipu
ii  libcurl3       7.19.7-1ubuntu Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutl 7.19.7-1ubuntu Multi-protocol file transfer library (GnuTLS
ii  libcwidget3    0.5.13-1ubuntu high-level terminal interface library for C+
ii  libdaemon0     0.14-2         lightweight C library for daemons - runtime 
ii  libdate-calc-p 6.0-1          Perl library for accessing dates
ii  libdatrie1     0.2.2-3        Double-array trie library
ii  libdb4.8       4.8.24-1ubuntu Berkeley v4.8 Database Libraries [runtime]
ii  libdbd-mysql-p 4.012-1ubuntu1 A Perl5 database interface to the MySQL data
ii  libdbi-perl    1.609-1build1  Perl Database Interface (DBI)
ii  libdbus-1-3    1.2.16-2ubuntu simple interprocess messaging system
ii  libdbus-glib-1 0.84-1         simple interprocess messaging system (GLib-b
ii  libdbusmenu-gl 0.2.9-0ubuntu3 Menus over DBus shared library for glib
ii  libdbusmenu-gt 0.2.9-0ubuntu3 Menus over DBus shared library for GTK
ii  libdbusmenu-qt 0.3.2-0ubuntu1 a Qt library that implements the DBusMenu sp
ii  libdc1394-22   2.1.2-2        high level programming interface for IEEE139
ii  libdca0        0.0.5-3        decoding library for DTS Coherent Acoustics 
ii  libdecoration0 1:0.8.4-0ubunt Compiz window decoration library
ii  libdesktopcouc 0.6.3-0ubuntu1 Glib-based API for Desktopcouch
ii  libdevkit-powe 1:0.9.1-1      abstraction for power management - shared li
ii  libdevmapper1. 2:1.02.39-1ubu The Linux Kernel Device Mapper userspace lib
ii  libdigest-hmac 1.01-7         create standard message integrity checks
ii  libdigest-sha1 2.12-1build1   NIST SHA-1 message digest algorithm
ii  libdirac-encod 1.0.2-2        open and royalty free high quality codec - e
ii  libdirectfb-1. 1.2.8-5ubuntu2 direct frame buffer graphics - shared librar
ii  libdjvulibre-t 3.5.22-1ubuntu Linguistic support files for libdjvulibre
ii  libdjvulibre21 3.5.22-1ubuntu Runtime support for the DjVu image format
ii  libdns64       1:9.7.0.dfsg.P DNS Shared Library used by BIND
ii  libdotconf1.0  1.0.13-3       Configuration file parser library - runtime 
ii  libdrm-intel1  2.4.18-1ubuntu Userspace interface to intel-specific kernel
ii  libdrm-nouveau 2.4.18-1ubuntu Userspace interface to nouveau-specific kern
ii  libdrm-radeon1 2.4.18-1ubuntu Userspace interface to radeon-specific kerne
ii  libdrm2        2.4.18-1ubuntu Userspace interface to kernel DRM services -
ii  libdv4         1.0.0-2ubuntu2 software library for DV format digital video
ii  libdvbpsi5     0.1.6-1        library for MPEG TS and DVB PSI tables decod
ii  libdvd0        0.1.12-0.2     extract video and audio tracks - runtime fil
ii  libdvdcss2     1.2.10-0.3medi Simple foundation for reading DVDs - runtime
ii  libdvdnav4     4.1.3-6        DVD navigation library
ii  libdvdread4    4.1.3-8ubuntu1 library for reading DVDs
ii  libebackend1.2 2.28.3.1-0ubun Utility library for evolution data servers
ii  libebml0       0.7.7-3.1      access library for the EBML format
ii  libebook1.2-9  2.28.3.1-0ubun Client library for evolution address books
ii  libecal1.2-7   2.28.3.1-0ubun Client library for evolution calendars
ii  libedata-book1 2.28.3.1-0ubun Backend library for evolution address books
ii  libedata-cal1. 2.28.3.1-0ubun Backend library for evolution calendars
ii  libedataserver 2.28.3.1-0ubun Utility library for evolution data servers
ii  libedataserver 2.28.3.1-0ubun GUI utility library for evolution data serve
ii  libedit2       2.11-20080614- BSD editline and history libraries
ii  libeggdbus-1-0 0.6-1          D-Bus bindings for GObject
ii  libegroupwise1 2.28.3.1-0ubun Client library for accessing groupwise POA t
ii  libelf1        0.143-1        library to read and write ELF files
ii  libenca0       1.12-1         Extremely Naive Charset Analyser - shared li
ii  libenchant1c2a 1.6.0-0ubuntu1 a wrapper library for various spell checker 
ii  libept0        0.5.30         High-level library for managing Debian packa
ii  libesd0        0.2.41-6ubuntu Enlightened Sound Daemon - Shared libraries
ii  libespeak1     1.43.03-0ubunt A multi-lingual software speech synthesizer:
ii  libevdocument2 2.30.1-0ubuntu GNOME document viewer backend library
ii  libevent-1.4-2 1.4.13-stable- An asynchronous event notification library
ii  libevent-execf 0.64-0ubuntu2  High level API for event-based execution flo
ii  libevent-perl  1.12-1         generic Perl event loop module
ii  libevent-rpc-p 1.01-1         Event based transparent Client/Server RPC fr
ii  libevview2     2.30.1-0ubuntu GNOME document viewer view library
ii  libexchange-st 2.28.3.1-0ubun Client library for accessing Exchange server
ii  libexempi3     2.1.1-1build2  library to parse XMP metadata (Library)
ii  libexif12      0.6.19-1       library to parse EXIF files
ii  libexiv2-6     0.19-1         EXIF/IPTC metadata manipulation library
ii  libexpat1      2.0.1-7ubuntu1 XML parsing C library - runtime library
ii  libfaac0       1.26-0.1ubuntu an AAC audio encoder - library files
ii  libfaad2       2.7-4          freeware Advanced Audio Decoder - runtime fi
ii  libffi5        3.0.9-1        Foreign Function Interface library runtime
ii  libfftw3-3     3.2.2-1        library for computing Fast Fourier Transform
ii  libfile-copy-r 0.38-1         Perl extension for recursively copying files
ii  libfile-find-r 0.32-1         module to search for files based on rules
ii  libflac8       1.2.1-2build2  Free Lossless Audio Codec - runtime C librar
ii  libflickrnet2. 1:2.2.0-3      Flickr.Net API Library
ii  libflite1      1.3-release-2b a small run-time speech synthesis engine - s
ii  libfont-afm-pe 1.20-1         Font::AFM - Interface to Adobe Font Metrics 
ii  libfontconfig1 2.8.0-2ubuntu1 generic font configuration library - runtime
ii  libfontenc1    1:1.0.5-1      X11 font encoding library
ii  libfreetype6   2.3.11-1ubuntu FreeType 2 font engine, shared library files
ii  libfreezethaw- 0.45-1         converting Perl structures to strings and ba
ii  libfribidi0    0.19.2-1       Free Implementation of the Unicode BiDi algo
ii  libfs6         2:1.0.2-1build X11 Font Services library
ii  libfuse2       2.8.1-1.1ubunt Filesystem in USErspace library
ii  libgadu3       1:1.9.0~rc2-1  Gadu-Gadu protocol library - runtime files
ii  libgail-common 2.20.1-0ubuntu GNOME Accessibility Implementation Library -
ii  libgail-gnome- 1.20.1-2       GNOME Accessibility Implementation Module fo
ii  libgail18      2.20.1-0ubuntu GNOME Accessibility Implementation Library -
ii  libgamin0      0.1.10-1ubuntu Client library for the gamin file and direct
ii  libgc1c2       1:6.8-1.2ubunt conservative garbage collector for C and C++
ii  libgcc1        1:4.4.3-4ubunt GCC support library
ii  libgconf2-4    2.28.1-0ubuntu GNOME configuration database system (shared 
ii  libgconf2.0-ci 2.24.1-6ubuntu CLI binding for GConf 2.24
ii  libgcr0        2.92.92.is.2.3 Library for Crypto UI related task - runtime
ii  libgcrypt11    1.4.4-5ubuntu2 LGPL Crypto library - runtime library
ii  libgd2-xpm     2.0.36~rc1~dfs GD Graphics Library version 2
ii  libgdata-commo 0.5.2-0ubuntu1 Library for accessing GData webservices - co
ii  libgdata-googl 2.28.3.1-0ubun Client library for accessing Google POA thro
ii  libgdata1.2-1  2.28.3.1-0ubun Client library for accessing Google POA thro
ii  libgdata6      0.5.2-0ubuntu1 Library for accessing GData webservices - sh
ii  libgdbm3       1.8.3-9        GNU dbm database routines (runtime version)
ii  libgdict-1.0-6 2.30.0-0ubuntu GNOME Dictionary base library
ii  libgdiplus     2.4.2-1build1  interface library for System.Drawing of Mono
ii  libgdu-gtk0    2.30.1-1       GTK+ standard dialog library for libgdu
ii  libgdu0        2.30.1-1       GObject based Disk Utility Library
ii  libgegl-0.0-0  0.0.22-0ubuntu Generic Graphics Library
ii  libgeoip1      1.4.6.dfsg-17  A non-DNS IP-to-country resolver library
ii  libgif4        4.1.6-9        library for GIF images (library)
ii  libgimp2.0     2.6.8-2ubuntu1 Libraries for the GNU Image Manipulation Pro
ii  libgksu2-0     2.0.13~pre1-1u library providing su and sudo functionality
ii  libgl1-mesa-dr 7.7.1-1ubuntu3 A free implementation of the OpenGL API -- D
ii  libgl1-mesa-gl 7.7.1-1ubuntu3 A free implementation of the OpenGL API -- G
ii  libglade2-0    1:2.6.4-1build library to load .glade files at runtime
ii  libglade2.0-ci 2.12.9-4       CLI binding for the Glade libraries 2.6
ii  libglib-perl   1:1.222-1      Perl interface to the GLib and GObject libra
ii  libglib2.0-0   2.24.1-0ubuntu The GLib library of C routines
ii  libglib2.0-cil 2.12.9-4       CLI binding for the GLib utility library 2.1
ii  libglib2.0-dat 2.24.1-0ubuntu Common files for GLib library
ii  libglibmm-2.4- 2.24.2-0ubuntu C++ wrapper for the GLib toolkit (shared lib
ii  libglitz-glx1  0.5.6-1build1  Glitz OpenGL library GLX backend
ii  libglitz1      0.5.6-1build1  Glitz OpenGL image compositing library
ii  libglu1-mesa   7.7.1-1ubuntu3 The OpenGL utility library (GLU)
ii  libgme0        0.5.5-1        Playback library for video game music files 
ii  libgmime-2.4-2 2.4.14-1+nmu1  MIME message parser and creator library - ru
ii  libgmime2.4-ci 2.4.14-1+nmu1  CLI binding for the GMime library
ii  libgmp3c2      2:4.3.2+dfsg-1 Multiprecision arithmetic library
ii  libgnome-bluet 2.30.0-0ubuntu GNOME Bluetooth tools - support library
ii  libgnome-deskt 1:2.30.0-0ubun Utility library for loading .desktop files -
ii  libgnome-keyri 2.30.0-0ubuntu GNOME keyring services library
ii  libgnome-keyri 1.0.0-3        CLI library to access the GNOME Keyring daem
ii  libgnome-mag2  1:0.16.1-0ubun screen magnification library for the GNOME d
ii  libgnome-media 2.30.0-0ubuntu runtime libraries for the GNOME media utilit
ii  libgnome-menu2 2.30.0-0ubuntu an implementation of the freedesktop menu sp
ii  libgnome-pilot 2.0.17-0ubuntu Support libraries for gnome-pilot
ii  libgnome-vfs2. 2.24.1-6ubuntu CLI binding for GnomeVFS 2.24
ii  libgnome-windo 1:2.30.1-0ubun Utility library for getting window manager s
ii  libgnome2-0    2.30.0-0ubuntu The GNOME library - runtime files
ii  libgnome2-canv 1.002-2build1  Perl interface to the GNOME canvas library
ii  libgnome2-comm 2.30.0-0ubuntu The GNOME library - common files
ii  libgnome2-perl 1.042-2build1  Perl interface to the GNOME libraries
ii  libgnome2-vfs- 1.081-1build1  Perl interface to the 2.x series of the GNOM
ii  libgnome2.24-c 2.24.1-6ubuntu CLI binding for GNOME 2.24
ii  libgnomecanvas 2.30.1-0ubuntu A powerful object-oriented display - runtime
ii  libgnomecanvas 2.30.1-0ubuntu A powerful object-oriented display - common 
ii  libgnomekbd-co 2.30.0-0ubuntu GNOME library to manage keyboard configurati
ii  libgnomekbd4   2.30.0-0ubuntu GNOME library to manage keyboard configurati
ii  libgnomepanel2 2.26.0-2ubuntu CLI binding for GNOME Panel 2.24
ii  libgnomeui-0   2.24.3-1       The GNOME libraries (User Interface) - runti
ii  libgnomeui-com 2.24.3-1       The GNOME libraries (User Interface) - commo
ii  libgnomevfs2-0 1:2.24.2-1ubun GNOME Virtual File System (runtime libraries
ii  libgnomevfs2-c 1:2.24.2-1ubun GNOME Virtual File System (common files)
ii  libgnomevfs2-e 1:2.24.2-1ubun GNOME Virtual File System (extra modules)
ii  libgnutls26    2.8.5-2        the GNU TLS library - runtime library
ii  libgomp1       4.4.3-4ubuntu5 GCC OpenMP (GOMP) support library
ii  libgoocanvas-c 0.15-0ubuntu2  new canvas widget for GTK+ that uses the cai
ii  libgoocanvas3  0.15-0ubuntu2  new canvas widget for GTK+ that uses the cai
ii  libgp11-0      2.92.92.is.2.3 Glib wrapper library for PKCS#11 - runtime
ii  libgpg-error0  1.6-1ubuntu2   library for common error values and messages
ii  libgpgme11     1.2.0-1.2ubunt GPGME - GnuPG Made Easy
ii  libgphoto2-2   2.4.8-0ubuntu2 gphoto2 digital camera library
ii  libgphoto2-por 2.4.8-0ubuntu2 gphoto2 digital camera port library
ii  libgpm2        1.20.4-3.2ubun General Purpose Mouse - shared library
ii  libgpod-common 0.7.93-0ubuntu common files for libgpod
ii  libgpod4       0.7.93-0ubuntu library to read and write songs and artwork 
ii  libgraphite3   1:2.3.1-0.2    SILGraphite - a "smart font" rendering engin
ii  libgraphviz4   2.20.2-8ubuntu rich set of graph drawing tools
ii  libgs8         8.71.dfsg.1-0u The Ghostscript PostScript/PDF interpreter L
ii  libgsf-1-114   1.14.16-1ubunt Structured File Library - runtime version
ii  libgsf-1-commo 1.14.16-1ubunt Structured File Library - common files
ii  libgsl0ldbl    1.13+dfsg-1    GNU Scientific Library (GSL) -- library pack
ii  libgsm1        1.0.13-3       Shared libraries for GSM speech compressor
ii  libgssapi-krb5 1.8.1+dfsg-2   MIT Kerberos runtime libraries - krb5 GSS-AP
ii  libgssdp-1.0-2 0.7.1-1        GObject-based library for SSDP
ii  libgstfarsight 0.0.17-2ubuntu Audio/Video communications framework: core l
ii  libgstreamer-p 0.10.28-1      GStreamer libraries from the "base" set
ii  libgstreamer0. 0.10.28-1      Core GStreamer libraries and elements
ii  libgtk-vnc-1.0 0.3.10-2ubuntu A VNC viewer widget for GTK+ (runtime librar
ii  libgtk2-ex-for 0.66-0ubuntu2  Makes building complex GUI's easy
ii  libgtk2-perl   1:1.221-4ubunt Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0    2.20.1-0ubuntu The GTK+ graphical user interface library
ii  libgtk2.0-bin  2.20.1-0ubuntu The programs for the GTK+ graphical user int
ii  libgtk2.0-cil  2.12.9-4       CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-comm 2.20.1-0ubuntu Common files for the GTK+ graphical user int
ii  libgtkhtml-edi 1:3.29.6.is.3. HTML rendering/editing library - editor widg
ii  libgtkhtml-edi 1:3.29.6.is.3. HTML rendering/editing library - editor widg
ii  libgtkhtml3.14 1:3.29.6.is.3. HTML rendering/editing library - runtime fil
ii  libgtkmm-2.4-1 1:2.20.3-0ubun C++ wrappers for GTK+ (shared libraries)
ii  libgtksourcevi 2.10.1-0ubuntu shared libraries for the GTK+ syntax highlig
ii  libgtksourcevi 2.10.1-0ubuntu common files for the GTK+ syntax highlightin
ii  libgtkspell0   2.0.16-1       a spell-checking addon for GTK's TextView wi
ii  libgtop2-7     2.26.1-0ubuntu gtop system monitoring library
ii  libgtop2-commo 2.26.1-0ubuntu common files for the gtop system monitoring 
ii  libgucharmap7  1:2.30.0-0ubun Unicode browser widget library (shared libra
ii  libgudev-1.0-0 1:151-12       GObject-based wrapper library for libudev
ii  libgupnp-1.0-3 0.13.2-1ubuntu GObject-based library for UPnP
ii  libgupnp-igd-1 0.1.3-4ubuntu1 library to handle UPnP IGD port mapping
ii  libgutenprint2 5.2.5-0ubuntu1 runtime for the Gutenprint printer driver li
ii  libgvfscommon0 1.6.1-0ubuntu1 userspace virtual filesystem - library
ii  libgweather-co 2.30.0-0ubuntu GWeather common files
ii  libgweather1   2.30.0-0ubuntu GWeather shared library
ii  libhal-storage 0.5.14-0ubuntu Hardware Abstraction Layer - shared library 
ii  libhal1        0.5.14-0ubuntu Hardware Abstraction Layer - shared library
ii  libhpmud0      3.10.2-2ubuntu HP Multi-Point Transport Driver (hpmud) run-
ii  libhtml-format 2.04-2         format HTML syntax trees into text, PostScri
ii  libhtml-parser 3.64-1         collection of modules that parse HTML text d
ii  libhtml-tagset 3.20-2         Data tables pertaining to HTML
ii  libhtml-templa 2.9-1          HTML::Template : A module for using HTML Tem
ii  libhtml-tree-p 3.23-1         represent and create HTML syntax trees
ii  libhttrack2    3.43.9-1ubuntu Httrack website copier library
ii  libhunspell-1. 1.2.8-6ubuntu1 spell checker and morphological analyzer (sh
ii  libhyphen0     2.4-6ubuntu1   ALTLinux hyphenation library - shared librar
ii  libibus1       1.2.0.20091215 New input method framework using dbus
ii  libical0       0.44-3         iCalendar library implementation in C (runti
ii  libice6        2:1.0.6-1      X11 Inter-Client Exchange library
ii  libicu42       4.2.1-3        International Components for Unicode
ii  libid3tag0     0.15.1b-10buil ID3 tag reading library from the MAD project
ii  libidl0        0.8.13-1       library for parsing CORBA IDL files
ii  libidn11       1.15-2         GNU Libidn library, implementation of IETF I
ii  libido-0.1-0   0.1.5-0ubuntu1 Shared library providing extra gtk menu item
ii  libiec61883-0  1.2.0-0.1build an partial implementation of IEC 61883
ii  libieee1284-3  0.2.11-5ubuntu cross-platform library for parallel port acc
ii  libijs-0.35    0.35-7build1   IJS raster image transport protocol: shared 
ii  libilmbase6    1.0.1-3build2  several utility libraries from ILM used by O
ii  libimobiledevi 0.9.7-1ubuntu1 Library for communicating with the iPhone an
ii  libindicate-gt 0.3.6-0ubuntu1 GNOME panel indicator applet - shared librar
ii  libindicate4   0.3.6-0ubuntu1 GNOME panel indicator applet - shared librar
ii  libindicator0  0.3.8-0ubuntu1 GNOME panel indicator applet - shared librar
ii  libintl-perl   1.20-1         Uniforum message translations system compati
ii  libio-pty-perl 1:1.07-2build1 Perl module for pseudo tty IO
ii  libio-socket-s 1.31-1         Perl module implementing object oriented int
ii  libio-string-p 1.08-2         Emulate IO::File interface for in-core strin
ii  libiodbc2      3.52.6-4       iODBC Driver Manager
ii  libiptcdata0   1.0.3-1ubuntu1 Library to parse IPTC metadata
ii  libisc60       1:9.7.0.dfsg.P ISC Shared Library used by BIND
ii  libisccc60     1:9.7.0.dfsg.P Command Channel Library used by BIND
ii  libisccfg60    1:9.7.0.dfsg.P Config File Handling Library used by BIND
ii  libiso9660-7   0.81-4         library to work with ISO9660 filesystems
ii  libiw30        30~pre9-3ubunt Wireless tools - library
ii  libjack0       0.118+svn3796- JACK Audio Connection Kit (libraries)
ii  libjasper1     1.900.1-7      The JasPer JPEG-2000 runtime library
ii  libjpeg-progs  7+really6b-15u Programs for manipulating JPEG files
ii  libjpeg62      6b-15ubuntu1   The Independent JPEG Group's JPEG runtime li
ii  libjs-jquery   1.3.3-2ubuntu1 JavaScript library for dynamic web applicati
ii  libjson-glib-1 0.7.6-0ubuntu2 GLib JSON manipulation library
ii  libk5crypto3   1.8.1+dfsg-2   MIT Kerberos runtime libraries - Crypto Libr
ii  libkate1       0.3.7-3        Kate is a codec for karaoke and text encapsu
ii  libkephal4     4:4.4.2-0ubunt API for easier handling of multihead systems
ii  libkeyutils1   1.2-12         Linux Key Management Utilities (library)
ii  libkfontinst4  4:4.4.2-0ubunt Libraries for font installation in kcontrol
ii  libklibc       1.5.17-4ubuntu minimal libc subset for use with initramfs
ii  libkpathsea5   2009-5ubuntu0. TeX Live: path search library for TeX (runti
ii  libkrb5-3      1.8.1+dfsg-2   MIT Kerberos runtime libraries
ii  libkrb5support 1.8.1+dfsg-2   MIT Kerberos runtime libraries - Support lib
ii  libkscreensave 4:4.4.2-0ubunt Library of the KDE Screensaver system
ii  libksgrd4      4:4.4.2-0ubunt Library for the ksysguard gui
ii  libkworkspace4 4:4.4.2-0ubunt Library for the kdebase workspace
ii  liblaunchpad-i 0.1.35         library for launchpad integration
ii  liblaunchpad-i 0.1.35         CLI bindings for liblaunchpad-integration
ii  liblcms1       1.18.dfsg-1ubu Color management library
ii  libldap-2.4-2  2.4.21-0ubuntu OpenLDAP libraries
ii  liblircclient0 0.8.6-0ubuntu4 infra-red remote control support - client li
ii  liblocale-gett 1.05-6         Using libc functions for internationalizatio
ii  liblockfile1   1.08-3ubuntu1  NFS-safe locking library, includes dotlockfi
ii  libloudmouth1- 1.4.3-5        Lightweight C Jabber library
ii  liblouis-data  1.7.0-2        Braille translation library - data
ii  liblouis0      1.7.0-2        Braille translation library - shared libs
ii  liblpint-bonob 0.1.35         library for launchpad integration
ii  libltdl7       2.2.6b-2ubuntu A system independent dlopen wrapper for GNU 
ii  liblua5.1-0    5.1.4-5        Simple, extensible, embeddable programming l
ii  liblua50       5.0.3-4        Main interpreter library for the Lua 5.0 pro
ii  liblualib50    5.0.3-4        Extension library for the Lua 5.0 programmin
ii  liblwres60     1:9.7.0.dfsg.P Lightweight Resolver Library used by BIND
ii  liblzma1       4.999.9beta+20 XZ-format compression library
ii  liblzo2-2      2.03-2         data compression library
ii  libm17n-0      1.5.5-1        a multilingual text processing library - run
ii  libmad0        0.15.1b-4ubunt MPEG audio decoder library
ii  libmagic1      5.03-5ubuntu1  File type determination library using "magic
ii  libmagickcore2 7:6.5.7.8-1ubu low-level image manipulation library
ii  libmagickcore2 7:6.5.7.8-1ubu low-level image manipulation library - extra
ii  libmagickwand2 7:6.5.7.8-1ubu image manipulation library
ii  libmailtools-p 2.05-1         Manipulate email in perl programs
ii  libmatroska0   0.8.1-1.1      extensible open standard audio/video contain
ii  libmeanwhile1  1.0.2-3build2  open implementation of the Lotus Sametime Co
ii  libmetacity-pr 1:2.30.1-0ubun library for the Metacity window manager
ii  libmimic0      1.0.4-2build1  A video codec for Mimic V2.x content
ii  libmjpegtools- 1:1.9.0-0.5ubu MJPEG video capture/editting/playback MPEG e
ii  libmldbm-perl  2.01-3         Store multidimensional hash structures in pe
ii  libmms0        0.4-2          MMS stream protocol library - shared library
ii  libmng1        1.0.9-1ubuntu1 Multiple-image Network Graphics library
ii  libmodplug0c2  1:0.8.7-1build shared libraries for mod music based on ModP
ii  libmono-addins 0.4-6          GTK# frontend library for Mono.Addins
ii  libmono-addins 0.4-6          addin framework for extensible CLI applicati
ii  libmono-cairo2 2.4.4~svn15184 Mono Cairo library (for CLI 2.0)
ii  libmono-corlib 2.4.4~svn15184 Mono core library (for CLI 2.0)
ii  libmono-data-t 2.4.4~svn15184 Mono Data Library (for CLI 2.0)
ii  libmono-i18n-w 2.4.4~svn15184 Mono I18N.West library (for CLI 2.0)
ii  libmono-posix2 2.4.4~svn15184 Mono.Posix library (for CLI 2.0)
ii  libmono-securi 2.4.4~svn15184 Mono Security library (for CLI 2.0)
ii  libmono-sharpz 2.4.4~svn15184 Mono SharpZipLib library (for CLI 2.0)
ii  libmono-sqlite 2.4.4~svn15184 Mono Sqlite library (for CLI 2.0)
ii  libmono-system 2.4.4~svn15184 Mono System.Data Library (for CLI 2.0)
ii  libmono-system 2.4.4~svn15184 Mono System.Runtime Library (for CLI 2.0)
ii  libmono-system 2.4.4~svn15184 Mono System.Web Library (for CLI 2.0)
ii  libmono-system 2.4.4~svn15184 Mono System libraries (for CLI 2.0)
ii  libmono2.0-cil 2.4.4~svn15184 Mono libraries (for CLI 2.0)
ii  libmp3lame0    3.98.2+debian- An MP3 encoding library
ii  libmp4v2-0     1:1.6dfsg-0.2u freeware Advanced Audio Decoder - runtime fi
ii  libmpcdec3     1:1.2.2-2.1ubu Musepack (MPC) format library
ii  libmpeg2-4     0.4.1-3        MPEG1 and MPEG2 video decoder library
ii  libmpfr1ldbl   2.4.2-3ubuntu1 multiple precision floating-point computatio
ii  libmtp8        1.0.2-1ubuntu1 Media Transfer Protocol (MTP) library
ii  libmusicbrainz 2.1.5-4        Second generation incarnation of the CD Inde
ii  libmysqlclient 5.1.41-3ubuntu MySQL database client library
ii  libnautilus-bu 2.25.3-0ubuntu Nautilus Burn Library - runtime version
ii  libnautilus-ex 1:2.30.1-0ubun libraries for nautilus components - runtime 
ii  libncurses5    5.7+20090803-2 shared libraries for terminal handling
ii  libncursesw5   5.7+20090803-2 shared libraries for terminal handling (wide
ii  libndesk-dbus- 0.4.1-3        CLI implementation of D-Bus (GLib mainloop i
ii  libndesk-dbus1 0.6.0-4        CLI implementation of D-Bus
ii  libneon27-gnut 0.29.0-1       An HTTP and WebDAV client library (GnuTLS en
ii  libnet-daemon- 0.43-1         Perl module for building portable Perl daemo
ii  libnet-dbus-pe 0.33.6-1build3 Extension for the DBus bindings
ii  libnet-dns-per 0.65-1build1   Perform DNS queries from a Perl script
ii  libnet-ip-perl 1.25-2         Perl extension for manipulating IPv4/IPv6 ad
ii  libnet-libidn- 0.12.ds-1      Perl bindings for GNU Libidn
ii  libnet-ssleay- 1.35-2ubuntu1  Perl module for Secure Sockets Layer (SSL)
ii  libnetpbm10    2:10.0-12.1ubu Graphics conversion tools shared libraries
ii  libnewt0.52    0.52.10-5ubunt Not Erik's Windowing Toolkit - text mode win
ii  libnice0       0.0.10-2build1 ICE library (shared library)
ii  libnih-dbus1   1.0.1-1        NIH D-Bus Bindings Library
ii  libnih1        1.0.1-1        NIH Utility Library
ii  libnl1         1.1-5build1    library for dealing with netlink sockets
ii  libnm-glib2    0.8-0ubuntu3   network management framework (GLib shared li
ii  libnm-util1    0.8-0ubuntu3   network management framework (shared library
ii  libnotify1     0.4.5-1ubuntu3 sends desktop notifications to a notificatio
ii  libnspr4-0d    4.8.4-0ubuntu1 NetScape Portable Runtime Library
ii  libnss-mdns    0.10-3ubuntu4  NSS module for Multicast DNS name resolution
ii  libnss3-1d     3.12.6-0ubuntu Network Security Service libraries
ii  libntfs-3g75   1:2010.3.6-1ub ntfs-3g filesystem in userspace (FUSE) libra
ii  libntfs10      2.0.0-1ubuntu4 library that provides common NTFS access fun
ii  libnumber-comp 0.01-6         module for performing numeric comparisons in
ii  libnunit2.4-ci 2.4.7+dfsg-5   Unit test framework for CLI
ii  libofa0        0.9.3-3.1      Library for acoustic fingerprinting
ii  libogg0        1.1.4~dfsg-2   Ogg bitstream library
ii  liboil0.3      0.3.16-1ubuntu Library of Optimized Inner Loops
ii  liboobs-1-4    2.30.0-0ubuntu GObject based interface to system-tools-back
ii  libopenal1     1:1.12.854-0ub Software implementation of the OpenAL API (s
ii  libopencore-am 0.1.2-1        Adaptive Multi Rate speech codec - shared li
ii  libopencore-am 0.1.2-1        Adaptive Multi-Rate - Wideband speech codec 
ii  libopenexr6    1.6.1-4.1      runtime files for the OpenEXR image library
ii  libopenjpeg2   1.3+dfsg-4     JPEG 2000 image compression/decompression li
ii  libopenobex1   1.5-2build1    OBEX protocol library
ii  liborbit2      1:2.14.18-0.1  libraries for ORBit2 - a CORBA ORB
ii  liborc-0.4-0   0.4.3-5        Library of Optimized Inner Loops Runtime Com
ii  libotf0        0.9.10-1       A Library for handling OpenType Font - runti
ii  libpackagekit- 0.5.7-0ubuntu2 Advanced library for accessing PackageKit us
ii  libpackagekit- 0.5.7-0ubuntu2 Library for accessing PackageKit using Qt.
ii  libpam-ck-conn 0.4.1-3ubuntu1 ConsoleKit PAM module
ii  libpam-gnome-k 2.92.92.is.2.3 PAM module to unlock the GNOME keyring upon 
ii  libpam-modules 1.1.1-2ubuntu2 Pluggable Authentication Modules for PAM
ii  libpam-runtime 1.1.1-2ubuntu2 Runtime support for the PAM library
ii  libpam0g       1.1.1-2ubuntu2 Pluggable Authentication Modules library
ii  libpanel-apple 1:2.30.0-0ubun library for GNOME Panel applets
ii  libpango-perl  1.221-2        Perl module to layout and render internation
ii  libpango1.0-0  1.28.0-0ubuntu Layout and rendering of internationalized te
ii  libpango1.0-co 1.28.0-0ubuntu Modules and configuration files for the Pang
ii  libpangomm-1.4 2.26.2-0ubuntu C++ Wrapper for pango (shared libraries)
ii  libpaper-utils 1.1.23+nmu1bui library for handling paper characteristics (
ii  libpaper1      1.1.23+nmu1bui library for handling paper characteristics
ii  libparse-debia 1.1.1-2ubuntu2 parse Debian changelogs and output them in o
ii  libparted0     2.2-5ubuntu5   The GNU Parted disk partitioning shared libr
ii  libparted0debi 2.2-5ubuntu5   The GNU Parted disk partitioning shared libr
ii  libpcap0.8     1.0.0-6        system interface for user-level packet captu
ii  libpci3        1:3.0.0-4ubunt Linux PCI Utilities (shared library)
ii  libpciaccess0  0.11.0-1       Generic PCI access library for X
ii  libpcre3       7.8-3build1    Perl 5 Compatible Regular Expression Library
ii  libpcsclite1   1.5.3-1ubuntu4 Middleware to access a smart card using PC/S
ii  libperl5.10    5.10.1-8ubuntu shared Perl library
ii  libphonon4     4:4.6.2-0ubunt Qt 4 Phonon module
ii  libpisock9     0.12.4-7ubuntu library for communicating with a PalmOS PDA
ii  libpisync1     0.12.4-7ubuntu synchronization library for PalmOS devices
ii  libpixman-1-0  0.16.4-1ubuntu pixel-manipulation library for X and cairo
ii  libplasma-appl 4:4.4.2-0ubunt Library for the plasma system monitor
ii  libplasma-geol 4:4.4.2-0ubunt Library for the plasma geolocation
ii  libplasma3     4:4.4.2-0ubunt library for the KDE 4 Plasma desktop
ii  libplasmaclock 4:4.4.2-0ubunt Library for the plasma clock
ii  libplasmagener 4:4.4.2-0ubunt shared elements for all the plasma shells
ii  libplist1      1.1-1ubuntu1   Library for handling Apple binary and XML pr
ii  libplrpc-perl  0.2020-2       Perl extensions for writing PlRPC servers an
ii  libplymouth2   0.8.2-2ubuntu2 graphical boot animation and logger - shared
ii  libpng12-0     1.2.42-1ubuntu PNG library - runtime
ii  libpolkit-agen 0.96-2         PolicyKit Authentication Agent API
ii  libpolkit-back 0.96-2         PolicyKit backend API
ii  libpolkit-gobj 0.96-2         PolicyKit Authorization API
ii  libpolkit-gtk- 0.96-2ubuntu2  PolicyKit GTK+ API
ii  libpolkit-qt-1 0.95.1-1fakesy PolicyKit-qt-1 library
ii  libpoppler-gli 0.12.4-0ubuntu PDF rendering library (GLib-based shared lib
ii  libpoppler5    0.12.4-0ubuntu PDF rendering library
ii  libpopt0       1.15-1         lib for parsing cmdline parameters
ii  libportaudio2  19+svn20090620 Portable audio I/O - shared library
ii  libpostproc-ex 4:0.5.1-1ubunt ffmpeg video postprocessing library
rc  libpostproc51  4:0.5.1-1ubunt ffmpeg video postprocessing library
ii  libprocesscore 4:4.4.2-0ubunt Library for ksysguard based process view
ii  libprocessui4  4:4.4.2-0ubunt Library for ksysguard process user interface
ii  libprotobuf5   2.2.0a-0.1ubun protocol buffers C++ library
ii  libprotoc5     2.2.0a-0.1ubun protocol buffers compiler library
ii  libproxy0      0.3.1-1ubuntu1 automatic proxy configuration management lib
ii  libpst4        0.6.41-0ubuntu Shared library needed by the readpst utiliti
ii  libpth20       2.0.7-14       The GNU Portable Threads
ii  libpulse-brows 1:0.9.22~0.9.2 PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainl 1:0.9.22~0.9.2 PulseAudio client libraries (glib support)
ii  libpulse0      1:0.9.22~0.9.2 PulseAudio client libraries
ii  libpurple-bin  1:2.6.6-1ubunt multi-protocol instant messaging library - e
ii  libpurple0     1:2.6.6-1ubunt multi-protocol instant messaging library
ii  libpython2.6   2.6.5-1ubuntu6 Shared Python runtime library (version 2.6)
ii  libqca2        2.0.2-1ubuntu2 libraries for the Qt Cryptographic Architect
ii  libqimageblitz 1:0.0.4-4build QImageBlitz image effects library
ii  libqt3-mt      3:3.3.8-b-6ubu Qt GUI Library (Threaded runtime version), V
ii  libqt4-assista 4:4.6.2-0ubunt Qt 4 assistant module
ii  libqt4-dbus    4:4.6.2-0ubunt Qt 4 D-Bus module
ii  libqt4-designe 4:4.6.2-0ubunt Qt 4 designer module
ii  libqt4-help    4:4.6.2-0ubunt Qt 4 help module
ii  libqt4-network 4:4.6.2-0ubunt Qt 4 network module
ii  libqt4-opengl  4:4.6.2-0ubunt Qt 4 OpenGL module
ii  libqt4-qt3supp 4:4.6.2-0ubunt Qt 3 compatibility library for Qt 4
ii  libqt4-script  4:4.6.2-0ubunt Qt 4 script module
ii  libqt4-scriptt 4:4.6.2-0ubunt Qt 4 script tools module
ii  libqt4-sql     4:4.6.2-0ubunt Qt 4 SQL module
ii  libqt4-sql-mys 4:4.6.2-0ubunt Qt 4 MySQL database driver
ii  libqt4-svg     4:4.6.2-0ubunt Qt 4 SVG module
ii  libqt4-test    4:4.6.2-0ubunt Qt 4 test module
ii  libqt4-webkit  4:4.6.2-0ubunt Qt 4 WebKit module
ii  libqt4-xml     4:4.6.2-0ubunt Qt 4 XML module
ii  libqt4-xmlpatt 4:4.6.2-0ubunt Qt 4 XML patterns module
ii  libqtcore4     4:4.6.2-0ubunt Qt 4 core module
ii  libqtgui4      4:4.6.2-0ubunt Qt 4 GUI module
ii  libquicktime1  2:1.1.4-1      library for reading and writing Quicktime fi
ii  libraptor1     1.4.21-1ubuntu Raptor RDF parser and serializer library
ii  librarian0     0.8.1-4ubuntu1 Documentation meta-data library (library pac
ii  librasqal2     0.9.17-1       Rasqal RDF query library
ii  libraw1394-11  2.0.4-1ubuntu2 library for direct access to IEEE 1394 bus (
ii  librdf0        1.0.10-1ubuntu Redland Resource Description Framework (RDF)
ii  libreadline5   5.2-7build1    GNU readline and history libraries, run-time
ii  libreadline6   6.1-1          GNU readline and history libraries, run-time
ii  librpc-xml-per 0.72-1         Perl module implementation of XML-RPC
ii  librsvg2-2     2.26.3-0ubuntu SAX-based renderer library for SVG files (ru
ii  librsvg2-commo 2.26.3-0ubuntu SAX-based renderer library for SVG files (ex
ii  libruby1.8     1.8.7.249-2    Libraries necessary to run Ruby 1.8
ii  libsamplerate0 0.1.7-3        Audio sample rate conversion library
ii  libsane        1.0.20-13ubunt API library for scanners
ii  libsasl2-2     2.1.23.dfsg1-5 Cyrus SASL - authentication abstraction libr
ii  libsasl2-modul 2.1.23.dfsg1-5 Cyrus SASL - pluggable authentication module
ii  libschroedinge 1.0.9.is.1.0.8 library for encoding/decoding of Dirac video
ii  libscim8c2a    1.4.9-2        library for SCIM platform
ii  libsctp1       1.0.11+dfsg-1  user-space access to Linux Kernel SCTP - sha
ii  libsdl-image1. 1.2.10-1       image loading library for Simple DirectMedia
ii  libsdl1.2debia 1.2.14-4ubuntu Simple DirectMedia Layer
ii  libsdl1.2debia 1.2.14-4ubuntu Simple DirectMedia Layer (with X11 and Pulse
ii  libselinux1    2.0.89-4       SELinux runtime shared libraries
ii  libsensors4    1:3.1.2-2      library to read temperature/voltage/fan sens
ii  libsepol1      2.0.40-2       SELinux library for manipulating binary secu
ii  libsgutils2-2  1.28-2         utilities for working with generic SCSI devi
ii  libshout3      2.2.2-5ubuntu1 MP3/Ogg Vorbis broadcast streaming library
ii  libsidplay1    1.36.59-5      SID (MOS 6581) emulation library
ii  libsigc++-2.0- 2.2.4.2-1      type-safe Signal Framework for C++ - runtime
ii  libsilc-1.1-2  1.1.10-2build1 SILC generic library
ii  libsilcclient- 1.1.10-2build1 SILC client library
ii  libslang2      2.2.2-2ubuntu1 The S-Lang programming library - runtime ver
ii  libslp1        1.2.1-7.6      OpenSLP libraries
ii  libsm6         2:1.1.1-1      X11 Session Management library
ii  libsmbclient   2:3.4.7~dfsg-1 shared library for communication with SMB/CI
ii  libsndfile1    1.0.21-2       Library for reading/writing audio files
ii  libsnmp-base   5.4.2.1~dfsg0u SNMP (Simple Network Management Protocol) MI
ii  libsnmp15      5.4.2.1~dfsg0u SNMP (Simple Network Management Protocol) li
ii  libsolidcontro 4:4.4.2-0ubunt Library for solid based network management
ii  libsolidcontro 4:4.4.2-0ubunt Library for solid based network interface ma
ii  libsoprano4    2.4.2+dfsg.1-0 libraries for the Soprano RDF framework
ii  libsoundtouch1 1.3.1-2        sound stretching library
ii  libsoup-gnome2 2.30.1-0ubuntu an HTTP library implementation in C -- GNOME
ii  libsoup2.4-1   2.30.1-0ubuntu an HTTP library implementation in C -- Share
ii  libsox-fmt-als 14.3.0-1.1buil SoX alsa format I/O library
ii  libsox-fmt-bas 14.3.0-1.1buil Minimal set of SoX format libraries
ii  libsox1a       14.3.0-1.1buil SoX library of audio effects and processing
ii  libspectre1    0.2.3-2        Library for rendering PostScript documents
ii  libspeechd2    0.6.8~unoffici Speech Dispatcher: Shared libraries
ii  libspeex1      1.2~rc1-1ubunt The Speex codec runtime library
ii  libspeexdsp1   1.2~rc1-1ubunt The Speex extended runtime library
ii  libsqlite0     2.8.17-6build2 SQLite shared library
ii  libsqlite3-0   3.6.22-1       SQLite 3 shared library
ii  libss2         1.41.11-1ubunt command-line interface parsing library
ii  libssh-4       0.4.2-1ubuntu1 A tiny C SSH library
ii  libssl0.9.8    0.9.8k-7ubuntu SSL shared libraries
ii  libstartup-not 0.10-1build1   library for program launch feedback (shared 
ii  libstdc++6     4.4.3-4ubuntu5 The GNU Standard C++ Library v3
ii  libstreamanaly 0.7.2-0ubuntu1 streamanalyzer library for Strigi Desktop Se
ii  libstreams0    0.7.2-0ubuntu1 streams library for for Strigi Desktop Searc
ii  libsub-name-pe 0.04-1build1   Assigns a new name to referenced sub
ii  libsvga1       1:1.4.3-29     console SVGA display libraries
ii  libswscale-ext 4:0.5.1-1ubunt ffmpeg video scaling library
rc  libswscale0    4:0.5.1-1ubunt ffmpeg video scaling library
ii  libsysfs2      2.1.0-6        interface library to sysfs
ii  libt1-5        5.1.2-3build1  Type 1 font rasterizer library - runtime
ii  libtag1-vanill 1.6.3-0ubuntu1 TagLib Audio Meta-Data Library (Vanilla flav
ii  libtag1c2a     1.6.3-0ubuntu1 TagLib Audio Meta-Data Library
ii  libtalloc2     2.0.1-1        hierarchical pool based memory allocator
ii  libtar         1.2.11-6       C library for manipulating tar archives
ii  libtaskmanager 4:4.4.2-0ubunt Library which provides task management facil
ii  libtasn1-3     2.4-1          Manage ASN.1 structures (runtime)
ii  libtdb1        1.2.0-1        Trivial Database - shared library
ii  libtelepathy-f 0.0.13-1       Glue library between telepathy and farsight2
ii  libtelepathy-g 0.10.1-1ubuntu Telepathy framework - GLib library
ii  libterm-readke 2.30-4build1   A perl module for simple terminal control
ii  libtext-charwi 0.04-6         get display widths of characters on the term
ii  libtext-glob-p 0.08-2         Perl module for matching globbing patterns a
ii  libtext-iconv- 1.7-2          converts between character sets in Perl
ii  libtext-wrapi1 0.06-7         internationalized substitute of Text::Wrap
ii  libthai-data   0.1.13-1build1 Data files for Thai language support library
ii  libthai0       0.1.13-1build1 Thai language support library
ii  libtheora0     1.1.1+dfsg.1-3 The Theora Video Compression Codec
ii  libtidy-0.99-0 20091223cvs-1  HTML syntax checker and reformatter - librar
ii  libtie-ixhash- 1.21-2         ordered associative arrays for Perl
ii  libtiff4       3.9.2-2        Tag Image File Format (TIFF) library
ii  libtimedate-pe 1.1900-1       Time and date functions for Perl
ii  libtommath0    0.39-3ubuntu1  multiple-precision integer library [runtime]
ii  libtotem-plpar 2.30.0git20100 Totem Playlist Parser library - runtime file
ii  libts-0.0-0    1.0-7build1    touch screen library
ii  libtwolame0    0.3.12-1       MPEG Audio Layer 2 encoding library
ii  libubuntuone-1 0.3.1-0ubuntu1 Ubuntu One widget library
ii  libudev0       151-12         udev library
ii  libunique-1.0- 1.1.6-1ubuntu2 Library for writing single instance applicat
ii  libupnp3       1:1.6.6-4      Portable SDK for UPnP Devices, version 1.6 (
ii  libupower-glib 0.9.1-1        abstraction for power management - shared li
ii  liburi-perl    1.52-1         module to manipulate and access URI strings
ii  libusb-0.1-4   2:0.1.12-14    userspace USB programming library
ii  libusb-1.0-0   2:1.0.6-1      userspace USB programming library
ii  libusbmuxd1    1.0.2-1ubuntu2 USB multiplexor daemon for iPhone and iPod T
ii  libuuid-perl   0.02-3build2   Perl extension for using UUID interfaces as 
ii  libuuid1       2.17.2-0ubuntu Universally Unique ID library
ii  libv4l-0       0.6.4-1ubuntu1 Collection of video4linux support libraries
ii  libvcdinfo0    0.7.23-4ubuntu library to extract information from VideoCD
ii  libvisual-0.4- 0.4.0-2.1+ubun Audio visualization framework
ii  libvisual-0.4- 0.4.0.dfsg.1-2 Audio visualization framework plugins
ii  libvlc2        1.0.6-1ubuntu1 multimedia player and streamer library
ii  libvlccore2    1.0.6-1ubuntu1 base library for VLC and its modules
ii  libvorbis0a    1.2.3-3ubuntu1 The Vorbis General Audio Compression Codec (
ii  libvorbisenc2  1.2.3-3ubuntu1 The Vorbis General Audio Compression Codec (
ii  libvorbisfile3 1.2.3-3ubuntu1 The Vorbis General Audio Compression Codec (
ii  libvte-common  1:0.23.5-0ubun Terminal emulator widget for GTK+ 2.0 - comm
ii  libvte9        1:0.23.5-0ubun Terminal emulator widget for GTK+ 2.0 - runt
ii  libwavpack1    4.60.1-1       an audio codec (lossy and lossless) - librar
ii  libwbclient0   2:3.4.7~dfsg-1 Samba winbind client library
ii  libweather-ion 4:4.4.2-0ubunt Library which provides an interface for weat
ii  libwebkit-1.0- 1.2.0-1        Web content engine library for Gtk+
ii  libwebkit-1.0- 1.2.0-1        Web content engine library for Gtk+ - data f
ii  libwildmidi0   0.2.2-2        software MIDI player library
ii  libwmf0.2-7    0.2.8.4-6.1ubu Windows metafile conversion library
ii  libwmf0.2-7-gt 0.2.8.4-6.1ubu Windows metafile conversion library
ii  libwnck-common 1:2.30.0-0ubun Window Navigator Construction Kit - common f
ii  libwnck22      1:2.30.0-0ubun Window Navigator Construction Kit - runtime 
ii  libwpd8c2a     0.8.14-1build1 Library for handling WordPerfect documents (
ii  libwpg-0.1-1   0.1.3-1build1  WordPerfect graphics import/convert library 
ii  libwps-0.1-1   0.1.2-1build1  Works text file format import filter library
ii  libwrap0       7.6.q-18       Wietse Venema's TCP wrappers library
ii  libwww-perl    5.834-1        Perl HTTP/WWW client/server library
ii  libwxbase2.6-0 2.6.3.2.2-3ubu wxBase library (runtime) - non-GUI support c
ii  libwxbase2.8-0 2.8.10.1-0ubun wxBase library (runtime) - non-GUI support c
ii  libwxgtk2.6-0  2.6.3.2.2-3ubu wxWidgets Cross-platform C++ GUI toolkit (GT
ii  libwxgtk2.8-0  2.8.10.1-0ubun wxWidgets Cross-platform C++ GUI toolkit (GT
ii  libx11-6       2:1.3.2-1ubunt X11 client-side library
ii  libx11-data    2:1.3.2-1ubunt X11 client-side library
ii  libx264-85     2:0.85.1448+gi x264 video coding library
ii  libx86-1       1.1+ds1-6      x86 real-mode library
ii  libxapian15    1.0.18-1       Search engine library
ii  libxau6        1:1.0.5-1      X11 authorisation library
ii  libxaw7        2:1.0.7-1      X11 Athena Widget library
ii  libxcb-atom1   0.3.6-1build1  utility libraries for X C Binding -- atom
ii  libxcb-aux0    0.3.6-1build1  utility libraries for X C Binding -- aux
ii  libxcb-event1  0.3.6-1build1  utility libraries for X C Binding -- event
ii  libxcb-keysyms 0.3.6-1build1  utility libraries for X C Binding -- keysyms
ii  libxcb-render- 0.3.6-1build1  utility libraries for X C Binding -- render-
ii  libxcb-render0 1.5-2          X C Binding, render extension
ii  libxcb-shape0  1.5-2          X C Binding, shape extension
ii  libxcb-shm0    1.5-2          X C Binding, shm extension
ii  libxcb-xv0     1.5-2          X C Binding, xv extension
ii  libxcb1        1.5-2          X C Binding
ii  libxcomposite1 1:0.4.1-1      X11 Composite extension library
ii  libxcursor1    1:1.1.10-1     X cursor management library
ii  libxdamage1    1:1.1.2-1      X11 damaged region extension library
ii  libxdmcp6      1:1.0.3-1      X11 Display Manager Control Protocol library
ii  libxext6       2:1.1.1-2      X11 miscellaneous extension library
ii  libxfixes3     1:4.0.4-1      X11 miscellaneous 'fixes' extension library
ii  libxfont1      1:1.4.1-1      X11 font rasterisation library
ii  libxft2        2.1.14-1ubuntu FreeType-based font drawing library for X
ii  libxi6         2:1.3-3        X11 Input extension library
ii  libxine1       1.1.17-1ubuntu the xine video/media player library, meta-pa
ii  libxine1-bin   1.1.17-1ubuntu the xine video/media player library, binary 
ii  libxine1-conso 1.1.17-1ubuntu libaa/libcaca/framebuffer/directfb related p
ii  libxine1-ffmpe 1.1.17-1ubuntu MPEG-related plugins for libxine1
ii  libxine1-misc- 1.1.17-1ubuntu Input, audio output and post plugins for lib
ii  libxine1-x     1.1.17-1ubuntu X desktop video output plugins for libxine1
ii  libxinerama1   2:1.1-2        X11 Xinerama extension library
ii  libxkbfile1    1:1.0.6-1      X11 keyboard file manipulation library
ii  libxklavier16  5.0-0ubuntu1   X Keyboard Extension high-level API
ii  libxml-libxml- 1.70.ds-1      Perl interface to the libxml2 library
ii  libxml-namespa 1.09-3         Perl module for supporting simple generic na
ii  libxml-parser- 2.36-1.1build3 Perl module for parsing XML files
ii  libxml-sax-exp 0.40-1         Perl module for a SAX2 driver for Expat (XML
ii  libxml-sax-per 0.96+dfsg-2    Perl module for using and building Perl SAX2
ii  libxml-twig-pe 1:3.32-3ubuntu Perl module for processing huge XML document
ii  libxml-xpath-p 1.13-7         Perl module for processing XPath
ii  libxml2        2.7.6.dfsg-1ub GNOME XML library
ii  libxml2-utils  2.7.6.dfsg-1ub XML utilities
ii  libxmu6        2:1.0.5-1      X11 miscellaneous utility library
ii  libxmuu1       2:1.0.5-1      X11 miscellaneous micro-utility library
ii  libxp6         1:1.0.0.xsf1-2 X Printing Extension (Xprint) client library
ii  libxpm4        1:3.5.8-1      X11 pixmap library
ii  libxrandr2     2:1.3.0-3      X11 RandR extension library
ii  libxrender1    1:0.9.5-1      X Rendering Extension client library
ii  libxres1       2:1.0.4-1      X11 Resource extension library
ii  libxslt1.1     1.1.26-1ubuntu XSLT processing library - runtime library
ii  libxss1        1:1.2.0-2      X11 Screen Saver extension library
ii  libxt6         1:1.0.7-1      X11 toolkit intrinsics library
ii  libxtst6       2:1.1.0-2      X11 Testing -- Resource extension library
ii  libxv1         2:1.0.5-1      X11 Video extension library
ii  libxvidcore4   2:1.2.2+debian An open source MPEG-4 video codec (library)
ii  libxvmc1       2:1.0.5-1ubunt X11 Video extension library
ii  libxxf86dga1   2:1.1.1-2      X11 Direct Graphics Access extension library
ii  libxxf86misc1  1:1.0.2-1      X11 XFree86 miscellaneous extension library
ii  libxxf86vm1    1:1.1.0-2      X11 XFree86 video mode extension library
ii  libzephyr4     3.0-1          Project Athena's notification service - non-
ii  liferea        1.6.2-1ubuntu6 feed aggregator for GNOME
ii  liferea-data   1.6.2-1ubuntu6 architecture independent data for liferea
ii  light-themes   0.1.6.5        Light Themes
ii  linux-firmware 1.34           Firmware for Linux kernel drivers
ii  linux-generic  2.6.32.22.23   Complete Generic Linux kernel
ii  linux-headers- 2.6.32-21.32   Header files related to Linux kernel version
ii  linux-headers- 2.6.32-21.32   Linux kernel headers for version 2.6.32 on x
ii  linux-headers- 2.6.32-22.36   Header files related to Linux kernel version
ii  linux-headers- 2.6.32-22.36   Linux kernel headers for version 2.6.32 on x
ii  linux-headers- 2.6.32.22.23   Generic Linux kernel headers
ii  linux-image-2. 2.6.32-21.32   Linux kernel image for version 2.6.32 on x86
ii  linux-image-2. 2.6.32-22.36   Linux kernel image for version 2.6.32 on x86
ii  linux-image-ge 2.6.32.22.23   Generic Linux kernel image
ii  linux-libc-dev 2.6.32-22.36   Linux Kernel Headers for development
ii  linux-sound-ba 1.0.22.1+dfsg- base package for ALSA and OSS sound systems
ii  lksctp-tools   1.0.11+dfsg-1  user-space access to Linux Kernel SCTP - com
ii  lm-sensors     1:3.1.2-2      utilities to read temperature/voltage/fan se
ii  locales        2.11+git201003 common files for locale support
ii  lockfile-progs 0.1.13ubuntu1  Programs for locking and unlocking files and
ii  login          1:4.1.4.2-1ubu system login tools
ii  logrotate      3.7.8-4ubuntu2 Log rotation utility
ii  lp-solve       5.5.0.13-7     Solve (mixed integer) linear programming pro
ii  lsb-base       4.0-0ubuntu8   Linux Standard Base 4.0 init script function
ii  lsb-release    4.0-0ubuntu8   Linux Standard Base version reporting utilit
ii  lsdvd          0.16-3ubuntu1  read the content info of a DVD
ii  lshw           02.14-1build1  information about hardware configuration
ii  lsof           4.81.dfsg.1-1b List open files
ii  ltrace         0.5.3-2ubuntu3 Tracks runtime library calls in dynamically 
ii  lzma           4.43-14ubuntu2 Compression method of 7z format in 7-Zip pro
ii  m17n-contrib   1.1.10-1       a multilingual text processing library - con
ii  m17n-db        1.5.5-1        a multilingual text processing library - dat
ii  make           3.81-7ubuntu1  An utility for Directing compilation.
ii  makedev        2.3.1-89ubuntu creates device files in /dev
ii  man-db         2.5.7-2        on-line manual pager
ii  manpages       3.23-1         Manual pages about using a GNU/Linux system
ii  manpages-dev   3.23-1         Manual pages about using GNU/Linux for devel
ii  mawk           1.3.3-15ubuntu a pattern scanning and text processing langu
ii  mc             3:4.7.0-1ubunt Midnight Commander - a powerful file manager
ii  media-player-i 6-1            Media player identification files
ii  medibuntu-keyr 2008.04.20     GnuPG key of the Medibuntu repository
ii  memtest86+     4.00-2ubuntu3  thorough real-mode memory tester
ii  mencoder       2:1.0~rc3+svn2 MPlayer's Movie Encoder
ii  menu           2.1.43ubuntu1  generates programs menu for all menu-aware a
ii  metacity       1:2.30.1-0ubun lightweight GTK+ window manager
ii  metacity-commo 1:2.30.1-0ubun shared files for the Metacity window manager
ii  mime-support   3.48-1ubuntu1  MIME files 'mime.types' & 'mailcap', and sup
ii  min12xxw       0.0.9-3ubuntu2 Printer driver for KonicaMinolta PagePro 1[2
ii  mjpegtools     1:1.9.0-0.5ubu MJPEG video capture/editting/playback MPEG e
ii  mlocate        0.22.2-1ubuntu quickly find files on the filesystem based o
ii  mobile-broadba 20100407-1     database of mobile broadband service provide
ii  modemmanager   0.3-0ubuntu2   D-Bus service for managing modems
ii  module-init-to 3.11.1-2ubuntu tools for managing Linux kernel modules
ii  mono-2.0-gac   2.4.4~svn15184 Mono GAC tool (for CLI 2.0)
ii  mono-gac       2.4.4~svn15184 Mono GAC tool
ii  mono-runtime   2.4.4~svn15184 Mono runtime
ii  mount          2.17.2-0ubuntu Tools for mounting and manipulating filesyst
ii  mountall       2.15           filesystem mounting tool
ii  mousetweaks    2.30.0-0ubuntu mouse accessibility enhancements for the GNO
ii  mplayer        2:1.0~rc3+svn2 movie player for Unix-like systems
ii  mscompress     0.3-3build1    Microsoft "compress.exe/expand.exe" compatib
ii  mtools         4.0.10-1ubuntu Tools for manipulating MSDOS files
ii  mtr-tiny       0.75-2build1   Full screen ncurses traceroute tool
ii  myspell-en-au  2.1-5          English_australian dictionary for myspell
ii  myspell-en-gb  1:3.2.0-3ubunt English_british dictionary for myspell
ii  myspell-en-za  1:3.2.0-3ubunt English_southafrican dictionary for myspell
ii  mysql-client   5.1.41-3ubuntu MySQL database client (metapackage depending
ii  mysql-client-5 5.1.41-3ubuntu MySQL database client binaries
ii  mysql-client-c 5.1.41-3ubuntu MySQL database core client binaries
ii  mysql-common   5.1.41-3ubuntu MySQL database common files (e.g. /etc/mysql
ii  mysql-navigato 1.4.2-12build1 GUI client program for MySQL database server
ii  mysql-server   5.1.41-3ubuntu MySQL database server (metapackage depending
ii  mysql-server-5 5.1.41-3ubuntu MySQL database server binaries
ii  mysql-server-c 5.1.41-3ubuntu MySQL database core server files
ii  nano           2.2.2-1        small, friendly text editor inspired by Pico
ii  nautilus       1:2.30.1-0ubun file manager and graphical shell for GNOME
ii  nautilus-actio 2.30.2-0ubuntu nautilus extension to configure programs to 
ii  nautilus-data  1:2.30.1-0ubun data files for nautilus
ii  nautilus-sendt 2.28.4-0ubuntu integrates Evolution and Pidgin into the Nau
ii  nautilus-sendt 2.30.1-0ubuntu GNOME multi-protocol chat and call client (n
ii  nautilus-share 0.7.2-12build1 Nautilus extension to share folder using Sam
ii  ncurses-base   5.7+20090803-2 basic terminal type definitions
ii  ncurses-bin    5.7+20090803-2 terminal-related programs and man pages
ii  net-tools      1.60-23ubuntu2 The NET-3 networking toolkit
ii  netbase        4.35ubuntu3    Basic TCP/IP networking system
ii  netcat-openbsd 1.89-3ubuntu2  TCP/IP swiss army knife
ii  netpbm         2:10.0-12.1ubu Graphics conversion tools between image form
ii  network-manage 0.8-0ubuntu3   network management framework daemon
ii  network-manage 0.8-0ubuntu3   network management framework (GNOME frontend
ii  network-manage 0.8-0ubuntu3   network management framework (PPTP plugin)
ii  network-manage 0.8-0ubuntu3   network management framework (PPTP plugin, G
ii  notify-osd     0.9.29-0ubuntu daemon that displays passive pop-up notifica
ii  notify-osd-ico 0.6            Notify-OSD icons
ii  nspluginwrappe 1.2.2-0ubuntu6 A wrapper to run Netscape plugins on other a
ii  ntfs-3g        1:2010.3.6-1ub read-write NTFS driver for FUSE
ii  ntfsprogs      2.0.0-1ubuntu4 tools for doing neat things in NTFS partitio
ii  ntp            1:4.2.4p8+dfsg Network Time Protocol daemon and utility pro
ii  ntpdate        1:4.2.4p8+dfsg client for setting system time from NTP serv
ii  nvidia-173-mod 173.14.22-0ubu Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-moda 96.43.17-0ubun Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common  0.2.23         Find obsolete NVIDIA drivers
ii  nvidia-current 195.36.15-0ubu Modaliases for the NVIDIA binary X.Org drive
ii  obex-data-serv 0.4.5-1        D-Bus service for OBEX client and server sid
ii  obexd-client   0.22-0ubuntu2  D-Bus OBEX client
ii  ogmtools       1:1.5-3ubuntu1 Tools for manipulating Ogg multimedia stream
ii  onboard        0.93.0-0ubuntu Simple On-screen Keyboard
ii  opendict       0.6.3-3        computer dictionary for several dictionary f
ii  openjdk-6-jre  6b18-1.8-0ubun OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre- 6b18-1.8-0ubun OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre- 6b18-1.8-0ubun OpenJDK Java runtime (architecture independe
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- shared library
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- spreadsheet
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- arch-independen
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- arch-dependent 
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- drawing
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- email mail merg
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- GNOME integrati
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- GTK+ integratio
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- English_british
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- English_america
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- Chinese_simplif
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- Chinese_traditi
ii  openoffice.org 0.5            Hyphenation patterns for OpenOffice.org
ii  openoffice.org 2.4-6ubuntu1   US English hyphenation patterns for OpenOffi
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- presentation
ii  openoffice.org 1:3.2.0-7ubunt common files for OpenOffice.org language and
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- English_british
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- English_southaf
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- Chinese_simplif
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- Chinese_traditi
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- equation editor
ii  openoffice.org 1:3.2.0-7ubunt Human symbol style for OpenOffice.org
ii  openoffice.org 2.1-5          Australian English Thesaurus for OpenOffice.
ii  openoffice.org 1:3.2.0-3ubunt English Thesaurus for OpenOffice.org
ii  openoffice.org 1:3.2.0-7ubunt office productivity suite -- word processor
ii  openprinting-p 20100216-0ubun OpenPrinting printer support - PostScript PP
ii  openproj       1.4-2          A desktop replacement for Microsoft Project
ii  openssh-client 1:5.3p1-3ubunt secure shell (SSH) client, for secure access
ii  openssl        0.9.8k-7ubuntu Secure Socket Layer (SSL) binary and related
ii  opera          10.10.4742.gcc The Opera Web Browser
ii  os-prober      1.38           utility to detect other OSes on a set of dri
ii  oxygen-icon-th 4:4.4.2-0ubunt Oxygen icon theme
ii  packagekit     0.5.7-0ubuntu2 provides a software installation daemon
ii  packagekit-bac 0.5.7-0ubuntu2 APT backend for packagekit
ii  parted         2.2-5ubuntu5   The GNU Parted disk partition resizing progr
ii  passwd         1:4.1.4.2-1ubu change and administer password and group dat
ii  patch          2.6-2ubuntu1   Apply a diff file to an original
ii  pciutils       1:3.0.0-4ubunt Linux PCI Utilities
ii  pcmciautils    014-4ubuntu4   PCMCIA utilities for Linux 2.6
ii  perl           5.10.1-8ubuntu Larry Wall's Practical Extraction and Report
ii  perl-base      5.10.1-8ubuntu minimal Perl system
ii  perl-modules   5.10.1-8ubuntu Core Perl modules
ii  phonon         4:4.6.2-0ubunt Qt 4 Phonon module metapackage
ii  phonon-backend 4:4.4.0-0ubunt Phonon Xine 1.1.x backend
ii  php5-common    5.3.2-1ubuntu4 Common files for packages built from the php
ii  php5-gd        5.3.2-1ubuntu4 GD module for php5
ii  php5-mysql     5.3.2-1ubuntu4 MySQL module for php5
ii  pinyin-databas 1.2.99-3       PinYin database used by ibus-pinyin
ii  pitivi         0.13.4-0ubuntu non-linear audio/video editor using GStreame
ii  pkg-config     0.22-1build2   manage compile and link flags for libraries
ii  plasma-dataeng 4:4.4.2-0ubunt KDE 4 base workspace Plasma data engines
ii  plasma-scripte 4:4.4.2-0ubunt javascript script engine for Plasma
ii  plasma-widgets 4:4.4.2-0ubunt KDE 4 base workspace Plasma widgets and cont
ii  plymouth       0.8.2-2ubuntu2 graphical boot animation and logger - main p
ii  plymouth-label 0.8.2-2ubuntu2 graphical boot animation and logger - label 
ii  plymouth-theme 0.8.2-2ubuntu2 graphical boot animation and logger - ubuntu
ii  plymouth-theme 0.8.2-2ubuntu2 graphical boot animation and logger - ubuntu
ii  plymouth-x11   0.8.2-2ubuntu2 graphical boot animation and logger - X11 in
ii  pm-utils       1.3.0-1ubuntu2 utilities and scripts for power management
ii  pm-utils-power 0.3.1          lightweight power saving policy when on batt
ii  pnm2ppa        1.13-0ubuntu1  PPM to PPA converter
ii  policykit-1    0.96-2         framework for managing administrative polici
ii  policykit-1-gn 0.96-2ubuntu2  GNOME authentication agent for PolicyKit-1
ii  policykit-desk 0.1            run common desktop actions without password
ii  polkit-kde-1   0.95.1-2ubuntu KDE dialogs for PolicyKit
ii  poppler-utils  0.12.4-0ubuntu PDF utilitites (based on libpoppler)
ii  popularity-con 1.48ubuntu1    Vote for your favourite packages automatical
ii  postfix        2.7.0-1        High-performance mail transport agent
ii  powermgmt-base 1.31           Common utils and configs for power managemen
ii  ppp            2.4.5~git20081 Point-to-Point Protocol (PPP) - daemon
ii  pppconfig      2.3.18ubuntu2  A text menu based utility for configuring pp
ii  pppoeconf      1.19ubuntu1    configures PPPoE/ADSL connections
ii  pptp-linux     1.7.2-4        Point-to-Point Tunneling Protocol (PPTP) Cli
ii  procps         1:3.2.8-1ubunt /proc file system utilities
ii  protobuf-compi 2.2.0a-0.1ubun compiler for protocol buffer definition file
ii  psfontmgr      0.11.10-4ubunt PostScript font manager -- part of Defoma, D
ii  psmisc         22.10-1        utilities that use the proc file system
ii  pulseaudio     1:0.9.22~0.9.2 PulseAudio sound server
ii  pulseaudio-eso 1:0.9.22~0.9.2 PulseAudio ESD compatibility layer
ii  pulseaudio-mod 1:0.9.22~0.9.2 Bluetooth module for PulseAudio sound server
ii  pulseaudio-mod 1:0.9.22~0.9.2 GConf module for PulseAudio sound server
ii  pulseaudio-mod 1:0.9.22~0.9.2 X11 module for PulseAudio sound server
ii  pulseaudio-uti 1:0.9.22~0.9.2 Command line tools for the PulseAudio sound 
ii  pxljr          1.1-0ubuntu7   Driver for HP's Color LaserJet 35xx/36xx col
ii  pychecker      0.8.18-4       Finds common bugs in Python source code
ii  python         2.6.5-0ubuntu1 An interactive high-level object-oriented la
ii  python-appindi 0.0.19-0ubuntu Python bindings for libappindicator
ii  python-apport  1.13.3-0ubuntu apport crash report handling library
ii  python-apt     0.7.94.2ubuntu Python interface to libapt-pkg
ii  python-aptdaem 0.11+bzr345-0u Python module for the server and client of a
ii  python-aptdaem 0.11+bzr345-0u Python GTK+ widgets to run an aptdaemon clie
ii  python-avahi   0.6.25-1ubuntu Python utility package for Avahi
ii  python-brlapi  4.1-2ubuntu6   Python bindings for BrlAPI
ii  python-cairo   1.8.8-1        Python bindings for the Cairo vector graphic
ii  python-central 0.6.15ubuntu1  register and build utility for Python packag
ii  python-configg 0.2dev-0ubuntu Glues together optparse.OptionParser and Con
ii  python-configo 4.7.1-1        simple but powerful config file reader and w
ii  python-couchdb 0.6-1          library for working with Apache CouchDB
ii  python-crypto  2.0.1+dfsg1-4u cryptographic algorithms and protocols for P
ii  python-cups    1.9.49-0ubuntu Python bindings for CUPS
ii  python-cupshel 1.2.0+20100408 Python modules for printer configuration wit
ii  python-dbus    0.83.0-1ubuntu simple interprocess messaging system (Python
ii  python-debian  0.1.14ubuntu2  Python modules to work with Debian-related d
ii  python-desktop 0.6.4-0ubuntu3 Python Desktop CouchDB
ii  python-desktop 0.6.4-0ubuntu3 Desktop CouchDB Records API
ii  python-egenix- 3.1.3-2ubuntu1 date and time handling routines for Python
ii  python-egenix- 3.1.3-2ubuntu1 collection of additional builtins for Python
ii  python-farsigh 0.0.17-2ubuntu Audio/Video communications framework: Python
ii  python-fstab   1.4-1          read, manipulate, and write /etc/fstab files
ii  python-gconf   2.28.0-1ubuntu Python bindings for the GConf configuration 
ii  python-gdbm    2.6.5-0ubuntu2 GNU dbm database support for Python
ii  python-glade2  2.17.0-0ubuntu GTK+ bindings: Glade support
ii  python-gmenu   2.30.0-0ubuntu an implementation of the freedesktop menu sp
ii  python-gnome2  2.28.0-1ubuntu Python bindings for the GNOME desktop enviro
ii  python-gnomeap 2.30.0-0ubuntu Python bindings for the GNOME panel applet l
ii  python-gnomeca 2.28.0-1ubuntu Python bindings for gnomecanvas (debug exten
ii  python-gnomeke 2.30.0-0ubuntu Python bindings for the GNOME keyring librar
ii  python-gnupgin 0.3.2-9.1      Python interface to GnuPG (GPG)
ii  python-gobject 2.21.1-0ubuntu Python bindings for the GObject library
ii  python-gst0.10 0.10.18-1      generic media-playing framework (Python bind
ii  python-gtk2    2.17.0-0ubuntu Python bindings for the GTK+ widget set
ii  python-gtksour 2.10.1-0ubuntu Python bindings for the GtkSourceView widget
ii  python-gtkspel 2.25.3-4.1ubun Python bindings for the GtkSpell library
ii  python-httplib 0.6.0-1        comprehensive HTTP client library written in
ii  python-ibus    1.2.0.20091215 New input method framework using dbus
ii  python-imaging 1.1.7-1        Python Imaging Library
ii  python-indicat 0.3.0-0ubuntu1 Python bindings for libindicate
ii  python-kde4    4:4.4.2-0ubunt Python bindings for the KDE 4 libraries
ii  python-launchp 0.1.35         library for launchpad integration
ii  python-launchp 1.6.0-0ubuntu1 Launchpad web services client library
ii  python-lazr.re 0.9.11-1ubuntu client for lazr.restful-based web services
ii  python-lazr.ur 1.0.2-1        library for parsing, manipulating, and gener
ii  python-libxml2 2.7.6.dfsg-1ub Python bindings for the GNOME XML library
ii  python-louis   1.7.0-2        Python bindings for liblouis
ii  python-mako    0.2.5-2ubuntu1 fast and lightweight templating for the Pyth
ii  python-minimal 2.6.5-0ubuntu1 A minimal subset of the Python language (def
ii  python-moinmoi 1.9.2-2ubuntu3 Python clone of WikiWiki - library
ii  python-newt    0.52.10-5ubunt A NEWT module for Python
ii  python-notify  0.1.1-2build3  Python bindings for libnotify
ii  python-oauth   1.0a~svn1124-0 implementation of the OAuth protocol
ii  python-openssl 0.10-1         Python wrapper around the OpenSSL library
ii  python-package 0.5.7-0ubuntu2 PackageKit Python bindings
ii  python-pam     0.4.2-12.1ubun A Python interface to the PAM library
ii  python-papyon  0.4.8-0ubuntu1 MSN client library written in Python
ii  python-paramik 1.7.6-2        Make ssh v2 connections with Python
ii  python-pexpect 2.3-1build1    Python module for automating interactive app
ii  python-pkg-res 0.6.10-4ubuntu Package Discovery and Resource Access using 
ii  python-problem 1.13.3-0ubuntu Python library to handle problem reports
ii  python-protobu 2.2.0a-0.1ubun Python bindings for protocol buffers
ii  python-pyatspi 1.30.0-0ubuntu Assistive Technology Service Provider Interf
ii  python-pycurl  7.19.0-3       Python bindings to libcurl
ii  python-pygment 1.2.2+dfsg-1ub syntax highlighting package written in Pytho
ii  python-pygooca 0.14.1-0ubuntu GooCanvas Python bindings
ii  python-pyinoti 0.8.9-1ubuntu2 simple Linux inotify Python bindings
ii  python-pyorbit 2.24.0-5ubuntu A Python language binding for the ORBit2 COR
ii  python-qt4     4.7.2-0ubuntu1 Python bindings for Qt4
ii  python-rdflib  2.4.2-1        RDF library containing an RDF triple store a
ii  python-serial  2.3-1          pyserial - module encapsulating access for t
ii  python-simplej 2.0.9-1build1  Simple, fast, extensible JSON encoder/decode
ii  python-sip     4.10.1-0ubuntu Python/C++ bindings generator runtime librar
ii  python-smbc    1.0.6-0ubuntu3 Python bindings for Samba clients (libsmbcli
ii  python-softwar 0.75.10        manage the repositories that you install sof
ii  python-speechd 0.6.8~unoffici Python interface to Speech Dispatcher
ii  python-support 1.0.4ubuntu1   automated rebuilding support for Python modu
ii  python-telepat 0.15.17-1      Python language bindings for telepathy
ii  python-twisted 10.0.0-2ubuntu Event-based framework for internet applicati
ii  python-twisted 10.0.0-2ubuntu Event-based framework for internet applicati
ii  python-twisted 10.0.0-1       A DNS protocol implementation with client an
ii  python-twisted 10.0.0-1       An HTTP protocol implementation together wit
ii  python-ubuntuo 0.3.1-0ubuntu1 Ubuntu One widget library
ii  python-ubuntuo 1.2.1-0ubuntu3 Ubuntu One client Python libraries
ii  python-ubuntuo 1.2.0-0ubuntu1 Python library for Ubuntu One file storage a
ii  python-uno     1:3.2.0-7ubunt Python-UNO bridge
ii  python-virtkey 0.50ubuntu3    Library to emulate keyboard keypresses.
ii  python-vte     1:0.23.5-0ubun Python bindings for the VTE widget set
ii  python-wadllib 1.1.4-1ubuntu1 Python library for navigating WADL files
ii  python-webkit  1.1.7-1        WebKit/Gtk Python bindings
ii  python-wnck    2.30.0-0ubuntu Python bindings for the WNCK library
ii  python-wxglade 0.6.3-0.1ubunt GUI designer written in Python with wxPython
ii  python-wxgtk2. 2.6.3.2.2-3ubu wxWidgets Cross-platform C++ GUI toolkit (wx
ii  python-wxgtk2. 2.8.10.1-0ubun wxWidgets Cross-platform C++ GUI toolkit (wx
ii  python-wxversi 2.8.10.1-0ubun wxWidgets Cross-platform C++ GUI toolkit (wx
ii  python-xapian  1.0.17-1ubuntu Xapian search engine interface for Python
ii  python-xdg     0.18-1ubuntu2  Python library to access freedesktop.org sta
ii  python-xkit    0.4.2.2        library for the manipulation of the xorg.con
ii  python-zope.in 3.5.3-1ubuntu2 Interfaces for Python
ii  python2.6      2.6.5-1ubuntu6 An interactive high-level object-oriented la
ii  python2.6-mini 2.6.5-1ubuntu6 A minimal subset of the Python language (ver
ii  qbzr           0.18.6-0ubuntu Graphical interface for Bazaar using the Qt 
ii  quadrapassel   1:2.30.0-0ubun Falling blocks game
ii  quanta         4:3.5.10-0ubun web development environment for KDE
ii  quanta-data    4:3.5.10-0ubun data files for Quanta Plus web development e
ii  radeontool     1.6.1-0ubuntu1 utility to control ATI Radeon backlight func
ii  rarian-compat  0.8.1-4ubuntu1 Documentation meta-data library (compatibili
ii  rdesktop       1.6.0-2ubuntu3 RDP client for Windows NT/2000 Terminal Serv
ii  readline-commo 6.1-1          GNU readline and history libraries, common f
ii  rhythmbox      0.12.8-0ubuntu music player and organizer for GNOME
ii  rhythmbox-plug 0.12.8-0ubuntu burning plugin for rhythmbox music player
ii  rhythmbox-plug 0.12.8-0ubuntu plugins for rhythmbox music player
ii  rhythmbox-ubun 0.0.9-0ubuntu1 Ubuntu One Music Store Rhythmbox plugin
ii  rsync          3.0.7-1ubuntu1 fast remote file copy program (like rcp)
ii  rsyslog        4.2.0-2ubuntu8 enhanced multi-threaded syslogd
ii  rtkit          0.6-0ubuntu1   Realtime Policy and Watchdog Daemon
ii  ruby           4.2            An interpreter of object-oriented scripting 
ii  ruby1.8        1.8.7.249-2    Interpreter of object-oriented scripting lan
ii  samba-common   2:3.4.7~dfsg-1 common files used by both the Samba server a
ii  samba-common-b 2:3.4.7~dfsg-1 common files used by both the Samba server a
ii  sane-utils     1.0.20-13ubunt API library for scanners -- utilities
ii  scim           1.4.9-2        smart common input method platform
ii  scim-bridge-ag 0.4.16-2ubuntu IME server of scim-bridge communicate with S
ii  scim-bridge-cl 0.4.16-2ubuntu IME server of scim-bridge communicate with S
ii  scim-gtk2-immo 1.4.9-2        GTK+2 input method module with SCIM as backe
ii  scim-modules-s 1.4.9-2        socket modules for SCIM platform
ii  scim-pinyin    0.5.91-1ubuntu smart pinyin IM engine for SCIM platform
ii  scim-qtimm     0.9.4-4ubuntu1 SCIM context plugin for qt-immodule
ii  screen         4.0.3-14ubuntu terminal multiplexor with VT100/ANSI termina
ii  screen-resolut 0.13           Extension for the GNOME screen resolution ap
ii  screensaver-de 0.2-1          Wallpapers for image processing screensavers
ii  seahorse       2.30.0-0ubuntu GNOME front end for GnuPG
ii  sed            4.2.1-6        The GNU sed stream editor
ii  sensible-utils 0.0.1ubuntu3   Utilities for sensible alternative selection
ii  sgml-base      1.26           SGML infrastructure and SGML catalog file su
ii  sgml-data      2.0.4          common SGML and XML data
ii  shared-desktop 0.3-1          shared ontologies for semantic searching
ii  shared-mime-in 0.71-1ubuntu2  FreeDesktop.org shared MIME database and spe
ii  shrinkta       0.1.12-0.2     DVD backup tool
ii  simple-scan    1.0.3-0ubuntu1 Simple Scanning Utility
ii  smartdimmer    0.8b4-1ubuntu3 Change LCD brightness on Geforce cards
ii  smbclient      2:3.4.7~dfsg-1 command-line SMB/CIFS clients for Unix
ii  software-cente 2.0.4          Utility for browsing, installing, and removi
ii  software-prope 0.75.10        manage the repositories that you install sof
ii  software-prope 0.75.10        manage the repositories that you install sof
ii  soprano-daemon 2.4.2+dfsg.1-0 daemon for the Soprano RDF framework
ii  sox            14.3.0-1.1buil Swiss army knife of sound processing
ii  spe            0.8.4.h-1ubunt Stani's Python Editor
ii  speech-dispatc 0.6.8~unoffici Common interface to speech synthesizers
ii  splix          2.0.0-2ubuntu3 Driver for Samsung's SPL2 (bw) and SPLc (col
ii  ssh-askpass-gn 1:5.3p1-3ubunt interactive X program to prompt users for a 
ii  ssl-cert       1.0.23ubuntu2  simple debconf wrapper for OpenSSL
ii  startupmanager 1.9.13-4ubuntu Grub, Usplash and Splash screen configuratio
ii  strace         4.5.19-2       A system call tracer
ii  subtitleripper 0.3.4-0.5ubunt DVD Subtitle Ripper for Linux
ii  sudo           1.7.2p1-1ubunt Provide limited super user privileges to spe
ii  synaptic       0.63.1ubuntu7  Graphical package manager
ii  syslinux       2:3.63+dfsg-2u Bootloader for Linux/i386 using MS-DOS flopp
ii  system-config- 1.2.0+20100408 Printer configuration GUI
ii  system-config- 1.2.0+20100408 Printer configuration GUI
ii  system-config- 1.2.0+20100408 Printer auto-configuration facility based on
ii  system-tools-b 2.9.4-0ubuntu1 System Tools to manage computer configuratio
ii  sysv-rc        2.87dsf-4ubunt System-V-like runlevel change mechanism
ii  sysvinit-utils 2.87dsf-4ubunt System-V-like utilities
ii  tango-icon-the 0.8.90-3       Tango icon theme
ii  tar            1.22-2         GNU version of the tar archiving utility
ii  tasksel        2.73ubuntu26   Tool for selecting tasks for installation on
ii  tasksel-data   2.73ubuntu26   Official tasks used for installation of Debi
ii  tcl8.4         8.4.19-4       Tcl (the Tool Command Language) v8.4 - run-t
ii  tcpd           7.6.q-18       Wietse Venema's TCP wrapper utilities
ii  tcpdump        4.0.0-6ubuntu3 A powerful tool for network monitoring and d
ii  telepathy-butt 0.5.9-0ubuntu1 MSN connection manager for Telepathy
ii  telepathy-gabb 0.8.12-0ubuntu Jabber/XMPP connection manager
ii  telepathy-haze 0.3.4-1        A telepathy connection manager that use libp
ii  telepathy-idle 0.1.6-1        IRC connection manager for Telepathy
ii  telepathy-miss 5.3.2-3        management daemon for Telepathy real-time co
ii  telepathy-salu 0.3.11-1       Link-local XMPP connection manager for the T
ii  telnet         0.17-36build1  The telnet client
ii  thoggen        0.7.1-1ubuntu1 DVD backup utility based on GStreamer and Gt
ii  tidy           20091223cvs-1  HTML syntax checker and reformatter
ii  time           1.7-23build1   The GNU time program for measuring cpu resou
ii  tk8.4          8.4.19-4       Tk toolkit for Tcl and X11, v8.4 - run-time 
ii  tomboy         1.2.1-0ubuntu1 desktop note taking program using Wiki style
ii  toshset        1.75-2         Access much of the Toshiba laptop hardware i
ii  totem          2.30.2-0ubuntu A simple media player for the GNOME desktop 
ii  totem-common   2.30.2-0ubuntu Data files for the Totem media player
ii  totem-mozilla  2.30.2-0ubuntu Totem Mozilla plugin
ii  totem-plugins  2.30.2-0ubuntu Plugins for the Totem media player
ii  transcode      3:1.1.5-0ubunt Utility to encode raw video/audio streams
ii  transcode-doc  3:1.1.5-0ubunt Documentation for transcode
ii  transcode-util 3:1.1.5-0ubunt Transcode utility programs
ii  transfig       1:3.2.5.a-2.1  Utilities for converting XFig figure files
ii  transmission-c 1.92-0ubuntu2. lightweight BitTorrent client (common files)
ii  transmission-g 1.92-0ubuntu2. lightweight BitTorrent client (GTK interface
ii  tsclient       0.150-3ubuntu1 front-end for viewing of remote desktops in 
ii  tsconf         1.0-7build1    touch screen library common files
ii  ttf-arphic-uka 0.2.20080216.1 "AR PL UKai" Chinese Unicode TrueType font c
ii  ttf-arphic-umi 0.2.20080216.1 "AR PL UMing" Chinese Unicode TrueType font 
ii  ttf-dejavu     2.30-2         Metapackage to pull in ttf-dejavu-core and t
ii  ttf-dejavu-cor 2.30-2         Vera font family derivate with additional ch
ii  ttf-dejavu-ext 2.30-2         Vera font family derivate with additional ch
ii  ttf-freefont   20090104-5     Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-font 1:0.5.8ubuntu2 Core collection of free fonts for languages 
ii  ttf-kacst-one  3.0-1ubuntu2   TrueType font designed for Arabic language
ii  ttf-khmeros-co 5.0-3ubuntu1   KhmerOS Unicode fonts for the Khmer language
ii  ttf-lao        0.0.20060226-6 TrueType font for Lao language
ii  ttf-liberation 1.05.2.2009101 Fonts with the same metrics as Times, Arial 
ii  ttf-mscorefont 3.2            Installer for Microsoft TrueType core fonts
ii  ttf-opensymbol 1:3.2.0-7ubunt OpenSymbol TrueType font
ii  ttf-punjabi-fo 1:0.5.8ubuntu2 Free TrueType fonts for the Punjabi language
ii  ttf-symbol-rep 1.1.42-0ubuntu Free font with the same metrics as Symbol
ii  ttf-takao-pgot 003.02.01-2ubu Japanese TrueType font set, Takao P Gothic F
ii  ttf-thai-tlwg  1:0.4.13-4     Thai fonts in TrueType format
ii  ttf-unfonts-co 1.0.1-7ubuntu1 Un series Korean TrueType fonts
ii  ttf-wqy-microh 0.2.0-beta-1   A droid derived Sans-Seri style CJK font
ii  ttf-wqy-zenhei 0.8.38-1ubuntu "WenQuanYi Zen Hei" A Hei-Ti Style (sans-ser
ii  twolame        0.3.12-1       MPEG Audio Layer 2 encoder (command line fro
ii  tzdata         2010j-0ubuntu0 time zone and daylight-saving time data
ii  tzdata-java    2010j-0ubuntu0 time zone and daylight-saving time data for 
ii  ubufox         0.9~rc2-0ubunt Ubuntu Firefox specific configuration defaul
ii  ubuntu-artwork 53.5           Ubuntu themes and artwork
ii  ubuntu-desktop 1.197          The Ubuntu desktop system
ii  ubuntu-docs    10.04.3        The Ubuntu Documentation Project
ii  ubuntu-keyring 2010.11.09     GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal 1.197          Minimal core of Ubuntu
ii  ubuntu-mono    0.0.18         Ubuntu Mono Icon theme
ii  ubuntu-restric 39             Commonly used restricted packages for Ubuntu
ii  ubuntu-sounds  0.12           Ubuntu's GNOME audio theme
ii  ubuntu-standar 1.197          The Ubuntu standard system
ii  ubuntu-system- 0.1.20         Dbus service to set various system-wide conf
ii  ubuntu-wallpap 0.31.3         Ubuntu Wallpapers
ii  ubuntuone-clie 1.2.1-0ubuntu3 Ubuntu One client
ii  ubuntuone-clie 1.2.1-0ubuntu3 Ubuntu One client GNOME integration
ii  ucf            3.0025         Update Configuration File: preserve user cha
ii  udev           151-12         rule-based device node and kernel event mana
ii  udisks         1.0.1-1build1  abstraction for enumerating block devices
ii  ufw            0.30pre1-0ubun program for managing a Netfilter firewall
ii  unattended-upg 0.55ubuntu4    automatic installation of security upgrades
ii  uno-libs3      1.6.0+OOo3.2.0 OpenOffice.org UNO runtime environment -- pu
ii  unrar          1:3.9.3-1      Unarchiver for .rar files (non-free version)
ii  unzip          6.0-1build1    De-archiver for .zip files
ii  update-inetd   4.35           inetd configuration file updater
ii  update-manager 1:0.134.9      GNOME application that manages apt updates
ii  update-manager 1:0.134.9      manage release upgrades
ii  update-manager 1:0.134.9      Support modules for Update Notifier KDE
ii  update-notifie 0.99.3         Daemon which notifies about package updates
ii  update-notifie 0.99.3         Files shared between update-notifier and ade
ii  upower         0.9.1-1        abstraction for power management
ii  upstart        0.6.5-6        event-based init daemon
ii  ure            1.6.0+OOo3.2.0 OpenOffice.org UNO runtime environment
ii  ureadahead     0.100.0-4.1    Read required files in advance
ii  usb-creator-co 0.2.22         Ubuntu startup disk creator common files
ii  usb-creator-gt 0.2.22         Ubuntu startup disk creator for GTK+
ii  usbmuxd        1.0.2-1ubuntu2 USB multiplexor daemon for iPhone and iPod T
ii  usbutils       0.86-2ubuntu1  Linux USB utilities
ii  util-linux     2.17.2-0ubuntu Miscellaneous system utilities
ii  uuid-runtime   2.17.2-0ubuntu runtime components for the Universally Uniqu
ii  vbetool        1.1-2          run real-mode video BIOS code to alter hardw
ii  vcdimager      0.7.23-4ubuntu A VideoCD (VCD) image mastering and ripping 
ii  vim-addon-mana 0.4.3          manager of addons for the Vim editor
ii  vim-common     2:7.2.330-1ubu Vi IMproved - Common files
ii  vim-gnome      2:7.2.330-1ubu Vi IMproved - enhanced vi editor - with GNOM
ii  vim-gui-common 2:7.2.330-1ubu Vi IMproved - Common GUI files
ii  vim-runtime    2:7.2.330-1ubu Vi IMproved - Runtime files
ii  vim-tiny       2:7.2.330-1ubu Vi IMproved - enhanced vi editor - compact v
ii  vinagre        2.30.1-0ubuntu remote desktop client for the GNOME Desktop
ii  vino           2.28.2-0ubuntu VNC server for GNOME
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - base binaries
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - kernel module 
ii  virtualbox-ose 3.1.6-dfsg-2ub x86 virtualization solution - Qt based user 
ii  virtuoso-nepom 6.1.0-0ubuntu3 OpenLink Virtuoso Open-Source Edition (OSE)
ii  vlc            1.0.6-1ubuntu1 multimedia player and streamer
ii  vlc-data       1.0.6-1ubuntu1 Common data for VLC
ii  vlc-nox        1.0.6-1ubuntu1 multimedia player and streamer (without X su
ii  vlc-plugin-pul 1.0.6-1ubuntu1 PulseAudio plugin for VLC
ii  w3m            0.5.2-2.1ubunt WWW browsable pager with excellent tables/fr
ii  w64codecs      20071007-0medi Proprietary codec binaries, x86_64 version
ii  wamerican      6-3            American English dictionary words for /usr/s
ii  wbritish       6-3            British English dictionary words for /usr/sh
ii  webhttrack     3.43.9-1ubuntu Copy websites to your computer, httrack with
ii  webhttrack-com 3.43.9-1ubuntu webhttrack common files
ii  webmin         1.510-2        A web-based administration interface for Uni
ii  wget           1.12-1.1ubuntu retrieves files from the web
ii  whiptail       0.52.10-5ubunt Displays user-friendly dialog boxes from she
ii  whois          5.0.0ubuntu3   an intelligent whois client
ii  winbind        2:3.4.7~dfsg-1 Samba nameservice integration server
ii  wine           1.1.42-0ubuntu Microsoft Windows Compatibility Layer (dummy
ii  wine1.2        1.1.42-0ubuntu Microsoft Windows Compatibility Layer (Binar
ii  wine1.2-gecko  1.0.0-0ubuntu4 Microsoft Windows Compatibility Layer (Web B
ii  winpdb         1.4.6-1        Platform independent Python debugger
ii  wireless-crda  1.12           Wireless Central Regulatory Domain Agent
ii  wireless-tools 30~pre9-3ubunt Tools for manipulating Linux Wireless Extens
ii  wodim          9:1.1.10-1ubun command line CD/DVD writing tool
ii  wpasupplicant  0.6.9-3ubuntu3 client support for WPA and WPA2 (IEEE 802.11
ii  wx2.8-doc      2.8.10.1-0ubun wxWidgets Cross-platform C++ GUI toolkit (do
ii  x-ttcidfont-co 32             TrueType and CID fonts configuration for X
ii  x11-apps       7.5+1ubuntu2   X applications
ii  x11-common     1:7.5+5ubuntu1 X Window System (X.Org) infrastructure
ii  x11-session-ut 7.5+1          X session utilities
ii  x11-utils      7.5+3          X11 utilities
ii  x11-xfs-utils  7.4+1build2    X font server utilities
ii  x11-xkb-utils  7.5+1          X11 XKB utilities
ii  x11-xserver-ut 7.5+1ubuntu2   X server utilities
ii  xauth          1:1.0.4-1      X authentication utility
ii  xbitmaps       1.1.0-1        Base X bitmaps
ii  xcursor-themes 1.0.2-1        Base X cursor themes
ii  xdg-user-dirs  0.12-0ubuntu2  tool to manage well known user directories
ii  xdg-user-dirs- 0.8-1ubuntu1   tool to manage well known user directories (
ii  xdg-utils      1.0.2-6.1ubunt desktop integration utilities from freedeskt
ii  xfonts-100dpi  1:1.0.1        100 dpi fonts for X
ii  xfonts-75dpi   1:1.0.1        75 dpi fonts for X
ii  xfonts-base    1:1.0.1        standard fonts for X
ii  xfonts-encodin 1:1.0.3-1      Encodings for X.Org fonts
ii  xfonts-mathml  4ubuntu1       Type1 Symbol font for MathML
ii  xfonts-scalabl 1:1.0.1-1      scalable fonts for X
ii  xfonts-utils   1:7.5+2        X Window System font utility programs
ii  xfonts-wqy     0.9.9-3.2      WenQuanYi Bitmap Song CJK font for X
ii  xine-ui        0.99.5+cvs2007 the xine video player, user interface
ii  xinit          1.2.0-1        X server initialisation tool
ii  xinput         1.5.0-2ubuntu1 Runtime configuration and test of XInput dev
ii  xkb-data       1.8-1ubuntu8   X Keyboard Extension (XKB) configuration dat
ii  xml-core       0.13           XML infrastructure and XML catalog file supp
ii  xorg           1:7.5+5ubuntu1 X.Org X Window System
ii  xorg-docs-core 1:1.5-1        Core documentation for the X.org X Window Sy
ii  xsane          0.996-2ubuntu3 featureful graphical frontend for SANE (Scan
ii  xsane-common   0.996-2ubuntu3 featureful graphical frontend for SANE (Scan
ii  xscreensaver-d 5.10-3ubuntu4  data files to be shared among screensaver fr
ii  xscreensaver-g 5.10-3ubuntu4  GL(Mesa) screen hacks for xscreensaver
ii  xserver-common 2:1.7.6-2ubunt common files used by various X servers
ii  xserver-xorg   1:7.5+5ubuntu1 the X.Org X server
ii  xserver-xorg-c 2:1.7.6-2ubunt Xorg X server - core server
ii  xserver-xorg-i 1:7.5+5ubuntu1 the X.Org X server -- input driver metapacka
ii  xserver-xorg-i 1:2.3.2-5ubunt X.Org X server -- evdev input driver
ii  xserver-xorg-i 1:1.5.0-1      X.Org X server -- mouse input driver
ii  xserver-xorg-i 1.2.2-1ubuntu4 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-i 1:12.6.5-4ubun X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-i 1:0.10.5-0ubun X.Org X server -- Wacom input driver
ii  xserver-xorg-v 1:7.5+5ubuntu1 the X.Org X server -- output driver metapack
ii  xserver-xorg-v 1:1.2.2-1      X.Org X server -- APM display driver
ii  xserver-xorg-v 1:0.7.2-1      X.Org X server -- ark display driver
ii  xserver-xorg-v 1:6.13.0-1ubun X.Org X server -- AMD/ATI display driver wra
ii  xserver-xorg-v 1:1.2.2-1      X.Org X server -- Chips display driver
ii  xserver-xorg-v 1:1.3.2-1ubunt X.Org X server -- Cirrus display driver
ii  xserver-xorg-v 1:0.4.1-1ubunt X.Org X server -- fbdev display driver
ii  xserver-xorg-v 1:1.3.3-1      X.Org X server -- i128 display driver
ii  xserver-xorg-v 2:2.9.1-3ubunt X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-v 6.8.2-2        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-v 1:1.4.11.dfsg- X.Org X server -- MGA display driver
ii  xserver-xorg-v 1:1.2.4-2      X.Org X server -- Neomagic display driver
ii  xserver-xorg-v 1:0.0.15+git20 X.Org X server -- Nouveau display driver (ex
ii  xserver-xorg-v 1:2.1.15-1ubun X.Org X server -- NV display driver
ii  xserver-xorg-v 1:0.2.904+svn8 X.Org X server -- VIA display driver
ii  xserver-xorg-v 6.8.1-2ubuntu1 X.Org X server -- ATI r128 display driver
ii  xserver-xorg-v 1:6.13.0-1ubun X.Org X server -- AMD/ATI Radeon display dri
ii  xserver-xorg-v 1:4.2.3-1      X.Org X server -- Rendition display driver
ii  xserver-xorg-v 1:0.6.3-1      X.Org X server -- legacy S3 display driver
ii  xserver-xorg-v 1:1.10.4-1     X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-v 1:2.3.1-1ubunt X.Org X server -- Savage display driver
ii  xserver-xorg-v 1:1.7.3-1      X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-v 1:0.10.2-2     X.Org X server -- SiS display driver
ii  xserver-xorg-v 1:0.9.3-1      X.Org X server -- SiS USB display driver
ii  xserver-xorg-v 1:1.4.3-1      X.Org X server -- tdfx display driver
ii  xserver-xorg-v 1:1.3.3-1      X.Org X server -- Trident display driver
ii  xserver-xorg-v 1:1.2.3-1      X.Org X server -- Tseng display driver
ii  xserver-xorg-v 1:0.2.0-4      X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-v 1:2.3.0-1ubunt X.Org X server -- VESA display driver
ii  xserver-xorg-v 1:10.16.9-1    X.Org X server -- VMware display driver
ii  xserver-xorg-v 1:1.2.3-1      X.Org X server -- Voodoo display driver
ii  xsltproc       1.1.26-1ubuntu XSLT command line processor
ii  xterm          256-1ubuntu1   X terminal emulator
ii  xulrunner-1.9. 1.9.2.3+nobino XUL + XPCOM application runner
ii  yelp           2.30.0-0ubuntu Help browser for GNOME
ii  zenity         2.30.0-0ubuntu Display graphical dialog boxes from shell sc
ii  zip            3.0-2          Archiver for .zip files
ii  zlib1g         1:1.2.3.3.dfsg compression library - runtime
gdeering@ubuntuLTS-desktop:~$ 

```

---

### Post by Don Barzini on 2010-06-21
It's possible the fix in the post linked below could be a good start toward fixing your problem.

[http://ubuntuforums.org/showpost.php?p=9094227&postcount=11](http://ubuntuforums.org/showpost.php?p=9094227&postcount=11)

You might also want to check the link below and the section "KMS with a Radeon card" for some more ideas....

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by Ashocka on 2010-06-26
There was a lot of segfaults, and I found corrupt files but all checks on the file system were OK, so I reinstalled the distro.  I did note however that booting into the old distro and using the previous kernel seemed stable.  But solved that way.

---

