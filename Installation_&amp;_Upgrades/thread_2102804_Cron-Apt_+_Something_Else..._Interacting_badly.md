---
title: "Cron-Apt + Something Else... Interacting badly"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by Kirk Schnable on 2013-01-08
I am one of two Linux techs managing a deployment of roughly 800 computers in an education environment.  Because our student end-users do not have administrative access to our computers, we were seeking a way to keep the computers up-to-date.  This led us to Cron-Apt.

We have always managed configurations, and installed applications, using the open source version of Puppet.  We continued with this, as our method of pushing out new applcations, using their package selection tools and only asking Puppet to install packages if they aren't installed.

Because many of our computers are mobile, we have had Puppet running some corrective commands automatically since the beginning of our 10.04 deployment.  Commands like
```
dpkg --configure -a
```
```
apt-get -f -y install
```
These commands have done a fantastic job (for the most part) of fixing packages on laptops\netbooks that the students impatiently shut down by pressing and holding the power button whilest rushing to their next class.

Over this winter break, we upgraded everything with a fresh image, from Ubuntu 10.04 LTS to Xubuntu 12.04 LTS.  This time around, we decided to deploy Cron-Apt doing a dist-upgrade automatically, to keep everything up-to-date. 

We tested the setup for weeks... actually having our beta image back in early December, and having a small subset of students use it knowingly.

Then, I suppose last week sometime, there was an update to GRUB.  grub2-common, grub-pc, etc.  You can imagine my feeling of genuine fear and dread yesterday when I saw batches of computers failing to boot, presenting only a blinking cursor.


Our instinct was to blame Cron-Apt, the new guy... but it seems the problem is far more complex than that.  My coworker and I stayed after school until past midnight last night, and we couldn't figure out how to reliably reproduce it exactly.

We did figure out a way to stop it from happening from the get-go to the other 700 of the computers... we redirected local DNS for us.archive.ubuntu.com, archive.ubuntu.com, and security.ubuntu.com to 127.0.0.1.  


From what we've seen so far, it's not Cron-Apt's fault.  If you run cron-apt on a freshly imaged computer, it updates GRUB, then the computer reboots fine.

It doesn't seem to be Puppet's fault either.  If you run our Puppet manifest on a freshly imaged computer, it installs some new packages that weren't on the image, and finishes.  On the flipside... if you run cron-apt, then you reboot and run Puppet, if you reboot the computer, it never comes back.  I tried running Puppet with our forceful apt reconfiguration commands (described above in the CODE boxes) commented out.  This helped.....sometimes but not always.

Running Puppet with all APT commands commented out... (or blocked external DNS so they can't fetch packages) helped 100% of the time preventing the problem. But I was very confused as to why this helped, because the things I'm installing with Puppet are very innocent, like Oracle Java 7, WINE, Flash Plugin, etc.

When we left at midnight last night, we were exhausted and out of ideas.  I will have to continue troubleshooting this today, and I will update this thread when I know more.  In the meantime, if anyone has seen anything remotely like this, I'd love to hear from you.

I suspect the problem may be related to an event which occurs once Cron-Apt updates GRUB boot loader, and then Puppet installs an unrelated package with dpkg force confold install.


I look forward to working with some fellow Ubuntu folks toward resolving this.

Thanks!
Kirk

---

### Post by Kirk Schnable on 2013-01-09
Today, we have done some diffing between dpkg lists.

**DPKG List of Installed Packages (clean image)**
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                                 Description
+++-=============================================-=======================================-=================================================================================================================================================
rc  abiword                                       2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration
ii  abiword-common                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- common files
ii  accountsservice                               0.6.15-2ubuntu9.4                       query and manipulate user account information
ii  acl                                           2.2.51-5ubuntu1                         Access control list utilities
ii  acpi-support                                  0.140                                   scripts for handling many ACPI events
ii  acpid                                         1:2.0.10-1ubuntu3                       Advanced Configuration and Power Interface event daemon
ii  adduser                                       3.113ubuntu2                            add and remove users and groups
rc  aisleriot                                     1:3.2.3.2-0ubuntu1                      Solitaire card games
rc  akonadi-backend-mysql                         1.7.2-0ubuntu1                          MySQL storage backend for Akonadi
rc  akonadi-server                                1.7.2-0ubuntu1                          Akonadi PIM storage service
ii  alacarte                                      0.13.2-2ubuntu4                         easy GNOME menu editing tool
ii  alsa-base                                     1.0.25+dfsg-0ubuntu1                    ALSA driver configuration files
ii  alsa-utils                                    1.0.25-1ubuntu5                         Utilities for configuring and using ALSA
ii  anacron                                       2.3-14ubuntu1                           cron-like program that doesn't go by time
ii  app-install-data                              0.12.04.4                               Ubuntu applications (data files)
ii  app-install-data-partner                      12.12.04.1                              Application Installer (data files for partner applications/repositories)
ii  apparmor                                      2.7.102-0ubuntu3.7                      User-space parser utility for AppArmor
ii  apport                                        2.0.1-0ubuntu15.1                       automatically generate crash reports for debugging
ii  apport-gtk                                    2.0.1-0ubuntu15.1                       GTK+ frontend for the apport crash report system
ii  apport-symptoms                               0.16.1                                  symptom scripts for apport
ii  apt                                           0.8.16~exp12ubuntu10.7                  commandline package manager
ii  apt-transport-https                           0.8.16~exp12ubuntu10.7                  https download transport for APT
ii  apt-utils                                     0.8.16~exp12ubuntu10.7                  package managment related utility programs
ii  apt-xapian-index                              0.44ubuntu5                             maintenance and search tools for a Xapian index of Debian packages
ii  aptdaemon                                     0.43+bzr805-0ubuntu7                    transaction based package management service
ii  aptdaemon-data                                0.43+bzr805-0ubuntu7                    data files for clients
ii  artha                                         1.0.2-1ubuntu1                          Handy off-line thesaurus based on WordNet
ii  aspell                                        0.60.7~20110707-1                       GNU Aspell spell-checker
ii  aspell-en                                     6.0-0-6ubuntu2                          English dictionary for GNU Aspell
ii  at                                            3.1.13-1ubuntu1                         Delayed job execution and batch processing
ii  at-spi2-core                                  2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface (dbus core)
ii  audacity                                      2.0.0-1ubuntu0.1                        fast, cross-platform audio editor
ii  audacity-data                                 2.0.0-1ubuntu0.1                        fast, cross-platform audio editor (data)
ii  augeas-lenses                                 0.10.0-0ubuntu4                         Set of lenses needed by libaugeas0 to parse config files
ii  avahi-autoipd                                 0.6.30-5ubuntu2                         Avahi IPv4LL network address configuration daemon
ii  avahi-daemon                                  0.6.30-5ubuntu2                         Avahi mDNS/DNS-SD daemon
ii  avahi-utils                                   0.6.30-5ubuntu2                         Avahi browsing, publishing and discovery utilities
ii  avogadro-data                                 1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Data Files)
ii  banshee                                       2.4.1-3ubuntu1~precise2                 Media Management and Playback application
ii  banshee-extension-soundmenu                   2.4.1-3ubuntu1~precise2                 Media Management and Playback application - sound menu extension
ii  base-files                                    6.5ubuntu6.4                            Debian base system miscellaneous files
ii  base-passwd                                   3.5.24                                  Debian base system master password and group files
ii  bash                                          4.2-2ubuntu2                            GNU Bourne Again SHell
ii  bash-completion                               1:1.3-1ubuntu8                          programmable completion for the bash shell
ii  bc                                            1.06.95-2                               The GNU bc arbitrary precision calculator language
ii  bind9-host                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Version of 'host' bundled with BIND 9.X
ii  binfmt-support                                2.0.8                                   Support for extra binary formats
ii  binutils                                      2.22-6ubuntu1                           GNU assembler, linker and binary utilities
ii  bison                                         1:2.5.dfsg-2.1                          YACC-compatible parser generator
ii  blender                                       2.62-1                                  Very fast and versatile 3D modeller/renderer
ii  blt                                           2.4z-4.2ubuntu1                         the BLT extension library for Tcl/Tk - run-time package
ii  blueman                                       1.23-0ubuntu2.1                         A Graphical bluetooth manager
ii  bluez                                         4.98-2ubuntu7                           Bluetooth tools and daemons
ii  bluez-alsa                                    4.98-2ubuntu7                           Bluetooth ALSA support
ii  bluez-cups                                    4.98-2ubuntu7                           Bluetooth printer driver for CUPS
ii  brasero                                       3.4.1-0ubuntu1.1                        CD/DVD burning application for GNOME
ii  brasero-cdrkit                                3.4.1-0ubuntu1.1                        cdrkit extensions for the Brasero burning application
ii  brasero-common                                3.4.1-0ubuntu1.1                        Common files for the Brasero CD burning application and library
ii  brltty                                        4.3-1ubuntu5                            Access software for a blind person using a braille display
ii  brltty-x11                                    4.3-1ubuntu5                            Access software for a blind person using a braille display - X11 drivers
ii  bsdmainutils                                  8.2.3ubuntu1                            collection of more utilities from FreeBSD
ii  bsdutils                                      1:2.20.1-1ubuntu3                       Basic utilities from 4.4BSD-Lite
ii  bsh                                           2.0b4-12build1                          Java scripting environment (BeanShell) Version 2
ii  bsh-gcj                                       2.0b4-12build1                          Java scripting environment (BeanShell) Version 2 (native code)
ii  build-essential                               11.5ubuntu2.1                           Informational list of build-essential packages
ii  busybox-initramfs                             1:1.18.5-1ubuntu4.1                     Standalone shell setup for initramfs
ii  busybox-static                                1:1.18.5-1ubuntu4.1                     Standalone rescue shell with tons of builtin utilities
ii  bzip2                                         1.0.6-1                                 high-quality block-sorting file compressor - utilities
ii  ca-certificates                               20111211                                Common CA certificates
ii  ca-certificates-java                          20110912ubuntu6                         Common CA certificates (JKS keystore)
ii  cabextract                                    1.4-1                                   Microsoft Cabinet file unpacker
rc  catfish                                       0.3.2-2ubuntu1                          file search tool that support several different engines
rc  charmap.app                                   0.2-11                                  Character map for GNUstep
ii  cheese                                        3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam
ii  cheese-common                                 3.4.1-0ubuntu2.1                        Common files for the Cheese tool to take pictures and videos
ii  chromium-browser                              20.0.1132.47~r144678-0ubuntu0.12.04.1   Chromium browser
ii  chromium-browser-l10n                         20.0.1132.47~r144678-0ubuntu0.12.04.1   chromium-browser language packages
ii  chromium-codecs-ffmpeg                        20.0.1132.47~r144678-0ubuntu0.12.04.1   Free ffmpeg codecs for the Chromium Browser
ii  clamav                                        0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - command-line interface
ii  clamav-base                                   0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - base package
ii  clamav-freshclam                              0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - virus database update utility
ii  cli-common                                    0.8.2                                   common files between all CLI packages
ii  cmap-adobe-japan1                             0+20090930-2                            CMaps for Adobe-Japan1
ii  colord                                        0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- system daemon
ii  command-not-found                             0.2.46ubuntu6                           Suggest installation of packages in interactive bash sessions
ii  command-not-found-data                        0.2.46ubuntu6                           Set of data files for command-not-found.
ii  conky                                         1.8.1-6                                 highly configurable system monitor (transitional package)
ii  conky-std                                     1.8.1-6                                 highly configurable system monitor (default version)
ii  console-setup                                 1.70ubuntu5                             console font and keymap setup program
ii  consolekit                                    0.4.5-2                                 framework for defining and tracking users, sessions and seats
ii  coreutils                                     8.13-3ubuntu3.2                         GNU core utilities
ii  cpio                                          2.11-7ubuntu3                           GNU cpio -- a program to manage archives of files
ii  cpp                                           4:4.6.3-1ubuntu5                        GNU C preprocessor (cpp)
ii  cpp-4.6                                       4.6.3-1ubuntu5                          GNU C preprocessor
ii  crda                                          1.1.2-1ubuntu1                          wireless Central Regulatory Domain Agent
ii  cron                                          3.0pl1-120ubuntu4                       process scheduling daemon
ii  cron-apt                                      0.9.0                                   automatic update of packages using apt-get
ii  cryptsetup-bin                                2:1.4.1-2ubuntu4                        disk encryption support - command line tools
ii  cups                                          1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - server
ii  cups-bsd                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - common files
ii  cups-filters                                  1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters
ii  cups-ppdc                                     1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation utilities
ii  curl                                          7.22.0-3ubuntu4                         Get a file from an HTTP, HTTPS or FTP server
ii  dash                                          0.5.7-2ubuntu2                          POSIX-compliant shell
ii  dbus                                          1.4.18-1ubuntu1.3                       simple interprocess messaging system (daemon and utilities)
ii  dbus-x11                                      1.4.18-1ubuntu1.3                       simple interprocess messaging system (X11 deps)
ii  dc                                            1.06.95-2                               The GNU dc arbitrary precision reverse-polish calculator
ii  dconf-gsettings-backend                       0.12.0-0ubuntu1.1                       simple configuration storage system - GSettings back-end
ii  dconf-service                                 0.12.0-0ubuntu1.1                       simple configuration storage system - D-Bus service
ii  dcraw                                         8.99-1build1                            decode raw digital camera images
ii  debconf                                       1.5.42ubuntu1                           Debian configuration management system
ii  debconf-i18n                                  1.5.42ubuntu1                           full internationalization support for debconf
ii  debconf-utils                                 1.5.42ubuntu1                           debconf utilities
ii  debianutils                                   4.2.1ubuntu2                            Miscellaneous utilities specific to Debian
ii  default-jre                                   1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime
ii  default-jre-headless                          1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime (headless)
ii  desktop-file-utils                            0.20-0ubuntu3                           Utilities for .desktop files
ii  devede                                        3.21.0-1                                simple application to create Video DVDs
ii  dia                                           0.97.2-5                                Diagram editor
ii  dia-common                                    0.97.2-5                                Diagram editor (common files)
ii  dia-libs                                      0.97.2-5                                Diagram editor (library files)
ii  dictionaries-common                           1.12.1ubuntu2                           Common utilities for spelling dictionary tools
ii  diffutils                                     1:3.2-1ubuntu1                          File comparison utilities
ii  dmidecode                                     2.11-4                                  SMBIOS/DMI table decoder
ii  dmsetup                                       2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  dmz-cursor-theme                              0.4.3                                   Style neutral, scalable cursor theme
ii  dnsmasq-base                                  2.59-4                                  Small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                      1:9.8.1.dfsg.P1-4ubuntu0.5              Clients provided with BIND
ii  doc-base                                      0.10.3                                  utilities to manage online documentation
ii  docbook-xml                                   4.5-7ubuntu1                            standard XML documentation system for software and systems
ii  docbook-xsl                                   1.76.1+dfsg-1ubuntu1                    stylesheets for processing DocBook XML to various output formats
ii  dosfstools                                    3.0.12-1ubuntu1                         utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                          1.16.1.2ubuntu7                         Debian package management system
ii  dpkg-dev                                      1.16.1.2ubuntu7                         Debian package development tools
ii  drgeo                                         1.1.0-9                                 An interactive geometry software
ii  drgeo-doc                                     1.5-6                                   The Dr. Geo online user manual
ii  dvd+rw-tools                                  7.1-10                                  DVD+-RW/R tools
ii  dvdauthor                                     0.7.0-1.1build1                         create DVD-Video file system
ii  e2fslibs                                      1.42-1ubuntu2                           ext2/ext3/ext4 file system libraries
ii  e2fsprogs                                     1.42-1ubuntu2                           ext2/ext3/ext4 file system utilities
ii  earth3d                                       1.0.5-3                                 Map client displaying a 3D model of the world
ii  ed                                            1.5-3                                   classic UNIX line editor
ii  eject                                         2.1.5+deb1+cvs20081104-9                ejects CDs and operates CD-Changers under Linux
ii  electric                                      8.10-2                                  electrical CAD system
ii  enchant                                       1.6.0-7                                 Wrapper for various spell checker engines (binary programs)
ii  esound-common                                 0.2.41-10build3                         Enlightened Sound Daemon - Common files
ii  espeak                                        1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer
ii  espeak-data                                   1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: speech data files
ii  evince                                        3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer
ii  evince-common                                 3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer - common files
ii  exo-utils                                     0.6.2-4                                 Utility files for libexo
ii  f-spot                                        0.8.2-4                                 personal photo management application
ii  facter                                        1.6.16-1puppetlabs1                     Ruby module for collecting simple facts about a host operating system
ii  fakeroot                                      1.18.2-1                                tool for simulating superuser privileges
ii  ffmpeg                                        4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder (transitional package)
ii  file                                          5.09-2                                  Determines file type using "magic" numbers
ii  file-roller                                   3.4.1-0ubuntu1                          archive manager for GNOME
ii  findutils                                     4.4.2-4ubuntu1                          utilities for finding files--find, xargs
ii  firefox                                       17.0.1+build1-0ubuntu0.12.04.1          Safe and easy web browser from Mozilla
ii  firefox-globalmenu                            17.0.1+build1-0ubuntu0.12.04.1          Unity appmenu integration for Firefox
ii  firefox-gnome-support                         17.0.1+build1-0ubuntu0.12.04.1          Safe and easy web browser from Mozilla - GNOME support
ii  firefox-locale-en                             17.0.1+build1-0ubuntu0.12.04.1          English language pack for Firefox
ii  flashplugin-installer                         11.2.202.258ubuntu0.12.04.1             Adobe Flash Player plugin installer
ii  flex                                          2.5.35-10ubuntu3                        A fast lexical analyzer generator.
ii  fontconfig                                    2.8.0-3ubuntu9.1                        generic font configuration library - support binaries
ii  fontconfig-config                             2.8.0-3ubuntu9.1                        generic font configuration library - configuration
ii  fonts-droid                                   20101110+git-2                          handheld device font with extensive style and language support
ii  fonts-horai-umefont                           434-1                                   Japanese TrueType font, Ume-font
ii  fonts-kacst                                   2.01+mry-3                              KACST free TrueType Arabic fonts
ii  fonts-kacst-one                               5.0+svn11846-2                          TrueType font designed for Arabic language
ii  fonts-khmeros-core                            5.0-5ubuntu1                            KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                                     0.0.20060226-8                          TrueType font for Lao language
ii  fonts-liberation                              1.07.0-2ubuntu0.1                       Fonts with the same metrics as Times, Arial and Courier
ii  fonts-nanum                                   3.010-2                                 Nanum Korean fonts
ii  fonts-opensymbol                              2:102.2+LibO3.5.4-0ubuntu1.1            OpenSymbol TrueType font
ii  fonts-sil-gentium                             20081126:1.02-12                        extended Unicode Latin font ("a typeface for the nations")
ii  fonts-sil-gentium-basic                       1.1-5                                   smart Unicode font families (Basic and Book Basic) based on Gentium
ii  fonts-takao-pgothic                           003.02.01-5ubuntu1                      Japanese TrueType font set, Takao P Gothic Fonts
ii  fonts-thai-tlwg                               1:0.4.17-1ubuntu1                       Thai fonts maintained by TLWG (meta package)
ii  fonts-tlwg-garuda                             1:0.4.17-1ubuntu1                       Thai Garuda font
ii  fonts-tlwg-kinnari                            1:0.4.17-1ubuntu1                       Thai Kinnari font
ii  fonts-tlwg-loma                               1:0.4.17-1ubuntu1                       Thai Loma font
ii  fonts-tlwg-mono                               1:0.4.17-1ubuntu1                       Thai TlwgMono font
ii  fonts-tlwg-norasi                             1:0.4.17-1ubuntu1                       Thai Norasi font
ii  fonts-tlwg-purisa                             1:0.4.17-1ubuntu1                       Thai Purisa font
ii  fonts-tlwg-sawasdee                           1:0.4.17-1ubuntu1                       Thai Sawasdee font
ii  fonts-tlwg-typewriter                         1:0.4.17-1ubuntu1                       Thai TlwgTypewriter font
ii  fonts-tlwg-typist                             1:0.4.17-1ubuntu1                       Thai TlwgTypist font
ii  fonts-tlwg-typo                               1:0.4.17-1ubuntu1                       Thai TlwgTypo font
ii  fonts-tlwg-umpush                             1:0.4.17-1ubuntu1                       Thai Umpush font
ii  fonts-tlwg-waree                              1:0.4.17-1ubuntu1                       Thai Waree font
ii  fonts-unfonts-core                            1.0.3.is.1.0.2-080608-5ubuntu1          Un series Korean TrueType fonts
ii  foomatic-db-compressed-ppds                   20120322-0ubuntu1                       OpenPrinting printer support - Compressed PPDs derived from the database
ii  foomatic-db-engine                            4.0.8-2ubuntu1                          OpenPrinting printer support - programs
ii  foomatic-filters                              4.0.16-0ubuntu0.2                       OpenPrinting printer support - filters
ii  freepats                                      20060219-1                              Free patch set for MIDI audio synthesis
ii  frei0r-plugins                                1.1.22git20091109-1.1ubuntu1            minimalistic plugin API for video effects, plugins collection
ii  friendly-recovery                             0.2.25                                  Make recovery more user-friendly
ii  ftp                                           0.17-25                                 classical file transfer client
ii  fuse                                          2.8.6-2ubuntu2                          Filesystem in Userspace
ii  g++                                           4:4.6.3-1ubuntu5                        GNU C++ compiler
ii  g++-4.6                                       4.6.3-1ubuntu5                          GNU C++ compiler
ii  gcalctool                                     6.4.1.1-0ubuntu3                        GNOME desktop calculator
ii  gcc                                           4:4.6.3-1ubuntu5                        GNU C compiler
ii  gcc-4.6                                       4.6.3-1ubuntu5                          GNU C compiler
ii  gcc-4.6-base                                  4.6.3-1ubuntu5                          GCC, the GNU Compiler Collection (base package)
ii  gcj-4.6-base                                  4.6.3-1ubuntu2                          GCC, the GNU Compiler Collection (gcj base package)
ii  gcj-4.6-jre-lib                               4.6.3-1ubuntu2                          Java runtime library for use with gcj (jar files)
ii  gconf-service                                 3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf-service-backend                         3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf2                                        3.2.5-0ubuntu2                          GNOME configuration database system (support tools)
ii  gconf2-common                                 3.2.5-0ubuntu2                          GNOME configuration database system (common files)
ii  gdb                                           7.4-2012.04-0ubuntu2.1                  The GNU Debugger
ii  gedit                                         3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment
ii  gedit-common                                  3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment (support files)
ii  gelemental                                    1.2.0-7ubuntu1                          Periodic Table viewer
ii  genisoimage                                   9:1.1.11-2ubuntu2                       Creates ISO-9660 CD-ROM filesystem images
ii  geoip-database                                20111220-1                              IP lookup command line tools that use the GeoIP library (country database)
ii  gettext                                       0.18.1.1-5ubuntu3                       GNU Internationalization utilities
ii  gettext-base                                  0.18.1.1-5ubuntu3                       GNU Internationalization utilities for the base system
ii  ghostscript                                   9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF
ii  ghostscript-cups                              9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - CUPS filters
ii  ghostscript-x                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - X11 support
ii  gigolo                                        0.4.1-3                                 frontend to manage connections to remote filesystems using GIO/GVfs
ii  gimp                                          2.6.12-1ubuntu1.2                       The GNU Image Manipulation Program
ii  gimp-data                                     2.6.12-1ubuntu1.2                       Data files for GIMP
ii  gimp-help-common                              2.6.1-1                                 Data files for the GIMP documentation
ii  gimp-help-en                                  2.6.1-1                                 Documentation for the GIMP (English)
ii  gir1.2-appindicator3-0.1                      0.4.92-0ubuntu1                         Typelib files for libappindicator3-1.
ii  gir1.2-atk-1.0                                2.4.0-0ubuntu1                          ATK accessibility toolkit (GObject introspection)
ii  gir1.2-atspi-2.0                              2.4.2-0ubuntu0.1                        Assistive Technology Service Provider (GObject introspection)
ii  gir1.2-dbusmenu-glib-0.4                      0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-glib4
ii  gir1.2-dbusmenu-gtk-0.4                       0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-gtk4
ii  gir1.2-dee-1.0                                1.0.10-0ubuntu1                         GObject introspection data for the Dee library
ii  gir1.2-freedesktop                            1.32.0-1                                Introspection data for some FreeDesktop components
ii  gir1.2-gdkpixbuf-2.0                          2.26.1-1                                GDK Pixbuf library - GObject-Introspection
ii  gir1.2-glib-2.0                               1.32.0-1                                Introspection data for GLib, GObject, Gio and GModule
ii  gir1.2-gmenu-3.0                              3.4.0-0ubuntu1                          GObject introspection data for the GNOME menu library
ii  gir1.2-gst-plugins-base-0.10                  0.10.36-1ubuntu0.1                      Description: GObject introspection data for the GStreamer Plugins Base library
ii  gir1.2-gstreamer-0.10                         0.10.36-1ubuntu1                        Description: GObject introspection data for the GStreamer library
ii  gir1.2-gtk-2.0                                2.24.10-0ubuntu6                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                                3.4.2-0ubuntu0.5                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtksource-3.0                          3.4.2-0ubuntu1                          gir files for the GTK+ syntax highlighting widget
ii  gir1.2-gudev-1.0                              175-0ubuntu9.2                          libgudev-1.0 introspection data
ii  gir1.2-javascriptcoregtk-3.0                  1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the GTK+-based JavaScriptCore library
ii  gir1.2-launchpad-integration-3.0              0.1.56.1                                library for launchpad integration (gir files)
ii  gir1.2-notify-0.7                             0.7.5-1                                 sends desktop notifications to a notification daemon (Introspection files)
ii  gir1.2-pango-1.0                              1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text - gir bindings
ii  gir1.2-peas-1.0                               1.2.0-1ubuntu1                          Application plugin library (introspection files)
ii  gir1.2-rb-3.0                                 2.96-0ubuntu4.2                         GObject introspection data for the rhythmbox music player
ii  gir1.2-soup-2.4                               2.38.1-1                                GObject introspection data for the libsoup HTTP library
ii  gir1.2-unity-5.0                              5.12.0-0ubuntu1.1                       GObject introspection data for the Unity library
ii  gir1.2-vte-2.90                               1:0.32.1-0ubuntu1                       GObject introspection data for the VTE library
ii  gir1.2-webkit-3.0                             1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the WebKit library
ii  gir1.2-wnck-3.0                               3.4.0-0ubuntu1                          GObject introspection data for the WNCK library
ii  gksu                                          2.0.2-6ubuntu1                          graphical frontend to su
ii  glib-networking                               2.32.1-1ubuntu2                         network-related giomodules for GLib
ii  glib-networking-common                        2.32.1-1ubuntu2                         network-related giomodules for GLib - data files
ii  glib-networking-services                      2.32.1-1ubuntu2                         network-related giomodules for GLib - D-Bus services
rc  gmusicbrowser                                 1.1.9-1                                 graphic jukebox for large collections of mp3/ogg/flac/mpc files
ii  gnome-accessibility-themes                    3.4.1-0ubuntu1.2                        accessibility themes for the GNOME desktop
ii  gnome-desktop-data                            1:2.32.1-0ubuntu9                       Common files for GNOME desktop apps
ii  gnome-desktop3-data                           3.4.2-0ubuntu0.1                        Common files for GNOME desktop apps
ii  gnome-games-data                              1:3.4.1-0ubuntu2.1                      data files for the GNOME games
ii  gnome-icon-theme                              3.4.0-0ubuntu1.1                        GNOME Desktop icon theme (small subset)
ii  gnome-keyring                                 3.2.2-2ubuntu4                          GNOME keyring services (daemon and tools)
ii  gnome-system-tools                            3.0.0-2ubuntu1                          Cross-platform configuration utilities for GNOME
ii  gnome-time-admin                              3.0.0-2ubuntu1                          GNOME Time Administration Tool
ii  gnome-user-guide                              3.4.1-1                                 GNOME user's guide
ii  gnome-video-effects                           0.4.0-1                                 GNOME Video Effects
rc  gnomine                                       1:3.4.1-0ubuntu2.1                      popular minesweeper puzzle game for GNOME
rc  gnumeric                                      1.10.17-1ubuntu2                        spreadsheet application for GNOME - main program
ii  gnupg                                         1.4.11-3ubuntu2.1                       GNU privacy guard - a free PGP replacement
rc  gnustep-base-common                           1.22.1-2ubuntu2                         GNUstep Base library - common files
rc  gnustep-base-runtime                          1.22.1-2ubuntu2                         GNUstep Base library - daemons and tools
rc  gnustep-common                                2.6.1-1                                 Common files for the core GNUstep environment
ii  google-chrome-stable                          23.0.1271.97-r171054                    The web browser from Google
rc  google-earth-stable                           7.0.1.8244-r0                           Explore, search and discover the planet
ii  gpgv                                          1.4.11-3ubuntu2.1                       GNU privacy guard - signature verification tool
ii  gpsd                                          3.4-2                                   Global Positioning System - daemon
ii  grep                                          2.10-1                                  GNU grep, egrep and fgrep
ii  groff-base                                    1.21-7                                  GNU troff text-formatting system (base system components)
ii  growisofs                                     7.1-10                                  DVD+-RW/R recorder
ii  grub-common                                   1.99-21ubuntu3.4                        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                         0.6                                     GRUB gfxpayload blacklist
ii  grub-pc                                       1.99-21ubuntu3.4                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                   1.99-21ubuntu3.4                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                  1.99-21ubuntu3.4                        GRand Unified Bootloader (common files for version 2)
ii  gs-cjk-resource                               1.20100103-3                            Resource files for gs-cjk, ghostscript CJK-TrueType extension
ii  gsettings-desktop-schemas                     3.4.1-0ubuntu1                          GSettings deskop-wide schemas
ii  gsfonts                                       1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1     Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                                   0.22                                    Make Ghostscript fonts available to X11
ii  gstreamer0.10-alsa                            0.10.36-1ubuntu0.1                      GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                          0.10.13-1                               FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                     0.10.15.debian-1ubuntu1                 Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnomevfs                        0.10.36-1ubuntu0.1                      GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                         0.10.17-2                               non-linear editing module for GStreamer
ii  gstreamer0.10-nice                            0.1.1-2ubuntu1                          ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad                     0.10.22.3-2ubuntu2.1                    GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse          0.10.21-1                               GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base                    0.10.36-1ubuntu0.1                      GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps               0.10.36-1ubuntu0.1                      GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good                    0.10.31-1ubuntu1                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                    0.10.18.3-1ubuntu1                      GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio                      0.10.31-1ubuntu1                        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                           0.10.36-1ubuntu1                        Tools for use with GStreamer
ii  gstreamer0.10-x                               0.10.36-1ubuntu0.1                      GStreamer plugins for X11 and Pango
ii  gthumb                                        3:2.14.3-0ubuntu1                       image viewer and browser
ii  gthumb-data                                   3:2.14.3-0ubuntu1                       image viewer and browser - arch-independent files
ii  gtk2-engines                                  1:2.20.2-1ubuntu1                       theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                          0.98.2-0ubuntu1                         cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                           2.24.10-0ubuntu6                        pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-unico                            1.0.2-0ubuntu1                          Unico Gtk+ 3 theme engine
ii  gucharmap                                     1:3.4.1.1-0ubuntu1                      Unicode character picker and font browser
ii  guile-1.6-libs                                1.6.8-10ubuntu4                         Main Guile libraries
ii  guile-1.8-libs                                1.8.8+1-6ubuntu2                        Core Guile libraries
ii  gvfs                                          1.12.1-0ubuntu1.1                       userspace virtual filesystem - GIO module
ii  gvfs-backends                                 1.12.1-0ubuntu1.1                       userspace virtual filesystem - backends
ii  gvfs-bin                                      1.12.1-0ubuntu1.1                       userspace virtual filesystem - binaries
ii  gvfs-common                                   1.12.1-0ubuntu1.1                       userspace virtual filesystem - common data files
ii  gvfs-daemons                                  1.12.1-0ubuntu1.1                       userspace virtual filesystem - servers
ii  gvfs-fuse                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - fuse server
ii  gvfs-libs                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - private libraries
ii  gzip                                          1.4-1ubuntu2                            GNU compression utilities
ii  hdparm                                        9.37-0ubuntu3.1                         tune hard disk parameters for high performance
ii  heirloom-mailx                                12.5-1build1                            feature-rich BSD mail(1)
ii  hicolor-icon-theme                            0.12-1ubuntu2                           default fallback theme for FreeDesktop.org icon themes
ii  hiera                                         1.1.1-1puppetlabs1                      A simple pluggable Hierarchical Database.
ii  hostname                                      3.06ubuntu1                             utility to set/show the host name or domain name
ii  hplip                                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                    3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - data files
ii  humanity-icon-theme                           0.5.3.11                                Humanity Icon theme
ii  hunspell-en-us                                20070829-4ubuntu3                       English_american dictionary for hunspell
ii  hwdata                                        0.233-1ubuntu1                          hardware identification / configuration data
ii  ibus                                          1.4.1-3ubuntu1                          Intelligent Input Bus - core
ii  ibus-gtk                                      1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3                                     1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+3 support
ii  ibus-pinyin                                   1.4.0-1                                 Pinyin engine for IBus
ii  ibus-pinyin-db-android                        1.4.0-1                                 Pinyin engine for IBus - Android database
ii  ibus-table                                    1.3.9.20110827-1ubuntu1                 table engine for IBus
ii  icc-profiles-free                             2.0.1+dfsg-1                            ICC color profiles for use with color profile aware software
ii  icedtea-6-jre-cacao                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre-jamvm                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using JamVM
ii  icedtea-netx                                  1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                           1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icoutils                                      0.29.1-2                                Create and extract MS Windows icons and cursors
ii  ifupdown                                      0.7~beta2ubuntu8                        high level tools to configure network interfaces
ii  im-switch                                     1.20ubuntu5.1                           Input method switch framework
ii  imagemagick                                   8:6.6.9.7-5ubuntu3.2                    image manipulation programs
ii  imagemagick-common                            8:6.6.9.7-5ubuntu3.2                    image manipulation programs -- infrastructure
ii  indicator-application                         0.5.0-0ubuntu1                          Application Indicators
ii  indicator-application-gtk2                    0.5.0-0ubuntu1                          Application Indicators
ii  indicator-sound                               0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  indicator-sound-gtk2                          0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  info                                          4.13a.dfsg.1-8ubuntu2                   Standalone GNU Info documentation browser
ii  initramfs-tools                               0.99ubuntu13                            tools for generating an initramfs
ii  initramfs-tools-bin                           0.99ubuntu13                            binaries used by initramfs-tools
ii  initscripts                                   2.88dsf-13.10ubuntu11.1                 scripts for initializing and shutting down the system
ii  inkscape                                      0.48.3.1-1ubuntu1                       vector-based drawing program
ii  inputattach                                   1:1.4.2-1                               utility to connect serial-attached peripherals to the input subsystem
ii  insserv                                       1.14.0-2.1ubuntu2                       Tool to organize boot sequence using LSB init.d script dependencies
ii  install-info                                  4.13a.dfsg.1-8ubuntu2                   Manage installed documentation in info format
ii  iproute                                       20111117-1ubuntu2                       networking and traffic control tools
ii  iptables                                      1.4.12-1ubuntu4                         administration tools for packet filtering and NAT
ii  iputils-arping                                3:20101006-1ubuntu1                     Tool to send ICMP echo requests to an ARP address
ii  iputils-ping                                  3:20101006-1ubuntu1                     Tools to test the reachability of network hosts
ii  iputils-tracepath                             3:20101006-1ubuntu1                     Tools to trace the network path to a remote host
ii  irqbalance                                    0.56-1ubuntu4                           Daemon to balance interrupts for SMP systems
ii  isc-dhcp-client                               4.1.ESV-R4-0ubuntu5.5                   ISC DHCP client
ii  isc-dhcp-common                               4.1.ESV-R4-0ubuntu5.5                   common files used by all the isc-dhcp* packages
ii  iso-codes                                     3.31-1                                  ISO language, territory, currency, script codes and their translations
ii  iw                                            3.2-1                                   tool for configuring Linux wireless devices
ii  java-common                                   0.43ubuntu2                             Base of all Java packages
ii  java-wrappers                                 0.1.24                                  wrappers for java executables
ii  jockey-common                                 0.9.7-0ubuntu7.4                        user interface and desktop integration for driver management
ii  jockey-gtk                                    0.9.7-0ubuntu7.4                        GNOME user interface and desktop integration for driver management
ii  kalgebra                                      4:4.8.4-0ubuntu0.1                      algebraic graphing calculator for KDE
ii  kalgebra-common                               4:4.8.4-0ubuntu0.1                      contains files common for kalgebra and kalgebramobile
ii  kalzium                                       4:4.8.5-0ubuntu0.1                      periodic table and chemistry tools for KDE
ii  kalzium-data                                  4:4.8.5-0ubuntu0.1                      data files for Kalzium
ii  kate-data                                     4:4.8.5-0ubuntu0.1                      shared data files for kate
ii  katepart                                      4:4.8.5-0ubuntu0.1                      kate KPart
ii  kbd                                           1.15.2-3ubuntu4                         Linux console font and keytable utilities
ii  kbruch                                        4:4.8.2-0ubuntu1                        fraction learning aid for KDE
ii  kde-runtime                                   4:4.8.5-0ubuntu0.1                      runtime components from the official KDE release
ii  kde-runtime-data                              4:4.8.5-0ubuntu0.1                      shared data files for the KDE base runtime module
ii  kdeedu-kvtml-data                             4:4.8.5-0ubuntu0.1                      kvtml files for kdeedu programs
ii  kdelibs-bin                                   4:4.8.5-0ubuntu0.1                      core executables for KDE Applications
ii  kdelibs5-data                                 4:4.8.5-0ubuntu0.1                      core shared data for all KDE Applications
ii  kdelibs5-plugins                              4:4.8.5-0ubuntu0.1                      core plugins for KDE Applications
rc  kdepim-runtime                                4:4.8.5-0ubuntu0.1                      Runtime components for akonadi-kde
ii  kdoctools                                     4:4.8.5-0ubuntu0.1                      various tools for accessing application documentation
ii  kerneloops-daemon                             0.12+git20090217-1ubuntu19              kernel oops tracker
ii  keyboard-configuration                        1.70ubuntu5                             system-wide keyboard preferences
ii  kig                                           4:4.8.4-0ubuntu0.1                      interactive geometry tool for KDE
ii  kino                                          1.3.4-1.3                               Non-linear editor for Digital Video data
ii  klibc-utils                                   1.5.25-1ubuntu2                         small utilities built with klibc for early boot
ii  kmplot                                        4:4.8.2-0ubuntu1                        mathematical function plotter for KDE
ii  kolourpaint4                                  4:4.8.4-0ubuntu0.1                      simple image editor and drawing application
ii  krb5-locales                                  1.10+dfsg~beta1-2ubuntu0.3              Internationalization support for MIT Kerberos
ii  krosspython                                   4:4.8.2-0ubuntu1                        Python module for Kross
ii  kstars                                        4:4.8.5-0ubuntu0.1                      desktop planetarium for KDE
ii  kstars-data                                   4:4.8.5-0ubuntu0.1                      data files for KStars desktop planetarium
ii  ktouch                                        4:4.8.2-0ubuntu1                        touch typing tutor for KDE
ii  ktouch-data                                   4:4.8.2-0ubuntu1                        data files for ktouch
ii  kturtle                                       4:4.8.2-0ubuntu1                        Logo educational programming environment for KDE
ii  kubuntu-debug-installer                       11.10ubuntu1                            Debug package installer for Kubuntu
ii  kwordquiz                                     4:4.8.3-0ubuntu0.1                      flashcard learning program for KDE
ii  language-pack-en                              1:12.04+20120801                        translation updates for language English
ii  language-pack-en-base                         1:12.04+20120801                        translations for language English
ii  language-pack-gnome-en                        1:12.04+20120801                        GNOME translation updates for language English
ii  language-pack-gnome-en-base                   1:12.04+20120801                        GNOME translations for language English
ii  language-selector-common                      0.79                                    Language selector for Ubuntu
ii  language-selector-gnome                       0.79                                    Language selector for Ubuntu
ii  laptop-detect                                 0.13.7ubuntu2                           attempt to detect a laptop
ii  launchpad-integration                         0.1.56.1                                launchpad integration
rc  leafpad                                       0.8.18.1-2                              GTK+ based simple text editor
ii  less                                          444-1ubuntu1                            pager program similar to more
ii  liba52-0.7.4                                  0.7.4-16build1                          library for decoding ATSC A/52 streams
ii  libaa1                                        1.4p5-39ubuntu1                         ASCII art library
ii  libaacs0                                      0.3.0-4                                 free-and-libre implementation of AACS
ii  libabiword-2.9                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- shared library
ii  libaccountsservice0                           0.6.15-2ubuntu9.4                       query and manipulate user account information - shared libraries
ii  libacl1                                       2.2.51-5ubuntu1                         Access control list shared library
rc  libakonadi-calendar4                          4:4.8.5-0ubuntu0.1                      library providing calendar helpers for Akonadi items
rc  libakonadi-contact4                           4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kabc4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kcal4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kde4                               4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kmime4                             4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-notes4                             4:4.8.5-0ubuntu0.1                      library providing notes helpers for Akonadi items
rc  libakonadiprotocolinternals1                  1.7.2-0ubuntu1                          libraries for the Akonadi PIM storage service
ii  libalgorithm-diff-perl                        1.19.02-2                               module to find differences between files
ii  libalgorithm-diff-xs-perl                     0.04-2build2                            module to find differences between files (XS accelerated)
ii  libalgorithm-merge-perl                       0.08-2                                  Perl module for three-way merge of textual data
ii  libanalitza4abi1                              4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions
ii  libanalitzagui4abi1                           4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions - GUI routines
ii  libao-common                                  1.1.0-1ubuntu2                          Cross Platform Audio Output Library (Common files)
ii  libao4                                        1.1.0-1ubuntu2                          Cross Platform Audio Output Library
ii  libappindicator1                              0.4.92-0ubuntu1                         Application Indicators
ii  libappindicator3-1                            0.4.92-0ubuntu1                         Application Indicators
ii  libapt-inst1.4                                0.8.16~exp12ubuntu10.7                  deb package format runtime library
ii  libapt-pkg4.12                                0.8.16~exp12ubuntu10.7                  package managment runtime library
ii  libarchive12                                  3.0.3-6ubuntu1                          Multi-format archive and compression library (shared library)
ii  libart-2.0-2                                  2.3.21-1ubuntu0.1                       Library of functions for 2D graphics - runtime files
ii  libart2.0-cil                                 2.24.2-1                                CLI binding for libart 2.3
ii  libasn1-8-heimdal                             1.6~git20120311.dfsg.1-2                Heimdal Kerberos - ASN.1 library
ii  libasound2                                    1.0.25-1ubuntu10.1                      shared library for ALSA applications
ii  libasound2-plugins                            1.0.25-1ubuntu1                         ALSA library additional plugins
ii  libaspell15                                   0.60.7~20110707-1                       GNU Aspell spell-checker runtime library
ii  libass4                                       0.10.0-3                                library for SSA/*** subtitles rendering
ii  libasyncns0                                   0.8-4                                   Asynchronous name service query library
ii  libatasmart4                                  0.18-3                                  ATA S.M.A.R.T. reading and parsing library
ii  libatk-wrapper-java                           0.30.4-0ubuntu2                         An ATK implementation for Java using JNI
ii  libatk-wrapper-java-jni                       0.30.4-0ubuntu2                         An ATK implementation for Java using JNI (jni bindings)
ii  libatk1.0-0                                   2.4.0-0ubuntu1                          ATK accessibility toolkit
ii  libatk1.0-data                                2.4.0-0ubuntu1                          Common files for the ATK accessibility toolkit
ii  libatkmm-1.6-1                                2.22.6-1ubuntu1                         C++ wrappers for ATK accessibility toolkit (shared libraries)
ii  libatspi2.0-0                                 2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface - shared library
ii  libattica0.3                                  0.3.0-0ubuntu2                          a Qt library that implements the Open Collaboration Services API
ii  libattr1                                      1:2.4.46-5ubuntu1                       Extended attribute shared library
ii  libaudclient2                                 3.2.1-2                                 audacious dbus remote control library
ii  libaudio-scrobbler-perl                       0.01-2.1                                perl interface to audioscrobbler.com/last.fm
ii  libaudio2                                     1.9.3-4                                 Network Audio System - shared libraries
ii  libaudiofile1                                 0.3.3-2                                 Open-source version of SGI's audiofile library
ii  libaugeas-ruby1.8                             0.3.0-1.1ubuntu4                        Augeas bindings for the Ruby language
ii  libaugeas0                                    0.10.0-0ubuntu4                         Augeas configuration editing library and API
ii  libav-tools                                   4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder
ii  libavahi-client3                              0.6.30-5ubuntu2                         Avahi client library
ii  libavahi-common-data                          0.6.30-5ubuntu2                         Avahi common data files
ii  libavahi-common3                              0.6.30-5ubuntu2                         Avahi common library
ii  libavahi-core7                                0.6.30-5ubuntu2                         Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                                0.6.30-5ubuntu2                         Avahi glib integration library
ii  libavc1394-0                                  0.5.3-1ubuntu2                          control IEEE 1394 audio/video devices
ii  libavcodec-extra-53                           4:0.8.4ubuntu0.12.04.1                  Libav codec library
rc  libavcodec53                                  4:0.8.4-0ubuntu0.12.04.1                Libav codec library
ii  libavdevice53                                 4:0.8.4-0ubuntu0.12.04.1                Libav device handling library
ii  libavfilter2                                  4:0.8.4-0ubuntu0.12.04.1                Libav video filtering library
ii  libavformat-extra-53                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libavformat53                                 4:0.8.4-0ubuntu0.12.04.1                Libav file format library
ii  libavogadro1                                  1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (library)
ii  libavutil-extra-51                            4:0.8.4ubuntu0.12.04.1                  Libav utility library
rc  libavutil51                                   4:0.8.4-0ubuntu0.12.04.1                Libav utility library
ii  libbabl-0.0-0                                 0.0.22-1.1                              Dynamic, any to any, pixel format conversion library
ii  libbind9-80                                   1:9.8.1.dfsg.P1-4ubuntu0.5              BIND9 Shared Library used by BIND
ii  libbison-dev                                  1:2.5.dfsg-2.1                          YACC-compatible parser generator - development library
ii  libblas3gf                                    1.2.20110419-2ubuntu1                   Basic Linear Algebra Reference implementations, shared library
ii  libblkid1                                     2.20.1-1ubuntu3                         block device id library
ii  libbluetooth3                                 4.98-2ubuntu7                           Library to use the BlueZ Linux Bluetooth stack
ii  libbluray1                                    1:0.2.1+git20111208.63e308d-3           Blu-ray disc playback support library (shared library)
ii  libbonobo2-0                                  2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library
ii  libbonobo2-common                             2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library -- support files
ii  libbonoboui2-0                                2.24.5-0ubuntu1.1                       The Bonobo UI library
ii  libbonoboui2-common                           2.24.5-0ubuntu1.1                       The Bonobo UI library -- common files
rc  libboost-program-options1.46.1                1.46.1-7ubuntu3                         program options library for C++
ii  libboost-python1.46.1                         1.46.1-7ubuntu3                         Boost.Python Library
ii  libbrasero-media3-1                           3.4.1-0ubuntu1.1                        CD/DVD burning library for GNOME - runtime
ii  libbrlapi0.5                                  4.3-1ubuntu5                            braille display access via BRLTTY - shared library
ii  libbsd0                                       0.3.0-2                                 utility functions from BSD systems - shared library
ii  libburn4                                      1.1.8-1                                 library to provide CD/DVD writing functions
ii  libbz2-1.0                                    1.0.6-1                                 high-quality block-sorting file compressor library - runtime
ii  libc-bin                                      2.15-0ubuntu10.3                        Embedded GNU C Library: Binaries
ii  libc-dev-bin                                  2.15-0ubuntu10.3                        Embedded GNU C Library: Development binaries
ii  libc6                                         2.15-0ubuntu10.3                        Embedded GNU C Library: Shared libraries
ii  libc6-dev                                     2.15-0ubuntu10.3                        Embedded GNU C Library: Development Libraries and Header Files
ii  libcaca0                                      0.99.beta17-2.1ubuntu2                  colour ASCII art library
ii  libcairo-gobject2                             1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library (GObject library)
ii  libcairo-perl                                 1.081-1build2                           Perl interface to the Cairo graphics library
ii  libcairo2                                     1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library
ii  libcairomm-1.0-1                              1.10.0-1ubuntu1                         C++ wrappers for Cairo (shared libraries)
ii  libcanberra-gtk3-0                            0.28-3ubuntu3                           GTK+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module                       0.28-3ubuntu3                           translates GTK3 widgets signals to event sounds
ii  libcanberra-pulse                             0.28-3ubuntu3                           PulseAudio backend for libcanberra
ii  libcanberra0                                  0.28-3ubuntu3                           simple abstract interface for playing event sounds
ii  libcap-ng0                                    0.6.6-1ubuntu1                          An alternate POSIX capabilities library
ii  libcap2                                       1:2.22-1ubuntu3                         support for getting/setting POSIX.1e capabilities
ii  libcap2-bin                                   1:2.22-1ubuntu3                         basic utility programs for using capabilities
ii  libcapi20-3                                   1:3.12.20071127-0ubuntu11               libraries for CAPI support
ii  libcdaudio1                                   0.99.12p2-10build1                      library for controlling a CD-ROM when playing audio CDs
ii  libcddb2                                      1.3.2-3fakesync1                        library to access CDDB data - runtime files
ii  libcdio-cdda1                                 0.83-1                                  library to read and control digital audio CDs
ii  libcdio-paranoia1                             0.83-1                                  library to read digital audio CDs with error correction
ii  libcdio13                                     0.83-1                                  library to read and control CD-ROM
ii  libcdparanoia0                                3.10.2+debian-10ubuntu1                 audio extraction tool for sampling CDs (library)
ii  libcdt4                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - cdt library
ii  libcelt0-0                                    0.7.1-1                                 The CELT codec runtime library
ii  libcfitsio3                                   3.290-1ubuntu1                          shared library for I/O with FITS format data files
ii  libcheese-gtk21                               3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - widgets
ii  libcheese3                                    3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - base library
ii  libck-connector0                              0.4.5-2                                 ConsoleKit libraries
ii  libclamav6                                    0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - library
ii  libclass-isa-perl                             0.36-3                                  report the search path for a class's ISA tree
ii  libcln6                                       1.3.2-1.1                               Class Library for Numbers (C++)
ii  libclucene0ldbl                               0.9.21b-2                               library for full-featured text search engine (runtime)
ii  libclutter-1.0-0                              1.10.6-1~precise1                       Open GL based interactive canvas library
ii  libclutter-1.0-common                         1.10.6-1~precise1                       Open GL based interactive canvas library (common files)
ii  libclutter-gst-1.0-0                          1.5.4-0ubuntu2                          Open GL based interactive canvas library GStreamer elements
ii  libclutter-gtk-1.0-0                          1.2.0-0ubuntu1                          Open GL based interactive canvas library GTK+ widget
ii  libclutter-imcontext-0.1-0                    0.1.4-2build1                           Open GL based interactive canvas library IMContext framework
ii  libcluttergesture-0.0.2-0                     0.0.2.1-2ubuntu3                        Open GL based interactive canvas library Gesture framework
ii  libcmis-0.2-0                                 0.1.0-1                                 CMIS protocol client library
ii  libcogl-common                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer (common files)
ii  libcogl-pango0                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcogl9                                      1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcolamd2.7.1                                1:3.4.0-2ubuntu3                        column approximate minimum degree ordering library for sparse matrices
ii  libcolord1                                    0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- runtime
ii  libcomerr2                                    1.42-1ubuntu2                           common error description library
ii  libconfig-inifiles-perl                       2.68-1ubuntu0.12.04.1                   Read .ini-style configuration files
ii  libcroco3                                     0.6.5-1                                 Cascading Style Sheet (CSS) parsing and manipulation toolkit
ii  libcrypt-passwdmd5-perl                       1.3-10                                  interoperable MD5-based crypt() for perl
ii  libcryptsetup4                                2:1.4.1-2ubuntu4                        disk encryption support - shared library
ii  libcrystalhd3                                 1:0.0~git20110715.fdd2f19-4.1           Crystal HD Video Decoder (shared library)
ii  libcups2                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Core library
ii  libcupscgi1                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - CGI library
ii  libcupsdriver1                                1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Driver library
ii  libcupsfilters1                               1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2                                 1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation library
ii  libcurl3                                      7.22.0-3ubuntu4                         Multi-protocol file transfer library (OpenSSL)
ii  libcurl3-gnutls                               7.22.0-3ubuntu4                         Multi-protocol file transfer library (GnuTLS)
ii  libdaemon0                                    0.14-2                                  lightweight C library for daemons - runtime library
ii  libdatrie1                                    0.2.5-3                                 Double-array trie library
ii  libdb5.1                                      5.1.25-11build1                         Berkeley v5.1 Database Libraries [runtime]
ii  libdbus-1-3                                   1.4.18-1ubuntu1.3                       simple interprocess messaging system (library)
ii  libdbus-glib-1-2                              0.98-1ubuntu1                           simple interprocess messaging system (GLib-based shared library)
ii  libdbus-glib1.0-cil                           0.5.0-3build1                           CLI implementation of D-Bus (GLib mainloop integration)
ii  libdbus1.0-cil                                0.7.0-4                                 CLI implementation of D-Bus
ii  libdbusmenu-glib4                             0.6.2-0ubuntu0.1                        library for passing menus over DBus
ii  libdbusmenu-gtk3-4                            0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk4                              0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-qt2                               0.9.2-0ubuntu1                          Qt implementation of the DBusMenu protocol
ii  libdc1394-22                                  2.2.0-2                                 high level programming interface for IEEE1394 digital camera
ii  libdca0                                       0.0.5-5                                 decoding library for DTS Coherent Acoustics streams
ii  libdconf0                                     0.12.0-0ubuntu1.1                       simple configuration storage system - runtime library
ii  libdee-1.0-4                                  1.0.10-0ubuntu1                         model to synchronize mutiple instances over DBus - shared lib
ii  libdevmapper-event1.02.1                      2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdevmapper1.02.1                            2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdigest-crc-perl                            0.18-1                                  Perl module providing generic CRC functions
ii  libdirac-encoder0                             1.0.2-4build1                           open and royalty free high quality codec - encoder library
ii  libdirectfb-1.2-9                             1.2.10.0-4.3ubuntu1                     direct frame buffer graphics - shared libraries
ii  libdiscid0                                    0.2.2-3                                 Library for creating MusicBrainz DiscIDs
ii  libdjvulibre-text                             3.5.24-9                                Linguistic support files for libdjvulibre
ii  libdjvulibre21                                3.5.24-9                                Runtime support for the DjVu image format
ii  libdlrestrictions1                            0.14.2ubuntu5                           library that implements library compatibility checks for dlopen()
ii  libdmapsharing-3.0-2                          2.9.14-1                                DMAP client and server library - runtime
rc  libdmtx0a                                     0.7.2-1build2                           Data Matrix barcodes (runtime library)
ii  libdns81                                      1:9.8.1.dfsg.P1-4ubuntu0.5              DNS Shared Library used by BIND
ii  libdotconf1.0                                 1.0.13-3                                Configuration file parser library - runtime files
ii  libdpkg-perl                                  1.16.1.2ubuntu7                         Dpkg perl modules
ii  libdrm-intel1                                 2.4.32-1ubuntu1                         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                              2.4.32-1ubuntu1                         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                                2.4.32-1ubuntu1                         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                       2.4.32-1ubuntu1                         Userspace interface to kernel DRM services -- runtime
ii  libdv4                                        1.0.0-3ubuntu1                          software library for DV format digital video (runtime lib)
ii  libdvbpsi7                                    0.2.2-1                                 library for MPEG TS and DVB PSI tables decoding and generating
ii  libdvdcss2                                    1.2.12-0.0medibuntu1                    Simple foundation for reading DVDs - runtime libraries
ii  libdvdnav4                                    4.2.0-1                                 DVD navigation library
ii  libdvdread4                                   4.2.0-1ubuntu3                          library for reading DVDs
ii  libebml3                                      1.2.2-2                                 access library for the EBML format (shared library)
ii  libedit2                                      2.11-20080614-3ubuntu2                  BSD editline and history libraries
ii  libelemental0                                 1.2.0-7ubuntu1                          Periodic Table viewer (data and shared library)
ii  libelf1                                       0.152-1ubuntu3                          library to read and write ELF files
ii  libenca0                                      1.13-4                                  Extremely Naive Charset Analyser - shared library files
ii  libenchant1c2a                                1.6.0-7                                 Wrapper library for various spell checker engines (runtime libs)
ii  libencode-locale-perl                         1.02-2                                  utility to determine the locale encoding
ii  libept1.4.12                                  1.0.6~exp1ubuntu1                       High-level library for managing Debian package information
ii  libesd0                                       0.2.41-10build3                         Enlightened Sound Daemon - Shared libraries
ii  libespeak1                                    1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: shared library
ii  libevent-2.0-5                                2.0.16-stable-1                         Asynchronous event notification library
ii  libevince3-3                                  3.4.0-0ubuntu1.4                        Document (PostScript, PDF) rendering library
ii  libexempi3                                    2.2.0-1                                 library to parse XMP metadata (Library)
ii  libexif12                                     0.6.20-2ubuntu0.1                       library to parse EXIF files
ii  libexiv2-11                                   0.22-2                                  EXIF/IPTC metadata manipulation library
ii  libexo-1-0                                    0.6.2-4                                 Library with extensions for Xfce
ii  libexo-common                                 0.6.2-4                                 libexo common files
ii  libexo-helpers                                0.6.2-4                                 libexo helpers
ii  libexpat1                                     2.0.1-7.2ubuntu1.1                      XML parsing C library - runtime library
ii  libexttextcat-data                            3.2.0-1ubuntu1                          Language detection library - data files
ii  libexttextcat0                                3.2.0-1ubuntu1                          Language detection library
ii  libfaac0                                      1.28-0ubuntu2                           AAC audio encoder (library)
ii  libfaad2                                      2.7-7                                   freeware Advanced Audio Decoder - runtime files
ii  libfarstream-0.1-0                            0.1.2-0ubuntu1                          Audio/Video communications framework: core library
ii  libffi6                                       3.0.11~rc1-5                            Foreign Function Interface library runtime
ii  libfftw3-3                                    3.3-1ubuntu1                            library for computing Fast Fourier Transforms
ii  libfile-basedir-perl                          0.03-1fakesync1                         Perl module to use the freedesktop basedir specification
ii  libfile-copy-recursive-perl                   0.38-1                                  Perl extension for recursively copying files and directories
ii  libfile-desktopentry-perl                     0.04-3                                  Perl module to handle freedesktop .desktop files
ii  libfile-listing-perl                          6.03-1                                  module to parse directory listings
ii  libfile-mimeinfo-perl                         0.15-2                                  Perl module to determine file types
ii  libfl-dev                                     2.5.35-10ubuntu3                        static library for flex (a fast lexical analyzer generator).
ii  libflac++6                                    1.2.1-6                                 Free Lossless Audio Codec - C++ runtime library
ii  libflac8                                      1.2.1-6                                 Free Lossless Audio Codec - runtime C library
ii  libflickrnet2.2-cil                           1:2.2.0-3build1                         Flickr.Net API Library
ii  libflite1                                     1.4-release-4                           Small run-time speech synthesis engine - shared libraries
ii  libfont-afm-perl                              1.20-1                                  Font::AFM - Interface to Adobe Font Metrics files
ii  libfontconfig1                                2.8.0-3ubuntu9.1                        generic font configuration library - runtime
ii  libfontenc1                                   1:1.1.0-1                               X11 font encoding library
ii  libframe6                                     2.2.4-0ubuntu0.12.04.1                  Touch Frame Library
ii  libfreetype6                                  2.4.8-1ubuntu2                          FreeType 2 font engine, shared library files
ii  libfribidi0                                   0.19.2-1                                Free Implementation of the Unicode BiDi algorithm
ii  libfs6                                        2:1.0.3-1                               X11 Font Services library
ii  libfuse2                                      2.8.6-2ubuntu2                          Filesystem in Userspace (library)
ii  libgail-3-0                                   3.4.2-0ubuntu0.5                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgail18                                     2.24.10-0ubuntu6                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgarcon-1-0                                 0.1.11-0ubuntu1                         freedesktop.org compliant menu implementation for Xfce
ii  libgarcon-common                              0.1.11-0ubuntu1                         common files for libgarcon menu implementation
ii  libgavl1                                      1.2.0-4                                 low level audio and video library - runtime files
ii  libgc1c2                                      1:7.1-8ubuntu0.12.04.1                  conservative garbage collector for C and C++
ii  libgcc1                                       1:4.6.3-1ubuntu5                        GCC support library
ii  libgcj-bc                                     4.6.3-1ubuntu5                          Link time only library for use with gcj
ii  libgcj-common                                 1:4.6.3-1ubuntu5                        Java runtime library (common files)
ii  libgcj12                                      4.6.3-1ubuntu2                          Java runtime library for use with gcj
ii  libgck-1-0                                    3.2.2-2ubuntu4                          Glib wrapper library for PKCS#11 - runtime
ii  libgconf-2-4                                  3.2.5-0ubuntu2                          GNOME configuration database system (shared libraries)
ii  libgconf2-4                                   3.2.5-0ubuntu2                          GNOME configuration database system (dummy package)
ii  libgconf2.0-cil                               2.24.2-1                                CLI binding for GConf 2.24
ii  libgcr-3-1                                    3.2.2-2ubuntu4                          Library for Crypto UI related task - runtime
ii  libgcr-3-common                               3.2.2-2ubuntu4                          Library for Crypto UI related task - common files
ii  libgcrypt11                                   1.5.0-3ubuntu0.1                        LGPL Crypto library - runtime library
ii  libgd2-xpm                                    2.0.36~rc1~dfsg-6ubuntu2                GD Graphics Library version 2
ii  libgdata1.9-cil                               1.9.0.0-1                               Google GData CLI client library
ii  libgdbm3                                      1.8.3-10                                GNU dbm database routines (runtime version)
ii  libgdiplus                                    2.10-3                                  interface library for System.Drawing of Mono
ii  libgdk-pixbuf2.0-0                            2.26.1-1                                GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                       2.26.1-1                                GDK Pixbuf library - data files
ii  libgdome2-0                                   0.8.1+debian-4.1build1                  DOM level2 library for accessing XML files
ii  libgdome2-cpp-smart0c2a                       0.2.6-6build2                           C++ bindings for GDome2 DOM implementation
ii  libgdu0                                       3.0.2-2ubuntu7                          GObject based Disk Utility Library
ii  libgee2                                       0.6.4-1                                 GObject based collection library
ii  libgegl-0.0-0                                 0.0.22-2ubuntu3                         Generic Graphics Library
ii  libgeis1                                      2.2.9.2-0ubuntu1                        Gesture engine interface support
ii  libgeoclue0                                   0.12.0-1ubuntu12                        C API for GeoClue
ii  libgeoip1                                     1.4.8+dfsg-2                            non-DNS IP-to-country resolver library
ii  libgettextpo0                                 0.18.1.1-5ubuntu3                       GNU Internationalization library
ii  libgfortran3                                  4.6.3-1ubuntu5                          Runtime library for GNU Fortran applications
ii  libgif4                                       4.1.6-9ubuntu1                          library for GIF images (library)
ii  libgimp2.0                                    2.6.12-1ubuntu1.2                       Libraries for the GNU Image Manipulation Program
ii  libgirepository-1.0-1                         1.32.0-1                                Library for handling GObject introspection data (runtime library)
ii  libgkeyfile1.0-cil                            0.1-2ubuntu2                            GObject-based wrapper library for GKeyFile -- CLI bindings
ii  libgksu2-0                                    2.0.13~pre1-5ubuntu2                    library providing su and sudo functionality
ii  libgl1-mesa-dri                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- GLX runtime
ii  libglade2-0                                   1:2.6.4-1ubuntu1.1                      library to load .glade files at runtime
ii  libglade2.0-cil                               2.12.10-2ubuntu4                        CLI binding for the Glade libraries 2.6
ii  libglapi-mesa                                 8.0.4-0ubuntu0.2                        free implementation of the GL API -- shared library
ii  libglew1.5                                    1.5.7.is.1.5.2-1ubuntu4                 The OpenGL Extension Wrangler - runtime environment
ii  libglew1.6                                    1.6.0-4                                 OpenGL Extension Wrangler - runtime environment
ii  libglib-perl                                  2:1.241-1                               interface to the GLib and GObject libraries
ii  libglib2.0-0                                  2.32.3-0ubuntu1                         GLib library of C routines
ii  libglib2.0-bin                                2.32.3-0ubuntu1                         Programs for the GLib library
ii  libglib2.0-cil                                2.12.10-2ubuntu4                        CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                               2.32.3-0ubuntu1                         Common files for GLib library
ii  libglibmm-2.4-1c2a                            2.32.0-0ubuntu1                         C++ wrapper for the GLib toolkit (shared libraries)
ii  libglu1-mesa                                  8.0.4-0ubuntu0.2                        Mesa OpenGL utility library (GLU)
ii  libgme0                                       0.5.5-2                                 Playback library for video game music files - shared library
ii  libgmime-2.6-0                                2.6.7-1                                 MIME message parser and creator library - runtime
ii  libgmp10                                      2:5.0.2+dfsg-2ubuntu1                   Multiprecision arithmetic library
ii  libgnome-bluetooth8                           3.2.2-0ubuntu5                          GNOME Bluetooth tools - support library
ii  libgnome-desktop-3-2                          3.4.2-0ubuntu0.1                        Utility library for loading .desktop files - runtime files
ii  libgnome-keyring-common                       3.2.2-2                                 GNOME keyring services library - data files
ii  libgnome-keyring0                             3.2.2-2                                 GNOME keyring services library
ii  libgnome-keyring1.0-cil                       1.0.0-3build1                           CLI library to access the GNOME Keyring daemon
ii  libgnome-menu-3-0                             3.4.0-0ubuntu1                          GNOME implementation of the freedesktop menu specification
ii  libgnome-menu2                                3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  libgnome-vfs2.0-cil                           2.24.2-1                                CLI binding for GnomeVFS 2.24
ii  libgnome2-0                                   2.32.1-2ubuntu1.1                       The GNOME library - runtime files
ii  libgnome2-bin                                 2.32.1-2ubuntu1.1                       The GNOME library - binary files
ii  libgnome2-common                              2.32.1-2ubuntu1.1                       The GNOME library - common files
ii  libgnome2.24-cil                              2.24.2-1                                CLI binding for GNOME 2.24
ii  libgnomecanvas2-0                             2.30.3-1ubuntu1.1                       powerful object-oriented display engine - runtime files
ii  libgnomecanvas2-common                        2.30.3-1ubuntu1.1                       powerful object-oriented display engine - common files
ii  libgnomeui-0                                  2.24.5-2ubuntu2                         GNOME user interface library - runtime files
ii  libgnomeui-common                             2.24.5-2ubuntu2                         GNOME user interface library - common files
ii  libgnomevfs2-0                                1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (runtime libraries)
ii  libgnomevfs2-common                           1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                            1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (extra modules)
rc  libgnustep-base1.22                           1.22.1-2ubuntu2                         GNUstep Base library
rc  libgnustep-gui0.20                            0.20.0-2                                GNUstep GUI Library
ii  libgnutls26                                   2.12.14-5ubuntu3.1                      GNU TLS library - runtime library
ii  libgoffice-0.8-8                              0.8.17-1                                Document centric objects library - runtime files
ii  libgoffice-0.8-8-common                       0.8.17-1                                Document centric objects library - common files
ii  libgomp1                                      4.6.3-1ubuntu5                          GCC OpenMP (GOMP) support library
ii  libgoocanvas-common                           0.15-1                                  translations for goocanvas
ii  libgoocanvas3                                 0.15-1                                  canvas widget for GTK+ that uses the cairo 2D library
ii  libgpg-error0                                 1.10-2ubuntu1                           library for common error values and messages in GnuPG components
ii  libgphoto2-2                                  2.4.13-1ubuntu1.2                       gphoto2 digital camera library
ii  libgphoto2-l10n                               2.4.13-1ubuntu1.2                       gphoto2 digital camera library - localized messages
ii  libgphoto2-port0                              2.4.13-1ubuntu1.2                       gphoto2 digital camera port library
ii  libgpm2                                       1.20.4-4                                General Purpose Mouse - shared library
ii  libgpod-common                                0.8.2-4                                 common files for libgpod
ii  libgpod4                                      0.8.2-4                                 library to read and write songs and artwork to an iPod
ii  libgps20                                      3.4-2                                   Global Positioning System - library
ii  libgrail5                                     3.0.6-0ubuntu0.12.04.01                 Gesture Recognition And Instantiation Library
ii  libgraph4                                     2.26.3-10ubuntu1                        rich set of graph drawing tools - graph library
ii  libgrip0                                      0.3.5-0ubuntu1~12.04.1                  provides multitouch gestures to GTK+ apps
ii  libgs9                                        9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - Library
ii  libgs9-common                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - common files
ii  libgsf-1-114                                  1.14.21-2                               Structured File Library - runtime version
ii  libgsf-1-common                               1.14.21-2                               Structured File Library - common files
ii  libgsl0ldbl                                   1.15+dfsg-1build1                       GNU Scientific Library (GSL) -- library package
ii  libgsm1                                       1.0.13-3                                Shared libraries for GSM speech compressor
ii  libgssapi-krb5-2                              1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgssapi3-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - GSSAPI support library
ii  libgssdp-1.0-3                                0.12.1-2                                GObject-based library for SSDP
ii  libgstreamer-perl                             0.16-1build1                            Perl interface to the GStreamer media processing framework
ii  libgstreamer-plugins-bad0.10-0                0.10.22.3-2ubuntu2.1                    GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0               0.10.36-1ubuntu0.1                      GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                            0.10.36-1ubuntu1                        Core GStreamer libraries and elements
ii  libgtk-3-0                                    3.4.2-0ubuntu0.5                        GTK+ graphical user interface library
ii  libgtk-3-bin                                  3.4.2-0ubuntu0.5                        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                               3.4.2-0ubuntu0.5                        common files for the GTK+ graphical user interface library
ii  libgtk-sharp-beans-cil                        2.14.1-2build2                          Supplementary CLI bindings for GTK 2.14+
ii  libgtk2-notify-perl                           0.05-3build1                            Perl interface to libnotify
ii  libgtk2-perl                                  2:1.223-1build3                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2-trayicon-perl                         0.06-1build2                            Perl interface to fill the system tray
ii  libgtk2.0-0                                   2.24.10-0ubuntu6                        GTK+ graphical user interface library
ii  libgtk2.0-bin                                 2.24.10-0ubuntu6                        programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                 2.12.10-2ubuntu4                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                              2.24.10-0ubuntu6                        common files for the GTK+ graphical user interface library
ii  libgtkmathview0c2a                            0.8.0-7                                 rendering engine for MathML documents
ii  libgtkmm-2.4-1c2a                             1:2.24.2-1ubuntu1                       C++ wrappers for GTK+ (shared libraries)
ii  libgtkmm-3.0-1                                3.4.0-0ubuntu1                          C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview-3.0-0                        3.4.2-0ubuntu1                          shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview-3.0-common                   3.4.2-0ubuntu1                          common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                                  2.0.16-1ubuntu5                         a spell-checking addon for GTK's TextView widget
ii  libgtop2-7                                    2.28.4-2                                gtop system monitoring library (shared)
ii  libgtop2-common                               2.28.4-2                                gtop system monitoring library (common)
ii  libgucharmap-2-90-7                           1:3.4.1.1-0ubuntu1                      Unicode browser widget library (shared library)
ii  libgudev-1.0-0                                1:175-0ubuntu9.2                        GObject-based wrapper library for libudev
ii  libgudev1.0-cil                               0.1-2build1                             GObject-based wrapper library for libudev -- CLI bindings
ii  libguile-ltdl-1                               1.6.8-10ubuntu4                         Guile's patched version of libtool's libltdl
ii  libgupnp-1.0-4                                0.18.1-2                                GObject-based library for UPnP
ii  libgupnp-igd-1.0-4                            0.2.1-2                                 library to handle UPnP IGD port mapping
ii  libgutenprint2                                5.2.8~pre1-0ubuntu2.1                   runtime for the Gutenprint printer driver library
ii  libgvc5                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - gvc library
ii  libhcrypto4-heimdal                           1.6~git20120311.dfsg.1-2                Heimdal Kerberos - crypto library
ii  libheimbase1-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - Base library
ii  libheimntlm0-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - NTLM support library
ii  libhpmud0                                     3.12.2-1ubuntu3.1                       HP Multi-Point Transport Driver (hpmud) run-time libraries
ii  libhsqldb-java                                1.8.0.10-9ubuntu2                       Java SQL database engine
ii  libhtml-form-perl                             6.00-1                                  module that represents an HTML form element
ii  libhtml-format-perl                           2.10-1                                  module for transforming HTML into various formats
ii  libhtml-parser-perl                           3.69-1build1                            collection of modules that parse HTML text documents
ii  libhtml-tagset-perl                           3.20-2                                  Data tables pertaining to HTML
ii  libhtml-tree-perl                             4.2-1                                   Perl module to represent and create HTML syntax trees
ii  libhttp-cookies-perl                          6.00-2                                  HTTP cookie jars
ii  libhttp-daemon-perl                           6.00-1                                  simple http server class
ii  libhttp-date-perl                             6.00-1                                  module of date conversion routines
ii  libhttp-message-perl                          6.01-1                                  perl interface to HTTP style messages
ii  libhttp-negotiate-perl                        6.00-2                                  implementation of content negotiation
ii  libhunspell-1.3-0                             1.3.2-4                                 spell checker and morphological analyzer (shared library)
ii  libhx509-5-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - X509 support library
ii  libhyphen0                                    2.8.3-1                                 ALTLinux hyphenation library - shared library
ii  libibus-1.0-0                                 1.4.1-3ubuntu1                          Intelligent Input Bus - shared library
ii  libical0                                      0.48-1ubuntu3                           iCalendar library implementation in C (runtime)
ii  libice6                                       2:1.0.7-2build1                         X11 Inter-Client Exchange library
ii  libicu48                                      4.8.1.1-3                               International Components for Unicode
ii  libid3tag0                                    0.15.1b-10build2                        ID3 tag reading library from the MAD project
ii  libidl-common                                 0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files (common files)
ii  libidl0                                       0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files
ii  libidn11                                      1.23-2                                  GNU Libidn library, implementation of IETF IDN specifications
ii  libido-0.1-0                                  0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libido3-0.1-0                                 0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libiec61883-0                                 1.2.0-0.1ubuntu1                        an partial implementation of IEC 61883
ii  libieee1284-3                                 0.2.11-10build1                         cross-platform library for parallel port access
ii  libijs-0.35                                   0.35-8                                  IJS raster image transport protocol: shared library
ii  libilmbase6                                   1.0.1-3build2                           several utility libraries from ILM used by OpenEXR
ii  libimlib2                                     1.4.4-1build1                           powerful image loading and rendering library
ii  libimobiledevice2                             1.1.1-4                                 Library for communicating with the iPhone and iPod Touch
ii  libindi-data                                  0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared data
ii  libindi0                                      0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared library
ii  libindicate-gtk3                              0.6.92-0ubuntu1                         library for raising indicators via DBus - GTK+ bindings
ii  libindicate5                                  0.6.92-0ubuntu1                         library for raising indicators via DBus
ii  libindicator-messages-status-provider1        0.6.0-0ubuntu2                          indicator status provider - shared library
ii  libindicator3-7                               0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libindicator7                                 0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libio-socket-inet6-perl                       2.69-2                                  object interface for AF_INET6 domain sockets
ii  libio-socket-ssl-perl                         1.53-1                                  Perl module implementing object oriented interface to SSL sockets
ii  libisc83                                      1:9.8.1.dfsg.P1-4ubuntu0.5              ISC Shared Library used by BIND
ii  libisccc80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Command Channel Library used by BIND
ii  libisccfg82                                   1:9.8.1.dfsg.P1-4ubuntu0.5              Config File Handling Library used by BIND
ii  libiso9660-8                                  0.83-1                                  library to work with ISO9660 filesystems
ii  libisofs6                                     1.1.6-1ubuntu1                          library to create ISO9660 images
ii  libiw30                                       30~pre9-5ubuntu2                        Wireless tools - library
ii  libjack-jackd2-0                              1.9.8~dfsg.1-1ubuntu1                   JACK Audio Connection Kit (libraries)
ii  libjasper1                                    1.900.1-13                              JasPer JPEG-2000 runtime library
ii  libjava3d-java                                1.5.2+dfsg-5                            Java 3D API (java library)
ii  libjava3d-jni                                 1.5.2+dfsg-5                            Java3D API (java jni library)
ii  libjavascriptcoregtk-1.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjavascriptcoregtk-3.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjbig2dec0                                  0.11-1ubuntu1                           JBIG2 decoder library - shared libraries
ii  libjline-java                                 1.0-1                                   Java library for handling console input
ii  libjpeg-progs                                 8c-2ubuntu7                             Programs for manipulating JPEG files (dependency package)
ii  libjpeg-turbo-progs                           1.1.90+svn733-0ubuntu4.1                Programs for manipulating JPEG files
ii  libjpeg-turbo8                                1.1.90+svn733-0ubuntu4.1                IJG JPEG compliant runtime library.
ii  libjpeg8                                      8c-2ubuntu7                             Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjs-jquery                                  1.7.1-1ubuntu1                          JavaScript library for dynamic web applications
ii  libjson-glib-1.0-0                            0.14.2-1                                GLib JSON manipulation library
ii  libjson-ruby                                  1.6.3-1                                 Transitional package for ruby-json
ii  libjson0                                      0.9-1ubuntu1                            JSON manipulation library - shared library
ii  libjte1                                       1.19-1                                  Jigdo Template Export - runtime library
ii  libk5crypto3                                  1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Crypto Library
rc  libkabc4                                      4:4.8.5-0ubuntu0.1                      library for handling address book data
rc  libkalarmcal2                                 4:4.8.5-0ubuntu0.1                      library for handling alarm calendar data
ii  libkate1                                      0.4.1-1                                 Kate is a codec for karaoke and text encapsulation
ii  libkatepartinterfaces4                        4:4.8.5-0ubuntu0.1                      kate part library
rc  libkcal4                                      4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalcore4                                  4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalutils4                                 4:4.8.5-0ubuntu0.1                      library with utility functions for the handling of calendar data
ii  libkcmutils4                                  4:4.8.5-0ubuntu0.1                      utility classes for using KCM modules
ii  libkde3support4                               4:4.8.5-0ubuntu0.1                      KDE 3 Support Library for the KDE 4 Platform
ii  libkdeclarative5                              4:4.8.5-0ubuntu0.1                      Declarative library for plasma
ii  libkdecore5                                   4:4.8.5-0ubuntu0.1                      KDE Platform Core Library
ii  libkdeedu-data                                4:4.8.5-0ubuntu0.1                      data files for libkdeedu
ii  libkdesu5                                     4:4.8.5-0ubuntu0.1                      Console-mode Authentication Library for the KDE Platform
ii  libkdeui5                                     4:4.8.5-0ubuntu0.1                      KDE Platform User Interface Library
ii  libkdewebkit5                                 4:4.8.5-0ubuntu0.1                      KDE WebKit Library
ii  libkdnssd4                                    4:4.8.5-0ubuntu0.1                      DNS-SD Protocol Library for the KDE Platform
ii  libkeduvocdocument4                           4:4.8.5-0ubuntu0.1                      library for reading and writing vocabulary files
ii  libkemoticons4                                4:4.8.5-0ubuntu0.1                      utility classes to deal with emoticon themes
ii  libkeybinder0                                 0.2.2-3build1                           registers global key bindings for applications
ii  libkeyutils1                                  1.5.2-2                                 Linux Key Management Utilities (library)
ii  libkfile4                                     4:4.8.5-0ubuntu0.1                      File Selection Dialog Library for KDE Platform
rc  libkholidays4                                 4:4.8.5-0ubuntu0.1                      holidays calculation library
ii  libkhtml5                                     4:4.8.5-0ubuntu0.1                      KHTML Web Content Rendering Engine
ii  libkidletime4                                 4:4.8.5-0ubuntu0.1                      library to provide information about idle time
rc  libkimap4                                     4:4.8.5-0ubuntu0.1                      library for handling IMAP data
ii  libkio5                                       4:4.8.5-0ubuntu0.1                      Network-enabled File Management Library for the KDE Platform
ii  libkjsapi4                                    4:4.8.5-0ubuntu0.1                      KJS API Library for the KDE Development Platform
ii  libkjsembed4                                  4:4.8.5-0ubuntu0.1                      library for binding JavaScript objects to QObjects
rc  libkldap4                                     4:4.8.5-0ubuntu0.1                      library for accessing LDAP
ii  libklibc                                      1.5.25-1ubuntu2                         minimal libc subset for use with initramfs
rc  libkmbox4                                     4:4.8.5-0ubuntu0.1                      library for handling mbox mailboxes
ii  libkmediaplayer4                              4:4.8.5-0ubuntu0.1                      KMediaPlayer Interface for the KDE Platform
rc  libkmime4                                     4:4.8.5-0ubuntu0.1                      library for handling MIME data
rc  libknewstuff2-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v2 Library for the KDE Platform
ii  libknewstuff3-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v3 Library for the KDE Platform
ii  libknotifyconfig4                             4:4.8.5-0ubuntu0.1                      library for configuring KDE Notifications
ii  libkntlm4                                     4:4.8.5-0ubuntu0.1                      NTLM Authentication Library for the KDE Platform
ii  libkparts4                                    4:4.8.5-0ubuntu0.1                      Framework for the KDE Platform Graphical Components
ii  libkpathsea5                                  2009-11ubuntu2                          TeX Live: path search library for TeX (runtime part)
rc  libkpimidentities4                            4:4.8.5-0ubuntu0.1                      library for managing user identities
rc  libkpimtextedit4                              4:4.8.5-0ubuntu0.1                      library that provides a textedit with PIM-specific features
rc  libkpimutils4                                 4:4.8.5-0ubuntu0.1                      library for dealing with email addresses
ii  libkprintutils4                               4:4.8.5-0ubuntu0.1                      utility classes to deal with printing
ii  libkpty4                                      4:4.8.5-0ubuntu0.1                      Pseudo Terminal Library for the KDE Platform
ii  libkrb5-26-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - libraries
ii  libkrb5-3                                     1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries
ii  libkrb5support0                               1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Support library
rc  libkresources4                                4:4.8.5-0ubuntu0.1                      KDE Resource framework library
ii  libkrosscore4                                 4:4.8.5-0ubuntu0.1                      Kross Core Library
ii  libktexteditor4                               4:4.8.5-0ubuntu0.1                      KTextEditor interfaces for the KDE Platform
ii  libkunitconversion4                           4:4.8.5-0ubuntu0.1                      Unit Conversion library for the KDE Platform
ii  liblapack3gf                                  3.3.1-1                                 library of linear algebra routines 3 - shared version
ii  liblaunchpad-integration-3.0-1                0.1.56.1                                library for launchpad integration
ii  liblaunchpad-integration-common               0.1.56.1                                library for launchpad integration common data
ii  liblaunchpad-integration1                     0.1.56.1                                library for launchpad integration
ii  liblcms1                                      1.19.dfsg-1ubuntu3                      Little CMS color management library
ii  liblcms2-2                                    2.2+git20110628-2ubuntu3                Little CMS 2 color management library
ii  libldap-2.4-2                                 2.4.28-1.1ubuntu4.2                     OpenLDAP libraries
ii  liblightdm-gobject-1-0                        1.2.1-0ubuntu1.1                        LightDM GObject client library
ii  liblightdm-qt-2-0                             1.2.1-0ubuntu1.1                        LightDM Qt client library
ii  liblink-grammar4                              4.7.4-2                                 Carnegie Mellon University's link grammar parser (libraries)
ii  liblircclient0                                0.9.0-0ubuntu1                          infra-red remote control support - client library
ii  libllvm3.0                                    3.0-4ubuntu1                            Low-Level Virtual Machine (LLVM), runtime library
ii  liblocale-gettext-perl                        1.05-7build1                            module using libc functions for internationalization in Perl
ii  liblockfile-bin                               1.09-3                                  support binaries for and cli utilities based on liblockfile
ii  liblockfile1                                  1.09-3                                  NFS-safe locking library
ii  libloudmouth1-0                               1.4.3-8                                 Lightweight C Jabber library
ii  liblqr-1-0                                    0.4.1-1.1                               converts plain array images into multi-size representation
ii  libltdl7                                      2.4.2-1ubuntu1                          A system independent dlopen wrapper for GNU libtool
ii  liblua5.1-0                                   5.1.4-12ubuntu1                         Shared library for the Lua interpreter version 5.1
ii  liblvm2app2.2                                 2.02.66-4ubuntu7.1                      LVM2 application library
ii  liblwp-mediatypes-perl                        6.01-1                                  module to guess media type for a file or a URL
ii  liblwp-protocol-https-perl                    6.02-1                                  https driver for LWP::UserAgent
ii  liblwres80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Lightweight Resolver Library used by BIND
ii  liblzma5                                      5.1.1alpha+20110809-3                   XZ-format compression library
ii  liblzo2-2                                     2.06-1                                  data compression library
ii  libmad0                                       0.15.1b-7ubuntu1                        MPEG audio decoder library
ii  libmagic1                                     5.09-2                                  File type determination library using "magic" numbers
ii  libmagick++4                                  8:6.6.9.7-5ubuntu3.2                    object-oriented C++ interface to ImageMagick
ii  libmagickcore4                                8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library
ii  libmagickcore4-extra                          8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library - extra codecs
ii  libmagickwand4                                8:6.6.9.7-5ubuntu3.2                    image manipulation library
ii  libmailtools-perl                             2.08-1                                  Manipulate email in perl programs
rc  libmailtransport4                             4:4.8.5-0ubuntu0.1                      mail transport service library
ii  libmarblewidget13                             4:4.8.5-0ubuntu0.1                      Marble globe widget library
ii  libmatroska5                                  1.3.0-1                                 extensible open standard audio/video container format (shared library)
ii  libmeanwhile1                                 1.0.2-4ubuntu1                          open implementation of the Lotus Sametime Community Client protocol
ii  libmhash2                                     0.9.9.9-1                               Library for cryptographic hashing and message authentication
rc  libmicroblog4                                 4:4.8.5-0ubuntu0.1                      library for using the Microblog Akonadi Resource
ii  libmimic0                                     1.0.4-2.1build1                         A video codec for Mimic V2.x content
ii  libminiupnpc8                                 1.6-3ubuntu1                            UPnP IGD client lightweight library
ii  libmjpegtools-1.9                             1:1.9.0-0.5ubuntu7                      MJPEG video capture/editting/playback MPEG encoding
ii  libmlt++3                                     0.7.6+git20120204-2                     MLT multimedia framework C++ wrapper (runtime)
ii  libmlt-data                                   0.7.6+git20120204-2                     multimedia framework (data)
ii  libmlt4                                       0.7.6+git20120204-2                     multimedia framework (runtime)
ii  libmms0                                       0.6.2-2                                 MMS stream protocol library - shared library
ii  libmng1                                       1.0.10-3                                Multiple-image Network Graphics library
ii  libmodplug1                                   1:0.8.8.4-1                             shared libraries for mod music based on ModPlug
ii  libmono-addins-gui0.2-cil                     0.6.2-2                                 GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                         0.6.2-2                                 addin framework for extensible CLI applications/libraries
ii  libmono-cairo4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono Cairo library (for CLI 4.0)
ii  libmono-corlib4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono core library (for CLI 4.0)
ii  libmono-data-tds4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Data Library (for CLI 4.0)
ii  libmono-i18n-west4.0-cil                      2.10.8.1-1ubuntu2.2                     Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono I18N base library (for CLI 4.0)
ii  libmono-posix4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono.Posix library (for CLI 4.0)
ii  libmono-security4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Security library (for CLI 4.0)
ii  libmono-sharpzip4.84-cil                      2.10.8.1-1ubuntu2.2                     Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono SIMD (for CLI 4.0)
ii  libmono-sqlite4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono Sqlite library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil           2.10.8.1-1ubuntu2.2                     Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Core library (for CLI 4.0)
ii  libmono-system-data4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Data library (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                 2.10.8.1-1ubuntu2.2                     Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil      2.10.8.1-1ubuntu2.2                     Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-security4.0-cil                2.10.8.1-1ubuntu2.2                     Mono System.Security library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil 2.10.8.1-1ubuntu2.2                     Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-services4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Web library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Xml library (for CLI 4.0)
ii  libmono-system4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono System libraries (for CLI 4.0)
ii  libmono-web4.0-cil                            2.10.8.1-1ubuntu2.2                     Mono.Web library (for CLI 4.0)
ii  libmono-zeroconf1.0-cil                       0.9.0-3                                 CLI library for multicast DNS service discovery
ii  libmount1                                     2.20.1-1ubuntu3                         block device id library
ii  libmp3lame0                                   3.99.3+repack1-1                        MP3 encoding library
ii  libmpc2                                       0.9-4                                   multiple precision complex floating-point library
ii  libmpcdec6                                    2:0.1~r459-1ubuntu1                     MusePack decoder - library
ii  libmpeg2-4                                    0.4.1-3                                 MPEG1 and MPEG2 video decoder library
ii  libmpfr4                                      3.1.0-3ubuntu2                          multiple precision floating-point computation
ii  libmpg123-0                                   1.12.1-3.2ubuntu1                       MPEG layer 1/2/3 audio decoder -- runtime library
ii  libmtdev1                                     1.1.0-2ubuntu1                          Multitouch Protocol Translation Library - shared library
ii  libmtp-common                                 1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) common files
ii  libmtp-runtime                                1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) runtime tools
ii  libmtp9                                       1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) library
ii  libmusicbrainz3-6                             3.0.2-2.1                               library to access the MusicBrainz.org database
ii  libmx-1.0-2                                   1.4.3-0ubuntu1                          toolkit for the Moblin user experience
ii  libmysqlclient18                              5.5.28-0ubuntu0.12.04.3                 MySQL database client library
ii  libmythes-1.2-0                               2:1.2.2-1                               simple thesaurus library
ii  libnautilus-extension1a                       1:3.4.2-0ubuntu5                        libraries for nautilus components - runtime version
ii  libncurses5                                   5.9-4                                   shared libraries for terminal handling
ii  libncursesw5                                  5.9-4                                   shared libraries for terminal handling (wide character support)
ii  libndesk-dbus1.0-cil                          0.6.0-5                                 CLI implementation of D-Bus
ii  libneon27-gnutls                              0.29.6-1                                HTTP and WebDAV client library (GnuTLS enabled)
ii  libnepomuk4                                   4:4.8.5-0ubuntu0.1                      Nepomuk Meta Data Library
ii  libnepomukdatamanagement4                     4:4.8.5-0ubuntu0.1                      Basic Nepomuk data manipulation interface
ii  libnepomukquery4a                             4:4.8.5-0ubuntu0.1                      Nepomuk Query Library for the KDE Platform
ii  libnepomuksync4                               4:4.8.5-0ubuntu0.1                      Nepomuk sync interface for the Backup and Sync service
ii  libnepomukutils4                              4:4.8.5-0ubuntu0.1                      Nepomuk Utility Library
ii  libnet-dbus-perl                              1.0.0-1build1                           Extension for the DBus bindings
ii  libnet-http-perl                              6.02-1                                  module providing low-level HTTP connection client
ii  libnet-ssleay-perl                            1.42-1build1                            Perl module for Secure Sockets Layer (SSL)
ii  libnetfilter-conntrack3                       0.9.1-1ubuntu1                          Netfilter netlink-conntrack library
ii  libnetpbm10                                   2:10.0-15                               Graphics conversion tools shared libraries
ii  libnettle4                                    2.4-1                                   low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52                                   0.52.11-2ubuntu10                       Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnfnetlink0                                 1.0.0-1                                 Netfilter netlink library
ii  libnice10                                     0.1.1-2ubuntu1                          ICE library (shared library)
ii  libnih-dbus1                                  1.0.3-4ubuntu9                          NIH D-Bus Bindings Library
ii  libnih1                                       1.0.3-4ubuntu9                          NIH Utility Library
ii  libnl-3-200                                   3.2.3-2ubuntu2                          library for dealing with netlink sockets
ii  libnl-genl-3-200                              3.2.3-2ubuntu2                          library for dealing with netlink sockets - generic netlink
ii  libnl-route-3-200                             3.2.3-2ubuntu2                          library for dealing with netlink sockets - route interface
ii  libnm-glib-vpn1                               0.9.4.0-0ubuntu4.1                      network management framework (GLib VPN shared library)
ii  libnm-glib4                                   0.9.4.0-0ubuntu4.1                      network management framework (GLib shared library)
ii  libnm-gtk-common                              0.9.4.1-0ubuntu2                        network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                    0.9.4.1-0ubuntu2                        network management framework (GNOME dialogs for wifi and mobile)
ii  libnm-util2                                   0.9.4.0-0ubuntu4.1                      network management framework (shared library)
ii  libnotify-bin                                 0.7.5-1                                 sends desktop notifications to a notification daemon (Utilities)
ii  libnotify0.4-cil                              0.4.0~r3032-4                           CLI library for desktop notifications
ii  libnotify4                                    0.7.5-1                                 sends desktop notifications to a notification daemon
ii  libnova-0.12-2                                0.12.2-0ubuntu2                         astronomical library
ii  libnspr4                                      4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnspr4-0d                                   4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnss-mdns                                   0.10-3.2                                NSS module for Multicast DNS name resolution
ii  libnss3                                       3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libnss3-1d                                    3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libntrack-qt4-1                               016-1ubuntu1                            Qt 4 API for ntrack
ii  libntrack0                                    016-1ubuntu1                            lightweight connectivity tracking library
rc  libobjc3                                      4.6.3-1ubuntu5                          Runtime library for GNU Objective-C applications
ii  libodbc1                                      2.2.14p2-5ubuntu3                       ODBC library for Unix
ii  libofa0                                       0.9.3-4                                 Library for acoustic fingerprinting
ii  libogg0                                       1.2.2~dfsg-1ubuntu1                     Ogg bitstream library
ii  liboil0.3                                     0.3.17-2ubuntu3                         Library of Optimized Inner Loops
ii  liboobs-1-5                                   3.0.0-1                                 GObject based interface to system-tools-backends - shared library
ii  libopenal-data                                1:1.13-4ubuntu3                         Software implementation of the OpenAL API (data files)
ii  libopenal1                                    1:1.13-4ubuntu3                         Software implementation of the OpenAL API (shared library)
ii  libopenbabel4                                 2.3.0+dfsg-3ubuntu3                     Chemical toolbox library
ii  libopencc1                                    0.3.0-1                                 simplified-traditional chinese conversion library - runtime
ii  libopencore-amrnb0                            0.1.2-1                                 Adaptive Multi Rate speech codec - shared library
ii  libopencore-amrwb0                            0.1.2-1                                 Adaptive Multi-Rate - Wideband speech codec - shared library
ii  libopencv-calib3d2.3                          2.3.1-7                                 computer vision Camera Calibration library
ii  libopencv-core2.3                             2.3.1-7                                 computer vision core library
ii  libopencv-features2d2.3                       2.3.1-7                                 computer vision Feature Detection and Descriptor Extraction library
ii  libopencv-flann2.3                            2.3.1-7                                 computer vision Clustering and Search in Multi-Dimensional spaces library
ii  libopencv-highgui2.3                          2.3.1-7                                 computer vision High-level GUI and Media I/O library
ii  libopencv-imgproc2.3                          2.3.1-7                                 computer vision Image Processing library
ii  libopencv-objdetect2.3                        2.3.1-7                                 computer vision Object Detection library
ii  libopenexr6                                   1.6.1-4.1                               runtime files for the OpenEXR image library
ii  libopenjpeg2                                  1.3+dfsg-4                              JPEG 2000 image compression/decompression library
ii  libopenobex1                                  1.5-2build1                             OBEX protocol library
ii  libopenspc0                                   0.3.99a-2                               library for playing SPC files
ii  liborbit2                                     1:2.14.19-0.1ubuntu1                    libraries for ORBit2 - a CORBA ORB
ii  liborc-0.4-0                                  1:0.4.16-1ubuntu2                       Library of Optimized Inner Loops Runtime Compiler
ii  libotr2                                       3.2.0-4ubuntu0.1                        Off-the-Record Messaging library
ii  libots0                                       0.5.0-2.1                               Open Text Summarizer (library)
ii  libp11-kit0                                   0.12-2ubuntu1                           Library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpam-cap                                    1:2.22-1ubuntu3                         PAM module for implementing capabilities
ii  libpam-ck-connector                           0.4.5-2                                 ConsoleKit PAM module
ii  libpam-gnome-keyring                          3.2.2-2ubuntu4                          PAM module to unlock the GNOME keyring upon login
ii  libpam-modules                                1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                            1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                                1.1.3-7ubuntu2                          Runtime support for the PAM library
ii  libpam0g                                      1.1.3-7ubuntu2                          Pluggable Authentication Modules library
ii  libpango-perl                                 1.222-1build1                           Perl module to layout and render international text
ii  libpango1.0-0                                 1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text
ii  libpangomm-1.4-1                              2.28.4-1ubuntu1                         C++ Wrapper for pango (shared libraries)
ii  libpaper-utils                                1.1.24+nmu1build1                       library for handling paper characteristics (utilities)
ii  libpaper1                                     1.1.24+nmu1build1                       library for handling paper characteristics
ii  libparted0debian1                             2.3-8ubuntu5.1                          disk partition manipulator - shared library
ii  libpathplan4                                  2.26.3-10ubuntu1                        rich set of graph drawing tools - pathplan library
ii  libpcap0.8                                    1.1.1-10                                system interface for user-level packet capture
ii  libpci3                                       1:3.1.8-2ubuntu5                        Linux PCI Utilities (shared library)
ii  libpciaccess0                                 0.12.902-1                              Generic PCI access library for X
ii  libpcre3                                      8.12-4                                  Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcsclite1                                  1.7.4-2ubuntu2                          Middleware to access a smart card using PC/SC (library)
ii  libpeas-1.0-0                                 1.2.0-1ubuntu1                          Application plugin library
ii  libpeas-common                                1.2.0-1ubuntu1                          Application plugin library (common files)
ii  libperl5.14                                   5.14.2-6ubuntu2.2                       shared Perl library
ii  libphonon4                                    4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - core library
ii  libpipeline1                                  1.2.1-1                                 pipeline manipulation library
ii  libpixman-1-0                                 0.24.4-1                                pixel-manipulation library for X and cairo
ii  libplasma3                                    4:4.8.5-0ubuntu0.1                      Plasma Library for the KDE Platform
ii  libplist1                                     1.8-1                                   Library for handling Apple binary and XML property lists
ii  libplymouth2                                  0.8.2-2ubuntu30                         graphical boot animation and logger - shared libraries
ii  libpng12-0                                    1.2.46-3ubuntu4                         PNG library - runtime
ii  libpolkit-agent-1-0                           0.104-1ubuntu1                          PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0                         0.104-1ubuntu1                          PolicyKit backend API
ii  libpolkit-gobject-1-0                         0.104-1ubuntu1                          PolicyKit Authorization API
ii  libpolkit-qt-1-1                              0.103.0-1                               PolicyKit-qt-1 library
ii  libpoppler-glib8                              0.18.4-1ubuntu3                         PDF rendering library (GLib-based shared library)
ii  libpoppler19                                  0.18.4-1ubuntu3                         PDF rendering library
ii  libpopt0                                      1.16-3ubuntu1                           lib for parsing cmdline parameters
ii  libportaudio2                                 19+svn20111121-1                        Portable audio I/O - shared library
ii  libportsmf0                                   0.1~svn20101010-3                       Portable Standard Midi File Library
ii  libpostproc-extra-52                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libpostproc52                                 4:0.8.4-0ubuntu0.12.04.1                Libav video postprocessing library
rc  libprison0                                    1.0+dfsg-1                              barcode API for Qt
ii  libproxy1                                     0.4.7-0ubuntu4.1                        automatic proxy configuration management library (shared)
ii  libpulse-mainloop-glib0                       1:1.1-0ubuntu15.1                       PulseAudio client libraries (glib support)
ii  libpulse0                                     1:1.1-0ubuntu15.1                       PulseAudio client libraries
ii  libpulsedsp                                   1:1.1-0ubuntu15.1                       PulseAudio OSS pre-load library
ii  libpurple-bin                                 1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library - extra utilities
ii  libpurple0                                    1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library
ii  libpython2.7                                  2.7.3-0ubuntu3.1                        Shared Python runtime library (version 2.7)
ii  libpython3.2                                  3.2.3-0ubuntu3.2                        Shared Python runtime library (version 3.2)
ii  libqalculate5                                 0.9.7-6ubuntu2                          Powerful and easy to use desktop calculator - library
ii  libqapt-runtime                               1.3.1-0ubuntu2                          Runtime components for the QApt library
ii  libqapt1                                      1.3.1-0ubuntu2                          QApt library package
ii  libqca2                                       2.0.3-2                                 libraries for the Qt Cryptographic Architecture
ii  libqimageblitz4                               1:0.0.6-4                               QImageBlitz image effects library
rc  libqrencode3                                  3.1.1-1ubuntu1                          QR Code encoding library
ii  libqt3-mt                                     3:3.3.8-b-8ubuntu3                      Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-dbus                                   4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus module
ii  libqt4-declarative                            4:4.8.1-0ubuntu4.3                      Qt 4 Declarative module
ii  libqt4-designer                               4:4.8.1-0ubuntu4.3                      Qt 4 designer module
ii  libqt4-help                                   4:4.8.1-0ubuntu4.3                      Qt 4 help module
ii  libqt4-network                                4:4.8.1-0ubuntu4.3                      Qt 4 network module
ii  libqt4-opengl                                 4:4.8.1-0ubuntu4.3                      Qt 4 OpenGL module
ii  libqt4-qt3support                             4:4.8.1-0ubuntu4.3                      Qt 3 compatibility library for Qt 4
ii  libqt4-script                                 4:4.8.1-0ubuntu4.3                      Qt 4 script module
ii  libqt4-scripttools                            4:4.8.1-0ubuntu4.3                      Qt 4 script tools module
ii  libqt4-sql                                    4:4.8.1-0ubuntu4.3                      Qt 4 SQL module
ii  libqt4-sql-mysql                              4:4.8.1-0ubuntu4.3                      Qt 4 MySQL database driver
ii  libqt4-svg                                    4:4.8.1-0ubuntu4.3                      Qt 4 SVG module
ii  libqt4-test                                   4:4.8.1-0ubuntu4.3                      Qt 4 test module
ii  libqt4-xml                                    4:4.8.1-0ubuntu4.3                      Qt 4 XML module
ii  libqt4-xmlpatterns                            4:4.8.1-0ubuntu4.3                      Qt 4 XML patterns module
ii  libqtassistantclient4                         4.6.3-3ubuntu2                          Qt Assistant client library (runtime)
ii  libqtcore4                                    4:4.8.1-0ubuntu4.3                      Qt 4 core module
ii  libqtgui4                                     4:4.8.1-0ubuntu4.3                      Qt 4 GUI module
ii  libqthreads-12                                1.6.8-10ubuntu4                         QuickThreads library for Guile
ii  libqtwebkit4                                  2.2.1-1ubuntu4                          Web content engine library for Qt
ii  libquadmath0                                  4.6.3-1ubuntu5                          GCC Quad-Precision Math Library
ii  libquicktime2                                 2:1.2.3-4build2                         library for reading and writing Quicktime files
ii  libquvi-scripts                               0.4.2-1                                 library for parsing video download links (Lua scripts)
ii  libquvi7                                      0.4.0-1                                 library for parsing video download links (runtime libraries)
ii  libraptor2-0                                  2.0.6-1                                 Raptor 2 RDF syntax library
ii  librarian0                                    0.8.1-5                                 Documentation meta-data library (library package)
ii  librasqal3                                    0.9.28-1                                Rasqal RDF query library
ii  libraw1394-11                                 2.0.7-1ubuntu1                          library for direct access to IEEE 1394 bus (aka FireWire)
ii  librdf0                                       1.0.14-1                                Redland Resource Description Framework (RDF) library
ii  libreadline5                                  5.2-11                                  GNU readline and history libraries, run-time libraries
ii  libreadline6                                  6.2-8                                   GNU readline and history libraries, run-time libraries
ii  libreoffice                                   1:3.5.4-0ubuntu1.1                      office productivity suite
ii  libreoffice-base                              1:3.5.4-0ubuntu1.1                      office productivity suite -- database
ii  libreoffice-base-core                         1:3.5.4-0ubuntu1.1                      office productivity suite -- shared library
ii  libreoffice-calc                              1:3.5.4-0ubuntu1.1                      office productivity suite -- spreadsheet
ii  libreoffice-common                            1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent files
ii  libreoffice-core                              1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-dependent files
ii  libreoffice-draw                              1:3.5.4-0ubuntu1.1                      office productivity suite -- drawing
ii  libreoffice-emailmerge                        1:3.5.4-0ubuntu1.1                      office productivity suite -- email mail merge
ii  libreoffice-filter-mobiledev                  1:3.5.4-0ubuntu1.1                      office productivity suite -- mobile devices filters
ii  libreoffice-gnome                             1:3.5.4-0ubuntu1.1                      office productivity suite -- GNOME integration
ii  libreoffice-gtk                               1:3.5.4-0ubuntu1.1                      office productivity suite -- GTK+ integration
ii  libreoffice-impress                           1:3.5.4-0ubuntu1.1                      office productivity suite -- presentation
ii  libreoffice-java-common                       1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent Java support files
ii  libreoffice-math                              1:3.5.4-0ubuntu1.1                      office productivity suite -- equation editor
ii  libreoffice-style-human                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Human symbol style
ii  libreoffice-style-tango                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Tango symbol style
ii  libreoffice-writer                            1:3.5.4-0ubuntu1.1                      office productivity suite -- word processor
ii  libresid-builder0c2a                          2.1.1-12                                SID chip emulation class based on resid
ii  librhythmbox-core5                            2.96-0ubuntu4.2                         support library for the rhythmbox music player
ii  libroken18-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - roken support library
ii  librsvg2-2                                    2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (runtime)
ii  librsvg2-common                               2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (extra runtime)
ii  librtmp0                                      2.4~20110711.gitc28f1bab-1              toolkit for RTMP streams (shared library)
ii  libruby                                       4.8                                     Transitional package for libruby1.8
ii  libruby1.8                                    1.8.7.352-2ubuntu1.1                    Libraries necessary to run Ruby 1.8
ii  libsamplerate0                                0.1.8-4                                 Audio sample rate conversion library
ii  libsane                                       1.0.22-7ubuntu1                         API library for scanners
ii  libsane-common                                1.0.22-7ubuntu1                         API library for scanners -- documentation and support files
ii  libsane-hpaio                                 3.12.2-1ubuntu3.1                       HP SANE backend for multi-function peripherals
ii  libsasl2-2                                    2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - authentication abstraction library
ii  libsasl2-modules                              2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - pluggable authentication modules
ii  libschroedinger-1.0-0                         1.0.11-1                                library for encoding/decoding of Dirac video streams
ii  libsdl-image1.2                               1.2.10-3                                image loading library for Simple DirectMedia Layer 1.2
ii  libsdl1.2debian                               1.2.14-6.4ubuntu3                       Simple DirectMedia Layer
ii  libselinux1                                   2.1.0-4.1ubuntu1                        SELinux runtime shared libraries
ii  libsensors4                                   1:3.3.1-2ubuntu1                        library to read temperature/voltage/fan sensors
ii  libservlet2.5-java                            6.0.35-1ubuntu3.1                       Servlet 2.5 and JSP 2.1 Java API classes
ii  libsexy2                                      0.1.11-2build2                          collection of additional GTK+ widgets - library
ii  libsgutils2-2                                 1.33-1                                  utilities for devices using the SCSI command set (shared libraries)
ii  libshadow-ruby1.8                             1.4.1-8build1                           Interface of shadow password for Ruby 1.8
ii  libshout3                                     2.2.2-7ubuntu1                          MP3/Ogg Vorbis broadcast streaming library
ii  libsidplay1                                   1.36.59-5                               SID (MOS 6581) emulation library
ii  libsidplay2                                   2.1.1-12                                SID (MOS 6581) emulation library
ii  libsigc++-2.0-0c2a                            2.2.10-0ubuntu2                         type-safe Signal Framework for C++ - runtime
ii  libslang2                                     2.2.4-3ubuntu1                          S-Lang programming library - runtime version
ii  libslp1                                       1.2.1-7.8ubuntu1                        OpenSLP libraries
ii  libslv2-9                                     0.6.6+dfsg1-1                           library for simple use of LV2 plugins
ii  libsm6                                        2:1.2.0-2build1                         X11 Session Management library
ii  libsmbclient                                  2:3.6.3-2ubuntu2.3                      shared library for communication with SMB/CIFS servers
ii  libsndfile1                                   1.0.25-4                                Library for reading/writing audio files
ii  libsnmp-base                                  5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) MIBs and documentation
ii  libsnmp15                                     5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) library
ii  libsocket6-perl                               0.23-1build2                            Perl extensions for IPv6
ii  libsolid4                                     4:4.8.5-0ubuntu0.1                      Solid Library for KDE Platform
ii  libsonic0                                     0.1.17-1.1                              Simple library to speed up or slow down speech
ii  libsoprano4                                   2.7.5+dfsg.1-0ubuntu1                   libraries for the Soprano RDF framework
ii  libsoundtouch0                                1.6.0-2build1                           Sound stretching library
ii  libsoup-gnome2.4-1                            2.38.1-1                                HTTP library implementation in C -- GNOME support library
ii  libsoup2.4-1                                  2.38.1-1                                HTTP library implementation in C -- Shared library
ii  libsox-fmt-alsa                               14.3.2-3                                SoX alsa format I/O library
ii  libsox-fmt-base                               14.3.2-3                                Minimal set of SoX format libraries
ii  libsox1b                                      14.3.2-3                                SoX library of audio effects and processing
ii  libspandsp2                                   0.0.6~pre18-2build1                     Telephony signal processing library
ii  libspectre1                                   0.2.6-1build1                           Library for rendering PostScript documents
ii  libspeechd2                                   0.7.1-6ubuntu3                          Speech Dispatcher: Shared libraries
ii  libspeex1                                     1.2~rc1-3ubuntu2                        The Speex codec runtime library
ii  libspeexdsp1                                  1.2~rc1-3ubuntu2                        The Speex extended runtime library
ii  libsqlite3-0                                  3.7.9-2ubuntu1.1                        SQLite 3 shared library
ii  libss2                                        1.42-1ubuntu2                           command-line interface parsing library
ii  libssh-4                                      0.5.2-1ubuntu0.12.04.1                  tiny C SSH library
ii  libssl1.0.0                                   1.0.1-4ubuntu5.5                        SSL shared libraries
ii  libstartup-notification0                      0.12-1ubuntu1                           library for program launch feedback (shared library)
ii  libstdc++6                                    4.6.3-1ubuntu5                          GNU Standard C++ Library v3
ii  libstdc++6-4.6-dev                            4.6.3-1ubuntu5                          GNU Standard C++ Library v3 (development files)
ii  libstlport4.6ldbl                             4.6.2-7                                 STLport C++ class library
ii  libstreamanalyzer0                            0.7.7-1.1ubuntu3                        streamanalyzer library for Strigi Desktop Search
ii  libstreams0                                   0.7.7-1.1ubuntu3                        streams library for for Strigi Desktop Search
ii  libsvga1                                      1:1.4.3-31                              console SVGA display libraries
ii  libswitch-perl                                2.16-2                                  switch statement for Perl
ii  libswscale-extra-2                            4:0.8.4ubuntu0.12.04.1                  Libav video software scaling library
rc  libswscale2                                   4:0.8.4-0ubuntu0.12.04.1                Libav video scaling library
ii  libsysfs2                                     2.1.0+repack-1                          interface library to sysfs
ii  libt1-5                                       5.1.2-3.4ubuntu1                        Type 1 font rasterizer library - runtime
ii  libtag1-vanilla                               1.7-1ubuntu5                            audio meta-data library - vanilla flavour
ii  libtag1c2a                                    1.7-1ubuntu5                            audio meta-data library
ii  libtagc0                                      1.7-1ubuntu5                            audio meta-data library - C bindings
ii  libtaglib2.0-cil                              2.0.4.0-1                               CLI library for accessing audio and video files metadata
ii  libtalloc2                                    2.0.7-3                                 hierarchical pool based memory allocator
ii  libtar0                                       1.2.11-8                                C library for manipulating tar archives
ii  libtasn1-3                                    2.10-1ubuntu1.1                         Manage ASN.1 structures (runtime)
ii  libtdb1                                       1.2.9-4                                 Trivial Database - shared library
ii  libtelepathy-glib0                            0.18.0-1ubuntu1                         Telepathy framework - GLib library
ii  libtext-charwidth-perl                        0.04-7build1                            get display widths of characters on the terminal
ii  libtext-iconv-perl                            1.7-5                                   converts between character sets in Perl
ii  libtext-wrapi18n-perl                         0.06-7                                  internationalized substitute of Text::Wrap
ii  libthai-data                                  0.1.16-3                                Data files for Thai language support library
ii  libthai0                                      0.1.16-3                                Thai language support library
ii  libtheora0                                    1.1.1+dfsg.1-3ubuntu2                   The Theora Video Compression Codec
ii  libthreadweaver4                              4:4.8.5-0ubuntu0.1                      ThreadWeaver Library for the KDE Platform
ii  libthunarx-2-0                                1.2.3-3ubuntu2                          extension library for thunar
ii  libtidy-0.99-0                                20091223cvs-1ubuntu2                    HTML syntax checker and reformatter - library
ii  libtie-ixhash-perl                            1.21-2                                  ordered associative arrays for Perl
ii  libtiff4                                      3.9.5-2ubuntu1.4                        Tag Image File Format (TIFF) library
ii  libtimedate-perl                              1.2000-1                                collection of modules to manipulate date/time information
ii  libtinfo5                                     5.9-4                                   shared low-level terminfo library for terminal handling
ii  libtommath0                                   0.42.0-1                                multiple-precision integer library [runtime]
ii  libtotem-plparser17                           3.4.1-1                                 Totem Playlist Parser library - runtime files
ii  libts-0.0-0                                   1.0-10                                  touch screen library
ii  libtumbler-1-0                                0.1.24-0ubuntu1                         library for tumbler, a D-Bus thumbnailing service
ii  libtwolame0                                   0.3.13-1build1                          MPEG Audio Layer 2 encoding library
ii  libudev0                                      175-0ubuntu9.2                          udev library
ii  libunique-1.0-0                               1.1.6-4                                 Library for writing single instance applications - shared libraries
ii  libunistring0                                 0.9.3-5                                 Unicode string library for C
ii  libunity9                                     5.12.0-0ubuntu1.1                       binding to get places into the launcher - shared library
ii  libupnp3                                      1:1.6.6-5.1                             Portable SDK for UPnP Devices, version 1.6 (shared libraries)
ii  libupower-glib1                               0.9.15-3git1                            abstraction for power management - shared library
ii  liburi-perl                                   1.59-1                                  module to manipulate and access URI strings
ii  libusb-0.1-4                                  2:0.1.12-20                             userspace USB programming library
ii  libusb-1.0-0                                  2:1.0.9~rc3-2ubuntu1                    userspace USB programming library
ii  libusbmuxd1                                   1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libutempter0                                  1.1.5-4                                 A privileged helper for utmp/wtmp updates (runtime)
ii  libutouch-evemu1                              1.0.9-0ubuntu1                          KernelInput Event Device Emulation Library
ii  libutouch-frame1                              2.2.3-0ubuntu1                          Touch Frame Library
ii  libutouch-geis1                               2.2.9-0ubuntu3                          Gesture engine interface support
ii  libutouch-grail1                              3.0.5-0ubuntu1                          Gesture Recognition And Instantiation Library
ii  libuuid-perl                                  0.02-4ubuntu1                           Perl extension for using UUID interfaces as defined in e2fsprogs
ii  libuuid1                                      2.20.1-1ubuntu3                         Universally Unique ID library
ii  libv4l-0                                      0.8.6-1ubuntu2                          Collection of video4linux support libraries
ii  libv4lconvert0                                0.8.6-1ubuntu2                          Video4linux frame format conversion library
ii  libva-x11-1                                   1.0.15-4                                Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva1                                        1.0.15-4                                Video Acceleration (VA) API for Linux -- runtime
ii  libvamp-hostsdk3                              2.1-1                                   helper library for Vamp hosts written in C++
ii  libvcdinfo0                                   0.7.23-4.1ubuntu1                       library to extract information from VideoCD
ii  libvdpau1                                     0.4.1-3ubuntu1.1                        Video Decode and Presentation API for Unix (libraries)
ii  libvecmath-java                               1.5.2-3                                 javax.vecmath vector math package
ii  libvirtodbc0                                  6.1.4+dfsg1-0ubuntu1                    high-performance database - ODBC libraries
ii  libvisual-0.4-0                               0.4.0-4                                 Audio visualization framework
ii  libvisual-0.4-plugins                         0.4.0.dfsg.1-7                          Audio visualization framework plugins
ii  libvlc5                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer library
ii  libvlccore5                                   2.0.3-0ubuntu0.12.04.1                  base library for VLC and its modules
ii  libvo-aacenc0                                 0.1.1-2                                 VisualOn AAC encoder library
ii  libvo-amrwbenc0                               0.1.1-2                                 VisualOn AMR-WB encoder library
ii  libvorbis0a                                   1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Decoder library)
ii  libvorbisenc2                                 1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Encoder library)
ii  libvorbisfile3                                1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (High Level API)
ii  libvpx1                                       1.0.0-1                                 VP8 video codec (shared library)
ii  libvte-2.90-9                                 1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - runtime files
ii  libvte-2.90-common                            1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - common files
ii  libvte-common                                 1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.x - common files
ii  libvte9                                       1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.0 - runtime files
ii  libwavpack1                                   4.60.1-2                                audio codec (lossy and lossless) - library
ii  libwbclient0                                  2:3.6.3-2ubuntu2.3                      Samba winbind client library
ii  libwebkitgtk-1.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwildmidi-config                            0.2.3.4-2.1                             software MIDI player configuration
ii  libwildmidi1                                  0.2.3.4-2.1                             software MIDI player library
ii  libwind0-heimdal                              1.6~git20120311.dfsg.1-2                Heimdal Kerberos - stringprep implementation
ii  libwmf-bin                                    0.2.8.4-10ubuntu1                       Windows metafile conversion tools
ii  libwmf0.2-7                                   0.2.8.4-10ubuntu1                       Windows metafile conversion library
ii  libwnck-3-0                                   3.4.0-0ubuntu1                          Window Navigator Construction Kit - runtime files
ii  libwnck-3-common                              3.4.0-0ubuntu1                          Window Navigator Construction Kit - common files
ii  libwnck-common                                1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - common files
ii  libwnck22                                     1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - runtime files
ii  libwpd-0.9-9                                  0.9.4-1                                 Library for handling WordPerfect documents (shared library)
ii  libwpg-0.2-2                                  0.2.1-1                                 WordPerfect graphics import/convert library (shared library)
ii  libwps-0.2-2                                  0.2.4-1                                 Works text file format import filter library (shared library)
ii  libwrap0                                      7.6.q-21                                Wietse Venema's TCP wrappers library
ii  libwv-1.2-4                                   1.2.9-2                                 Library for accessing Microsoft Word documents
ii  libwww-perl                                   6.03-1                                  simple and consistent interface to the world-wide web
ii  libwww-robotrules-perl                        6.01-1                                  database of robots.txt-derived permissions
ii  libwxbase2.8-0                                2.8.12.1-6ubuntu2                       wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxgtk2.8-0                                 2.8.12.1-6ubuntu2                       wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libx11-6                                      2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-data                                   2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-xcb1                                   2:1.4.99.1-0ubuntu2                     Xlib/XCB interface library
ii  libx264-120                                   2:0.120.2151+gita3f4407-2               x264 video coding library
ii  libx86-1                                      1.1+ds1-7ubuntu1                        x86 real-mode library
ii  libxapian22                                   1.2.8-1                                 Search engine library
ii  libxatracker1                                 8.0.4-0ubuntu0.2                        X acceleration library -- runtime
ii  libxau6                                       1:1.0.6-4                               X11 authorisation library
ii  libxaw7                                       2:1.0.9-3ubuntu1                        X11 Athena Widget library
ii  libxcb-composite0                             1.8.1-1ubuntu0.1                        X C Binding, composite extension
ii  libxcb-dri2-0                                 1.8.1-1ubuntu0.1                        X C Binding, dri2 extension
ii  libxcb-glx0                                   1.8.1-1ubuntu0.1                        X C Binding, glx extension
ii  libxcb-keysyms1                               0.3.8-1build1                           utility libraries for X C Binding -- keysyms
ii  libxcb-randr0                                 1.8.1-1ubuntu0.1                        X C Binding, randr extension
ii  libxcb-render0                                1.8.1-1ubuntu0.1                        X C Binding, render extension
ii  libxcb-shape0                                 1.8.1-1ubuntu0.1                        X C Binding, shape extension
ii  libxcb-shm0                                   1.8.1-1ubuntu0.1                        X C Binding, shm extension
ii  libxcb-util0                                  0.3.8-2                                 utility libraries for X C Binding -- atom, aux and event
ii  libxcb-xv0                                    1.8.1-1ubuntu0.1                        X C Binding, xv extension
ii  libxcb1                                       1.8.1-1ubuntu0.1                        X C Binding
ii  libxcomposite1                                1:0.4.3-2build1                         X11 Composite extension library
ii  libxcursor1                                   1:1.1.12-1                              X cursor management library
ii  libxdamage1                                   1:1.1.3-2build1                         X11 damaged region extension library
ii  libxdmcp6                                     1:1.1.0-4                               X11 Display Manager Control Protocol library
ii  libxerces2-java                               2.11.0-4                                Validating XML parser for Java with DOM level 3 support
ii  libxext6                                      2:1.3.0-3build1                         X11 miscellaneous extension library
ii  libxfce4ui-1-0                                4.8.1-1                                 widget library for Xfce
ii  libxfce4util-bin                              4.8.2-1                                 tools for libxfce4util
ii  libxfce4util-common                           4.8.2-1                                 common files for libxfce4util
ii  libxfce4util4                                 4.8.2-1                                 Utility functions library for Xfce4
ii  libxfcegui4-4                                 4.8.1-5ubuntu1                          Basic GUI C functions for Xfce4
ii  libxfconf-0-2                                 4.8.1-1                                 Client library for Xfce4 configure interface
ii  libxfixes3                                    1:5.0-4ubuntu4                          X11 miscellaneous 'fixes' extension library
ii  libxfont1                                     1:1.4.4-1                               X11 font rasterisation library
ii  libxft2                                       2.2.0-3ubuntu2                          FreeType-based font drawing library for X
ii  libxi6                                        2:1.6.0-0ubuntu2                        X11 Input extension library
ii  libxinerama1                                  2:1.1.1-3build1                         X11 Xinerama extension library
ii  libxkbfile1                                   1:1.0.7-1ubuntu0.1                      X11 keyboard file manipulation library
ii  libxklavier16                                 5.2.1-1ubuntu1                          X Keyboard Extension high-level API
ii  libxml-commons-external-java                  1.4.01-2                                XML Commons external code - DOM, SAX, and JAXP, etc
ii  libxml-commons-resolver1.1-java               1.2-7                                   XML entity and URI resolver library
ii  libxml-parser-perl                            2.41-1build1                            Perl module for parsing XML files
ii  libxml-twig-perl                              1:3.39-1ubuntu1                         Perl module for processing huge XML documents in tree mode
ii  libxml-xpath-perl                             1.13-7                                  Perl module for processing XPath
ii  libxml2                                       2.7.8.dfsg-5.1ubuntu4.3                 GNOME XML library
ii  libxml2-utils                                 2.7.8.dfsg-5.1ubuntu4.3                 XML utilities
ii  libxmmsclient6                                0.8+dfsg-2                              XMMS2 - client library
ii  libxmu6                                       2:1.1.0-3                               X11 miscellaneous utility library
ii  libxmuu1                                      2:1.1.0-3                               X11 miscellaneous micro-utility library
ii  libxp6                                        1:1.0.1-2                               X Printing Extension (Xprint) client library
ii  libxpm4                                       1:3.5.9-4                               X11 pixmap library
ii  libxrandr2                                    2:1.3.2-2                               X11 RandR extension library
ii  libxrender1                                   1:0.9.6-2build1                         X Rendering Extension client library
ii  libxres1                                      2:1.0.5-1                               X11 Resource extension library
ii  libxslt1.1                                    1.1.26-8ubuntu1.2                       XSLT 1.0 processing library - runtime library
ii  libxss1                                       1:1.2.1-2                               X11 Screen Saver extension library
ii  libxt6                                        1:1.1.1-2build1                         X11 toolkit intrinsics library
ii  libxtst6                                      2:1.2.0-4                               X11 Testing -- Record extension library
ii  libxv1                                        2:1.0.6-2build1                         X11 Video extension library
ii  libxvidcore4                                  2:1.3.2-6                               Open source MPEG-4 video codec (library)
ii  libxvmc1                                      2:1.0.6-1ubuntu2                        X11 Video extension library
ii  libxxf86dga1                                  2:1.1.2-1                               X11 Direct Graphics Access extension library
ii  libxxf86vm1                                   1:1.1.1-2build1                         X11 XFree86 video mode extension library
ii  libyajl1                                      1.0.12-2                                Yet Another JSON Library
ii  libyaml-tiny-perl                             1.50-1                                  Perl module for reading and writing YAML files
ii  libyelp0                                      3.4.1-0ubuntu1                          Library for the GNOME help browser
ii  libzbar0                                      0.10+doc-7build2                        bar code scanner and decoder (library)
ii  libzeitgeist-1.0-1                            0.3.18-1ubuntu1                         library to access Zeitgeist - shared library
ii  libzephyr4                                    3.0.1-1                                 Project Athena's notification service - non-Kerberos libraries
ii  libzvbi-common                                0.2.33-4                                Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0                                      0.2.33-4                                Vertical Blanking Interval decoder (VBI) - runtime files
ii  lightdm                                       1.2.1-0ubuntu1.1                        Display Manager
ii  lightdm-gtk-greeter                           1.1.5-0ubuntu1.1                        LightDM GTK+ Greeter
ii  lightdm-kde-greeter                           0.1.1-0ubuntu0.1                        LightDM KDE greeter
ii  link-grammar-dictionaries-en                  4.7.4-2                                 Carnegie Mellon University's link grammar parser (English dictionary)
ii  linux-firmware                                1.79.1                                  Firmware for Linux kernel drivers
ii  linux-generic                                 3.2.0.35.40                             Complete Generic Linux kernel
ii  linux-headers-3.2.0-35                        3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic                3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                         3.2.0.35.40                             Generic Linux kernel headers
ii  linux-image-3.2.0-29-generic                  3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic                  3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic                  3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic                  3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                           3.2.0.35.40                             Generic Linux kernel image
ii  linux-libc-dev                                3.2.0-35.55                             Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu1                    base package for ALSA and OSS sound systems
ii  locales                                       2.13+git20120306-3                      common files for locale support
ii  lockfile-progs                                0.1.16                                  Programs for locking and unlocking files and mailboxes
ii  login                                         1:4.1.4.2+svn3283-3ubuntu5.1            system login tools
ii  logrotate                                     3.7.8-6ubuntu5                          Log rotation utility
ii  lp-solve                                      5.5.0.13-7                              Solve (mixed integer) linear programming problems
ii  lsb-base                                      4.0-0ubuntu20.2                         Linux Standard Base 4.0 init script functionality
ii  lsb-release                                   4.0-0ubuntu20.2                         Linux Standard Base version reporting utility
ii  lshw                                          02.15-2                                 information about hardware configuration
ii  lsof                                          4.81.dfsg.1-1build1                     List open files
ii  ltrace                                        0.5.3-2.1ubuntu2                        Tracks runtime library calls in dynamically linked programs
ii  lynx-cur                                      2.8.8dev.9-2ubuntu0.12.04.1             Text-mode WWW Browser with NLS support (development version)
ii  m4                                            1.4.16-2ubuntu1                         a macro processing language
rc  mahjongg                                      1:3.4.1-0ubuntu2.1                      classic Eastern tile game for GNOME
ii  make                                          3.81-8.1ubuntu1.1                       An utility for Directing compilation.
ii  makedev                                       2.3.1-89ubuntu2                         creates device files in /dev
ii  man-db                                        2.6.1-2                                 on-line manual pager
ii  manpages                                      3.35-0.1ubuntu1                         Manual pages about using a GNU/Linux system
ii  manpages-dev                                  3.35-0.1ubuntu1                         Manual pages about using GNU/Linux for development
ii  marble                                        4:4.8.5-0ubuntu0.1                      globe and map widget
ii  marble-data                                   4:4.8.5-0ubuntu0.1                      data files for Marble
ii  marble-plugins                                4:4.8.5-0ubuntu0.1                      plugins for Marble
ii  mawk                                          1.3.3-17                                a pattern scanning and text processing language
ii  media-player-info                             16-1                                    Media player identification files
ii  melt                                          0.7.6+git20120204-2                     command line media player and video editor
ii  memtest86+                                    4.20-1.1ubuntu1                         thorough real-mode memory tester
ii  mencoder                                      2:1.0~rc4.dfsg1+svn34540-1              MPlayer's Movie Encoder
ii  mime-support                                  3.51-1ubuntu1                           MIME files 'mime.types' & 'mailcap', and support programs
ii  miscfiles                                     1.4.2.dfsg.1-9                          Dictionaries and other interesting files
ii  mlocate                                       0.23.1-1ubuntu2                         quickly find files on the filesystem based on their name
ii  mobile-broadband-provider-info                20120410-0ubuntu1                       database of mobile broadband service providers
ii  modemmanager                                  0.5.2.0-0ubuntu2                        D-Bus service for managing modems
ii  module-init-tools                             3.16-1ubuntu2                           tools for managing Linux kernel modules
ii  mono-4.0-gac                                  2.10.8.1-1ubuntu2.2                     Mono GAC tool (for CLI 4.0)
ii  mono-gac                                      2.10.8.1-1ubuntu2.2                     Mono GAC tool
ii  mono-runtime                                  2.10.8.1-1ubuntu2.2                     Mono runtime
ii  mount                                         2.20.1-1ubuntu3                         Tools for mounting and manipulating filesystems
ii  mountall                                      2.36                                    filesystem mounting tool
ii  mpg321                                        0.2.13-4ubuntu1                         Simple and lightweight command line MP3 player
ii  mplayer                                       2:1.0~rc4.dfsg1+svn34540-1              movie player for Unix-like systems
ii  mscompress                                    0.3-3.1                                 Microsoft "compress.exe/expand.exe" compatible (de)compressor
ii  mtools                                        4.0.12-1                                Tools for manipulating MSDOS files
ii  mtr-tiny                                      0.80-1ubuntu1                           Full screen ncurses traceroute tool
ii  multiarch-support                             2.15-0ubuntu10.3                        Transitional package to ensure multiarch compatibility
ii  mysql-common                                  5.5.28-0ubuntu0.12.04.3                 MySQL database common files, e.g. /etc/mysql/my.cnf
ii  nano                                          2.2.6-1                                 small, friendly text editor inspired by Pico
ii  nautilus                                      1:3.4.2-0ubuntu5                        file manager and graphical shell for GNOME
ii  nautilus-data                                 1:3.4.2-0ubuntu5                        data files for nautilus
ii  nautilus-sendto                               3.0.1-2ubuntu2                          integrates Evolution and Pidgin into the Nautilus file manager
ii  ncurses-base                                  5.9-4                                   basic terminal type definitions
ii  ncurses-bin                                   5.9-4                                   terminal-related programs and man pages
ii  net-tools                                     1.60-24.1ubuntu2                        The NET-3 networking toolkit
ii  netbase                                       4.47ubuntu1                             Basic TCP/IP networking system
ii  netcat-openbsd                                1.89-4ubuntu1                           TCP/IP swiss army knife
ii  netpbm                                        2:10.0-15                               Graphics conversion tools between image formats
ii  network-manager                               0.9.4.0-0ubuntu4.1                      network management framework (daemon and userspace tools)
ii  network-manager-gnome                         0.9.4.1-0ubuntu2                        network management framework (GNOME frontend)
ii  network-manager-pptp                          0.9.4.0-0ubuntu1                        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                    0.9.4.0-0ubuntu1                        network management framework (PPTP plugin GNOME GUI)
ii  ntfs-3g                                       1:2012.1.15AR.1-1ubuntu1.2              read/write NTFS driver for FUSE
ii  ntpdate                                       1:4.2.6.p3+dfsg-1ubuntu3.1              client for setting system time from NTP servers
ii  ntrack-module-libnl-0                         016-1ubuntu1                            libnl based ntrack module
ii  numlockx                                      1.2-2                                   enable NumLock in X11 sessions
ii  nvidia-common                                 1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  obex-data-server                              0.4.6-0ubuntu1                          D-Bus service for OBEX client and server side functionality
ii  odbcinst                                      2.2.14p2-5ubuntu3                       Helper program for accessing odbc ini files
ii  odbcinst1debian2                              2.2.14p2-5ubuntu3                       Support library for accessing odbc ini files
rc  onboard                                       0.97.0-0ubuntu4                         Simple On-screen Keyboard
ii  oneconf                                       0.2.8.1                                 synchronize your configuration data over the network
ii  openjdk-6-jre                                 6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                        6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                             6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime (architecture independent libraries)
ii  openprinting-ppds                             20120322-0ubuntu1                       OpenPrinting printer support - PostScript PPD files
ii  openshot                                      1.4.0-1ubuntu1                          Create and edit videos and movies
ii  openshot-doc                                  1.4.0-1ubuntu1                          Help manual for OpenShot Video Editor
ii  openssh-client                                1:5.9p1-5ubuntu1                        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                                1:5.9p1-5ubuntu1                        secure shell (SSH) server, for secure access from remote machines
ii  openssl                                       1.0.1-4ubuntu5.5                        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  os-prober                                     1.51ubuntu3                             utility to detect other OSes on a set of drives
ii  oxygen-icon-theme                             4:4.8.3-0ubuntu0.1                      Oxygen icon theme
ii  p7zip-full                                    9.20.1~dfsg.1-4                         7z and 7za file archivers with high compression ratio
ii  parley                                        4:4.8.5-0ubuntu0.1                      vocabulary trainer for KDE
ii  parley-data                                   4:4.8.5-0ubuntu0.1                      data files for the Parley vocabulary trainer
ii  parted                                        2.3-8ubuntu5.1                          disk partition manipulator
ii  passwd                                        1:4.1.4.2+svn3283-3ubuntu5.1            change and administer password and group data
ii  pastebinit                                    1.3-2ubuntu2.1                          command-line pastebin client
ii  patch                                         2.6.1-3                                 Apply a diff file to an original
ii  pavucontrol                                   0.99.2-1build1                          PulseAudio Volume Control
ii  pbis-open                                     7.0.1.918                               Authentication services for Active Directory domains
ii  pbis-open-gui                                 7.0.1.918                               Desktop utility for joining Active Directory domains
ii  pbis-open-legacy                              7.0.1.918                               Provides symbolic links from the older command names and paths in Likewise Open to the new names and paths in PowerBroker Identity Services Open.
ii  pciutils                                      1:3.1.8-2ubuntu5                        Linux PCI Utilities
ii  pcmciautils                                   018-6                                   PCMCIA utilities for Linux 2.6
ii  perl                                          5.14.2-6ubuntu2.2                       Larry Wall's Practical Extraction and Report Language
ii  perl-base                                     5.14.2-6ubuntu2.2                       minimal Perl system
ii  perl-modules                                  5.14.2-6ubuntu2.2                       Core Perl modules
ii  perlmagick                                    8:6.6.9.7-5ubuntu3.2                    Perl interface to the ImageMagick graphics routines
ii  phonon                                        4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - metapackage
ii  phonon-backend-gstreamer                      4:4.7.0really4.6.2-0ubuntu0.1           Phonon GStreamer 0.10.x backend
rc  pidgin                                        1:2.10.3-0ubuntu1.1                     graphical multi-protocol instant messaging client for X
ii  pidgin-data                                   1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging client - data files
ii  pidgin-microblog                              0.3.0-3                                 Microblogging plugins for Pidgin
ii  pitivi                                        0.15.2-0ubuntu0.1                       non-linear audio/video editor using GStreamer
ii  pkg-config                                    0.26-1ubuntu1                           manage compile and link flags for libraries
ii  plasma-scriptengine-javascript                4:4.8.5-0ubuntu0.1                      JavaScript script engine for Plasma
ii  plymouth                                      0.8.2-2ubuntu30                         graphical boot animation and logger - main package
ii  plymouth-label                                0.8.2-2ubuntu30                         graphical boot animation and logger - label control
ii  plymouth-theme-ubuntu-text                    0.8.2-2ubuntu30                         graphical boot animation and logger - ubuntu-logo theme
ii  plymouth-theme-xubuntu-logo                   12.04.11                                graphical boot animation and logger - xubuntu-logo theme
ii  plymouth-theme-xubuntu-text                   12.04.11                                graphical boot animation and logger - xubuntu-text theme
ii  pm-utils                                      1.4.1-9                                 utilities and scripts for power management
ii  policykit-1                                   0.104-1ubuntu1                          framework for managing administrative policies and privileges
ii  policykit-1-gnome                             0.105-1ubuntu3.1                        GNOME authentication agent for PolicyKit-1
ii  policykit-desktop-privileges                  0.10                                    run common desktop actions without password
ii  poppler-data                                  0.4.5-2                                 Encoding data for the poppler PDF rendering library
ii  poppler-utils                                 0.18.4-1ubuntu3                         PDF utilities (based on Poppler)
ii  popularity-contest                            1.53ubuntu1                             Vote for your favourite packages automatically
ii  powermgmt-base                                1.31                                    Common utils and configs for power management
ii  ppp                                           2.4.5-5ubuntu1                          Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                                     2.3.18+nmu3ubuntu1                      A text menu based utility for configuring ppp
ii  pppoeconf                                     1.20ubuntu1                             configures PPPoE/ADSL connections
ii  pptp-linux                                    1.7.2-6                                 Point-to-Point Tunneling Protocol (PPTP) Client
ii  printer-driver-c2esp                          23-1                                    printer driver for Kodak ESP AiO color inkjet Series
ii  printer-driver-foo2zjs                        20111202dfsg0-1ubuntu1                  printer driver for ZjStream-based printers
ii  printer-driver-gutenprint                     5.2.8~pre1-0ubuntu2.1                   printer drivers for CUPS
ii  printer-driver-hpcups                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  printer-driver-hpijs                          3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - gs IJS driver (hpijs)
ii  printer-driver-min12xxw                       0.0.9-6ubuntu1                          printer driver for KonicaMinolta PagePro 1[234]xxW
ii  printer-driver-pnm2ppa                        1.13+nondbs-0ubuntu1                    printer driver for HP-GDI printers
ii  printer-driver-postscript-hp                  3.12.2-1ubuntu3.1                       HP Printers PostScript Descriptions
ii  printer-driver-ptouch                         1.3-3ubuntu0.1                          printer driver Brother P-touch label printers
ii  printer-driver-pxljr                          1.3+repack0-2                           printer driver for HP Color LaserJet 35xx/36xx
ii  printer-driver-sag-gdi                        0.1-3                                   printer driver for Ricoh Aficio SP 1000s/SP 1100s
ii  printer-driver-splix                          2.0.0+svn300-1.1ubuntu2                 Driver for Samsung and Xerox SPL2 and SPLc laser printers
ii  procps                                        1:3.2.8-11ubuntu6                       /proc file system utilities
ii  psmisc                                        22.15-2ubuntu1.1                        utilities that use the proc file system
ii  pulseaudio                                    1:1.1-0ubuntu15.1                       PulseAudio sound server
ii  pulseaudio-module-x11                         1:1.1-0ubuntu15.1                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                              1:1.1-0ubuntu15.1                       Command line tools for the PulseAudio sound server
ii  puppet                                        3.0.1-1puppetlabs1                      Centralized configuration management - agent startup and compatibility scripts
ii  puppet-common                                 3.0.1-1puppetlabs1                      Centralized configuration management
ii  python                                        2.7.3-0ubuntu2                          interactive high-level object-oriented language (default version)
ii  python-appindicator                           0.4.92-0ubuntu1                         Python bindings for libappindicator
ii  python-apport                                 2.0.1-0ubuntu15.1                       apport crash report handling library
ii  python-apt                                    0.8.3ubuntu7                            Python interface to libapt-pkg
ii  python-apt-common                             0.8.3ubuntu7                            Python interface to libapt-pkg (locales)
ii  python-aptdaemon                              0.43+bzr805-0ubuntu7                    Python module for the server and client of aptdaemon
ii  python-aptdaemon.gtk3widgets                  0.43+bzr805-0ubuntu7                    Python GTK+ 3 widgets to run an aptdaemon client
ii  python-avogadro                               1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Python module)
ii  python-cairo                                  1.8.8-1ubuntu3                          Python bindings for the Cairo vector graphics library
ii  python-chardet                                2.0.1-2build1                           universal character encoding detector
ii  python-configobj                              4.7.2+ds-3build1                        simple but powerful config file reader and writer for Python
ii  python-crypto                                 2.4.1-1ubuntu0.1                        cryptographic algorithms and protocols for Python
ii  python-cups                                   1.9.61-0ubuntu2                         Python bindings for CUPS
ii  python-cupshelpers                            1.3.8+20120201-0ubuntu8.1               Python modules for printer configuration with CUPS
ii  python-dbus                                   1.0.0-1ubuntu1                          simple interprocess messaging system (Python interface)
ii  python-dbus-dev                               1.0.0-1ubuntu1                          main loop integration development files for python-dbus
ii  python-debian                                 0.1.21ubuntu1                           Python modules to work with Debian-related data formats
ii  python-debtagshw                              1.9+git20120320-0ubuntu1                Match debtags hardware:: tags against the actual hardware
ii  python-defer                                  1.0.2+bzr481-1                          Small framework for asynchronous programming
ii  python-gconf                                  2.28.1+dfsg-1                           Python bindings for the GConf configuration database system
ii  python-gdbm                                   2.7.3-1ubuntu1                          GNU dbm database support for Python
ii  python-gi                                     3.2.2-1~precise                         Python 2.x bindings for gobject-introspection libraries
ii  python-gi-cairo                               3.2.2-1~precise                         Python Cairo bindings for the GObject library
ii  python-glade2                                 2.24.0-3                                GTK+ bindings: Glade support
ii  python-gmenu                                  3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  python-gnomekeyring                           2.32.0+dfsg-1                           Python bindings for the GNOME keyring library
ii  python-gnupginterface                         0.3.2-9.1ubuntu3                        Python interface to GnuPG (GPG)
ii  python-gobject                                3.2.2-1~precise                         Python 2.x bindings for GObject - transitional package
ii  python-gobject-2                              2.28.6-10ubuntu1                        deprecated static Python bindings for the GObject library
ii  python-gst0.10                                0.10.22-3ubuntu0.1                      generic media-playing framework (Python bindings)
ii  python-gtk2                                   2.24.0-3                                Python bindings for the GTK+ widget set
ii  python-httplib2                               0.7.2-1ubuntu2                          comprehensive HTTP client library written for Python
ii  python-ibus                                   1.4.1-3ubuntu1                          Intelligent Input Bus - Python support
ii  python-imaging                                1.1.7-4                                 Python Imaging Library
ii  python-keyring                                0.9.2-0ubuntu0.12.04.2                  store and access your passwords safely
ii  python-launchpad-integration                  0.1.56.1                                library for launchpad integration
ii  python-launchpadlib                           1.9.12-1                                Launchpad web services client library
ii  python-lazr.restfulclient                     0.12.0-1ubuntu1                         client for lazr.restful-based web services
ii  python-lazr.uri                               1.0.3-1                                 library for parsing, manipulating, and generating URIs
ii  python-libxml2                                2.7.8.dfsg-5.1ubuntu4.3                 Python bindings for the GNOME XML library
ii  python-lxml                                   2.3.2-1                                 pythonic binding for the libxml2 and libxslt libraries
ii  python-mako                                   0.5.0-1                                 fast and lightweight templating for the Python platform
ii  python-markupsafe                             0.15-1                                  XML/HTML/XHTML Markup safe string for Python
ii  python-minimal                                2.7.3-0ubuntu2                          minimal subset of the Python language (default version)
ii  python-mlt3                                   0.7.6+git20120204-2                     multimedia framework (python bindings)
ii  python-notify                                 0.1.1-3                                 Python bindings for libnotify
ii  python-numpy                                  1:1.6.1-6ubuntu1                        Numerical Python adds a fast array facility to the Python language
ii  python-oauth                                  1.0.1-3build1                           Python library implementing of the OAuth protocol
ii  python-openssl                                0.12-1ubuntu2                           Python wrapper around the OpenSSL library
ii  python-pam                                    0.4.2-12.2ubuntu4                       A Python interface to the PAM library
ii  python-pexpect                                2.3-1ubuntu2                            Python module for automating interactive applications
ii  python-piston-mini-client                     0.7.2+bzr57-0ubuntu1                    library for writing clients for Django's Piston REST APIs
ii  python-pkg-resources                          0.6.24-1ubuntu1                         Package Discovery and Resource Access using pkg_resources
ii  python-problem-report                         2.0.1-0ubuntu15.1                       Python library to handle problem reports
ii  python-pycurl                                 7.19.0-4ubuntu3                         Python bindings to libcurl
ii  python-pygoocanvas                            0.14.1-1ubuntu6                         GooCanvas Python bindings
ii  python-qt4                                    4.9.1-2ubuntu1                          Python bindings for Qt4
ii  python-renderpm                               2.5-1.1build1                           python low level render interface
ii  python-reportlab                              2.5-1.1build1                           ReportLab library to create PDF documents using Python
ii  python-reportlab-accel                        2.5-1.1build1                           C coded extension accelerator for the ReportLab Toolkit
ii  python-serial                                 2.5-2.1build1                           pyserial - module encapsulating access for the serial port
ii  python-simplejson                             2.3.2-1                                 simple, fast, extensible JSON encoder/decoder for Python
ii  python-sip                                    4.13.2-1                                Python/C++ bindings generator runtime library
ii  python-smbc                                   1.0.13-0ubuntu1                         Python bindings for Samba clients (libsmbclient)
ii  python-software-properties                    0.82.7.3                                manage the repositories that you install software from
ii  python-support                                1.0.14ubuntu2                           automated rebuilding support for Python modules
ii  python-tk                                     2.7.3-1ubuntu1                          Tkinter - Writing Tk applications with Python
ii  python-twisted-bin                            11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-core                           11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-web                            11.1.0-1                                HTTP protocol implementation together with clients and servers
ii  python-ubuntu-sso-client                      3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - Python library
ii  python-uniconvertor                           1.1.4-1ubuntu1                          Universal vector graphics translator
ii  python-uno                                    1:3.5.4-0ubuntu1.1                      Python-UNO bridge
ii  python-virtkey                                0.60.0-0ubuntu5                         Library to emulate keyboard keypresses.
ii  python-wadllib                                1.3.0-2                                 Python library for navigating WADL files
ii  python-xapian                                 1.2.8-1                                 Xapian search engine interface for Python
ii  python-xdg                                    0.19-3ubuntu2                           Python library to access freedesktop.org standards
ii  python-xkit                                   0.4.2.3build1                           library for the manipulation of the xorg.conf
ii  python-zeitgeist                              0.9.0-1ubuntu1                          event logging framework - Python bindings
ii  python-zope.interface                         3.6.1-1ubuntu3                          Interfaces for Python
ii  python2.7                                     2.7.3-0ubuntu3.1                        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                             2.7.3-0ubuntu3.1                        Minimal subset of the Python language (version 2.7)
ii  python3.2                                     3.2.3-0ubuntu3.2                        Interactive high-level object-oriented language (version 3.2)
ii  python3.2-minimal                             3.2.3-0ubuntu3.2                        Minimal subset of the Python language (version 3.2)
ii  qapt-batch                                    1.3.1-0ubuntu2                          Batch package manager for KDE
ii  qdbus                                         4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus tool
ii  radeontool                                    1.6.2-1.1                               utility to control ATI Radeon backlight functions on laptops
ii  rarian-compat                                 0.8.1-5                                 Documentation meta-data library (compatibility tools)
ii  readline-common                               6.2-8                                   GNU readline and history libraries, common files
ii  resolvconf                                    1.63ubuntu16                            name server information handler
ii  rfkill                                        0.4-1ubuntu2                            tool for enabling and disabling wireless devices
ii  rhythmbox                                     2.96-0ubuntu4.2                         music player and organizer for GNOME
ii  rhythmbox-data                                2.96-0ubuntu4.2                         data files for rhythmbox
ii  rhythmbox-mozilla                             2.96-0ubuntu4.2                         Rhythmbox Mozilla plugin
ii  rhythmbox-plugin-cdrecorder                   2.96-0ubuntu4.2                         burning plugin for rhythmbox music player
ii  rhythmbox-plugin-zeitgeist                    2.96-0ubuntu4.2                         zeitgeist plugin for rhythmbox music player
ii  rhythmbox-plugins                             2.96-0ubuntu4.2                         plugins for rhythmbox music player
ii  ristretto                                     0.3.6-0ubuntu1                          lightweight picture-viewer for the Xfce desktop environment
ii  rsync                                         3.0.9-1ubuntu1                          fast, versatile, remote (and local) file-copying tool
ii  rsyslog                                       5.8.6-1ubuntu8                          reliable system and kernel logging daemon
ii  rtkit                                         0.10-2                                  Realtime Policy and Watchdog Daemon
ii  ruby                                          4.8                                     Transitional package for ruby1.8
ii  ruby-json                                     1.6.3-1                                 JSON library for Ruby
ii  ruby1.8                                       1.8.7.352-2ubuntu1.1                    Interpreter of object-oriented scripting language Ruby 1.8
ii  samba-common                                  2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  samba-common-bin                              2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  sane-utils                                    1.0.22-7ubuntu1                         API library for scanners -- utilities
ii  screensaver-default-images                    0.2-1                                   Wallpapers for image processing screensavers
ii  scribus                                       1.4.0.dfsg+r17300-1ubuntu1              Open Source Desktop Page Layout - stable branch
ii  sed                                           4.2.1-9                                 The GNU sed stream editor
ii  sensible-utils                                0.0.6ubuntu2                            Utilities for sensible alternative selection
ii  sessioninstaller                              0.20+bzr128-0ubuntu1.2                  APT based installer using PackageKit's session DBus API
ii  sgml-base                                     1.26+nmu1ubuntu1                        SGML infrastructure and SGML catalog file support
ii  sgml-data                                     2.0.6                                   common SGML and XML data
ii  shared-desktop-ontologies                     0.8.1-1                                 shared ontologies for semantic searching
ii  shared-mime-info                              1.0-0ubuntu4.1                          FreeDesktop.org shared MIME database and spec
ii  shimmer-themes                                1.3.0-0ubuntu1                          Gtk+ themes from Shimmer Project
ii  simple-scan                                   3.4.1-0ubuntu1.1                        Simple Scanning Utility
ii  smbclient                                     2:3.6.3-2ubuntu2.3                      command-line SMB/CIFS clients for Unix
ii  software-center                               5.2.6                                   Utility for browsing, installing, and removing software
ii  software-center-aptdaemon-plugins             0.1.2                                   The aptdaemon plugins for software-center
ii  software-properties-common                    0.82.7.3                                manage the repositories that you install software from (common)
ii  software-properties-gtk                       0.82.7.3                                manage the repositories that you install software from (gtk)
ii  soprano-daemon                                2.7.5+dfsg.1-0ubuntu1                   daemon for the Soprano RDF framework
ii  sound-theme-freedesktop                       0.7.pristine-2                          freedesktop.org sound theme
ii  speech-dispatcher                             0.7.1-6ubuntu3                          Common interface to speech synthesizers
ii  ssh-import-id                                 2.10-0ubuntu1                           securely retrieve an SSH public key and install it locally
ii  ssl-cert                                      1.0.28ubuntu0.1                         simple debconf wrapper for OpenSSL
ii  step                                          4:4.8.5-0ubuntu0.1                      interactive physical simulator for KDE
ii  strace                                        4.5.20-2.3ubuntu1                       A system call tracer
ii  sudo                                          1.8.3p1-1ubuntu3.3                      Provide limited super user privileges to specific users
ii  synaptic                                      0.75.9ubuntu1                           Graphical package manager
ii  syslinux                                      2:4.05+dfsg-2                           collection of boot loaders
ii  syslinux-common                               2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies
ii  system-config-printer-common                  1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-gnome                   1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-udev                    1.3.8+20120201-0ubuntu8.1               Printer auto-configuration facility based on udev
ii  system-tools-backends                         2.10.2-1ubuntu1                         System Tools to manage computer configuration -- scripts
ii  sysv-rc                                       2.88dsf-13.10ubuntu11.1                 System-V-like runlevel change mechanism
ii  sysvinit-utils                                2.88dsf-13.10ubuntu11.1                 System-V-like utilities
ii  tar                                           1.26-4ubuntu1                           GNU version of the tar archiving utility
ii  tcl8.5                                        8.5.11-1ubuntu1                         Tcl (the Tool Command Language) v8.5 - run-time files
ii  tcpd                                          7.6.q-21                                Wietse Venema's TCP wrapper utilities
ii  tcpdump                                       4.2.1-1ubuntu2                          command-line network traffic analyzer
ii  telnet                                        0.17-36build1                           The telnet client
ii  thunar                                        1.2.3-3ubuntu2                          File Manager for Xfce
ii  thunar-archive-plugin                         0.3.0-4                                 Archive plugin for Thunar file manager
ii  thunar-data                                   1.2.3-3ubuntu2                          Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                      0.2.0-1                                 Media tags plugin for Thunar file manager
ii  thunar-volman                                 0.6.1-0ubuntu1                          Thunar extension for volumes management
rc  thunderbird                                   16.0.2+build1-0ubuntu0.12.04.1          Email, RSS and newsgroup client with integrated spam filter
ii  tilem                                         0.973-1                                 TilEm, a TI 83+ emulator
ii  time                                          1.7-23.1                                The GNU time program for measuring cpu resource usage
ii  tk8.5                                         8.5.11-1                                Tk toolkit for Tcl and X11, v8.5 - run-time files
ii  toshset                                       1.76-2                                  Access much of the Toshiba laptop hardware interface
rc  transmission-gtk                              2.51-0ubuntu1                           lightweight BitTorrent client (GTK interface)
ii  tree                                          1.5.3-2                                 displays directory tree, in color
ii  tsconf                                        1.0-10                                  touch screen library common files
ii  ttf-dejavu                                    2.33-2ubuntu1                           Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra
ii  ttf-dejavu-core                               2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-dejavu-extra                              2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-droid                                     20101110+git-2                          transitional dummy package
ii  ttf-freefont                                  20100919-1                              Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                          1:0.5.11ubuntu1                         Core collection of free fonts for languages of India
ii  ttf-lyx                                       2.0.2-1ubuntu2                          TrueType versions of some TeX fonts
ii  ttf-mscorefonts-installer                     3.4ubuntu3                              Installer for Microsoft TrueType core fonts
ii  ttf-punjabi-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Punjabi language
ii  ttf-sil-gentium-basic                         1.1-5                                   transitional dummy package
ii  ttf-ubuntu-font-family                        0.80-0ubuntu2                           Ubuntu Font Family, sans-serif typeface hinted for clarity
ii  ttf-umefont                                   434-1                                   transitional dummy package
ii  ttf-unfonts-core                              1.0.3.is.1.0.2-080608-5ubuntu1          transitional dummy package
ii  ttf-wqy-microhei                              0.2.0-beta-1ubuntu1                     A droid derived Sans-Seri style CJK font
ii  tumbler                                       0.1.24-0ubuntu1                         D-Bus thumbnailing service
ii  tumbler-common                                0.1.24-0ubuntu1                         D-Bus thumbnailing service (common files)
ii  tzdata                                        2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data
ii  tzdata-java                                   2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data for use by java runtimes
ii  ubuntu-extras-keyring                         2010.09.27                              GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring                                2011.11.21.1                            GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                                1.267                                   Minimal core of Ubuntu
ii  ubuntu-restricted-addons                      12                                      Commonly used restricted packages for Ubuntu
ii  ubuntu-sso-client                             3.0.2-0ubuntu3                          Ubuntu Single Sign-On client
ii  ubuntu-sso-client-gtk                         3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - GTK+ frontend
ii  ubuntu-standard                               1.267                                   The Ubuntu standard system
ii  ucf                                           3.0025+nmu2ubuntu1                      Update Configuration File: preserve user changes to config files.
ii  udev                                          175-0ubuntu9.2                          rule-based device node and kernel event manager
ii  udisks                                        1.0.4-5ubuntu2.1                        storage media interface
ii  ufw                                           0.31.1-1                                program for managing a Netfilter firewall
ii  unattended-upgrades                           0.76                                    automatic installation of security upgrades
ii  unixodbc                                      2.2.14p2-5ubuntu3                       Basic ODBC tools
ii  uno-libs3                                     3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment -- public shared libraries
ii  unrar                                         1:4.0.3-1                               Unarchiver for .rar files (non-free version)
ii  unzip                                         6.0-4ubuntu1                            De-archiver for .zip files
ii  update-inetd                                  4.41                                    inetd configuration file updater
ii  update-manager                                1:0.156.14.11                           GNOME application that manages apt updates
ii  update-manager-core                           1:0.156.14.11                           manage release upgrades
ii  update-notifier                               0.119ubuntu8.6                          Daemon which notifies about package updates
ii  update-notifier-common                        0.119ubuntu8.6                          Files shared between update-notifier and other packages
ii  upower                                        0.9.15-3git1                            abstraction for power management
ii  upstart                                       1.5-0ubuntu7                            event-based init daemon
ii  ure                                           3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment
ii  ureadahead                                    0.100.0-12                              Read required files in advance
ii  usb-creator-common                            0.2.38                                  create a startup disk using a CD or disc image (common files)
ii  usb-creator-gtk                               0.2.38                                  create a startup disk using a CD or disc image (for GNOME)
ii  usb-modeswitch                                1.2.3+repack0-1ubuntu2                  mode switching tool for controlling "flip flop" USB devices
ii  usb-modeswitch-data                           20120120-0ubuntu1                       mode switching data for usb-modeswitch
ii  usbmuxd                                       1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices
ii  usbutils                                      1:005-1                                 Linux USB utilities
ii  util-linux                                    2.20.1-1ubuntu3                         Miscellaneous system utilities
ii  uuid-runtime                                  2.20.1-1ubuntu3                         runtime components for the Universally Unique ID library
ii  vbetool                                       1.1-2ubuntu1                            run real-mode video BIOS code to alter hardware state
ii  vcdimager                                     0.7.23-4.1ubuntu1                       A VideoCD (VCD) image mastering and ripping tool
ii  vim-common                                    2:7.3.429-2ubuntu2.1                    Vi IMproved - Common files
ii  vim-tiny                                      2:7.3.429-2ubuntu2.1                    Vi IMproved - enhanced vi editor - compact version
ii  virtuoso-minimal                              6.1.4+dfsg1-0ubuntu1                    high-performance database - core dependency package
ii  virtuoso-opensource-6.1-bin                   6.1.4+dfsg1-0ubuntu1                    high-performance database - binaries
ii  virtuoso-opensource-6.1-common                6.1.4+dfsg1-0ubuntu1                    high-performance database - common files
ii  vlc                                           2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer
ii  vlc-data                                      2.0.3-0ubuntu0.12.04.1                  Common data for VLC
ii  vlc-nox                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer (without X support)
ii  vlc-plugin-notify                             2.0.3-0ubuntu0.12.04.1                  LibNotify plugin for VLC
ii  vlc-plugin-pulse                              2.0.3-0ubuntu0.12.04.1                  PulseAudio plugin for VLC
ii  vym                                           2.0.3-1                                 mindmapping tool
ii  wamerican                                     7.1-1                                   American English dictionary words for /usr/share/dict
ii  wbritish                                      7.1-1                                   British English dictionary words for /usr/share/dict
ii  wget                                          1.13.4-2ubuntu1                         retrieves files from the web
ii  whiptail                                      0.52.11-2ubuntu10                       Displays user-friendly dialog boxes from shell scripts
rc  winbind                                       2:3.6.3-2ubuntu2.3                      Samba nameservice integration server
ii  wine                                          1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (meta-package)
ii  wine-gecko1.4                                 1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine1.4                                       1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.4-common                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4-i386                                  1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                                    0.0+20120308                            Microsoft Windows Compatibility Layer (winetricks)
ii  wireless-regdb                                2011.04.28-1ubuntu3                     wireless regulatory database
ii  wireless-tools                                30~pre9-5ubuntu2                        Tools for manipulating Linux Wireless Extensions
ii  wodim                                         9:1.1.11-2ubuntu2                       command line CD/DVD writing tool
ii  wordnet                                       1:3.0-26.1                              electronic lexical database of English language
ii  wordnet-base                                  1:3.0-26.1                              electronic lexical database of English language (base data)
ii  wordnet-sense-index                           1:3.0-26.1                              electronic lexical database of English language (index.sense)
ii  wpasupplicant                                 0.7.3-6ubuntu2.1                        client support for WPA and WPA2 (IEEE 802.11i)
ii  x11-apps                                      7.6+5ubuntu1                            X applications
ii  x11-common                                    1:7.6+12ubuntu1                         X Window System (X.Org) infrastructure
ii  x11-session-utils                             7.6+2                                   X session utilities
ii  x11-utils                                     7.6+4ubuntu0.1                          X11 utilities
ii  x11-xfs-utils                                 7.6+1                                   X font server utilities
ii  x11-xkb-utils                                 7.6+4                                   X11 XKB utilities
ii  x11-xserver-utils                             7.6+3                                   X server utilities
ii  xauth                                         1:1.0.6-1                               X authentication utility
ii  xbitmaps                                      1.1.1-1                                 Base X bitmaps
rc  xchat                                         2.8.8-3ubuntu12                         IRC client for X similar to AmIRC
ii  xchat-common                                  2.8.8-3ubuntu12                         Common files for X-Chat
ii  xcursor-themes                                1.0.3-1                                 Base X cursor themes
ii  xdg-user-dirs                                 0.14-0ubuntu2                           tool to manage well known user directories
ii  xdg-user-dirs-gtk                             0.9-0ubuntu1                            tool to manage well known user directories (Gtk extension)
ii  xdg-utils                                     1.1.0~rc1-2ubuntu6                      desktop integration utilities from freedesktop.org
ii  xfce-keyboard-shortcuts                       4.8.1-1                                 xfce keyboard shortcuts configuration
ii  xfce4-appfinder                               4.8.0-3                                 Application finder for the Xfce4 Desktop Environment
ii  xfce4-cpugraph-plugin                         1.0.1-2                                 CPU load graph plugin for the Xfce4 panel
ii  xfce4-datetime-plugin                         0.6.1-3ubuntu1                          date and time plugin for the Xfce4 panel
ii  xfce4-dict                                    0.6.0-5                                 Dictionary plugin for Xfce4 panel
ii  xfce4-indicator-plugin                        0.4.0-0ubuntu2                          plugin to display information from applications in the Xfce4 panel
ii  xfce4-mailwatch-plugin                        1.1.0-5                                 mail watcher plugin for the Xfce4 panel
ii  xfce4-netload-plugin                          1.1.0-1                                 network load monitor plugin for the Xfce4 panel
ii  xfce4-notes                                   1.7.7-2ubuntu1                          Notes application for the Xfce4 desktop
ii  xfce4-notes-plugin                            1.7.7-2ubuntu1                          Notes plugin for the Xfce4 desktop
ii  xfce4-notifyd                                 0.2.2-1                                 simple, visually-appealing notification daemon for Xfce
ii  xfce4-panel                                   4.8.6-2ubuntu2                          panel for Xfce4 desktop environment
ii  xfce4-places-plugin                           1.2.0-3                                 quick access to folders, documents and removable media
ii  xfce4-power-manager                           1.0.11-0ubuntu2                         power manager for Xfce desktop
ii  xfce4-power-manager-data                      1.0.11-0ubuntu2                         power manager for Xfce desktop, arch-indep files
ii  xfce4-quicklauncher-plugin                    1.9.4-9                                 rapid launcher plugin for the Xfce4 panel
ii  xfce4-screenshooter                           1.8.0-2                                 screenshots utility for Xfce
ii  xfce4-session                                 4.8.3-0ubuntu2                          Xfce4 Session Manager
ii  xfce4-settings                                4.8.3-1ubuntu3                          graphical application for managing Xfce settings
ii  xfce4-systemload-plugin                       1:1.0.0-1ubuntu1                        system load monitor plugin for the Xfce4 panel
ii  xfce4-taskmanager                             1.0.0-2                                 process manager for the Xfce4 Desktop Environment
ii  xfce4-terminal                                0.4.8-1ubuntu1                          Xfce terminal emulator
ii  xfce4-utils                                   4.8.3-1ubuntu2                          Various tools for Xfce
ii  xfce4-verve-plugin                            1.0.0-1                                 Verve (command line) plugin for Xfce panel
ii  xfce4-volumed                                 0.1.13-2ubuntu1                         volume keys daemon
ii  xfce4-weather-plugin                          0.7.4-3                                 weather information plugin for the Xfce4 panel
ii  xfce4-xkb-plugin                              0.5.4.3-1ubuntu1                        xkb layout switch plugin for the Xfce4 panel
ii  xfconf                                        4.8.1-1                                 utilities for managing settings in Xfce
ii  xfdesktop4                                    4.8.3-2ubuntu7                          xfce desktop background, icons and root menu manager
ii  xfdesktop4-data                               4.8.3-2ubuntu7                          xfce desktop background, icons and root menu (common files)
ii  xfonts-base                                   1:1.0.3                                 standard fonts for X
ii  xfonts-encodings                              1:1.0.4-1ubuntu1                        Encodings for X.Org fonts
ii  xfonts-mathml                                 4ubuntu1                                Type1 Symbol font for MathML
ii  xfonts-scalable                               1:1.0.3-1                               scalable fonts for X
ii  xfonts-utils                                  1:7.6+1                                 X Window System font utility programs
ii  xfwm4                                         4.8.3-1ubuntu1.1                        window manager of the Xfce project
ii  xinit                                         1.3.1-1                                 X server initialisation tool
ii  xinput                                        1.5.99.1-0ubuntu2                       Runtime configuration and test of XInput devices
ii  xkb-data                                      2.5-1ubuntu1.3                          X Keyboard Extension (XKB) configuration data
ii  xml-core                                      0.13                                    XML infrastructure and XML catalog file support
ii  xorg                                          1:7.6+12ubuntu1                         X.Org X Window System
ii  xorg-docs-core                                1:1.6-1ubuntu2                          Core documentation for the X.org X Window System
ii  xplanet                                       1.2.1-4.1                               planetary body renderer
ii  xplanet-images                                1.2.1-4.1                               imagery for xplanet
rc  xscreensaver                                  5.15-2ubuntu1                           Automatic screensaver for X
ii  xscreensaver-data                             5.15-2ubuntu1                           data files to be shared among screensaver frontends
ii  xscreensaver-gl                               5.15-2ubuntu1                           GL(Mesa) screen hacks for xscreensaver
ii  xserver-common                                2:1.11.4-0ubuntu10.8                    common files used by various X servers
ii  xserver-xorg                                  1:7.6+12ubuntu1                         X.Org X server
ii  xserver-xorg-core                             2:1.11.4-0ubuntu10.8                    Xorg X server - core server
ii  xserver-xorg-input-all                        1:7.6+12ubuntu1                         X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                      1:2.7.0-0ubuntu1.2                      X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                      1:1.7.1-1build3                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics                  1.6.2-1ubuntu1~precise2                 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                    1:12.9.0-0ubuntu0.1                     X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                      1:0.14.0-0ubuntu2.1                     X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                        1:7.6+12ubuntu1                         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                        1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus                     1:1.3.2-4build1                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                      1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                      2.11.13-2build1                         X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel                      2:2.17.0-1ubuntu4.2                     X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                     6.9.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                        1:1.4.13.dfsg-4build2                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                   1:1.2.5-2build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau                    1:0.0.16+git20111201+b5534a1-1build2    X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome                 1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                        0.0.16-2                                X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                       6.8.1-5build2                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                     1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                         1:0.6.3-4build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage                     1:2.3.3-1ubuntu1                        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion              1:1.7.5-1build2                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                        1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                     1:0.9.4-2build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                       1:1.4.3-4build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                    1:1.3.4-2build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                       1:2.3.0-7build2                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                     1:12.0.1-1ubuntu1.1                     X.Org X server -- VMware display driver
ii  xsltproc                                      1.1.26-8ubuntu1.2                       XSLT 1.0 command line processor
ii  xterm                                         271-1ubuntu2.1                          X terminal emulator
ii  xubuntu-artwork                               12.04.11                                Xubuntu themes and artwork
ii  xubuntu-default-settings                      12.04.11                                default settings for the Xubuntu desktop
ii  xubuntu-desktop                               2.152                                   Xubuntu desktop system
ii  xubuntu-docs                                  11.10.0                                 xubuntu documentation
ii  xubuntu-icon-theme                            12.04.11                                Xubuntu icon theme
ii  xubuntu-restricted-addons                     12                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-restricted-extras                     57                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-wallpapers                            12.04.11                                Xubuntu wallpapers
ii  xul-ext-ubufox                                2.6-0ubuntu0.12.04.1                    Ubuntu-specific configuration defaults and apt support for Firefox
ii  xz-lzma                                       5.1.1alpha+20110809-3                   XZ-format compression utilities - compatibility commands
ii  xz-utils                                      5.1.1alpha+20110809-3                   XZ-format compression utilities
ii  yelp                                          3.4.1-0ubuntu1                          Help browser for GNOME
ii  yelp-xsl                                      3.4.1-1                                 XSL stylesheets for the yelp help browser
ii  zeitgeist                                     0.9.0-1ubuntu1                          event logging framework
ii  zeitgeist-core                                0.9.0-1ubuntu1                          event logging framework - engine
ii  zeitgeist-datahub                             0.8.2-1ubuntu2                          event logging framework - passive logging daemon
ii  zenity                                        3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts
ii  zenity-common                                 3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts (common files)
ii  zip                                           3.0-4                                   Archiver for .zip files
ii  zlib1g                                        1:1.2.3.4.dfsg-3ubuntu4                 compression library - runtime

```

**DPKG List of Installed Packages (after cron-apt runs)**
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                                 Description
+++-=============================================-=======================================-=================================================================================================================================================
rc  abiword                                       2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration
ii  abiword-common                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- common files
ii  accountsservice                               0.6.15-2ubuntu9.4                       query and manipulate user account information
ii  acl                                           2.2.51-5ubuntu1                         Access control list utilities
ii  acpi-support                                  0.140                                   scripts for handling many ACPI events
ii  acpid                                         1:2.0.10-1ubuntu3                       Advanced Configuration and Power Interface event daemon
ii  adduser                                       3.113ubuntu2                            add and remove users and groups
rc  aisleriot                                     1:3.2.3.2-0ubuntu1                      Solitaire card games
rc  akonadi-backend-mysql                         1.7.2-0ubuntu1                          MySQL storage backend for Akonadi
rc  akonadi-server                                1.7.2-0ubuntu1                          Akonadi PIM storage service
ii  alacarte                                      0.13.2-2ubuntu4                         easy GNOME menu editing tool
ii  alsa-base                                     1.0.25+dfsg-0ubuntu1                    ALSA driver configuration files
ii  alsa-utils                                    1.0.25-1ubuntu5                         Utilities for configuring and using ALSA
ii  anacron                                       2.3-14ubuntu1                           cron-like program that doesn't go by time
ii  app-install-data                              0.12.04.4                               Ubuntu applications (data files)
ii  app-install-data-partner                      12.12.04.1                              Application Installer (data files for partner applications/repositories)
ii  apparmor                                      2.7.102-0ubuntu3.7                      User-space parser utility for AppArmor
ii  apport                                        2.0.1-0ubuntu15.1                       automatically generate crash reports for debugging
ii  apport-gtk                                    2.0.1-0ubuntu15.1                       GTK+ frontend for the apport crash report system
ii  apport-symptoms                               0.16.1                                  symptom scripts for apport
ii  apt                                           0.8.16~exp12ubuntu10.7                  commandline package manager
ii  apt-transport-https                           0.8.16~exp12ubuntu10.7                  https download transport for APT
ii  apt-utils                                     0.8.16~exp12ubuntu10.7                  package managment related utility programs
ii  apt-xapian-index                              0.44ubuntu5                             maintenance and search tools for a Xapian index of Debian packages
ii  aptdaemon                                     0.43+bzr805-0ubuntu7                    transaction based package management service
ii  aptdaemon-data                                0.43+bzr805-0ubuntu7                    data files for clients
ii  artha                                         1.0.2-1ubuntu1                          Handy off-line thesaurus based on WordNet
ii  aspell                                        0.60.7~20110707-1                       GNU Aspell spell-checker
ii  aspell-en                                     6.0-0-6ubuntu2                          English dictionary for GNU Aspell
ii  at                                            3.1.13-1ubuntu1                         Delayed job execution and batch processing
ii  at-spi2-core                                  2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface (dbus core)
ii  audacity                                      2.0.0-1ubuntu0.1                        fast, cross-platform audio editor
ii  audacity-data                                 2.0.0-1ubuntu0.1                        fast, cross-platform audio editor (data)
ii  augeas-lenses                                 0.10.0-0ubuntu4                         Set of lenses needed by libaugeas0 to parse config files
ii  avahi-autoipd                                 0.6.30-5ubuntu2                         Avahi IPv4LL network address configuration daemon
ii  avahi-daemon                                  0.6.30-5ubuntu2                         Avahi mDNS/DNS-SD daemon
ii  avahi-utils                                   0.6.30-5ubuntu2                         Avahi browsing, publishing and discovery utilities
ii  avogadro-data                                 1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Data Files)
ii  banshee                                       2.4.1-3ubuntu1~precise2                 Media Management and Playback application
ii  banshee-extension-soundmenu                   2.4.1-3ubuntu1~precise2                 Media Management and Playback application - sound menu extension
ii  base-files                                    6.5ubuntu6.4                            Debian base system miscellaneous files
ii  base-passwd                                   3.5.24                                  Debian base system master password and group files
ii  bash                                          4.2-2ubuntu2                            GNU Bourne Again SHell
ii  bash-completion                               1:1.3-1ubuntu8                          programmable completion for the bash shell
ii  bc                                            1.06.95-2                               The GNU bc arbitrary precision calculator language
ii  bind9-host                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Version of 'host' bundled with BIND 9.X
ii  binfmt-support                                2.0.8                                   Support for extra binary formats
ii  binutils                                      2.22-6ubuntu1                           GNU assembler, linker and binary utilities
ii  bison                                         1:2.5.dfsg-2.1                          YACC-compatible parser generator
ii  blender                                       2.62-1                                  Very fast and versatile 3D modeller/renderer
ii  blt                                           2.4z-4.2ubuntu1                         the BLT extension library for Tcl/Tk - run-time package
ii  blueman                                       1.23-0ubuntu2.1                         A Graphical bluetooth manager
ii  bluez                                         4.98-2ubuntu7                           Bluetooth tools and daemons
ii  bluez-alsa                                    4.98-2ubuntu7                           Bluetooth ALSA support
ii  bluez-cups                                    4.98-2ubuntu7                           Bluetooth printer driver for CUPS
ii  brasero                                       3.4.1-0ubuntu1.1                        CD/DVD burning application for GNOME
ii  brasero-cdrkit                                3.4.1-0ubuntu1.1                        cdrkit extensions for the Brasero burning application
ii  brasero-common                                3.4.1-0ubuntu1.1                        Common files for the Brasero CD burning application and library
ii  brltty                                        4.3-1ubuntu5                            Access software for a blind person using a braille display
ii  brltty-x11                                    4.3-1ubuntu5                            Access software for a blind person using a braille display - X11 drivers
ii  bsdmainutils                                  8.2.3ubuntu1                            collection of more utilities from FreeBSD
ii  bsdutils                                      1:2.20.1-1ubuntu3                       Basic utilities from 4.4BSD-Lite
ii  bsh                                           2.0b4-12build1                          Java scripting environment (BeanShell) Version 2
ii  bsh-gcj                                       2.0b4-12build1                          Java scripting environment (BeanShell) Version 2 (native code)
ii  build-essential                               11.5ubuntu2.1                           Informational list of build-essential packages
ii  busybox-initramfs                             1:1.18.5-1ubuntu4.1                     Standalone shell setup for initramfs
ii  busybox-static                                1:1.18.5-1ubuntu4.1                     Standalone rescue shell with tons of builtin utilities
ii  bzip2                                         1.0.6-1                                 high-quality block-sorting file compressor - utilities
ii  ca-certificates                               20111211                                Common CA certificates
ii  ca-certificates-java                          20110912ubuntu6                         Common CA certificates (JKS keystore)
ii  cabextract                                    1.4-1                                   Microsoft Cabinet file unpacker
rc  catfish                                       0.3.2-2ubuntu1                          file search tool that support several different engines
rc  charmap.app                                   0.2-11                                  Character map for GNUstep
ii  cheese                                        3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam
ii  cheese-common                                 3.4.1-0ubuntu2.1                        Common files for the Cheese tool to take pictures and videos
ii  chromium-browser                              20.0.1132.47~r144678-0ubuntu0.12.04.1   Chromium browser
ii  chromium-browser-l10n                         20.0.1132.47~r144678-0ubuntu0.12.04.1   chromium-browser language packages
ii  chromium-codecs-ffmpeg                        20.0.1132.47~r144678-0ubuntu0.12.04.1   Free ffmpeg codecs for the Chromium Browser
ii  clamav                                        0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - command-line interface
ii  clamav-base                                   0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - base package
ii  clamav-freshclam                              0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - virus database update utility
ii  cli-common                                    0.8.2                                   common files between all CLI packages
ii  cmap-adobe-japan1                             0+20090930-2                            CMaps for Adobe-Japan1
ii  colord                                        0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- system daemon
ii  command-not-found                             0.2.46ubuntu6                           Suggest installation of packages in interactive bash sessions
ii  command-not-found-data                        0.2.46ubuntu6                           Set of data files for command-not-found.
ii  conky                                         1.8.1-6                                 highly configurable system monitor (transitional package)
ii  conky-std                                     1.8.1-6                                 highly configurable system monitor (default version)
ii  console-setup                                 1.70ubuntu5                             console font and keymap setup program
ii  consolekit                                    0.4.5-2                                 framework for defining and tracking users, sessions and seats
ii  coreutils                                     8.13-3ubuntu3.2                         GNU core utilities
ii  cpio                                          2.11-7ubuntu3                           GNU cpio -- a program to manage archives of files
ii  cpp                                           4:4.6.3-1ubuntu5                        GNU C preprocessor (cpp)
ii  cpp-4.6                                       4.6.3-1ubuntu5                          GNU C preprocessor
ii  crda                                          1.1.2-1ubuntu1                          wireless Central Regulatory Domain Agent
ii  cron                                          3.0pl1-120ubuntu4                       process scheduling daemon
ii  cron-apt                                      0.9.0                                   automatic update of packages using apt-get
ii  cryptsetup-bin                                2:1.4.1-2ubuntu4                        disk encryption support - command line tools
ii  cups                                          1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - server
ii  cups-bsd                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - common files
ii  cups-filters                                  1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters
ii  cups-ppdc                                     1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation utilities
ii  curl                                          7.22.0-3ubuntu4                         Get a file from an HTTP, HTTPS or FTP server
ii  dash                                          0.5.7-2ubuntu2                          POSIX-compliant shell
ii  dbus                                          1.4.18-1ubuntu1.3                       simple interprocess messaging system (daemon and utilities)
ii  dbus-x11                                      1.4.18-1ubuntu1.3                       simple interprocess messaging system (X11 deps)
ii  dc                                            1.06.95-2                               The GNU dc arbitrary precision reverse-polish calculator
ii  dconf-gsettings-backend                       0.12.0-0ubuntu1.1                       simple configuration storage system - GSettings back-end
ii  dconf-service                                 0.12.0-0ubuntu1.1                       simple configuration storage system - D-Bus service
ii  dcraw                                         8.99-1build1                            decode raw digital camera images
ii  debconf                                       1.5.42ubuntu1                           Debian configuration management system
ii  debconf-i18n                                  1.5.42ubuntu1                           full internationalization support for debconf
ii  debconf-utils                                 1.5.42ubuntu1                           debconf utilities
ii  debianutils                                   4.2.1ubuntu2                            Miscellaneous utilities specific to Debian
ii  default-jre                                   1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime
ii  default-jre-headless                          1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime (headless)
ii  desktop-file-utils                            0.20-0ubuntu3                           Utilities for .desktop files
ii  devede                                        3.21.0-1                                simple application to create Video DVDs
ii  dia                                           0.97.2-5                                Diagram editor
ii  dia-common                                    0.97.2-5                                Diagram editor (common files)
ii  dia-libs                                      0.97.2-5                                Diagram editor (library files)
ii  dictionaries-common                           1.12.1ubuntu2                           Common utilities for spelling dictionary tools
ii  diffutils                                     1:3.2-1ubuntu1                          File comparison utilities
ii  dmidecode                                     2.11-4                                  SMBIOS/DMI table decoder
ii  dmsetup                                       2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  dmz-cursor-theme                              0.4.3                                   Style neutral, scalable cursor theme
ii  dnsmasq-base                                  2.59-4                                  Small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                      1:9.8.1.dfsg.P1-4ubuntu0.5              Clients provided with BIND
ii  doc-base                                      0.10.3                                  utilities to manage online documentation
ii  docbook-xml                                   4.5-7ubuntu1                            standard XML documentation system for software and systems
ii  docbook-xsl                                   1.76.1+dfsg-1ubuntu1                    stylesheets for processing DocBook XML to various output formats
ii  dosfstools                                    3.0.12-1ubuntu1                         utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                          1.16.1.2ubuntu7                         Debian package management system
ii  dpkg-dev                                      1.16.1.2ubuntu7                         Debian package development tools
ii  drgeo                                         1.1.0-9                                 An interactive geometry software
ii  drgeo-doc                                     1.5-6                                   The Dr. Geo online user manual
ii  dvd+rw-tools                                  7.1-10                                  DVD+-RW/R tools
ii  dvdauthor                                     0.7.0-1.1build1                         create DVD-Video file system
ii  e2fslibs                                      1.42-1ubuntu2                           ext2/ext3/ext4 file system libraries
ii  e2fsprogs                                     1.42-1ubuntu2                           ext2/ext3/ext4 file system utilities
ii  earth3d                                       1.0.5-3                                 Map client displaying a 3D model of the world
ii  ed                                            1.5-3                                   classic UNIX line editor
ii  eject                                         2.1.5+deb1+cvs20081104-9                ejects CDs and operates CD-Changers under Linux
ii  electric                                      8.10-2                                  electrical CAD system
ii  enchant                                       1.6.0-7                                 Wrapper for various spell checker engines (binary programs)
ii  esound-common                                 0.2.41-10build3                         Enlightened Sound Daemon - Common files
ii  espeak                                        1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer
ii  espeak-data                                   1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: speech data files
ii  evince                                        3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer
ii  evince-common                                 3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer - common files
ii  exo-utils                                     0.6.2-4                                 Utility files for libexo
ii  f-spot                                        0.8.2-4                                 personal photo management application
ii  facter                                        1.6.17-1puppetlabs1                     Ruby module for collecting simple facts about a host operating system
ii  fakeroot                                      1.18.2-1                                tool for simulating superuser privileges
ii  ffmpeg                                        4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder (transitional package)
ii  file                                          5.09-2                                  Determines file type using "magic" numbers
ii  file-roller                                   3.4.1-0ubuntu1                          archive manager for GNOME
ii  findutils                                     4.4.2-4ubuntu1                          utilities for finding files--find, xargs
ii  firefox                                       18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla
ii  firefox-globalmenu                            18.0+build1-0ubuntu0.12.04.3            Unity appmenu integration for Firefox
ii  firefox-gnome-support                         18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla - GNOME support
ii  firefox-locale-en                             18.0+build1-0ubuntu0.12.04.3            English language pack for Firefox
ii  flashplugin-installer                         11.2.202.261ubuntu0.12.04.1             Adobe Flash Player plugin installer
ii  flex                                          2.5.35-10ubuntu3                        A fast lexical analyzer generator.
ii  fontconfig                                    2.8.0-3ubuntu9.1                        generic font configuration library - support binaries
ii  fontconfig-config                             2.8.0-3ubuntu9.1                        generic font configuration library - configuration
ii  fonts-droid                                   20101110+git-2                          handheld device font with extensive style and language support
ii  fonts-horai-umefont                           434-1                                   Japanese TrueType font, Ume-font
ii  fonts-kacst                                   2.01+mry-3                              KACST free TrueType Arabic fonts
ii  fonts-kacst-one                               5.0+svn11846-2                          TrueType font designed for Arabic language
ii  fonts-khmeros-core                            5.0-5ubuntu1                            KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                                     0.0.20060226-8                          TrueType font for Lao language
ii  fonts-liberation                              1.07.0-2ubuntu0.1                       Fonts with the same metrics as Times, Arial and Courier
ii  fonts-nanum                                   3.010-2                                 Nanum Korean fonts
ii  fonts-opensymbol                              2:102.2+LibO3.5.4-0ubuntu1.1            OpenSymbol TrueType font
ii  fonts-sil-gentium                             20081126:1.02-12                        extended Unicode Latin font ("a typeface for the nations")
ii  fonts-sil-gentium-basic                       1.1-5                                   smart Unicode font families (Basic and Book Basic) based on Gentium
ii  fonts-takao-pgothic                           003.02.01-5ubuntu1                      Japanese TrueType font set, Takao P Gothic Fonts
ii  fonts-thai-tlwg                               1:0.4.17-1ubuntu1                       Thai fonts maintained by TLWG (meta package)
ii  fonts-tlwg-garuda                             1:0.4.17-1ubuntu1                       Thai Garuda font
ii  fonts-tlwg-kinnari                            1:0.4.17-1ubuntu1                       Thai Kinnari font
ii  fonts-tlwg-loma                               1:0.4.17-1ubuntu1                       Thai Loma font
ii  fonts-tlwg-mono                               1:0.4.17-1ubuntu1                       Thai TlwgMono font
ii  fonts-tlwg-norasi                             1:0.4.17-1ubuntu1                       Thai Norasi font
ii  fonts-tlwg-purisa                             1:0.4.17-1ubuntu1                       Thai Purisa font
ii  fonts-tlwg-sawasdee                           1:0.4.17-1ubuntu1                       Thai Sawasdee font
ii  fonts-tlwg-typewriter                         1:0.4.17-1ubuntu1                       Thai TlwgTypewriter font
ii  fonts-tlwg-typist                             1:0.4.17-1ubuntu1                       Thai TlwgTypist font
ii  fonts-tlwg-typo                               1:0.4.17-1ubuntu1                       Thai TlwgTypo font
ii  fonts-tlwg-umpush                             1:0.4.17-1ubuntu1                       Thai Umpush font
ii  fonts-tlwg-waree                              1:0.4.17-1ubuntu1                       Thai Waree font
ii  fonts-unfonts-core                            1.0.3.is.1.0.2-080608-5ubuntu1          Un series Korean TrueType fonts
ii  foomatic-db-compressed-ppds                   20120322-0ubuntu1                       OpenPrinting printer support - Compressed PPDs derived from the database
ii  foomatic-db-engine                            4.0.8-2ubuntu1                          OpenPrinting printer support - programs
ii  foomatic-filters                              4.0.16-0ubuntu0.2                       OpenPrinting printer support - filters
ii  freepats                                      20060219-1                              Free patch set for MIDI audio synthesis
ii  frei0r-plugins                                1.1.22git20091109-1.1ubuntu1            minimalistic plugin API for video effects, plugins collection
ii  friendly-recovery                             0.2.25                                  Make recovery more user-friendly
ii  ftp                                           0.17-25                                 classical file transfer client
ii  fuse                                          2.8.6-2ubuntu2                          Filesystem in Userspace
ii  g++                                           4:4.6.3-1ubuntu5                        GNU C++ compiler
ii  g++-4.6                                       4.6.3-1ubuntu5                          GNU C++ compiler
ii  gcalctool                                     6.4.1.1-0ubuntu3                        GNOME desktop calculator
ii  gcc                                           4:4.6.3-1ubuntu5                        GNU C compiler
ii  gcc-4.6                                       4.6.3-1ubuntu5                          GNU C compiler
ii  gcc-4.6-base                                  4.6.3-1ubuntu5                          GCC, the GNU Compiler Collection (base package)
ii  gcj-4.6-base                                  4.6.3-1ubuntu2                          GCC, the GNU Compiler Collection (gcj base package)
ii  gcj-4.6-jre-lib                               4.6.3-1ubuntu2                          Java runtime library for use with gcj (jar files)
ii  gconf-service                                 3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf-service-backend                         3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf2                                        3.2.5-0ubuntu2                          GNOME configuration database system (support tools)
ii  gconf2-common                                 3.2.5-0ubuntu2                          GNOME configuration database system (common files)
ii  gdb                                           7.4-2012.04-0ubuntu2.1                  The GNU Debugger
ii  gedit                                         3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment
ii  gedit-common                                  3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment (support files)
ii  gelemental                                    1.2.0-7ubuntu1                          Periodic Table viewer
ii  genisoimage                                   9:1.1.11-2ubuntu2                       Creates ISO-9660 CD-ROM filesystem images
ii  geoip-database                                20111220-1                              IP lookup command line tools that use the GeoIP library (country database)
ii  gettext                                       0.18.1.1-5ubuntu3                       GNU Internationalization utilities
ii  gettext-base                                  0.18.1.1-5ubuntu3                       GNU Internationalization utilities for the base system
ii  ghostscript                                   9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF
ii  ghostscript-cups                              9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - CUPS filters
ii  ghostscript-x                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - X11 support
ii  gigolo                                        0.4.1-3                                 frontend to manage connections to remote filesystems using GIO/GVfs
ii  gimp                                          2.6.12-1ubuntu1.2                       The GNU Image Manipulation Program
ii  gimp-data                                     2.6.12-1ubuntu1.2                       Data files for GIMP
ii  gimp-help-common                              2.6.1-1                                 Data files for the GIMP documentation
ii  gimp-help-en                                  2.6.1-1                                 Documentation for the GIMP (English)
ii  gir1.2-appindicator3-0.1                      0.4.92-0ubuntu1                         Typelib files for libappindicator3-1.
ii  gir1.2-atk-1.0                                2.4.0-0ubuntu1                          ATK accessibility toolkit (GObject introspection)
ii  gir1.2-atspi-2.0                              2.4.2-0ubuntu0.1                        Assistive Technology Service Provider (GObject introspection)
ii  gir1.2-dbusmenu-glib-0.4                      0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-glib4
ii  gir1.2-dbusmenu-gtk-0.4                       0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-gtk4
ii  gir1.2-dee-1.0                                1.0.10-0ubuntu1                         GObject introspection data for the Dee library
ii  gir1.2-freedesktop                            1.32.0-1                                Introspection data for some FreeDesktop components
ii  gir1.2-gdkpixbuf-2.0                          2.26.1-1                                GDK Pixbuf library - GObject-Introspection
ii  gir1.2-glib-2.0                               1.32.0-1                                Introspection data for GLib, GObject, Gio and GModule
ii  gir1.2-gmenu-3.0                              3.4.0-0ubuntu1                          GObject introspection data for the GNOME menu library
ii  gir1.2-gst-plugins-base-0.10                  0.10.36-1ubuntu0.1                      Description: GObject introspection data for the GStreamer Plugins Base library
ii  gir1.2-gstreamer-0.10                         0.10.36-1ubuntu1                        Description: GObject introspection data for the GStreamer library
ii  gir1.2-gtk-2.0                                2.24.10-0ubuntu6                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                                3.4.2-0ubuntu0.5                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtksource-3.0                          3.4.2-0ubuntu1                          gir files for the GTK+ syntax highlighting widget
ii  gir1.2-gudev-1.0                              175-0ubuntu9.2                          libgudev-1.0 introspection data
ii  gir1.2-javascriptcoregtk-3.0                  1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the GTK+-based JavaScriptCore library
ii  gir1.2-launchpad-integration-3.0              0.1.56.1                                library for launchpad integration (gir files)
ii  gir1.2-notify-0.7                             0.7.5-1                                 sends desktop notifications to a notification daemon (Introspection files)
ii  gir1.2-pango-1.0                              1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text - gir bindings
ii  gir1.2-peas-1.0                               1.2.0-1ubuntu1                          Application plugin library (introspection files)
ii  gir1.2-rb-3.0                                 2.96-0ubuntu4.2                         GObject introspection data for the rhythmbox music player
ii  gir1.2-soup-2.4                               2.38.1-1                                GObject introspection data for the libsoup HTTP library
ii  gir1.2-unity-5.0                              5.12.0-0ubuntu1.1                       GObject introspection data for the Unity library
ii  gir1.2-vte-2.90                               1:0.32.1-0ubuntu1                       GObject introspection data for the VTE library
ii  gir1.2-webkit-3.0                             1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the WebKit library
ii  gir1.2-wnck-3.0                               3.4.0-0ubuntu1                          GObject introspection data for the WNCK library
ii  gksu                                          2.0.2-6ubuntu1                          graphical frontend to su
ii  glib-networking                               2.32.1-1ubuntu2                         network-related giomodules for GLib
ii  glib-networking-common                        2.32.1-1ubuntu2                         network-related giomodules for GLib - data files
ii  glib-networking-services                      2.32.1-1ubuntu2                         network-related giomodules for GLib - D-Bus services
rc  gmusicbrowser                                 1.1.9-1                                 graphic jukebox for large collections of mp3/ogg/flac/mpc files
ii  gnome-accessibility-themes                    3.4.1-0ubuntu1.2                        accessibility themes for the GNOME desktop
ii  gnome-desktop-data                            1:2.32.1-0ubuntu9                       Common files for GNOME desktop apps
ii  gnome-desktop3-data                           3.4.2-0ubuntu0.1                        Common files for GNOME desktop apps
ii  gnome-games-data                              1:3.4.1-0ubuntu2.1                      data files for the GNOME games
ii  gnome-icon-theme                              3.4.0-0ubuntu1.1                        GNOME Desktop icon theme (small subset)
ii  gnome-keyring                                 3.2.2-2ubuntu4                          GNOME keyring services (daemon and tools)
ii  gnome-system-tools                            3.0.0-2ubuntu1                          Cross-platform configuration utilities for GNOME
ii  gnome-time-admin                              3.0.0-2ubuntu1                          GNOME Time Administration Tool
ii  gnome-user-guide                              3.4.1-1                                 GNOME user's guide
ii  gnome-video-effects                           0.4.0-1                                 GNOME Video Effects
rc  gnomine                                       1:3.4.1-0ubuntu2.1                      popular minesweeper puzzle game for GNOME
rc  gnumeric                                      1.10.17-1ubuntu2                        spreadsheet application for GNOME - main program
ii  gnupg                                         1.4.11-3ubuntu2.1                       GNU privacy guard - a free PGP replacement
rc  gnustep-base-common                           1.22.1-2ubuntu2                         GNUstep Base library - common files
rc  gnustep-base-runtime                          1.22.1-2ubuntu2                         GNUstep Base library - daemons and tools
rc  gnustep-common                                2.6.1-1                                 Common files for the core GNUstep environment
ii  google-chrome-stable                          23.0.1271.97-r171054                    The web browser from Google
rc  google-earth-stable                           7.0.1.8244-r0                           Explore, search and discover the planet
ii  gpgv                                          1.4.11-3ubuntu2.1                       GNU privacy guard - signature verification tool
ii  gpsd                                          3.4-2                                   Global Positioning System - daemon
ii  grep                                          2.10-1                                  GNU grep, egrep and fgrep
ii  groff-base                                    1.21-7                                  GNU troff text-formatting system (base system components)
ii  growisofs                                     7.1-10                                  DVD+-RW/R recorder
ii  grub-common                                   1.99-21ubuntu3.7                        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                         0.6                                     GRUB gfxpayload blacklist
ii  grub-pc                                       1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                   1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                  1.99-21ubuntu3.7                        GRand Unified Bootloader (common files for version 2)
ii  gs-cjk-resource                               1.20100103-3                            Resource files for gs-cjk, ghostscript CJK-TrueType extension
ii  gsettings-desktop-schemas                     3.4.1-0ubuntu1                          GSettings deskop-wide schemas
ii  gsfonts                                       1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1     Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                                   0.22                                    Make Ghostscript fonts available to X11
ii  gstreamer0.10-alsa                            0.10.36-1ubuntu0.1                      GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                          0.10.13-1                               FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                     0.10.15.debian-1ubuntu1                 Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnomevfs                        0.10.36-1ubuntu0.1                      GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                         0.10.17-2                               non-linear editing module for GStreamer
ii  gstreamer0.10-nice                            0.1.1-2ubuntu1                          ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad                     0.10.22.3-2ubuntu2.1                    GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse          0.10.21-1                               GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base                    0.10.36-1ubuntu0.1                      GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps               0.10.36-1ubuntu0.1                      GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good                    0.10.31-1ubuntu1                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                    0.10.18.3-1ubuntu1                      GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio                      0.10.31-1ubuntu1                        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                           0.10.36-1ubuntu1                        Tools for use with GStreamer
ii  gstreamer0.10-x                               0.10.36-1ubuntu0.1                      GStreamer plugins for X11 and Pango
ii  gthumb                                        3:2.14.3-0ubuntu1                       image viewer and browser
ii  gthumb-data                                   3:2.14.3-0ubuntu1                       image viewer and browser - arch-independent files
ii  gtk2-engines                                  1:2.20.2-1ubuntu1                       theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                          0.98.2-0ubuntu1                         cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                           2.24.10-0ubuntu6                        pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-unico                            1.0.2-0ubuntu1                          Unico Gtk+ 3 theme engine
ii  gucharmap                                     1:3.4.1.1-0ubuntu1                      Unicode character picker and font browser
ii  guile-1.6-libs                                1.6.8-10ubuntu4                         Main Guile libraries
ii  guile-1.8-libs                                1.8.8+1-6ubuntu2                        Core Guile libraries
ii  gvfs                                          1.12.1-0ubuntu1.1                       userspace virtual filesystem - GIO module
ii  gvfs-backends                                 1.12.1-0ubuntu1.1                       userspace virtual filesystem - backends
ii  gvfs-bin                                      1.12.1-0ubuntu1.1                       userspace virtual filesystem - binaries
ii  gvfs-common                                   1.12.1-0ubuntu1.1                       userspace virtual filesystem - common data files
ii  gvfs-daemons                                  1.12.1-0ubuntu1.1                       userspace virtual filesystem - servers
ii  gvfs-fuse                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - fuse server
ii  gvfs-libs                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - private libraries
ii  gzip                                          1.4-1ubuntu2                            GNU compression utilities
ii  hdparm                                        9.37-0ubuntu3.1                         tune hard disk parameters for high performance
ii  heirloom-mailx                                12.5-1build1                            feature-rich BSD mail(1)
ii  hicolor-icon-theme                            0.12-1ubuntu2                           default fallback theme for FreeDesktop.org icon themes
ii  hiera                                         1.1.2-1puppetlabs1                      A simple pluggable Hierarchical Database.
ii  hostname                                      3.06ubuntu1                             utility to set/show the host name or domain name
ii  hplip                                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                    3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - data files
ii  humanity-icon-theme                           0.5.3.11                                Humanity Icon theme
ii  hunspell-en-us                                20070829-4ubuntu3                       English_american dictionary for hunspell
ii  hwdata                                        0.233-1ubuntu1                          hardware identification / configuration data
ii  ibus                                          1.4.1-3ubuntu1                          Intelligent Input Bus - core
ii  ibus-gtk                                      1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3                                     1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+3 support
ii  ibus-pinyin                                   1.4.0-1                                 Pinyin engine for IBus
ii  ibus-pinyin-db-android                        1.4.0-1                                 Pinyin engine for IBus - Android database
ii  ibus-table                                    1.3.9.20110827-1ubuntu1                 table engine for IBus
ii  icc-profiles-free                             2.0.1+dfsg-1                            ICC color profiles for use with color profile aware software
ii  icedtea-6-jre-cacao                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre-jamvm                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using JamVM
ii  icedtea-netx                                  1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                           1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icoutils                                      0.29.1-2                                Create and extract MS Windows icons and cursors
ii  ifupdown                                      0.7~beta2ubuntu8                        high level tools to configure network interfaces
ii  im-switch                                     1.20ubuntu5.1                           Input method switch framework
ii  imagemagick                                   8:6.6.9.7-5ubuntu3.2                    image manipulation programs
ii  imagemagick-common                            8:6.6.9.7-5ubuntu3.2                    image manipulation programs -- infrastructure
ii  indicator-application                         0.5.0-0ubuntu1                          Application Indicators
ii  indicator-application-gtk2                    0.5.0-0ubuntu1                          Application Indicators
ii  indicator-sound                               0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  indicator-sound-gtk2                          0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  info                                          4.13a.dfsg.1-8ubuntu2                   Standalone GNU Info documentation browser
ii  initramfs-tools                               0.99ubuntu13                            tools for generating an initramfs
ii  initramfs-tools-bin                           0.99ubuntu13                            binaries used by initramfs-tools
ii  initscripts                                   2.88dsf-13.10ubuntu11.1                 scripts for initializing and shutting down the system
ii  inkscape                                      0.48.3.1-1ubuntu1                       vector-based drawing program
ii  inputattach                                   1:1.4.2-1                               utility to connect serial-attached peripherals to the input subsystem
ii  insserv                                       1.14.0-2.1ubuntu2                       Tool to organize boot sequence using LSB init.d script dependencies
ii  install-info                                  4.13a.dfsg.1-8ubuntu2                   Manage installed documentation in info format
ii  iproute                                       20111117-1ubuntu2                       networking and traffic control tools
ii  iptables                                      1.4.12-1ubuntu4                         administration tools for packet filtering and NAT
ii  iputils-arping                                3:20101006-1ubuntu1                     Tool to send ICMP echo requests to an ARP address
ii  iputils-ping                                  3:20101006-1ubuntu1                     Tools to test the reachability of network hosts
ii  iputils-tracepath                             3:20101006-1ubuntu1                     Tools to trace the network path to a remote host
ii  irqbalance                                    0.56-1ubuntu4                           Daemon to balance interrupts for SMP systems
ii  isc-dhcp-client                               4.1.ESV-R4-0ubuntu5.5                   ISC DHCP client
ii  isc-dhcp-common                               4.1.ESV-R4-0ubuntu5.5                   common files used by all the isc-dhcp* packages
ii  iso-codes                                     3.31-1                                  ISO language, territory, currency, script codes and their translations
ii  iw                                            3.2-1                                   tool for configuring Linux wireless devices
ii  java-common                                   0.43ubuntu2                             Base of all Java packages
ii  java-wrappers                                 0.1.24                                  wrappers for java executables
ii  jockey-common                                 0.9.7-0ubuntu7.4                        user interface and desktop integration for driver management
ii  jockey-gtk                                    0.9.7-0ubuntu7.4                        GNOME user interface and desktop integration for driver management
ii  kalgebra                                      4:4.8.4-0ubuntu0.1                      algebraic graphing calculator for KDE
ii  kalgebra-common                               4:4.8.4-0ubuntu0.1                      contains files common for kalgebra and kalgebramobile
ii  kalzium                                       4:4.8.5-0ubuntu0.1                      periodic table and chemistry tools for KDE
ii  kalzium-data                                  4:4.8.5-0ubuntu0.1                      data files for Kalzium
ii  kate-data                                     4:4.8.5-0ubuntu0.1                      shared data files for kate
ii  katepart                                      4:4.8.5-0ubuntu0.1                      kate KPart
ii  kbd                                           1.15.2-3ubuntu4                         Linux console font and keytable utilities
ii  kbruch                                        4:4.8.2-0ubuntu1                        fraction learning aid for KDE
ii  kde-runtime                                   4:4.8.5-0ubuntu0.1                      runtime components from the official KDE release
ii  kde-runtime-data                              4:4.8.5-0ubuntu0.1                      shared data files for the KDE base runtime module
ii  kdeedu-kvtml-data                             4:4.8.5-0ubuntu0.1                      kvtml files for kdeedu programs
ii  kdelibs-bin                                   4:4.8.5-0ubuntu0.1                      core executables for KDE Applications
ii  kdelibs5-data                                 4:4.8.5-0ubuntu0.1                      core shared data for all KDE Applications
ii  kdelibs5-plugins                              4:4.8.5-0ubuntu0.1                      core plugins for KDE Applications
rc  kdepim-runtime                                4:4.8.5-0ubuntu0.1                      Runtime components for akonadi-kde
ii  kdoctools                                     4:4.8.5-0ubuntu0.1                      various tools for accessing application documentation
ii  kerneloops-daemon                             0.12+git20090217-1ubuntu19              kernel oops tracker
ii  keyboard-configuration                        1.70ubuntu5                             system-wide keyboard preferences
ii  kig                                           4:4.8.4-0ubuntu0.1                      interactive geometry tool for KDE
ii  kino                                          1.3.4-1.3                               Non-linear editor for Digital Video data
ii  klibc-utils                                   1.5.25-1ubuntu2                         small utilities built with klibc for early boot
ii  kmplot                                        4:4.8.2-0ubuntu1                        mathematical function plotter for KDE
ii  kolourpaint4                                  4:4.8.4-0ubuntu0.1                      simple image editor and drawing application
ii  krb5-locales                                  1.10+dfsg~beta1-2ubuntu0.3              Internationalization support for MIT Kerberos
ii  krosspython                                   4:4.8.2-0ubuntu1                        Python module for Kross
ii  kstars                                        4:4.8.5-0ubuntu0.1                      desktop planetarium for KDE
ii  kstars-data                                   4:4.8.5-0ubuntu0.1                      data files for KStars desktop planetarium
ii  ktouch                                        4:4.8.2-0ubuntu1                        touch typing tutor for KDE
ii  ktouch-data                                   4:4.8.2-0ubuntu1                        data files for ktouch
ii  kturtle                                       4:4.8.2-0ubuntu1                        Logo educational programming environment for KDE
ii  kubuntu-debug-installer                       11.10ubuntu1                            Debug package installer for Kubuntu
ii  kwordquiz                                     4:4.8.3-0ubuntu0.1                      flashcard learning program for KDE
ii  language-pack-en                              1:12.04+20120801                        translation updates for language English
ii  language-pack-en-base                         1:12.04+20120801                        translations for language English
ii  language-pack-gnome-en                        1:12.04+20120801                        GNOME translation updates for language English
ii  language-pack-gnome-en-base                   1:12.04+20120801                        GNOME translations for language English
ii  language-selector-common                      0.79                                    Language selector for Ubuntu
ii  language-selector-gnome                       0.79                                    Language selector for Ubuntu
ii  laptop-detect                                 0.13.7ubuntu2                           attempt to detect a laptop
ii  launchpad-integration                         0.1.56.1                                launchpad integration
rc  leafpad                                       0.8.18.1-2                              GTK+ based simple text editor
ii  less                                          444-1ubuntu1                            pager program similar to more
ii  liba52-0.7.4                                  0.7.4-16build1                          library for decoding ATSC A/52 streams
ii  libaa1                                        1.4p5-39ubuntu1                         ASCII art library
ii  libaacs0                                      0.3.0-4                                 free-and-libre implementation of AACS
ii  libabiword-2.9                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- shared library
ii  libaccountsservice0                           0.6.15-2ubuntu9.4                       query and manipulate user account information - shared libraries
ii  libacl1                                       2.2.51-5ubuntu1                         Access control list shared library
rc  libakonadi-calendar4                          4:4.8.5-0ubuntu0.1                      library providing calendar helpers for Akonadi items
rc  libakonadi-contact4                           4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kabc4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kcal4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kde4                               4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kmime4                             4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-notes4                             4:4.8.5-0ubuntu0.1                      library providing notes helpers for Akonadi items
rc  libakonadiprotocolinternals1                  1.7.2-0ubuntu1                          libraries for the Akonadi PIM storage service
ii  libalgorithm-diff-perl                        1.19.02-2                               module to find differences between files
ii  libalgorithm-diff-xs-perl                     0.04-2build2                            module to find differences between files (XS accelerated)
ii  libalgorithm-merge-perl                       0.08-2                                  Perl module for three-way merge of textual data
ii  libanalitza4abi1                              4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions
ii  libanalitzagui4abi1                           4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions - GUI routines
ii  libao-common                                  1.1.0-1ubuntu2                          Cross Platform Audio Output Library (Common files)
ii  libao4                                        1.1.0-1ubuntu2                          Cross Platform Audio Output Library
ii  libappindicator1                              0.4.92-0ubuntu1                         Application Indicators
ii  libappindicator3-1                            0.4.92-0ubuntu1                         Application Indicators
ii  libapt-inst1.4                                0.8.16~exp12ubuntu10.7                  deb package format runtime library
ii  libapt-pkg4.12                                0.8.16~exp12ubuntu10.7                  package managment runtime library
ii  libarchive12                                  3.0.3-6ubuntu1                          Multi-format archive and compression library (shared library)
ii  libart-2.0-2                                  2.3.21-1ubuntu0.1                       Library of functions for 2D graphics - runtime files
ii  libart2.0-cil                                 2.24.2-1                                CLI binding for libart 2.3
ii  libasn1-8-heimdal                             1.6~git20120311.dfsg.1-2                Heimdal Kerberos - ASN.1 library
ii  libasound2                                    1.0.25-1ubuntu10.1                      shared library for ALSA applications
ii  libasound2-plugins                            1.0.25-1ubuntu1                         ALSA library additional plugins
ii  libaspell15                                   0.60.7~20110707-1                       GNU Aspell spell-checker runtime library
ii  libass4                                       0.10.0-3                                library for SSA/*** subtitles rendering
ii  libasyncns0                                   0.8-4                                   Asynchronous name service query library
ii  libatasmart4                                  0.18-3                                  ATA S.M.A.R.T. reading and parsing library
ii  libatk-wrapper-java                           0.30.4-0ubuntu2                         An ATK implementation for Java using JNI
ii  libatk-wrapper-java-jni                       0.30.4-0ubuntu2                         An ATK implementation for Java using JNI (jni bindings)
ii  libatk1.0-0                                   2.4.0-0ubuntu1                          ATK accessibility toolkit
ii  libatk1.0-data                                2.4.0-0ubuntu1                          Common files for the ATK accessibility toolkit
ii  libatkmm-1.6-1                                2.22.6-1ubuntu1                         C++ wrappers for ATK accessibility toolkit (shared libraries)
ii  libatspi2.0-0                                 2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface - shared library
ii  libattica0.3                                  0.3.0-0ubuntu2                          a Qt library that implements the Open Collaboration Services API
ii  libattr1                                      1:2.4.46-5ubuntu1                       Extended attribute shared library
ii  libaudclient2                                 3.2.1-2                                 audacious dbus remote control library
ii  libaudio-scrobbler-perl                       0.01-2.1                                perl interface to audioscrobbler.com/last.fm
ii  libaudio2                                     1.9.3-4                                 Network Audio System - shared libraries
ii  libaudiofile1                                 0.3.3-2                                 Open-source version of SGI's audiofile library
ii  libaugeas-ruby1.8                             0.3.0-1.1ubuntu4                        Augeas bindings for the Ruby language
ii  libaugeas0                                    0.10.0-0ubuntu4                         Augeas configuration editing library and API
ii  libav-tools                                   4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder
ii  libavahi-client3                              0.6.30-5ubuntu2                         Avahi client library
ii  libavahi-common-data                          0.6.30-5ubuntu2                         Avahi common data files
ii  libavahi-common3                              0.6.30-5ubuntu2                         Avahi common library
ii  libavahi-core7                                0.6.30-5ubuntu2                         Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                                0.6.30-5ubuntu2                         Avahi glib integration library
ii  libavc1394-0                                  0.5.3-1ubuntu2                          control IEEE 1394 audio/video devices
ii  libavcodec-extra-53                           4:0.8.4ubuntu0.12.04.1                  Libav codec library
rc  libavcodec53                                  4:0.8.4-0ubuntu0.12.04.1                Libav codec library
ii  libavdevice53                                 4:0.8.4-0ubuntu0.12.04.1                Libav device handling library
ii  libavfilter2                                  4:0.8.4-0ubuntu0.12.04.1                Libav video filtering library
ii  libavformat-extra-53                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libavformat53                                 4:0.8.4-0ubuntu0.12.04.1                Libav file format library
ii  libavogadro1                                  1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (library)
ii  libavutil-extra-51                            4:0.8.4ubuntu0.12.04.1                  Libav utility library
rc  libavutil51                                   4:0.8.4-0ubuntu0.12.04.1                Libav utility library
ii  libbabl-0.0-0                                 0.0.22-1.1                              Dynamic, any to any, pixel format conversion library
ii  libbind9-80                                   1:9.8.1.dfsg.P1-4ubuntu0.5              BIND9 Shared Library used by BIND
ii  libbison-dev                                  1:2.5.dfsg-2.1                          YACC-compatible parser generator - development library
ii  libblas3gf                                    1.2.20110419-2ubuntu1                   Basic Linear Algebra Reference implementations, shared library
ii  libblkid1                                     2.20.1-1ubuntu3                         block device id library
ii  libbluetooth3                                 4.98-2ubuntu7                           Library to use the BlueZ Linux Bluetooth stack
ii  libbluray1                                    1:0.2.1+git20111208.63e308d-3           Blu-ray disc playback support library (shared library)
ii  libbonobo2-0                                  2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library
ii  libbonobo2-common                             2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library -- support files
ii  libbonoboui2-0                                2.24.5-0ubuntu1.1                       The Bonobo UI library
ii  libbonoboui2-common                           2.24.5-0ubuntu1.1                       The Bonobo UI library -- common files
rc  libboost-program-options1.46.1                1.46.1-7ubuntu3                         program options library for C++
ii  libboost-python1.46.1                         1.46.1-7ubuntu3                         Boost.Python Library
ii  libbrasero-media3-1                           3.4.1-0ubuntu1.1                        CD/DVD burning library for GNOME - runtime
ii  libbrlapi0.5                                  4.3-1ubuntu5                            braille display access via BRLTTY - shared library
ii  libbsd0                                       0.3.0-2                                 utility functions from BSD systems - shared library
ii  libburn4                                      1.1.8-1                                 library to provide CD/DVD writing functions
ii  libbz2-1.0                                    1.0.6-1                                 high-quality block-sorting file compressor library - runtime
ii  libc-bin                                      2.15-0ubuntu10.3                        Embedded GNU C Library: Binaries
ii  libc-dev-bin                                  2.15-0ubuntu10.3                        Embedded GNU C Library: Development binaries
ii  libc6                                         2.15-0ubuntu10.3                        Embedded GNU C Library: Shared libraries
ii  libc6-dev                                     2.15-0ubuntu10.3                        Embedded GNU C Library: Development Libraries and Header Files
ii  libcaca0                                      0.99.beta17-2.1ubuntu2                  colour ASCII art library
ii  libcairo-gobject2                             1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library (GObject library)
ii  libcairo-perl                                 1.081-1build2                           Perl interface to the Cairo graphics library
ii  libcairo2                                     1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library
ii  libcairomm-1.0-1                              1.10.0-1ubuntu1                         C++ wrappers for Cairo (shared libraries)
ii  libcanberra-gtk3-0                            0.28-3ubuntu3                           GTK+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module                       0.28-3ubuntu3                           translates GTK3 widgets signals to event sounds
ii  libcanberra-pulse                             0.28-3ubuntu3                           PulseAudio backend for libcanberra
ii  libcanberra0                                  0.28-3ubuntu3                           simple abstract interface for playing event sounds
ii  libcap-ng0                                    0.6.6-1ubuntu1                          An alternate POSIX capabilities library
ii  libcap2                                       1:2.22-1ubuntu3                         support for getting/setting POSIX.1e capabilities
ii  libcap2-bin                                   1:2.22-1ubuntu3                         basic utility programs for using capabilities
ii  libcapi20-3                                   1:3.12.20071127-0ubuntu11               libraries for CAPI support
ii  libcdaudio1                                   0.99.12p2-10build1                      library for controlling a CD-ROM when playing audio CDs
ii  libcddb2                                      1.3.2-3fakesync1                        library to access CDDB data - runtime files
ii  libcdio-cdda1                                 0.83-1                                  library to read and control digital audio CDs
ii  libcdio-paranoia1                             0.83-1                                  library to read digital audio CDs with error correction
ii  libcdio13                                     0.83-1                                  library to read and control CD-ROM
ii  libcdparanoia0                                3.10.2+debian-10ubuntu1                 audio extraction tool for sampling CDs (library)
ii  libcdt4                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - cdt library
ii  libcelt0-0                                    0.7.1-1                                 The CELT codec runtime library
ii  libcfitsio3                                   3.290-1ubuntu1                          shared library for I/O with FITS format data files
ii  libcheese-gtk21                               3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - widgets
ii  libcheese3                                    3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - base library
ii  libck-connector0                              0.4.5-2                                 ConsoleKit libraries
ii  libclamav6                                    0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - library
ii  libclass-isa-perl                             0.36-3                                  report the search path for a class's ISA tree
ii  libcln6                                       1.3.2-1.1                               Class Library for Numbers (C++)
ii  libclucene0ldbl                               0.9.21b-2                               library for full-featured text search engine (runtime)
ii  libclutter-1.0-0                              1.10.6-1~precise1                       Open GL based interactive canvas library
ii  libclutter-1.0-common                         1.10.6-1~precise1                       Open GL based interactive canvas library (common files)
ii  libclutter-gst-1.0-0                          1.5.4-0ubuntu2                          Open GL based interactive canvas library GStreamer elements
ii  libclutter-gtk-1.0-0                          1.2.0-0ubuntu1                          Open GL based interactive canvas library GTK+ widget
ii  libclutter-imcontext-0.1-0                    0.1.4-2build1                           Open GL based interactive canvas library IMContext framework
ii  libcluttergesture-0.0.2-0                     0.0.2.1-2ubuntu3                        Open GL based interactive canvas library Gesture framework
ii  libcmis-0.2-0                                 0.1.0-1                                 CMIS protocol client library
ii  libcogl-common                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer (common files)
ii  libcogl-pango0                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcogl9                                      1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcolamd2.7.1                                1:3.4.0-2ubuntu3                        column approximate minimum degree ordering library for sparse matrices
ii  libcolord1                                    0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- runtime
ii  libcomerr2                                    1.42-1ubuntu2                           common error description library
ii  libconfig-inifiles-perl                       2.68-1ubuntu0.12.04.1                   Read .ini-style configuration files
ii  libcroco3                                     0.6.5-1                                 Cascading Style Sheet (CSS) parsing and manipulation toolkit
ii  libcrypt-passwdmd5-perl                       1.3-10                                  interoperable MD5-based crypt() for perl
ii  libcryptsetup4                                2:1.4.1-2ubuntu4                        disk encryption support - shared library
ii  libcrystalhd3                                 1:0.0~git20110715.fdd2f19-4.1           Crystal HD Video Decoder (shared library)
ii  libcups2                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Core library
ii  libcupscgi1                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - CGI library
ii  libcupsdriver1                                1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Driver library
ii  libcupsfilters1                               1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2                                 1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation library
ii  libcurl3                                      7.22.0-3ubuntu4                         Multi-protocol file transfer library (OpenSSL)
ii  libcurl3-gnutls                               7.22.0-3ubuntu4                         Multi-protocol file transfer library (GnuTLS)
ii  libdaemon0                                    0.14-2                                  lightweight C library for daemons - runtime library
ii  libdatrie1                                    0.2.5-3                                 Double-array trie library
ii  libdb5.1                                      5.1.25-11build1                         Berkeley v5.1 Database Libraries [runtime]
ii  libdbus-1-3                                   1.4.18-1ubuntu1.3                       simple interprocess messaging system (library)
ii  libdbus-glib-1-2                              0.98-1ubuntu1                           simple interprocess messaging system (GLib-based shared library)
ii  libdbus-glib1.0-cil                           0.5.0-3build1                           CLI implementation of D-Bus (GLib mainloop integration)
ii  libdbus1.0-cil                                0.7.0-4                                 CLI implementation of D-Bus
ii  libdbusmenu-glib4                             0.6.2-0ubuntu0.1                        library for passing menus over DBus
ii  libdbusmenu-gtk3-4                            0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk4                              0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-qt2                               0.9.2-0ubuntu1                          Qt implementation of the DBusMenu protocol
ii  libdc1394-22                                  2.2.0-2                                 high level programming interface for IEEE1394 digital camera
ii  libdca0                                       0.0.5-5                                 decoding library for DTS Coherent Acoustics streams
ii  libdconf0                                     0.12.0-0ubuntu1.1                       simple configuration storage system - runtime library
ii  libdee-1.0-4                                  1.0.10-0ubuntu1                         model to synchronize mutiple instances over DBus - shared lib
ii  libdevmapper-event1.02.1                      2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdevmapper1.02.1                            2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdigest-crc-perl                            0.18-1                                  Perl module providing generic CRC functions
ii  libdirac-encoder0                             1.0.2-4build1                           open and royalty free high quality codec - encoder library
ii  libdirectfb-1.2-9                             1.2.10.0-4.3ubuntu1                     direct frame buffer graphics - shared libraries
ii  libdiscid0                                    0.2.2-3                                 Library for creating MusicBrainz DiscIDs
ii  libdjvulibre-text                             3.5.24-9                                Linguistic support files for libdjvulibre
ii  libdjvulibre21                                3.5.24-9                                Runtime support for the DjVu image format
ii  libdlrestrictions1                            0.14.2ubuntu5                           library that implements library compatibility checks for dlopen()
ii  libdmapsharing-3.0-2                          2.9.14-1                                DMAP client and server library - runtime
rc  libdmtx0a                                     0.7.2-1build2                           Data Matrix barcodes (runtime library)
ii  libdns81                                      1:9.8.1.dfsg.P1-4ubuntu0.5              DNS Shared Library used by BIND
ii  libdotconf1.0                                 1.0.13-3                                Configuration file parser library - runtime files
ii  libdpkg-perl                                  1.16.1.2ubuntu7                         Dpkg perl modules
ii  libdrm-intel1                                 2.4.32-1ubuntu1                         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                              2.4.32-1ubuntu1                         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                                2.4.32-1ubuntu1                         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                       2.4.32-1ubuntu1                         Userspace interface to kernel DRM services -- runtime
ii  libdv4                                        1.0.0-3ubuntu1                          software library for DV format digital video (runtime lib)
ii  libdvbpsi7                                    0.2.2-1                                 library for MPEG TS and DVB PSI tables decoding and generating
ii  libdvdcss2                                    1.2.12-0.0medibuntu1                    Simple foundation for reading DVDs - runtime libraries
ii  libdvdnav4                                    4.2.0-1                                 DVD navigation library
ii  libdvdread4                                   4.2.0-1ubuntu3                          library for reading DVDs
ii  libebml3                                      1.2.2-2                                 access library for the EBML format (shared library)
ii  libedit2                                      2.11-20080614-3ubuntu2                  BSD editline and history libraries
ii  libelemental0                                 1.2.0-7ubuntu1                          Periodic Table viewer (data and shared library)
ii  libelf1                                       0.152-1ubuntu3                          library to read and write ELF files
ii  libenca0                                      1.13-4                                  Extremely Naive Charset Analyser - shared library files
ii  libenchant1c2a                                1.6.0-7                                 Wrapper library for various spell checker engines (runtime libs)
ii  libencode-locale-perl                         1.02-2                                  utility to determine the locale encoding
ii  libept1.4.12                                  1.0.6~exp1ubuntu1                       High-level library for managing Debian package information
ii  libesd0                                       0.2.41-10build3                         Enlightened Sound Daemon - Shared libraries
ii  libespeak1                                    1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: shared library
ii  libevent-2.0-5                                2.0.16-stable-1                         Asynchronous event notification library
ii  libevince3-3                                  3.4.0-0ubuntu1.4                        Document (PostScript, PDF) rendering library
ii  libexempi3                                    2.2.0-1                                 library to parse XMP metadata (Library)
ii  libexif12                                     0.6.20-2ubuntu0.1                       library to parse EXIF files
ii  libexiv2-11                                   0.22-2                                  EXIF/IPTC metadata manipulation library
ii  libexo-1-0                                    0.6.2-4                                 Library with extensions for Xfce
ii  libexo-common                                 0.6.2-4                                 libexo common files
ii  libexo-helpers                                0.6.2-4                                 libexo helpers
ii  libexpat1                                     2.0.1-7.2ubuntu1.1                      XML parsing C library - runtime library
ii  libexttextcat-data                            3.2.0-1ubuntu1                          Language detection library - data files
ii  libexttextcat0                                3.2.0-1ubuntu1                          Language detection library
ii  libfaac0                                      1.28-0ubuntu2                           AAC audio encoder (library)
ii  libfaad2                                      2.7-7                                   freeware Advanced Audio Decoder - runtime files
ii  libfarstream-0.1-0                            0.1.2-0ubuntu1                          Audio/Video communications framework: core library
ii  libffi6                                       3.0.11~rc1-5                            Foreign Function Interface library runtime
ii  libfftw3-3                                    3.3-1ubuntu1                            library for computing Fast Fourier Transforms
ii  libfile-basedir-perl                          0.03-1fakesync1                         Perl module to use the freedesktop basedir specification
ii  libfile-copy-recursive-perl                   0.38-1                                  Perl extension for recursively copying files and directories
ii  libfile-desktopentry-perl                     0.04-3                                  Perl module to handle freedesktop .desktop files
ii  libfile-listing-perl                          6.03-1                                  module to parse directory listings
ii  libfile-mimeinfo-perl                         0.15-2                                  Perl module to determine file types
ii  libfl-dev                                     2.5.35-10ubuntu3                        static library for flex (a fast lexical analyzer generator).
ii  libflac++6                                    1.2.1-6                                 Free Lossless Audio Codec - C++ runtime library
ii  libflac8                                      1.2.1-6                                 Free Lossless Audio Codec - runtime C library
ii  libflickrnet2.2-cil                           1:2.2.0-3build1                         Flickr.Net API Library
ii  libflite1                                     1.4-release-4                           Small run-time speech synthesis engine - shared libraries
ii  libfont-afm-perl                              1.20-1                                  Font::AFM - Interface to Adobe Font Metrics files
ii  libfontconfig1                                2.8.0-3ubuntu9.1                        generic font configuration library - runtime
ii  libfontenc1                                   1:1.1.0-1                               X11 font encoding library
ii  libframe6                                     2.2.4-0ubuntu0.12.04.1                  Touch Frame Library
ii  libfreetype6                                  2.4.8-1ubuntu2                          FreeType 2 font engine, shared library files
ii  libfribidi0                                   0.19.2-1                                Free Implementation of the Unicode BiDi algorithm
ii  libfs6                                        2:1.0.3-1                               X11 Font Services library
ii  libfuse2                                      2.8.6-2ubuntu2                          Filesystem in Userspace (library)
ii  libgail-3-0                                   3.4.2-0ubuntu0.5                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgail18                                     2.24.10-0ubuntu6                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgarcon-1-0                                 0.1.11-0ubuntu1                         freedesktop.org compliant menu implementation for Xfce
ii  libgarcon-common                              0.1.11-0ubuntu1                         common files for libgarcon menu implementation
ii  libgavl1                                      1.2.0-4                                 low level audio and video library - runtime files
ii  libgc1c2                                      1:7.1-8ubuntu0.12.04.1                  conservative garbage collector for C and C++
ii  libgcc1                                       1:4.6.3-1ubuntu5                        GCC support library
ii  libgcj-bc                                     4.6.3-1ubuntu5                          Link time only library for use with gcj
ii  libgcj-common                                 1:4.6.3-1ubuntu5                        Java runtime library (common files)
ii  libgcj12                                      4.6.3-1ubuntu2                          Java runtime library for use with gcj
ii  libgck-1-0                                    3.2.2-2ubuntu4                          Glib wrapper library for PKCS#11 - runtime
ii  libgconf-2-4                                  3.2.5-0ubuntu2                          GNOME configuration database system (shared libraries)
ii  libgconf2-4                                   3.2.5-0ubuntu2                          GNOME configuration database system (dummy package)
ii  libgconf2.0-cil                               2.24.2-1                                CLI binding for GConf 2.24
ii  libgcr-3-1                                    3.2.2-2ubuntu4                          Library for Crypto UI related task - runtime
ii  libgcr-3-common                               3.2.2-2ubuntu4                          Library for Crypto UI related task - common files
ii  libgcrypt11                                   1.5.0-3ubuntu0.1                        LGPL Crypto library - runtime library
ii  libgd2-xpm                                    2.0.36~rc1~dfsg-6ubuntu2                GD Graphics Library version 2
ii  libgdata1.9-cil                               1.9.0.0-1                               Google GData CLI client library
ii  libgdbm3                                      1.8.3-10                                GNU dbm database routines (runtime version)
ii  libgdiplus                                    2.10-3                                  interface library for System.Drawing of Mono
ii  libgdk-pixbuf2.0-0                            2.26.1-1                                GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                       2.26.1-1                                GDK Pixbuf library - data files
ii  libgdome2-0                                   0.8.1+debian-4.1build1                  DOM level2 library for accessing XML files
ii  libgdome2-cpp-smart0c2a                       0.2.6-6build2                           C++ bindings for GDome2 DOM implementation
ii  libgdu0                                       3.0.2-2ubuntu7                          GObject based Disk Utility Library
ii  libgee2                                       0.6.4-1                                 GObject based collection library
ii  libgegl-0.0-0                                 0.0.22-2ubuntu3                         Generic Graphics Library
ii  libgeis1                                      2.2.9.2-0ubuntu1                        Gesture engine interface support
ii  libgeoclue0                                   0.12.0-1ubuntu12                        C API for GeoClue
ii  libgeoip1                                     1.4.8+dfsg-2                            non-DNS IP-to-country resolver library
ii  libgettextpo0                                 0.18.1.1-5ubuntu3                       GNU Internationalization library
ii  libgfortran3                                  4.6.3-1ubuntu5                          Runtime library for GNU Fortran applications
ii  libgif4                                       4.1.6-9ubuntu1                          library for GIF images (library)
ii  libgimp2.0                                    2.6.12-1ubuntu1.2                       Libraries for the GNU Image Manipulation Program
ii  libgirepository-1.0-1                         1.32.0-1                                Library for handling GObject introspection data (runtime library)
ii  libgkeyfile1.0-cil                            0.1-2ubuntu2                            GObject-based wrapper library for GKeyFile -- CLI bindings
ii  libgksu2-0                                    2.0.13~pre1-5ubuntu2                    library providing su and sudo functionality
ii  libgl1-mesa-dri                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- GLX runtime
ii  libglade2-0                                   1:2.6.4-1ubuntu1.1                      library to load .glade files at runtime
ii  libglade2.0-cil                               2.12.10-2ubuntu4                        CLI binding for the Glade libraries 2.6
ii  libglapi-mesa                                 8.0.4-0ubuntu0.2                        free implementation of the GL API -- shared library
ii  libglew1.5                                    1.5.7.is.1.5.2-1ubuntu4                 The OpenGL Extension Wrangler - runtime environment
ii  libglew1.6                                    1.6.0-4                                 OpenGL Extension Wrangler - runtime environment
ii  libglib-perl                                  2:1.241-1                               interface to the GLib and GObject libraries
ii  libglib2.0-0                                  2.32.3-0ubuntu1                         GLib library of C routines
ii  libglib2.0-bin                                2.32.3-0ubuntu1                         Programs for the GLib library
ii  libglib2.0-cil                                2.12.10-2ubuntu4                        CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                               2.32.3-0ubuntu1                         Common files for GLib library
ii  libglibmm-2.4-1c2a                            2.32.0-0ubuntu1                         C++ wrapper for the GLib toolkit (shared libraries)
ii  libglu1-mesa                                  8.0.4-0ubuntu0.2                        Mesa OpenGL utility library (GLU)
ii  libgme0                                       0.5.5-2                                 Playback library for video game music files - shared library
ii  libgmime-2.6-0                                2.6.7-1                                 MIME message parser and creator library - runtime
ii  libgmp10                                      2:5.0.2+dfsg-2ubuntu1                   Multiprecision arithmetic library
ii  libgnome-bluetooth8                           3.2.2-0ubuntu5                          GNOME Bluetooth tools - support library
ii  libgnome-desktop-3-2                          3.4.2-0ubuntu0.1                        Utility library for loading .desktop files - runtime files
ii  libgnome-keyring-common                       3.2.2-2                                 GNOME keyring services library - data files
ii  libgnome-keyring0                             3.2.2-2                                 GNOME keyring services library
ii  libgnome-keyring1.0-cil                       1.0.0-3build1                           CLI library to access the GNOME Keyring daemon
ii  libgnome-menu-3-0                             3.4.0-0ubuntu1                          GNOME implementation of the freedesktop menu specification
ii  libgnome-menu2                                3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  libgnome-vfs2.0-cil                           2.24.2-1                                CLI binding for GnomeVFS 2.24
ii  libgnome2-0                                   2.32.1-2ubuntu1.1                       The GNOME library - runtime files
ii  libgnome2-bin                                 2.32.1-2ubuntu1.1                       The GNOME library - binary files
ii  libgnome2-common                              2.32.1-2ubuntu1.1                       The GNOME library - common files
ii  libgnome2.24-cil                              2.24.2-1                                CLI binding for GNOME 2.24
ii  libgnomecanvas2-0                             2.30.3-1ubuntu1.1                       powerful object-oriented display engine - runtime files
ii  libgnomecanvas2-common                        2.30.3-1ubuntu1.1                       powerful object-oriented display engine - common files
ii  libgnomeui-0                                  2.24.5-2ubuntu2                         GNOME user interface library - runtime files
ii  libgnomeui-common                             2.24.5-2ubuntu2                         GNOME user interface library - common files
ii  libgnomevfs2-0                                1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (runtime libraries)
ii  libgnomevfs2-common                           1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                            1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (extra modules)
rc  libgnustep-base1.22                           1.22.1-2ubuntu2                         GNUstep Base library
rc  libgnustep-gui0.20                            0.20.0-2                                GNUstep GUI Library
ii  libgnutls26                                   2.12.14-5ubuntu3.1                      GNU TLS library - runtime library
ii  libgoffice-0.8-8                              0.8.17-1                                Document centric objects library - runtime files
ii  libgoffice-0.8-8-common                       0.8.17-1                                Document centric objects library - common files
ii  libgomp1                                      4.6.3-1ubuntu5                          GCC OpenMP (GOMP) support library
ii  libgoocanvas-common                           0.15-1                                  translations for goocanvas
ii  libgoocanvas3                                 0.15-1                                  canvas widget for GTK+ that uses the cairo 2D library
ii  libgpg-error0                                 1.10-2ubuntu1                           library for common error values and messages in GnuPG components
ii  libgphoto2-2                                  2.4.13-1ubuntu1.2                       gphoto2 digital camera library
ii  libgphoto2-l10n                               2.4.13-1ubuntu1.2                       gphoto2 digital camera library - localized messages
ii  libgphoto2-port0                              2.4.13-1ubuntu1.2                       gphoto2 digital camera port library
ii  libgpm2                                       1.20.4-4                                General Purpose Mouse - shared library
ii  libgpod-common                                0.8.2-4                                 common files for libgpod
ii  libgpod4                                      0.8.2-4                                 library to read and write songs and artwork to an iPod
ii  libgps20                                      3.4-2                                   Global Positioning System - library
ii  libgrail5                                     3.0.6-0ubuntu0.12.04.01                 Gesture Recognition And Instantiation Library
ii  libgraph4                                     2.26.3-10ubuntu1                        rich set of graph drawing tools - graph library
ii  libgrip0                                      0.3.5-0ubuntu1~12.04.1                  provides multitouch gestures to GTK+ apps
ii  libgs9                                        9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - Library
ii  libgs9-common                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - common files
ii  libgsf-1-114                                  1.14.21-2                               Structured File Library - runtime version
ii  libgsf-1-common                               1.14.21-2                               Structured File Library - common files
ii  libgsl0ldbl                                   1.15+dfsg-1build1                       GNU Scientific Library (GSL) -- library package
ii  libgsm1                                       1.0.13-3                                Shared libraries for GSM speech compressor
ii  libgssapi-krb5-2                              1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgssapi3-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - GSSAPI support library
ii  libgssdp-1.0-3                                0.12.1-2                                GObject-based library for SSDP
ii  libgstreamer-perl                             0.16-1build1                            Perl interface to the GStreamer media processing framework
ii  libgstreamer-plugins-bad0.10-0                0.10.22.3-2ubuntu2.1                    GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0               0.10.36-1ubuntu0.1                      GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                            0.10.36-1ubuntu1                        Core GStreamer libraries and elements
ii  libgtk-3-0                                    3.4.2-0ubuntu0.5                        GTK+ graphical user interface library
ii  libgtk-3-bin                                  3.4.2-0ubuntu0.5                        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                               3.4.2-0ubuntu0.5                        common files for the GTK+ graphical user interface library
ii  libgtk-sharp-beans-cil                        2.14.1-2build2                          Supplementary CLI bindings for GTK 2.14+
ii  libgtk2-notify-perl                           0.05-3build1                            Perl interface to libnotify
ii  libgtk2-perl                                  2:1.223-1build3                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2-trayicon-perl                         0.06-1build2                            Perl interface to fill the system tray
ii  libgtk2.0-0                                   2.24.10-0ubuntu6                        GTK+ graphical user interface library
ii  libgtk2.0-bin                                 2.24.10-0ubuntu6                        programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                 2.12.10-2ubuntu4                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                              2.24.10-0ubuntu6                        common files for the GTK+ graphical user interface library
ii  libgtkmathview0c2a                            0.8.0-7                                 rendering engine for MathML documents
ii  libgtkmm-2.4-1c2a                             1:2.24.2-1ubuntu1                       C++ wrappers for GTK+ (shared libraries)
ii  libgtkmm-3.0-1                                3.4.0-0ubuntu1                          C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview-3.0-0                        3.4.2-0ubuntu1                          shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview-3.0-common                   3.4.2-0ubuntu1                          common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                                  2.0.16-1ubuntu5                         a spell-checking addon for GTK's TextView widget
ii  libgtop2-7                                    2.28.4-2                                gtop system monitoring library (shared)
ii  libgtop2-common                               2.28.4-2                                gtop system monitoring library (common)
ii  libgucharmap-2-90-7                           1:3.4.1.1-0ubuntu1                      Unicode browser widget library (shared library)
ii  libgudev-1.0-0                                1:175-0ubuntu9.2                        GObject-based wrapper library for libudev
ii  libgudev1.0-cil                               0.1-2build1                             GObject-based wrapper library for libudev -- CLI bindings
ii  libguile-ltdl-1                               1.6.8-10ubuntu4                         Guile's patched version of libtool's libltdl
ii  libgupnp-1.0-4                                0.18.1-2                                GObject-based library for UPnP
ii  libgupnp-igd-1.0-4                            0.2.1-2                                 library to handle UPnP IGD port mapping
ii  libgutenprint2                                5.2.8~pre1-0ubuntu2.1                   runtime for the Gutenprint printer driver library
ii  libgvc5                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - gvc library
ii  libhcrypto4-heimdal                           1.6~git20120311.dfsg.1-2                Heimdal Kerberos - crypto library
ii  libheimbase1-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - Base library
ii  libheimntlm0-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - NTLM support library
ii  libhpmud0                                     3.12.2-1ubuntu3.1                       HP Multi-Point Transport Driver (hpmud) run-time libraries
ii  libhsqldb-java                                1.8.0.10-9ubuntu2                       Java SQL database engine
ii  libhtml-form-perl                             6.00-1                                  module that represents an HTML form element
ii  libhtml-format-perl                           2.10-1                                  module for transforming HTML into various formats
ii  libhtml-parser-perl                           3.69-1build1                            collection of modules that parse HTML text documents
ii  libhtml-tagset-perl                           3.20-2                                  Data tables pertaining to HTML
ii  libhtml-tree-perl                             4.2-1                                   Perl module to represent and create HTML syntax trees
ii  libhttp-cookies-perl                          6.00-2                                  HTTP cookie jars
ii  libhttp-daemon-perl                           6.00-1                                  simple http server class
ii  libhttp-date-perl                             6.00-1                                  module of date conversion routines
ii  libhttp-message-perl                          6.01-1                                  perl interface to HTTP style messages
ii  libhttp-negotiate-perl                        6.00-2                                  implementation of content negotiation
ii  libhunspell-1.3-0                             1.3.2-4                                 spell checker and morphological analyzer (shared library)
ii  libhx509-5-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - X509 support library
ii  libhyphen0                                    2.8.3-1                                 ALTLinux hyphenation library - shared library
ii  libibus-1.0-0                                 1.4.1-3ubuntu1                          Intelligent Input Bus - shared library
ii  libical0                                      0.48-1ubuntu3                           iCalendar library implementation in C (runtime)
ii  libice6                                       2:1.0.7-2build1                         X11 Inter-Client Exchange library
ii  libicu48                                      4.8.1.1-3                               International Components for Unicode
ii  libid3tag0                                    0.15.1b-10build2                        ID3 tag reading library from the MAD project
ii  libidl-common                                 0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files (common files)
ii  libidl0                                       0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files
ii  libidn11                                      1.23-2                                  GNU Libidn library, implementation of IETF IDN specifications
ii  libido-0.1-0                                  0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libido3-0.1-0                                 0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libiec61883-0                                 1.2.0-0.1ubuntu1                        an partial implementation of IEC 61883
ii  libieee1284-3                                 0.2.11-10build1                         cross-platform library for parallel port access
ii  libijs-0.35                                   0.35-8                                  IJS raster image transport protocol: shared library
ii  libilmbase6                                   1.0.1-3build2                           several utility libraries from ILM used by OpenEXR
ii  libimlib2                                     1.4.4-1build1                           powerful image loading and rendering library
ii  libimobiledevice2                             1.1.1-4                                 Library for communicating with the iPhone and iPod Touch
ii  libindi-data                                  0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared data
ii  libindi0                                      0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared library
ii  libindicate-gtk3                              0.6.92-0ubuntu1                         library for raising indicators via DBus - GTK+ bindings
ii  libindicate5                                  0.6.92-0ubuntu1                         library for raising indicators via DBus
ii  libindicator-messages-status-provider1        0.6.0-0ubuntu2                          indicator status provider - shared library
ii  libindicator3-7                               0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libindicator7                                 0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libio-socket-inet6-perl                       2.69-2                                  object interface for AF_INET6 domain sockets
ii  libio-socket-ssl-perl                         1.53-1                                  Perl module implementing object oriented interface to SSL sockets
ii  libisc83                                      1:9.8.1.dfsg.P1-4ubuntu0.5              ISC Shared Library used by BIND
ii  libisccc80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Command Channel Library used by BIND
ii  libisccfg82                                   1:9.8.1.dfsg.P1-4ubuntu0.5              Config File Handling Library used by BIND
ii  libiso9660-8                                  0.83-1                                  library to work with ISO9660 filesystems
ii  libisofs6                                     1.1.6-1ubuntu1                          library to create ISO9660 images
ii  libiw30                                       30~pre9-5ubuntu2                        Wireless tools - library
ii  libjack-jackd2-0                              1.9.8~dfsg.1-1ubuntu1                   JACK Audio Connection Kit (libraries)
ii  libjasper1                                    1.900.1-13                              JasPer JPEG-2000 runtime library
ii  libjava3d-java                                1.5.2+dfsg-5                            Java 3D API (java library)
ii  libjava3d-jni                                 1.5.2+dfsg-5                            Java3D API (java jni library)
ii  libjavascriptcoregtk-1.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjavascriptcoregtk-3.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjbig2dec0                                  0.11-1ubuntu1                           JBIG2 decoder library - shared libraries
ii  libjline-java                                 1.0-1                                   Java library for handling console input
ii  libjpeg-progs                                 8c-2ubuntu7                             Programs for manipulating JPEG files (dependency package)
ii  libjpeg-turbo-progs                           1.1.90+svn733-0ubuntu4.1                Programs for manipulating JPEG files
ii  libjpeg-turbo8                                1.1.90+svn733-0ubuntu4.1                IJG JPEG compliant runtime library.
ii  libjpeg8                                      8c-2ubuntu7                             Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjs-jquery                                  1.7.1-1ubuntu1                          JavaScript library for dynamic web applications
ii  libjson-glib-1.0-0                            0.14.2-1                                GLib JSON manipulation library
ii  libjson-ruby                                  1.6.3-1                                 Transitional package for ruby-json
ii  libjson0                                      0.9-1ubuntu1                            JSON manipulation library - shared library
ii  libjte1                                       1.19-1                                  Jigdo Template Export - runtime library
ii  libk5crypto3                                  1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Crypto Library
rc  libkabc4                                      4:4.8.5-0ubuntu0.1                      library for handling address book data
rc  libkalarmcal2                                 4:4.8.5-0ubuntu0.1                      library for handling alarm calendar data
ii  libkate1                                      0.4.1-1                                 Kate is a codec for karaoke and text encapsulation
ii  libkatepartinterfaces4                        4:4.8.5-0ubuntu0.1                      kate part library
rc  libkcal4                                      4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalcore4                                  4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalutils4                                 4:4.8.5-0ubuntu0.1                      library with utility functions for the handling of calendar data
ii  libkcmutils4                                  4:4.8.5-0ubuntu0.1                      utility classes for using KCM modules
ii  libkde3support4                               4:4.8.5-0ubuntu0.1                      KDE 3 Support Library for the KDE 4 Platform
ii  libkdeclarative5                              4:4.8.5-0ubuntu0.1                      Declarative library for plasma
ii  libkdecore5                                   4:4.8.5-0ubuntu0.1                      KDE Platform Core Library
ii  libkdeedu-data                                4:4.8.5-0ubuntu0.1                      data files for libkdeedu
ii  libkdesu5                                     4:4.8.5-0ubuntu0.1                      Console-mode Authentication Library for the KDE Platform
ii  libkdeui5                                     4:4.8.5-0ubuntu0.1                      KDE Platform User Interface Library
ii  libkdewebkit5                                 4:4.8.5-0ubuntu0.1                      KDE WebKit Library
ii  libkdnssd4                                    4:4.8.5-0ubuntu0.1                      DNS-SD Protocol Library for the KDE Platform
ii  libkeduvocdocument4                           4:4.8.5-0ubuntu0.1                      library for reading and writing vocabulary files
ii  libkemoticons4                                4:4.8.5-0ubuntu0.1                      utility classes to deal with emoticon themes
ii  libkeybinder0                                 0.2.2-3build1                           registers global key bindings for applications
ii  libkeyutils1                                  1.5.2-2                                 Linux Key Management Utilities (library)
ii  libkfile4                                     4:4.8.5-0ubuntu0.1                      File Selection Dialog Library for KDE Platform
rc  libkholidays4                                 4:4.8.5-0ubuntu0.1                      holidays calculation library
ii  libkhtml5                                     4:4.8.5-0ubuntu0.1                      KHTML Web Content Rendering Engine
ii  libkidletime4                                 4:4.8.5-0ubuntu0.1                      library to provide information about idle time
rc  libkimap4                                     4:4.8.5-0ubuntu0.1                      library for handling IMAP data
ii  libkio5                                       4:4.8.5-0ubuntu0.1                      Network-enabled File Management Library for the KDE Platform
ii  libkjsapi4                                    4:4.8.5-0ubuntu0.1                      KJS API Library for the KDE Development Platform
ii  libkjsembed4                                  4:4.8.5-0ubuntu0.1                      library for binding JavaScript objects to QObjects
rc  libkldap4                                     4:4.8.5-0ubuntu0.1                      library for accessing LDAP
ii  libklibc                                      1.5.25-1ubuntu2                         minimal libc subset for use with initramfs
rc  libkmbox4                                     4:4.8.5-0ubuntu0.1                      library for handling mbox mailboxes
ii  libkmediaplayer4                              4:4.8.5-0ubuntu0.1                      KMediaPlayer Interface for the KDE Platform
rc  libkmime4                                     4:4.8.5-0ubuntu0.1                      library for handling MIME data
rc  libknewstuff2-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v2 Library for the KDE Platform
ii  libknewstuff3-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v3 Library for the KDE Platform
ii  libknotifyconfig4                             4:4.8.5-0ubuntu0.1                      library for configuring KDE Notifications
ii  libkntlm4                                     4:4.8.5-0ubuntu0.1                      NTLM Authentication Library for the KDE Platform
ii  libkparts4                                    4:4.8.5-0ubuntu0.1                      Framework for the KDE Platform Graphical Components
ii  libkpathsea5                                  2009-11ubuntu2                          TeX Live: path search library for TeX (runtime part)
rc  libkpimidentities4                            4:4.8.5-0ubuntu0.1                      library for managing user identities
rc  libkpimtextedit4                              4:4.8.5-0ubuntu0.1                      library that provides a textedit with PIM-specific features
rc  libkpimutils4                                 4:4.8.5-0ubuntu0.1                      library for dealing with email addresses
ii  libkprintutils4                               4:4.8.5-0ubuntu0.1                      utility classes to deal with printing
ii  libkpty4                                      4:4.8.5-0ubuntu0.1                      Pseudo Terminal Library for the KDE Platform
ii  libkrb5-26-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - libraries
ii  libkrb5-3                                     1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries
ii  libkrb5support0                               1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Support library
rc  libkresources4                                4:4.8.5-0ubuntu0.1                      KDE Resource framework library
ii  libkrosscore4                                 4:4.8.5-0ubuntu0.1                      Kross Core Library
ii  libktexteditor4                               4:4.8.5-0ubuntu0.1                      KTextEditor interfaces for the KDE Platform
ii  libkunitconversion4                           4:4.8.5-0ubuntu0.1                      Unit Conversion library for the KDE Platform
ii  liblapack3gf                                  3.3.1-1                                 library of linear algebra routines 3 - shared version
ii  liblaunchpad-integration-3.0-1                0.1.56.1                                library for launchpad integration
ii  liblaunchpad-integration-common               0.1.56.1                                library for launchpad integration common data
ii  liblaunchpad-integration1                     0.1.56.1                                library for launchpad integration
ii  liblcms1                                      1.19.dfsg-1ubuntu3                      Little CMS color management library
ii  liblcms2-2                                    2.2+git20110628-2ubuntu3                Little CMS 2 color management library
ii  libldap-2.4-2                                 2.4.28-1.1ubuntu4.2                     OpenLDAP libraries
ii  liblightdm-gobject-1-0                        1.2.1-0ubuntu1.1                        LightDM GObject client library
ii  liblightdm-qt-2-0                             1.2.1-0ubuntu1.1                        LightDM Qt client library
ii  liblink-grammar4                              4.7.4-2                                 Carnegie Mellon University's link grammar parser (libraries)
ii  liblircclient0                                0.9.0-0ubuntu1                          infra-red remote control support - client library
ii  libllvm3.0                                    3.0-4ubuntu1                            Low-Level Virtual Machine (LLVM), runtime library
ii  liblocale-gettext-perl                        1.05-7build1                            module using libc functions for internationalization in Perl
ii  liblockfile-bin                               1.09-3                                  support binaries for and cli utilities based on liblockfile
ii  liblockfile1                                  1.09-3                                  NFS-safe locking library
ii  libloudmouth1-0                               1.4.3-8                                 Lightweight C Jabber library
ii  liblqr-1-0                                    0.4.1-1.1                               converts plain array images into multi-size representation
ii  libltdl7                                      2.4.2-1ubuntu1                          A system independent dlopen wrapper for GNU libtool
ii  liblua5.1-0                                   5.1.4-12ubuntu1                         Shared library for the Lua interpreter version 5.1
ii  liblvm2app2.2                                 2.02.66-4ubuntu7.1                      LVM2 application library
ii  liblwp-mediatypes-perl                        6.01-1                                  module to guess media type for a file or a URL
ii  liblwp-protocol-https-perl                    6.02-1                                  https driver for LWP::UserAgent
ii  liblwres80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Lightweight Resolver Library used by BIND
ii  liblzma5                                      5.1.1alpha+20110809-3                   XZ-format compression library
ii  liblzo2-2                                     2.06-1                                  data compression library
ii  libmad0                                       0.15.1b-7ubuntu1                        MPEG audio decoder library
ii  libmagic1                                     5.09-2                                  File type determination library using "magic" numbers
ii  libmagick++4                                  8:6.6.9.7-5ubuntu3.2                    object-oriented C++ interface to ImageMagick
ii  libmagickcore4                                8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library
ii  libmagickcore4-extra                          8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library - extra codecs
ii  libmagickwand4                                8:6.6.9.7-5ubuntu3.2                    image manipulation library
ii  libmailtools-perl                             2.08-1                                  Manipulate email in perl programs
rc  libmailtransport4                             4:4.8.5-0ubuntu0.1                      mail transport service library
ii  libmarblewidget13                             4:4.8.5-0ubuntu0.1                      Marble globe widget library
ii  libmatroska5                                  1.3.0-1                                 extensible open standard audio/video container format (shared library)
ii  libmeanwhile1                                 1.0.2-4ubuntu1                          open implementation of the Lotus Sametime Community Client protocol
ii  libmhash2                                     0.9.9.9-1                               Library for cryptographic hashing and message authentication
rc  libmicroblog4                                 4:4.8.5-0ubuntu0.1                      library for using the Microblog Akonadi Resource
ii  libmimic0                                     1.0.4-2.1build1                         A video codec for Mimic V2.x content
ii  libminiupnpc8                                 1.6-3ubuntu1                            UPnP IGD client lightweight library
ii  libmjpegtools-1.9                             1:1.9.0-0.5ubuntu7                      MJPEG video capture/editting/playback MPEG encoding
ii  libmlt++3                                     0.7.6+git20120204-2                     MLT multimedia framework C++ wrapper (runtime)
ii  libmlt-data                                   0.7.6+git20120204-2                     multimedia framework (data)
ii  libmlt4                                       0.7.6+git20120204-2                     multimedia framework (runtime)
ii  libmms0                                       0.6.2-2                                 MMS stream protocol library - shared library
ii  libmng1                                       1.0.10-3                                Multiple-image Network Graphics library
ii  libmodplug1                                   1:0.8.8.4-1                             shared libraries for mod music based on ModPlug
ii  libmono-addins-gui0.2-cil                     0.6.2-2                                 GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                         0.6.2-2                                 addin framework for extensible CLI applications/libraries
ii  libmono-cairo4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono Cairo library (for CLI 4.0)
ii  libmono-corlib4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono core library (for CLI 4.0)
ii  libmono-data-tds4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Data Library (for CLI 4.0)
ii  libmono-i18n-west4.0-cil                      2.10.8.1-1ubuntu2.2                     Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono I18N base library (for CLI 4.0)
ii  libmono-posix4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono.Posix library (for CLI 4.0)
ii  libmono-security4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Security library (for CLI 4.0)
ii  libmono-sharpzip4.84-cil                      2.10.8.1-1ubuntu2.2                     Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono SIMD (for CLI 4.0)
ii  libmono-sqlite4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono Sqlite library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil           2.10.8.1-1ubuntu2.2                     Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Core library (for CLI 4.0)
ii  libmono-system-data4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Data library (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                 2.10.8.1-1ubuntu2.2                     Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil      2.10.8.1-1ubuntu2.2                     Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-security4.0-cil                2.10.8.1-1ubuntu2.2                     Mono System.Security library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil 2.10.8.1-1ubuntu2.2                     Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-services4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Web library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Xml library (for CLI 4.0)
ii  libmono-system4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono System libraries (for CLI 4.0)
ii  libmono-web4.0-cil                            2.10.8.1-1ubuntu2.2                     Mono.Web library (for CLI 4.0)
ii  libmono-zeroconf1.0-cil                       0.9.0-3                                 CLI library for multicast DNS service discovery
ii  libmount1                                     2.20.1-1ubuntu3                         block device id library
ii  libmp3lame0                                   3.99.3+repack1-1                        MP3 encoding library
ii  libmpc2                                       0.9-4                                   multiple precision complex floating-point library
ii  libmpcdec6                                    2:0.1~r459-1ubuntu1                     MusePack decoder - library
ii  libmpeg2-4                                    0.4.1-3                                 MPEG1 and MPEG2 video decoder library
ii  libmpfr4                                      3.1.0-3ubuntu2                          multiple precision floating-point computation
ii  libmpg123-0                                   1.12.1-3.2ubuntu1                       MPEG layer 1/2/3 audio decoder -- runtime library
ii  libmtdev1                                     1.1.0-2ubuntu1                          Multitouch Protocol Translation Library - shared library
ii  libmtp-common                                 1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) common files
ii  libmtp-runtime                                1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) runtime tools
ii  libmtp9                                       1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) library
ii  libmusicbrainz3-6                             3.0.2-2.1                               library to access the MusicBrainz.org database
ii  libmx-1.0-2                                   1.4.3-0ubuntu1                          toolkit for the Moblin user experience
ii  libmysqlclient18                              5.5.28-0ubuntu0.12.04.3                 MySQL database client library
ii  libmythes-1.2-0                               2:1.2.2-1                               simple thesaurus library
ii  libnautilus-extension1a                       1:3.4.2-0ubuntu6                        libraries for nautilus components - runtime version
ii  libncurses5                                   5.9-4                                   shared libraries for terminal handling
ii  libncursesw5                                  5.9-4                                   shared libraries for terminal handling (wide character support)
ii  libndesk-dbus1.0-cil                          0.6.0-5                                 CLI implementation of D-Bus
ii  libneon27-gnutls                              0.29.6-1                                HTTP and WebDAV client library (GnuTLS enabled)
ii  libnepomuk4                                   4:4.8.5-0ubuntu0.1                      Nepomuk Meta Data Library
ii  libnepomukdatamanagement4                     4:4.8.5-0ubuntu0.1                      Basic Nepomuk data manipulation interface
ii  libnepomukquery4a                             4:4.8.5-0ubuntu0.1                      Nepomuk Query Library for the KDE Platform
ii  libnepomuksync4                               4:4.8.5-0ubuntu0.1                      Nepomuk sync interface for the Backup and Sync service
ii  libnepomukutils4                              4:4.8.5-0ubuntu0.1                      Nepomuk Utility Library
ii  libnet-dbus-perl                              1.0.0-1build1                           Extension for the DBus bindings
ii  libnet-http-perl                              6.02-1                                  module providing low-level HTTP connection client
ii  libnet-ssleay-perl                            1.42-1build1                            Perl module for Secure Sockets Layer (SSL)
ii  libnetfilter-conntrack3                       0.9.1-1ubuntu1                          Netfilter netlink-conntrack library
ii  libnetpbm10                                   2:10.0-15                               Graphics conversion tools shared libraries
ii  libnettle4                                    2.4-1                                   low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52                                   0.52.11-2ubuntu10                       Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnfnetlink0                                 1.0.0-1                                 Netfilter netlink library
ii  libnice10                                     0.1.1-2ubuntu1                          ICE library (shared library)
ii  libnih-dbus1                                  1.0.3-4ubuntu9                          NIH D-Bus Bindings Library
ii  libnih1                                       1.0.3-4ubuntu9                          NIH Utility Library
ii  libnl-3-200                                   3.2.3-2ubuntu2                          library for dealing with netlink sockets
ii  libnl-genl-3-200                              3.2.3-2ubuntu2                          library for dealing with netlink sockets - generic netlink
ii  libnl-route-3-200                             3.2.3-2ubuntu2                          library for dealing with netlink sockets - route interface
ii  libnm-glib-vpn1                               0.9.4.0-0ubuntu4.1                      network management framework (GLib VPN shared library)
ii  libnm-glib4                                   0.9.4.0-0ubuntu4.1                      network management framework (GLib shared library)
ii  libnm-gtk-common                              0.9.4.1-0ubuntu2                        network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                    0.9.4.1-0ubuntu2                        network management framework (GNOME dialogs for wifi and mobile)
ii  libnm-util2                                   0.9.4.0-0ubuntu4.1                      network management framework (shared library)
ii  libnotify-bin                                 0.7.5-1                                 sends desktop notifications to a notification daemon (Utilities)
ii  libnotify0.4-cil                              0.4.0~r3032-4                           CLI library for desktop notifications
ii  libnotify4                                    0.7.5-1                                 sends desktop notifications to a notification daemon
ii  libnova-0.12-2                                0.12.2-0ubuntu2                         astronomical library
ii  libnspr4                                      4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnspr4-0d                                   4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnss-mdns                                   0.10-3.2                                NSS module for Multicast DNS name resolution
ii  libnss3                                       3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libnss3-1d                                    3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libntrack-qt4-1                               016-1ubuntu1                            Qt 4 API for ntrack
ii  libntrack0                                    016-1ubuntu1                            lightweight connectivity tracking library
rc  libobjc3                                      4.6.3-1ubuntu5                          Runtime library for GNU Objective-C applications
ii  libodbc1                                      2.2.14p2-5ubuntu3                       ODBC library for Unix
ii  libofa0                                       0.9.3-4                                 Library for acoustic fingerprinting
ii  libogg0                                       1.2.2~dfsg-1ubuntu1                     Ogg bitstream library
ii  liboil0.3                                     0.3.17-2ubuntu3                         Library of Optimized Inner Loops
ii  liboobs-1-5                                   3.0.0-1                                 GObject based interface to system-tools-backends - shared library
ii  libopenal-data                                1:1.13-4ubuntu3                         Software implementation of the OpenAL API (data files)
ii  libopenal1                                    1:1.13-4ubuntu3                         Software implementation of the OpenAL API (shared library)
ii  libopenbabel4                                 2.3.0+dfsg-3ubuntu3                     Chemical toolbox library
ii  libopencc1                                    0.3.0-1                                 simplified-traditional chinese conversion library - runtime
ii  libopencore-amrnb0                            0.1.2-1                                 Adaptive Multi Rate speech codec - shared library
ii  libopencore-amrwb0                            0.1.2-1                                 Adaptive Multi-Rate - Wideband speech codec - shared library
ii  libopencv-calib3d2.3                          2.3.1-7                                 computer vision Camera Calibration library
ii  libopencv-core2.3                             2.3.1-7                                 computer vision core library
ii  libopencv-features2d2.3                       2.3.1-7                                 computer vision Feature Detection and Descriptor Extraction library
ii  libopencv-flann2.3                            2.3.1-7                                 computer vision Clustering and Search in Multi-Dimensional spaces library
ii  libopencv-highgui2.3                          2.3.1-7                                 computer vision High-level GUI and Media I/O library
ii  libopencv-imgproc2.3                          2.3.1-7                                 computer vision Image Processing library
ii  libopencv-objdetect2.3                        2.3.1-7                                 computer vision Object Detection library
ii  libopenexr6                                   1.6.1-4.1                               runtime files for the OpenEXR image library
ii  libopenjpeg2                                  1.3+dfsg-4                              JPEG 2000 image compression/decompression library
ii  libopenobex1                                  1.5-2build1                             OBEX protocol library
ii  libopenspc0                                   0.3.99a-2                               library for playing SPC files
ii  liborbit2                                     1:2.14.19-0.1ubuntu1                    libraries for ORBit2 - a CORBA ORB
ii  liborc-0.4-0                                  1:0.4.16-1ubuntu2                       Library of Optimized Inner Loops Runtime Compiler
ii  libotr2                                       3.2.0-4ubuntu0.1                        Off-the-Record Messaging library
ii  libots0                                       0.5.0-2.1                               Open Text Summarizer (library)
ii  libp11-kit0                                   0.12-2ubuntu1                           Library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpam-cap                                    1:2.22-1ubuntu3                         PAM module for implementing capabilities
ii  libpam-ck-connector                           0.4.5-2                                 ConsoleKit PAM module
ii  libpam-gnome-keyring                          3.2.2-2ubuntu4                          PAM module to unlock the GNOME keyring upon login
ii  libpam-modules                                1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                            1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                                1.1.3-7ubuntu2                          Runtime support for the PAM library
ii  libpam0g                                      1.1.3-7ubuntu2                          Pluggable Authentication Modules library
ii  libpango-perl                                 1.222-1build1                           Perl module to layout and render international text
ii  libpango1.0-0                                 1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text
ii  libpangomm-1.4-1                              2.28.4-1ubuntu1                         C++ Wrapper for pango (shared libraries)
ii  libpaper-utils                                1.1.24+nmu1build1                       library for handling paper characteristics (utilities)
ii  libpaper1                                     1.1.24+nmu1build1                       library for handling paper characteristics
ii  libparted0debian1                             2.3-8ubuntu5.1                          disk partition manipulator - shared library
ii  libpathplan4                                  2.26.3-10ubuntu1                        rich set of graph drawing tools - pathplan library
ii  libpcap0.8                                    1.1.1-10                                system interface for user-level packet capture
ii  libpci3                                       1:3.1.8-2ubuntu5                        Linux PCI Utilities (shared library)
ii  libpciaccess0                                 0.12.902-1                              Generic PCI access library for X
ii  libpcre3                                      8.12-4                                  Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcsclite1                                  1.7.4-2ubuntu2                          Middleware to access a smart card using PC/SC (library)
ii  libpeas-1.0-0                                 1.2.0-1ubuntu1                          Application plugin library
ii  libpeas-common                                1.2.0-1ubuntu1                          Application plugin library (common files)
ii  libperl5.14                                   5.14.2-6ubuntu2.2                       shared Perl library
ii  libphonon4                                    4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - core library
ii  libpipeline1                                  1.2.1-1                                 pipeline manipulation library
ii  libpixman-1-0                                 0.24.4-1                                pixel-manipulation library for X and cairo
ii  libplasma3                                    4:4.8.5-0ubuntu0.1                      Plasma Library for the KDE Platform
ii  libplist1                                     1.8-1                                   Library for handling Apple binary and XML property lists
ii  libplymouth2                                  0.8.2-2ubuntu30                         graphical boot animation and logger - shared libraries
ii  libpng12-0                                    1.2.46-3ubuntu4                         PNG library - runtime
ii  libpolkit-agent-1-0                           0.104-1ubuntu1                          PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0                         0.104-1ubuntu1                          PolicyKit backend API
ii  libpolkit-gobject-1-0                         0.104-1ubuntu1                          PolicyKit Authorization API
ii  libpolkit-qt-1-1                              0.103.0-1                               PolicyKit-qt-1 library
ii  libpoppler-glib8                              0.18.4-1ubuntu3                         PDF rendering library (GLib-based shared library)
ii  libpoppler19                                  0.18.4-1ubuntu3                         PDF rendering library
ii  libpopt0                                      1.16-3ubuntu1                           lib for parsing cmdline parameters
ii  libportaudio2                                 19+svn20111121-1                        Portable audio I/O - shared library
ii  libportsmf0                                   0.1~svn20101010-3                       Portable Standard Midi File Library
ii  libpostproc-extra-52                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libpostproc52                                 4:0.8.4-0ubuntu0.12.04.1                Libav video postprocessing library
rc  libprison0                                    1.0+dfsg-1                              barcode API for Qt
ii  libproxy1                                     0.4.7-0ubuntu4.1                        automatic proxy configuration management library (shared)
ii  libpulse-mainloop-glib0                       1:1.1-0ubuntu15.1                       PulseAudio client libraries (glib support)
ii  libpulse0                                     1:1.1-0ubuntu15.1                       PulseAudio client libraries
ii  libpulsedsp                                   1:1.1-0ubuntu15.1                       PulseAudio OSS pre-load library
ii  libpurple-bin                                 1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library - extra utilities
ii  libpurple0                                    1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library
ii  libpython2.7                                  2.7.3-0ubuntu3.1                        Shared Python runtime library (version 2.7)
ii  libpython3.2                                  3.2.3-0ubuntu3.2                        Shared Python runtime library (version 3.2)
ii  libqalculate5                                 0.9.7-6ubuntu2                          Powerful and easy to use desktop calculator - library
ii  libqapt-runtime                               1.3.1-0ubuntu2                          Runtime components for the QApt library
ii  libqapt1                                      1.3.1-0ubuntu2                          QApt library package
ii  libqca2                                       2.0.3-2                                 libraries for the Qt Cryptographic Architecture
ii  libqimageblitz4                               1:0.0.6-4                               QImageBlitz image effects library
rc  libqrencode3                                  3.1.1-1ubuntu1                          QR Code encoding library
ii  libqt3-mt                                     3:3.3.8-b-8ubuntu3                      Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-dbus                                   4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus module
ii  libqt4-declarative                            4:4.8.1-0ubuntu4.3                      Qt 4 Declarative module
ii  libqt4-designer                               4:4.8.1-0ubuntu4.3                      Qt 4 designer module
ii  libqt4-help                                   4:4.8.1-0ubuntu4.3                      Qt 4 help module
ii  libqt4-network                                4:4.8.1-0ubuntu4.3                      Qt 4 network module
ii  libqt4-opengl                                 4:4.8.1-0ubuntu4.3                      Qt 4 OpenGL module
ii  libqt4-qt3support                             4:4.8.1-0ubuntu4.3                      Qt 3 compatibility library for Qt 4
ii  libqt4-script                                 4:4.8.1-0ubuntu4.3                      Qt 4 script module
ii  libqt4-scripttools                            4:4.8.1-0ubuntu4.3                      Qt 4 script tools module
ii  libqt4-sql                                    4:4.8.1-0ubuntu4.3                      Qt 4 SQL module
ii  libqt4-sql-mysql                              4:4.8.1-0ubuntu4.3                      Qt 4 MySQL database driver
ii  libqt4-svg                                    4:4.8.1-0ubuntu4.3                      Qt 4 SVG module
ii  libqt4-test                                   4:4.8.1-0ubuntu4.3                      Qt 4 test module
ii  libqt4-xml                                    4:4.8.1-0ubuntu4.3                      Qt 4 XML module
ii  libqt4-xmlpatterns                            4:4.8.1-0ubuntu4.3                      Qt 4 XML patterns module
ii  libqtassistantclient4                         4.6.3-3ubuntu2                          Qt Assistant client library (runtime)
ii  libqtcore4                                    4:4.8.1-0ubuntu4.3                      Qt 4 core module
ii  libqtgui4                                     4:4.8.1-0ubuntu4.3                      Qt 4 GUI module
ii  libqthreads-12                                1.6.8-10ubuntu4                         QuickThreads library for Guile
ii  libqtwebkit4                                  2.2.1-1ubuntu4                          Web content engine library for Qt
ii  libquadmath0                                  4.6.3-1ubuntu5                          GCC Quad-Precision Math Library
ii  libquicktime2                                 2:1.2.3-4build2                         library for reading and writing Quicktime files
ii  libquvi-scripts                               0.4.2-1                                 library for parsing video download links (Lua scripts)
ii  libquvi7                                      0.4.0-1                                 library for parsing video download links (runtime libraries)
ii  libraptor2-0                                  2.0.6-1                                 Raptor 2 RDF syntax library
ii  librarian0                                    0.8.1-5                                 Documentation meta-data library (library package)
ii  librasqal3                                    0.9.28-1                                Rasqal RDF query library
ii  libraw1394-11                                 2.0.7-1ubuntu1                          library for direct access to IEEE 1394 bus (aka FireWire)
ii  librdf0                                       1.0.14-1                                Redland Resource Description Framework (RDF) library
ii  libreadline5                                  5.2-11                                  GNU readline and history libraries, run-time libraries
ii  libreadline6                                  6.2-8                                   GNU readline and history libraries, run-time libraries
ii  libreoffice                                   1:3.5.4-0ubuntu1.1                      office productivity suite
ii  libreoffice-base                              1:3.5.4-0ubuntu1.1                      office productivity suite -- database
ii  libreoffice-base-core                         1:3.5.4-0ubuntu1.1                      office productivity suite -- shared library
ii  libreoffice-calc                              1:3.5.4-0ubuntu1.1                      office productivity suite -- spreadsheet
ii  libreoffice-common                            1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent files
ii  libreoffice-core                              1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-dependent files
ii  libreoffice-draw                              1:3.5.4-0ubuntu1.1                      office productivity suite -- drawing
ii  libreoffice-emailmerge                        1:3.5.4-0ubuntu1.1                      office productivity suite -- email mail merge
ii  libreoffice-filter-mobiledev                  1:3.5.4-0ubuntu1.1                      office productivity suite -- mobile devices filters
ii  libreoffice-gnome                             1:3.5.4-0ubuntu1.1                      office productivity suite -- GNOME integration
ii  libreoffice-gtk                               1:3.5.4-0ubuntu1.1                      office productivity suite -- GTK+ integration
ii  libreoffice-impress                           1:3.5.4-0ubuntu1.1                      office productivity suite -- presentation
ii  libreoffice-java-common                       1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent Java support files
ii  libreoffice-math                              1:3.5.4-0ubuntu1.1                      office productivity suite -- equation editor
ii  libreoffice-style-human                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Human symbol style
ii  libreoffice-style-tango                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Tango symbol style
ii  libreoffice-writer                            1:3.5.4-0ubuntu1.1                      office productivity suite -- word processor
ii  libresid-builder0c2a                          2.1.1-12                                SID chip emulation class based on resid
ii  librhythmbox-core5                            2.96-0ubuntu4.2                         support library for the rhythmbox music player
ii  libroken18-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - roken support library
ii  librsvg2-2                                    2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (runtime)
ii  librsvg2-common                               2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (extra runtime)
ii  librtmp0                                      2.4~20110711.gitc28f1bab-1              toolkit for RTMP streams (shared library)
ii  libruby                                       4.8                                     Transitional package for libruby1.8
ii  libruby1.8                                    1.8.7.352-2ubuntu1.1                    Libraries necessary to run Ruby 1.8
ii  libsamplerate0                                0.1.8-4                                 Audio sample rate conversion library
ii  libsane                                       1.0.22-7ubuntu1                         API library for scanners
ii  libsane-common                                1.0.22-7ubuntu1                         API library for scanners -- documentation and support files
ii  libsane-hpaio                                 3.12.2-1ubuntu3.1                       HP SANE backend for multi-function peripherals
ii  libsasl2-2                                    2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - authentication abstraction library
ii  libsasl2-modules                              2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - pluggable authentication modules
ii  libschroedinger-1.0-0                         1.0.11-1                                library for encoding/decoding of Dirac video streams
ii  libsdl-image1.2                               1.2.10-3                                image loading library for Simple DirectMedia Layer 1.2
ii  libsdl1.2debian                               1.2.14-6.4ubuntu3                       Simple DirectMedia Layer
ii  libselinux1                                   2.1.0-4.1ubuntu1                        SELinux runtime shared libraries
ii  libsensors4                                   1:3.3.1-2ubuntu1                        library to read temperature/voltage/fan sensors
ii  libservlet2.5-java                            6.0.35-1ubuntu3.1                       Servlet 2.5 and JSP 2.1 Java API classes
ii  libsexy2                                      0.1.11-2build2                          collection of additional GTK+ widgets - library
ii  libsgutils2-2                                 1.33-1                                  utilities for devices using the SCSI command set (shared libraries)
ii  libshadow-ruby1.8                             1.4.1-8build1                           Interface of shadow password for Ruby 1.8
ii  libshout3                                     2.2.2-7ubuntu1                          MP3/Ogg Vorbis broadcast streaming library
ii  libsidplay1                                   1.36.59-5                               SID (MOS 6581) emulation library
ii  libsidplay2                                   2.1.1-12                                SID (MOS 6581) emulation library
ii  libsigc++-2.0-0c2a                            2.2.10-0ubuntu2                         type-safe Signal Framework for C++ - runtime
ii  libslang2                                     2.2.4-3ubuntu1                          S-Lang programming library - runtime version
ii  libslp1                                       1.2.1-7.8ubuntu1                        OpenSLP libraries
ii  libslv2-9                                     0.6.6+dfsg1-1                           library for simple use of LV2 plugins
ii  libsm6                                        2:1.2.0-2build1                         X11 Session Management library
ii  libsmbclient                                  2:3.6.3-2ubuntu2.3                      shared library for communication with SMB/CIFS servers
ii  libsndfile1                                   1.0.25-4                                Library for reading/writing audio files
ii  libsnmp-base                                  5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) MIBs and documentation
ii  libsnmp15                                     5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) library
ii  libsocket6-perl                               0.23-1build2                            Perl extensions for IPv6
ii  libsolid4                                     4:4.8.5-0ubuntu0.1                      Solid Library for KDE Platform
ii  libsonic0                                     0.1.17-1.1                              Simple library to speed up or slow down speech
ii  libsoprano4                                   2.7.5+dfsg.1-0ubuntu1                   libraries for the Soprano RDF framework
ii  libsoundtouch0                                1.6.0-2build1                           Sound stretching library
ii  libsoup-gnome2.4-1                            2.38.1-1                                HTTP library implementation in C -- GNOME support library
ii  libsoup2.4-1                                  2.38.1-1                                HTTP library implementation in C -- Shared library
ii  libsox-fmt-alsa                               14.3.2-3                                SoX alsa format I/O library
ii  libsox-fmt-base                               14.3.2-3                                Minimal set of SoX format libraries
ii  libsox1b                                      14.3.2-3                                SoX library of audio effects and processing
ii  libspandsp2                                   0.0.6~pre18-2build1                     Telephony signal processing library
ii  libspectre1                                   0.2.6-1build1                           Library for rendering PostScript documents
ii  libspeechd2                                   0.7.1-6ubuntu3                          Speech Dispatcher: Shared libraries
ii  libspeex1                                     1.2~rc1-3ubuntu2                        The Speex codec runtime library
ii  libspeexdsp1                                  1.2~rc1-3ubuntu2                        The Speex extended runtime library
ii  libsqlite3-0                                  3.7.9-2ubuntu1.1                        SQLite 3 shared library
ii  libss2                                        1.42-1ubuntu2                           command-line interface parsing library
ii  libssh-4                                      0.5.2-1ubuntu0.12.04.1                  tiny C SSH library
ii  libssl1.0.0                                   1.0.1-4ubuntu5.5                        SSL shared libraries
ii  libstartup-notification0                      0.12-1ubuntu1                           library for program launch feedback (shared library)
ii  libstdc++6                                    4.6.3-1ubuntu5                          GNU Standard C++ Library v3
ii  libstdc++6-4.6-dev                            4.6.3-1ubuntu5                          GNU Standard C++ Library v3 (development files)
ii  libstlport4.6ldbl                             4.6.2-7                                 STLport C++ class library
ii  libstreamanalyzer0                            0.7.7-1.1ubuntu3                        streamanalyzer library for Strigi Desktop Search
ii  libstreams0                                   0.7.7-1.1ubuntu3                        streams library for for Strigi Desktop Search
ii  libsvga1                                      1:1.4.3-31                              console SVGA display libraries
ii  libswitch-perl                                2.16-2                                  switch statement for Perl
ii  libswscale-extra-2                            4:0.8.4ubuntu0.12.04.1                  Libav video software scaling library
rc  libswscale2                                   4:0.8.4-0ubuntu0.12.04.1                Libav video scaling library
ii  libsysfs2                                     2.1.0+repack-1                          interface library to sysfs
ii  libt1-5                                       5.1.2-3.4ubuntu1                        Type 1 font rasterizer library - runtime
ii  libtag1-vanilla                               1.7-1ubuntu5                            audio meta-data library - vanilla flavour
ii  libtag1c2a                                    1.7-1ubuntu5                            audio meta-data library
ii  libtagc0                                      1.7-1ubuntu5                            audio meta-data library - C bindings
ii  libtaglib2.0-cil                              2.0.4.0-1                               CLI library for accessing audio and video files metadata
ii  libtalloc2                                    2.0.7-3                                 hierarchical pool based memory allocator
ii  libtar0                                       1.2.11-8                                C library for manipulating tar archives
ii  libtasn1-3                                    2.10-1ubuntu1.1                         Manage ASN.1 structures (runtime)
ii  libtdb1                                       1.2.9-4                                 Trivial Database - shared library
ii  libtelepathy-glib0                            0.18.0-1ubuntu1                         Telepathy framework - GLib library
ii  libtext-charwidth-perl                        0.04-7build1                            get display widths of characters on the terminal
ii  libtext-iconv-perl                            1.7-5                                   converts between character sets in Perl
ii  libtext-wrapi18n-perl                         0.06-7                                  internationalized substitute of Text::Wrap
ii  libthai-data                                  0.1.16-3                                Data files for Thai language support library
ii  libthai0                                      0.1.16-3                                Thai language support library
ii  libtheora0                                    1.1.1+dfsg.1-3ubuntu2                   The Theora Video Compression Codec
ii  libthreadweaver4                              4:4.8.5-0ubuntu0.1                      ThreadWeaver Library for the KDE Platform
ii  libthunarx-2-0                                1.2.3-3ubuntu2                          extension library for thunar
ii  libtidy-0.99-0                                20091223cvs-1ubuntu2                    HTML syntax checker and reformatter - library
ii  libtie-ixhash-perl                            1.21-2                                  ordered associative arrays for Perl
ii  libtiff4                                      3.9.5-2ubuntu1.4                        Tag Image File Format (TIFF) library
ii  libtimedate-perl                              1.2000-1                                collection of modules to manipulate date/time information
ii  libtinfo5                                     5.9-4                                   shared low-level terminfo library for terminal handling
ii  libtommath0                                   0.42.0-1                                multiple-precision integer library [runtime]
ii  libtotem-plparser17                           3.4.1-1                                 Totem Playlist Parser library - runtime files
ii  libts-0.0-0                                   1.0-10                                  touch screen library
ii  libtumbler-1-0                                0.1.24-0ubuntu1                         library for tumbler, a D-Bus thumbnailing service
ii  libtwolame0                                   0.3.13-1build1                          MPEG Audio Layer 2 encoding library
ii  libudev0                                      175-0ubuntu9.2                          udev library
ii  libunique-1.0-0                               1.1.6-4                                 Library for writing single instance applications - shared libraries
ii  libunistring0                                 0.9.3-5                                 Unicode string library for C
ii  libunity9                                     5.12.0-0ubuntu1.1                       binding to get places into the launcher - shared library
ii  libupnp3                                      1:1.6.6-5.1                             Portable SDK for UPnP Devices, version 1.6 (shared libraries)
ii  libupower-glib1                               0.9.15-3git1                            abstraction for power management - shared library
ii  liburi-perl                                   1.59-1                                  module to manipulate and access URI strings
ii  libusb-0.1-4                                  2:0.1.12-20                             userspace USB programming library
ii  libusb-1.0-0                                  2:1.0.9~rc3-2ubuntu1                    userspace USB programming library
ii  libusbmuxd1                                   1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libutempter0                                  1.1.5-4                                 A privileged helper for utmp/wtmp updates (runtime)
ii  libutouch-evemu1                              1.0.9-0ubuntu1                          KernelInput Event Device Emulation Library
ii  libutouch-frame1                              2.2.3-0ubuntu1                          Touch Frame Library
ii  libutouch-geis1                               2.2.9-0ubuntu3                          Gesture engine interface support
ii  libutouch-grail1                              3.0.5-0ubuntu1                          Gesture Recognition And Instantiation Library
ii  libuuid-perl                                  0.02-4ubuntu1                           Perl extension for using UUID interfaces as defined in e2fsprogs
ii  libuuid1                                      2.20.1-1ubuntu3                         Universally Unique ID library
ii  libv4l-0                                      0.8.6-1ubuntu2                          Collection of video4linux support libraries
ii  libv4lconvert0                                0.8.6-1ubuntu2                          Video4linux frame format conversion library
ii  libva-x11-1                                   1.0.15-4                                Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva1                                        1.0.15-4                                Video Acceleration (VA) API for Linux -- runtime
ii  libvamp-hostsdk3                              2.1-1                                   helper library for Vamp hosts written in C++
ii  libvcdinfo0                                   0.7.23-4.1ubuntu1                       library to extract information from VideoCD
ii  libvdpau1                                     0.4.1-3ubuntu1.1                        Video Decode and Presentation API for Unix (libraries)
ii  libvecmath-java                               1.5.2-3                                 javax.vecmath vector math package
ii  libvirtodbc0                                  6.1.4+dfsg1-0ubuntu1                    high-performance database - ODBC libraries
ii  libvisual-0.4-0                               0.4.0-4                                 Audio visualization framework
ii  libvisual-0.4-plugins                         0.4.0.dfsg.1-7                          Audio visualization framework plugins
ii  libvlc5                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer library
ii  libvlccore5                                   2.0.3-0ubuntu0.12.04.1                  base library for VLC and its modules
ii  libvo-aacenc0                                 0.1.1-2                                 VisualOn AAC encoder library
ii  libvo-amrwbenc0                               0.1.1-2                                 VisualOn AMR-WB encoder library
ii  libvorbis0a                                   1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Decoder library)
ii  libvorbisenc2                                 1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Encoder library)
ii  libvorbisfile3                                1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (High Level API)
ii  libvpx1                                       1.0.0-1                                 VP8 video codec (shared library)
ii  libvte-2.90-9                                 1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - runtime files
ii  libvte-2.90-common                            1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - common files
ii  libvte-common                                 1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.x - common files
ii  libvte9                                       1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.0 - runtime files
ii  libwavpack1                                   4.60.1-2                                audio codec (lossy and lossless) - library
ii  libwbclient0                                  2:3.6.3-2ubuntu2.3                      Samba winbind client library
ii  libwebkitgtk-1.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwildmidi-config                            0.2.3.4-2.1                             software MIDI player configuration
ii  libwildmidi1                                  0.2.3.4-2.1                             software MIDI player library
ii  libwind0-heimdal                              1.6~git20120311.dfsg.1-2                Heimdal Kerberos - stringprep implementation
ii  libwmf-bin                                    0.2.8.4-10ubuntu1                       Windows metafile conversion tools
ii  libwmf0.2-7                                   0.2.8.4-10ubuntu1                       Windows metafile conversion library
ii  libwnck-3-0                                   3.4.0-0ubuntu1                          Window Navigator Construction Kit - runtime files
ii  libwnck-3-common                              3.4.0-0ubuntu1                          Window Navigator Construction Kit - common files
ii  libwnck-common                                1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - common files
ii  libwnck22                                     1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - runtime files
ii  libwpd-0.9-9                                  0.9.4-1                                 Library for handling WordPerfect documents (shared library)
ii  libwpg-0.2-2                                  0.2.1-1                                 WordPerfect graphics import/convert library (shared library)
ii  libwps-0.2-2                                  0.2.4-1                                 Works text file format import filter library (shared library)
ii  libwrap0                                      7.6.q-21                                Wietse Venema's TCP wrappers library
ii  libwv-1.2-4                                   1.2.9-2                                 Library for accessing Microsoft Word documents
ii  libwww-perl                                   6.03-1                                  simple and consistent interface to the world-wide web
ii  libwww-robotrules-perl                        6.01-1                                  database of robots.txt-derived permissions
ii  libwxbase2.8-0                                2.8.12.1-6ubuntu2                       wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxgtk2.8-0                                 2.8.12.1-6ubuntu2                       wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libx11-6                                      2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-data                                   2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-xcb1                                   2:1.4.99.1-0ubuntu2                     Xlib/XCB interface library
ii  libx264-120                                   2:0.120.2151+gita3f4407-2               x264 video coding library
ii  libx86-1                                      1.1+ds1-7ubuntu1                        x86 real-mode library
ii  libxapian22                                   1.2.8-1                                 Search engine library
ii  libxatracker1                                 8.0.4-0ubuntu0.2                        X acceleration library -- runtime
ii  libxau6                                       1:1.0.6-4                               X11 authorisation library
ii  libxaw7                                       2:1.0.9-3ubuntu1                        X11 Athena Widget library
ii  libxcb-composite0                             1.8.1-1ubuntu0.1                        X C Binding, composite extension
ii  libxcb-dri2-0                                 1.8.1-1ubuntu0.1                        X C Binding, dri2 extension
ii  libxcb-glx0                                   1.8.1-1ubuntu0.1                        X C Binding, glx extension
ii  libxcb-keysyms1                               0.3.8-1build1                           utility libraries for X C Binding -- keysyms
ii  libxcb-randr0                                 1.8.1-1ubuntu0.1                        X C Binding, randr extension
ii  libxcb-render0                                1.8.1-1ubuntu0.1                        X C Binding, render extension
ii  libxcb-shape0                                 1.8.1-1ubuntu0.1                        X C Binding, shape extension
ii  libxcb-shm0                                   1.8.1-1ubuntu0.1                        X C Binding, shm extension
ii  libxcb-util0                                  0.3.8-2                                 utility libraries for X C Binding -- atom, aux and event
ii  libxcb-xv0                                    1.8.1-1ubuntu0.1                        X C Binding, xv extension
ii  libxcb1                                       1.8.1-1ubuntu0.1                        X C Binding
ii  libxcomposite1                                1:0.4.3-2build1                         X11 Composite extension library
ii  libxcursor1                                   1:1.1.12-1                              X cursor management library
ii  libxdamage1                                   1:1.1.3-2build1                         X11 damaged region extension library
ii  libxdmcp6                                     1:1.1.0-4                               X11 Display Manager Control Protocol library
ii  libxerces2-java                               2.11.0-4                                Validating XML parser for Java with DOM level 3 support
ii  libxext6                                      2:1.3.0-3build1                         X11 miscellaneous extension library
ii  libxfce4ui-1-0                                4.8.1-1                                 widget library for Xfce
ii  libxfce4util-bin                              4.8.2-1                                 tools for libxfce4util
ii  libxfce4util-common                           4.8.2-1                                 common files for libxfce4util
ii  libxfce4util4                                 4.8.2-1                                 Utility functions library for Xfce4
ii  libxfcegui4-4                                 4.8.1-5ubuntu1                          Basic GUI C functions for Xfce4
ii  libxfconf-0-2                                 4.8.1-1                                 Client library for Xfce4 configure interface
ii  libxfixes3                                    1:5.0-4ubuntu4                          X11 miscellaneous 'fixes' extension library
ii  libxfont1                                     1:1.4.4-1                               X11 font rasterisation library
ii  libxft2                                       2.2.0-3ubuntu2                          FreeType-based font drawing library for X
ii  libxi6                                        2:1.6.0-0ubuntu2                        X11 Input extension library
ii  libxinerama1                                  2:1.1.1-3build1                         X11 Xinerama extension library
ii  libxkbfile1                                   1:1.0.7-1ubuntu0.1                      X11 keyboard file manipulation library
ii  libxklavier16                                 5.2.1-1ubuntu1                          X Keyboard Extension high-level API
ii  libxml-commons-external-java                  1.4.01-2                                XML Commons external code - DOM, SAX, and JAXP, etc
ii  libxml-commons-resolver1.1-java               1.2-7                                   XML entity and URI resolver library
ii  libxml-parser-perl                            2.41-1build1                            Perl module for parsing XML files
ii  libxml-twig-perl                              1:3.39-1ubuntu1                         Perl module for processing huge XML documents in tree mode
ii  libxml-xpath-perl                             1.13-7                                  Perl module for processing XPath
ii  libxml2                                       2.7.8.dfsg-5.1ubuntu4.3                 GNOME XML library
ii  libxml2-utils                                 2.7.8.dfsg-5.1ubuntu4.3                 XML utilities
ii  libxmmsclient6                                0.8+dfsg-2                              XMMS2 - client library
ii  libxmu6                                       2:1.1.0-3                               X11 miscellaneous utility library
ii  libxmuu1                                      2:1.1.0-3                               X11 miscellaneous micro-utility library
ii  libxp6                                        1:1.0.1-2                               X Printing Extension (Xprint) client library
ii  libxpm4                                       1:3.5.9-4                               X11 pixmap library
ii  libxrandr2                                    2:1.3.2-2                               X11 RandR extension library
ii  libxrender1                                   1:0.9.6-2build1                         X Rendering Extension client library
ii  libxres1                                      2:1.0.5-1                               X11 Resource extension library
ii  libxslt1.1                                    1.1.26-8ubuntu1.2                       XSLT 1.0 processing library - runtime library
ii  libxss1                                       1:1.2.1-2                               X11 Screen Saver extension library
ii  libxt6                                        1:1.1.1-2build1                         X11 toolkit intrinsics library
ii  libxtst6                                      2:1.2.0-4                               X11 Testing -- Record extension library
ii  libxv1                                        2:1.0.6-2build1                         X11 Video extension library
ii  libxvidcore4                                  2:1.3.2-6                               Open source MPEG-4 video codec (library)
ii  libxvmc1                                      2:1.0.6-1ubuntu2                        X11 Video extension library
ii  libxxf86dga1                                  2:1.1.2-1                               X11 Direct Graphics Access extension library
ii  libxxf86vm1                                   1:1.1.1-2build1                         X11 XFree86 video mode extension library
ii  libyajl1                                      1.0.12-2                                Yet Another JSON Library
ii  libyaml-tiny-perl                             1.50-1                                  Perl module for reading and writing YAML files
ii  libyelp0                                      3.4.1-0ubuntu1                          Library for the GNOME help browser
ii  libzbar0                                      0.10+doc-7build2                        bar code scanner and decoder (library)
ii  libzeitgeist-1.0-1                            0.3.18-1ubuntu1                         library to access Zeitgeist - shared library
ii  libzephyr4                                    3.0.1-1                                 Project Athena's notification service - non-Kerberos libraries
ii  libzvbi-common                                0.2.33-4                                Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0                                      0.2.33-4                                Vertical Blanking Interval decoder (VBI) - runtime files
ii  lightdm                                       1.2.1-0ubuntu1.1                        Display Manager
ii  lightdm-gtk-greeter                           1.1.5-0ubuntu1.1                        LightDM GTK+ Greeter
ii  lightdm-kde-greeter                           0.1.1-0ubuntu0.1                        LightDM KDE greeter
ii  link-grammar-dictionaries-en                  4.7.4-2                                 Carnegie Mellon University's link grammar parser (English dictionary)
ii  linux-firmware                                1.79.1                                  Firmware for Linux kernel drivers
ii  linux-generic                                 3.2.0.35.40                             Complete Generic Linux kernel
ii  linux-headers-3.2.0-35                        3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic                3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                         3.2.0.35.40                             Generic Linux kernel headers
ii  linux-image-3.2.0-29-generic                  3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic                  3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic                  3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic                  3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                           3.2.0.35.40                             Generic Linux kernel image
ii  linux-libc-dev                                3.2.0-35.55                             Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu1                    base package for ALSA and OSS sound systems
ii  locales                                       2.13+git20120306-3                      common files for locale support
ii  lockfile-progs                                0.1.16                                  Programs for locking and unlocking files and mailboxes
ii  login                                         1:4.1.4.2+svn3283-3ubuntu5.1            system login tools
ii  logrotate                                     3.7.8-6ubuntu5                          Log rotation utility
ii  lp-solve                                      5.5.0.13-7                              Solve (mixed integer) linear programming problems
ii  lsb-base                                      4.0-0ubuntu20.2                         Linux Standard Base 4.0 init script functionality
ii  lsb-release                                   4.0-0ubuntu20.2                         Linux Standard Base version reporting utility
ii  lshw                                          02.15-2                                 information about hardware configuration
ii  lsof                                          4.81.dfsg.1-1build1                     List open files
ii  ltrace                                        0.5.3-2.1ubuntu2                        Tracks runtime library calls in dynamically linked programs
ii  lynx-cur                                      2.8.8dev.9-2ubuntu0.12.04.1             Text-mode WWW Browser with NLS support (development version)
ii  m4                                            1.4.16-2ubuntu1                         a macro processing language
rc  mahjongg                                      1:3.4.1-0ubuntu2.1                      classic Eastern tile game for GNOME
ii  make                                          3.81-8.1ubuntu1.1                       An utility for Directing compilation.
ii  makedev                                       2.3.1-89ubuntu2                         creates device files in /dev
ii  man-db                                        2.6.1-2ubuntu1                          on-line manual pager
ii  manpages                                      3.35-0.1ubuntu1                         Manual pages about using a GNU/Linux system
ii  manpages-dev                                  3.35-0.1ubuntu1                         Manual pages about using GNU/Linux for development
ii  marble                                        4:4.8.5-0ubuntu0.1                      globe and map widget
ii  marble-data                                   4:4.8.5-0ubuntu0.1                      data files for Marble
ii  marble-plugins                                4:4.8.5-0ubuntu0.1                      plugins for Marble
ii  mawk                                          1.3.3-17                                a pattern scanning and text processing language
ii  media-player-info                             16-1                                    Media player identification files
ii  melt                                          0.7.6+git20120204-2                     command line media player and video editor
ii  memtest86+                                    4.20-1.1ubuntu1                         thorough real-mode memory tester
ii  mencoder                                      2:1.0~rc4.dfsg1+svn34540-1              MPlayer's Movie Encoder
ii  mime-support                                  3.51-1ubuntu1                           MIME files 'mime.types' & 'mailcap', and support programs
ii  miscfiles                                     1.4.2.dfsg.1-9                          Dictionaries and other interesting files
ii  mlocate                                       0.23.1-1ubuntu2                         quickly find files on the filesystem based on their name
ii  mobile-broadband-provider-info                20120410-0ubuntu1                       database of mobile broadband service providers
ii  modemmanager                                  0.5.2.0-0ubuntu2                        D-Bus service for managing modems
ii  module-init-tools                             3.16-1ubuntu2                           tools for managing Linux kernel modules
ii  mono-4.0-gac                                  2.10.8.1-1ubuntu2.2                     Mono GAC tool (for CLI 4.0)
ii  mono-gac                                      2.10.8.1-1ubuntu2.2                     Mono GAC tool
ii  mono-runtime                                  2.10.8.1-1ubuntu2.2                     Mono runtime
ii  mount                                         2.20.1-1ubuntu3                         Tools for mounting and manipulating filesystems
ii  mountall                                      2.36.3                                  filesystem mounting tool
ii  mpg321                                        0.2.13-4ubuntu1                         Simple and lightweight command line MP3 player
ii  mplayer                                       2:1.0~rc4.dfsg1+svn34540-1              movie player for Unix-like systems
ii  mscompress                                    0.3-3.1                                 Microsoft "compress.exe/expand.exe" compatible (de)compressor
ii  mtools                                        4.0.12-1                                Tools for manipulating MSDOS files
ii  mtr-tiny                                      0.80-1ubuntu1                           Full screen ncurses traceroute tool
ii  multiarch-support                             2.15-0ubuntu10.3                        Transitional package to ensure multiarch compatibility
ii  mysql-common                                  5.5.28-0ubuntu0.12.04.3                 MySQL database common files, e.g. /etc/mysql/my.cnf
ii  nano                                          2.2.6-1                                 small, friendly text editor inspired by Pico
ii  nautilus                                      1:3.4.2-0ubuntu6                        file manager and graphical shell for GNOME
ii  nautilus-data                                 1:3.4.2-0ubuntu6                        data files for nautilus
ii  nautilus-sendto                               3.0.1-2ubuntu2                          integrates Evolution and Pidgin into the Nautilus file manager
ii  ncurses-base                                  5.9-4                                   basic terminal type definitions
ii  ncurses-bin                                   5.9-4                                   terminal-related programs and man pages
ii  net-tools                                     1.60-24.1ubuntu2                        The NET-3 networking toolkit
ii  netbase                                       4.47ubuntu1                             Basic TCP/IP networking system
ii  netcat-openbsd                                1.89-4ubuntu1                           TCP/IP swiss army knife
ii  netpbm                                        2:10.0-15                               Graphics conversion tools between image formats
ii  network-manager                               0.9.4.0-0ubuntu4.1                      network management framework (daemon and userspace tools)
ii  network-manager-gnome                         0.9.4.1-0ubuntu2                        network management framework (GNOME frontend)
ii  network-manager-pptp                          0.9.4.0-0ubuntu1                        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                    0.9.4.0-0ubuntu1                        network management framework (PPTP plugin GNOME GUI)
ii  ntfs-3g                                       1:2012.1.15AR.1-1ubuntu1.2              read/write NTFS driver for FUSE
ii  ntpdate                                       1:4.2.6.p3+dfsg-1ubuntu3.1              client for setting system time from NTP servers
ii  ntrack-module-libnl-0                         016-1ubuntu1                            libnl based ntrack module
ii  numlockx                                      1.2-2                                   enable NumLock in X11 sessions
ii  nvidia-common                                 1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  obex-data-server                              0.4.6-0ubuntu1                          D-Bus service for OBEX client and server side functionality
ii  odbcinst                                      2.2.14p2-5ubuntu3                       Helper program for accessing odbc ini files
ii  odbcinst1debian2                              2.2.14p2-5ubuntu3                       Support library for accessing odbc ini files
rc  onboard                                       0.97.0-0ubuntu4                         Simple On-screen Keyboard
ii  oneconf                                       0.2.8.1                                 synchronize your configuration data over the network
ii  openjdk-6-jre                                 6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                        6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                             6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime (architecture independent libraries)
ii  openprinting-ppds                             20120322-0ubuntu1                       OpenPrinting printer support - PostScript PPD files
ii  openshot                                      1.4.0-1ubuntu1                          Create and edit videos and movies
ii  openshot-doc                                  1.4.0-1ubuntu1                          Help manual for OpenShot Video Editor
ii  openssh-client                                1:5.9p1-5ubuntu1                        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                                1:5.9p1-5ubuntu1                        secure shell (SSH) server, for secure access from remote machines
ii  openssl                                       1.0.1-4ubuntu5.5                        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  os-prober                                     1.51ubuntu3                             utility to detect other OSes on a set of drives
ii  oxygen-icon-theme                             4:4.8.3-0ubuntu0.1                      Oxygen icon theme
ii  p7zip-full                                    9.20.1~dfsg.1-4                         7z and 7za file archivers with high compression ratio
ii  parley                                        4:4.8.5-0ubuntu0.1                      vocabulary trainer for KDE
ii  parley-data                                   4:4.8.5-0ubuntu0.1                      data files for the Parley vocabulary trainer
ii  parted                                        2.3-8ubuntu5.1                          disk partition manipulator
ii  passwd                                        1:4.1.4.2+svn3283-3ubuntu5.1            change and administer password and group data
ii  pastebinit                                    1.3-2ubuntu2.1                          command-line pastebin client
ii  patch                                         2.6.1-3                                 Apply a diff file to an original
ii  pavucontrol                                   0.99.2-1build1                          PulseAudio Volume Control
ii  pbis-open                                     7.0.1.918                               Authentication services for Active Directory domains
ii  pbis-open-gui                                 7.0.1.918                               Desktop utility for joining Active Directory domains
ii  pbis-open-legacy                              7.0.1.918                               Provides symbolic links from the older command names and paths in Likewise Open to the new names and paths in PowerBroker Identity Services Open.
ii  pciutils                                      1:3.1.8-2ubuntu5                        Linux PCI Utilities
ii  pcmciautils                                   018-6                                   PCMCIA utilities for Linux 2.6
ii  perl                                          5.14.2-6ubuntu2.2                       Larry Wall's Practical Extraction and Report Language
ii  perl-base                                     5.14.2-6ubuntu2.2                       minimal Perl system
ii  perl-modules                                  5.14.2-6ubuntu2.2                       Core Perl modules
ii  perlmagick                                    8:6.6.9.7-5ubuntu3.2                    Perl interface to the ImageMagick graphics routines
ii  phonon                                        4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - metapackage
ii  phonon-backend-gstreamer                      4:4.7.0really4.6.2-0ubuntu0.1           Phonon GStreamer 0.10.x backend
rc  pidgin                                        1:2.10.3-0ubuntu1.1                     graphical multi-protocol instant messaging client for X
ii  pidgin-data                                   1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging client - data files
ii  pidgin-microblog                              0.3.0-3                                 Microblogging plugins for Pidgin
ii  pitivi                                        0.15.2-0ubuntu0.1                       non-linear audio/video editor using GStreamer
ii  pkg-config                                    0.26-1ubuntu1                           manage compile and link flags for libraries
ii  plasma-scriptengine-javascript                4:4.8.5-0ubuntu0.1                      JavaScript script engine for Plasma
ii  plymouth                                      0.8.2-2ubuntu30                         graphical boot animation and logger - main package
ii  plymouth-label                                0.8.2-2ubuntu30                         graphical boot animation and logger - label control
ii  plymouth-theme-ubuntu-text                    0.8.2-2ubuntu30                         graphical boot animation and logger - ubuntu-logo theme
ii  plymouth-theme-xubuntu-logo                   12.04.11                                graphical boot animation and logger - xubuntu-logo theme
ii  plymouth-theme-xubuntu-text                   12.04.11                                graphical boot animation and logger - xubuntu-text theme
ii  pm-utils                                      1.4.1-9                                 utilities and scripts for power management
ii  policykit-1                                   0.104-1ubuntu1                          framework for managing administrative policies and privileges
ii  policykit-1-gnome                             0.105-1ubuntu3.1                        GNOME authentication agent for PolicyKit-1
ii  policykit-desktop-privileges                  0.10                                    run common desktop actions without password
ii  poppler-data                                  0.4.5-2                                 Encoding data for the poppler PDF rendering library
ii  poppler-utils                                 0.18.4-1ubuntu3                         PDF utilities (based on Poppler)
ii  popularity-contest                            1.53ubuntu1                             Vote for your favourite packages automatically
ii  powermgmt-base                                1.31                                    Common utils and configs for power management
ii  ppp                                           2.4.5-5ubuntu1                          Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                                     2.3.18+nmu3ubuntu1                      A text menu based utility for configuring ppp
ii  pppoeconf                                     1.20ubuntu1                             configures PPPoE/ADSL connections
ii  pptp-linux                                    1.7.2-6                                 Point-to-Point Tunneling Protocol (PPTP) Client
ii  printer-driver-c2esp                          23-1                                    printer driver for Kodak ESP AiO color inkjet Series
ii  printer-driver-foo2zjs                        20111202dfsg0-1ubuntu1                  printer driver for ZjStream-based printers
ii  printer-driver-gutenprint                     5.2.8~pre1-0ubuntu2.1                   printer drivers for CUPS
ii  printer-driver-hpcups                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  printer-driver-hpijs                          3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - gs IJS driver (hpijs)
ii  printer-driver-min12xxw                       0.0.9-6ubuntu1                          printer driver for KonicaMinolta PagePro 1[234]xxW
ii  printer-driver-pnm2ppa                        1.13+nondbs-0ubuntu1                    printer driver for HP-GDI printers
ii  printer-driver-postscript-hp                  3.12.2-1ubuntu3.1                       HP Printers PostScript Descriptions
ii  printer-driver-ptouch                         1.3-3ubuntu0.1                          printer driver Brother P-touch label printers
ii  printer-driver-pxljr                          1.3+repack0-2                           printer driver for HP Color LaserJet 35xx/36xx
ii  printer-driver-sag-gdi                        0.1-3                                   printer driver for Ricoh Aficio SP 1000s/SP 1100s
ii  printer-driver-splix                          2.0.0+svn300-1.1ubuntu2                 Driver for Samsung and Xerox SPL2 and SPLc laser printers
ii  procps                                        1:3.2.8-11ubuntu6                       /proc file system utilities
ii  psmisc                                        22.15-2ubuntu1.1                        utilities that use the proc file system
ii  pulseaudio                                    1:1.1-0ubuntu15.1                       PulseAudio sound server
ii  pulseaudio-module-x11                         1:1.1-0ubuntu15.1                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                              1:1.1-0ubuntu15.1                       Command line tools for the PulseAudio sound server
iU  puppet                                        3.0.2-1puppetlabs1                      Centralized configuration management - agent startup and compatibility scripts
ii  puppet-common                                 3.0.2-1puppetlabs1                      Centralized configuration management
ii  python                                        2.7.3-0ubuntu2                          interactive high-level object-oriented language (default version)
ii  python-appindicator                           0.4.92-0ubuntu1                         Python bindings for libappindicator
ii  python-apport                                 2.0.1-0ubuntu15.1                       apport crash report handling library
ii  python-apt                                    0.8.3ubuntu7                            Python interface to libapt-pkg
ii  python-apt-common                             0.8.3ubuntu7                            Python interface to libapt-pkg (locales)
ii  python-aptdaemon                              0.43+bzr805-0ubuntu7                    Python module for the server and client of aptdaemon
ii  python-aptdaemon.gtk3widgets                  0.43+bzr805-0ubuntu7                    Python GTK+ 3 widgets to run an aptdaemon client
ii  python-avogadro                               1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Python module)
ii  python-cairo                                  1.8.8-1ubuntu3                          Python bindings for the Cairo vector graphics library
ii  python-chardet                                2.0.1-2build1                           universal character encoding detector
ii  python-configobj                              4.7.2+ds-3build1                        simple but powerful config file reader and writer for Python
ii  python-crypto                                 2.4.1-1ubuntu0.1                        cryptographic algorithms and protocols for Python
ii  python-cups                                   1.9.61-0ubuntu2                         Python bindings for CUPS
ii  python-cupshelpers                            1.3.8+20120201-0ubuntu8.1               Python modules for printer configuration with CUPS
ii  python-dbus                                   1.0.0-1ubuntu1                          simple interprocess messaging system (Python interface)
ii  python-dbus-dev                               1.0.0-1ubuntu1                          main loop integration development files for python-dbus
ii  python-debian                                 0.1.21ubuntu1                           Python modules to work with Debian-related data formats
ii  python-debtagshw                              1.9+git20120320-0ubuntu1                Match debtags hardware:: tags against the actual hardware
ii  python-defer                                  1.0.2+bzr481-1                          Small framework for asynchronous programming
ii  python-gconf                                  2.28.1+dfsg-1                           Python bindings for the GConf configuration database system
ii  python-gdbm                                   2.7.3-1ubuntu1                          GNU dbm database support for Python
ii  python-gi                                     3.2.2-1~precise                         Python 2.x bindings for gobject-introspection libraries
ii  python-gi-cairo                               3.2.2-1~precise                         Python Cairo bindings for the GObject library
ii  python-glade2                                 2.24.0-3                                GTK+ bindings: Glade support
ii  python-gmenu                                  3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  python-gnomekeyring                           2.32.0+dfsg-1                           Python bindings for the GNOME keyring library
ii  python-gnupginterface                         0.3.2-9.1ubuntu3                        Python interface to GnuPG (GPG)
ii  python-gobject                                3.2.2-1~precise                         Python 2.x bindings for GObject - transitional package
ii  python-gobject-2                              2.28.6-10ubuntu1                        deprecated static Python bindings for the GObject library
ii  python-gst0.10                                0.10.22-3ubuntu0.1                      generic media-playing framework (Python bindings)
ii  python-gtk2                                   2.24.0-3                                Python bindings for the GTK+ widget set
ii  python-httplib2                               0.7.2-1ubuntu2                          comprehensive HTTP client library written for Python
ii  python-ibus                                   1.4.1-3ubuntu1                          Intelligent Input Bus - Python support
ii  python-imaging                                1.1.7-4                                 Python Imaging Library
ii  python-keyring                                0.9.2-0ubuntu0.12.04.2                  store and access your passwords safely
ii  python-launchpad-integration                  0.1.56.1                                library for launchpad integration
ii  python-launchpadlib                           1.9.12-1                                Launchpad web services client library
ii  python-lazr.restfulclient                     0.12.0-1ubuntu1                         client for lazr.restful-based web services
ii  python-lazr.uri                               1.0.3-1                                 library for parsing, manipulating, and generating URIs
ii  python-libxml2                                2.7.8.dfsg-5.1ubuntu4.3                 Python bindings for the GNOME XML library
ii  python-lxml                                   2.3.2-1                                 pythonic binding for the libxml2 and libxslt libraries
ii  python-mako                                   0.5.0-1                                 fast and lightweight templating for the Python platform
ii  python-markupsafe                             0.15-1                                  XML/HTML/XHTML Markup safe string for Python
ii  python-minimal                                2.7.3-0ubuntu2                          minimal subset of the Python language (default version)
ii  python-mlt3                                   0.7.6+git20120204-2                     multimedia framework (python bindings)
ii  python-notify                                 0.1.1-3                                 Python bindings for libnotify
ii  python-numpy                                  1:1.6.1-6ubuntu1                        Numerical Python adds a fast array facility to the Python language
ii  python-oauth                                  1.0.1-3build1                           Python library implementing of the OAuth protocol
ii  python-openssl                                0.12-1ubuntu2                           Python wrapper around the OpenSSL library
ii  python-pam                                    0.4.2-12.2ubuntu4                       A Python interface to the PAM library
ii  python-pexpect                                2.3-1ubuntu2                            Python module for automating interactive applications
ii  python-piston-mini-client                     0.7.2+bzr57-0ubuntu1                    library for writing clients for Django's Piston REST APIs
ii  python-pkg-resources                          0.6.24-1ubuntu1                         Package Discovery and Resource Access using pkg_resources
ii  python-problem-report                         2.0.1-0ubuntu15.1                       Python library to handle problem reports
ii  python-pycurl                                 7.19.0-4ubuntu3                         Python bindings to libcurl
ii  python-pygoocanvas                            0.14.1-1ubuntu6                         GooCanvas Python bindings
ii  python-qt4                                    4.9.1-2ubuntu1                          Python bindings for Qt4
ii  python-renderpm                               2.5-1.1build1                           python low level render interface
ii  python-reportlab                              2.5-1.1build1                           ReportLab library to create PDF documents using Python
ii  python-reportlab-accel                        2.5-1.1build1                           C coded extension accelerator for the ReportLab Toolkit
ii  python-serial                                 2.5-2.1build1                           pyserial - module encapsulating access for the serial port
ii  python-simplejson                             2.3.2-1                                 simple, fast, extensible JSON encoder/decoder for Python
ii  python-sip                                    4.13.2-1                                Python/C++ bindings generator runtime library
ii  python-smbc                                   1.0.13-0ubuntu1                         Python bindings for Samba clients (libsmbclient)
ii  python-software-properties                    0.82.7.3                                manage the repositories that you install software from
ii  python-support                                1.0.14ubuntu2                           automated rebuilding support for Python modules
ii  python-tk                                     2.7.3-1ubuntu1                          Tkinter - Writing Tk applications with Python
ii  python-twisted-bin                            11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-core                           11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-web                            11.1.0-1                                HTTP protocol implementation together with clients and servers
ii  python-ubuntu-sso-client                      3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - Python library
ii  python-uniconvertor                           1.1.4-1ubuntu1                          Universal vector graphics translator
ii  python-uno                                    1:3.5.4-0ubuntu1.1                      Python-UNO bridge
ii  python-virtkey                                0.60.0-0ubuntu5                         Library to emulate keyboard keypresses.
ii  python-wadllib                                1.3.0-2                                 Python library for navigating WADL files
ii  python-xapian                                 1.2.8-1                                 Xapian search engine interface for Python
ii  python-xdg                                    0.19-3ubuntu2                           Python library to access freedesktop.org standards
ii  python-xkit                                   0.4.2.3build1                           library for the manipulation of the xorg.conf
ii  python-zeitgeist                              0.9.0-1ubuntu1                          event logging framework - Python bindings
ii  python-zope.interface                         3.6.1-1ubuntu3                          Interfaces for Python
ii  python2.7                                     2.7.3-0ubuntu3.1                        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                             2.7.3-0ubuntu3.1                        Minimal subset of the Python language (version 2.7)
ii  python3.2                                     3.2.3-0ubuntu3.2                        Interactive high-level object-oriented language (version 3.2)
ii  python3.2-minimal                             3.2.3-0ubuntu3.2                        Minimal subset of the Python language (version 3.2)
ii  qapt-batch                                    1.3.1-0ubuntu2                          Batch package manager for KDE
ii  qdbus                                         4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus tool
ii  radeontool                                    1.6.2-1.1                               utility to control ATI Radeon backlight functions on laptops
ii  rarian-compat                                 0.8.1-5                                 Documentation meta-data library (compatibility tools)
ii  readline-common                               6.2-8                                   GNU readline and history libraries, common files
ii  resolvconf                                    1.63ubuntu16                            name server information handler
ii  rfkill                                        0.4-1ubuntu2                            tool for enabling and disabling wireless devices
ii  rhythmbox                                     2.96-0ubuntu4.2                         music player and organizer for GNOME
ii  rhythmbox-data                                2.96-0ubuntu4.2                         data files for rhythmbox
ii  rhythmbox-mozilla                             2.96-0ubuntu4.2                         Rhythmbox Mozilla plugin
ii  rhythmbox-plugin-cdrecorder                   2.96-0ubuntu4.2                         burning plugin for rhythmbox music player
ii  rhythmbox-plugin-zeitgeist                    2.96-0ubuntu4.2                         zeitgeist plugin for rhythmbox music player
ii  rhythmbox-plugins                             2.96-0ubuntu4.2                         plugins for rhythmbox music player
ii  ristretto                                     0.3.6-0ubuntu1                          lightweight picture-viewer for the Xfce desktop environment
ii  rsync                                         3.0.9-1ubuntu1                          fast, versatile, remote (and local) file-copying tool
ii  rsyslog                                       5.8.6-1ubuntu8                          reliable system and kernel logging daemon
ii  rtkit                                         0.10-2                                  Realtime Policy and Watchdog Daemon
ii  ruby                                          4.8                                     Transitional package for ruby1.8
ii  ruby-json                                     1.6.3-1                                 JSON library for Ruby
ii  ruby1.8                                       1.8.7.352-2ubuntu1.1                    Interpreter of object-oriented scripting language Ruby 1.8
ii  samba-common                                  2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  samba-common-bin                              2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  sane-utils                                    1.0.22-7ubuntu1                         API library for scanners -- utilities
ii  screensaver-default-images                    0.2-1                                   Wallpapers for image processing screensavers
ii  scribus                                       1.4.0.dfsg+r17300-1ubuntu1              Open Source Desktop Page Layout - stable branch
ii  sed                                           4.2.1-9                                 The GNU sed stream editor
ii  sensible-utils                                0.0.6ubuntu2                            Utilities for sensible alternative selection
ii  sessioninstaller                              0.20+bzr128-0ubuntu1.2                  APT based installer using PackageKit's session DBus API
ii  sgml-base                                     1.26+nmu1ubuntu1                        SGML infrastructure and SGML catalog file support
ii  sgml-data                                     2.0.6                                   common SGML and XML data
ii  shared-desktop-ontologies                     0.8.1-1                                 shared ontologies for semantic searching
ii  shared-mime-info                              1.0-0ubuntu4.1                          FreeDesktop.org shared MIME database and spec
ii  shimmer-themes                                1.3.0-0ubuntu1                          Gtk+ themes from Shimmer Project
ii  simple-scan                                   3.4.1-0ubuntu1.1                        Simple Scanning Utility
ii  smbclient                                     2:3.6.3-2ubuntu2.3                      command-line SMB/CIFS clients for Unix
ii  software-center                               5.2.7                                   Utility for browsing, installing, and removing software
ii  software-center-aptdaemon-plugins             0.1.2                                   The aptdaemon plugins for software-center
ii  software-properties-common                    0.82.7.3                                manage the repositories that you install software from (common)
ii  software-properties-gtk                       0.82.7.3                                manage the repositories that you install software from (gtk)
ii  soprano-daemon                                2.7.5+dfsg.1-0ubuntu1                   daemon for the Soprano RDF framework
ii  sound-theme-freedesktop                       0.7.pristine-2                          freedesktop.org sound theme
ii  speech-dispatcher                             0.7.1-6ubuntu3                          Common interface to speech synthesizers
ii  ssh-import-id                                 2.10-0ubuntu1                           securely retrieve an SSH public key and install it locally
ii  ssl-cert                                      1.0.28ubuntu0.1                         simple debconf wrapper for OpenSSL
ii  step                                          4:4.8.5-0ubuntu0.1                      interactive physical simulator for KDE
ii  strace                                        4.5.20-2.3ubuntu1                       A system call tracer
ii  sudo                                          1.8.3p1-1ubuntu3.3                      Provide limited super user privileges to specific users
ii  synaptic                                      0.75.9ubuntu1                           Graphical package manager
ii  syslinux                                      2:4.05+dfsg-2                           collection of boot loaders
ii  syslinux-common                               2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies
ii  system-config-printer-common                  1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-gnome                   1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-udev                    1.3.8+20120201-0ubuntu8.1               Printer auto-configuration facility based on udev
ii  system-tools-backends                         2.10.2-1ubuntu1                         System Tools to manage computer configuration -- scripts
ii  sysv-rc                                       2.88dsf-13.10ubuntu11.1                 System-V-like runlevel change mechanism
ii  sysvinit-utils                                2.88dsf-13.10ubuntu11.1                 System-V-like utilities
ii  tar                                           1.26-4ubuntu1                           GNU version of the tar archiving utility
ii  tcl8.5                                        8.5.11-1ubuntu1                         Tcl (the Tool Command Language) v8.5 - run-time files
ii  tcpd                                          7.6.q-21                                Wietse Venema's TCP wrapper utilities
ii  tcpdump                                       4.2.1-1ubuntu2                          command-line network traffic analyzer
ii  telnet                                        0.17-36build1                           The telnet client
ii  thunar                                        1.2.3-3ubuntu2                          File Manager for Xfce
ii  thunar-archive-plugin                         0.3.0-4                                 Archive plugin for Thunar file manager
ii  thunar-data                                   1.2.3-3ubuntu2                          Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                      0.2.0-1                                 Media tags plugin for Thunar file manager
ii  thunar-volman                                 0.6.1-0ubuntu1                          Thunar extension for volumes management
rc  thunderbird                                   16.0.2+build1-0ubuntu0.12.04.1          Email, RSS and newsgroup client with integrated spam filter
ii  tilem                                         0.973-1                                 TilEm, a TI 83+ emulator
ii  time                                          1.7-23.1                                The GNU time program for measuring cpu resource usage
ii  tk8.5                                         8.5.11-1                                Tk toolkit for Tcl and X11, v8.5 - run-time files
ii  toshset                                       1.76-2                                  Access much of the Toshiba laptop hardware interface
rc  transmission-gtk                              2.51-0ubuntu1                           lightweight BitTorrent client (GTK interface)
ii  tree                                          1.5.3-2                                 displays directory tree, in color
ii  tsconf                                        1.0-10                                  touch screen library common files
ii  ttf-dejavu                                    2.33-2ubuntu1                           Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra
ii  ttf-dejavu-core                               2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-dejavu-extra                              2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-droid                                     20101110+git-2                          transitional dummy package
ii  ttf-freefont                                  20100919-1                              Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                          1:0.5.11ubuntu1                         Core collection of free fonts for languages of India
ii  ttf-lyx                                       2.0.2-1ubuntu2                          TrueType versions of some TeX fonts
ii  ttf-mscorefonts-installer                     3.4ubuntu3                              Installer for Microsoft TrueType core fonts
ii  ttf-punjabi-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Punjabi language
ii  ttf-sil-gentium-basic                         1.1-5                                   transitional dummy package
ii  ttf-ubuntu-font-family                        0.80-0ubuntu2                           Ubuntu Font Family, sans-serif typeface hinted for clarity
ii  ttf-umefont                                   434-1                                   transitional dummy package
ii  ttf-unfonts-core                              1.0.3.is.1.0.2-080608-5ubuntu1          transitional dummy package
ii  ttf-wqy-microhei                              0.2.0-beta-1ubuntu1                     A droid derived Sans-Seri style CJK font
ii  tumbler                                       0.1.24-0ubuntu1                         D-Bus thumbnailing service
ii  tumbler-common                                0.1.24-0ubuntu1                         D-Bus thumbnailing service (common files)
ii  tzdata                                        2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data
ii  tzdata-java                                   2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data for use by java runtimes
ii  ubuntu-extras-keyring                         2010.09.27                              GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring                                2011.11.21.1                            GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                                1.267                                   Minimal core of Ubuntu
ii  ubuntu-restricted-addons                      12                                      Commonly used restricted packages for Ubuntu
ii  ubuntu-sso-client                             3.0.2-0ubuntu3                          Ubuntu Single Sign-On client
ii  ubuntu-sso-client-gtk                         3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - GTK+ frontend
ii  ubuntu-standard                               1.267                                   The Ubuntu standard system
ii  ucf                                           3.0025+nmu2ubuntu1                      Update Configuration File: preserve user changes to config files.
ii  udev                                          175-0ubuntu9.2                          rule-based device node and kernel event manager
ii  udisks                                        1.0.4-5ubuntu2.1                        storage media interface
ii  ufw                                           0.31.1-1                                program for managing a Netfilter firewall
ii  unattended-upgrades                           0.76ubuntu1                             automatic installation of security upgrades
ii  unixodbc                                      2.2.14p2-5ubuntu3                       Basic ODBC tools
ii  uno-libs3                                     3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment -- public shared libraries
ii  unrar                                         1:4.0.3-1                               Unarchiver for .rar files (non-free version)
ii  unzip                                         6.0-4ubuntu1                            De-archiver for .zip files
ii  update-inetd                                  4.41                                    inetd configuration file updater
ii  update-manager                                1:0.156.14.11                           GNOME application that manages apt updates
ii  update-manager-core                           1:0.156.14.11                           manage release upgrades
ii  update-notifier                               0.119ubuntu8.6                          Daemon which notifies about package updates
ii  update-notifier-common                        0.119ubuntu8.6                          Files shared between update-notifier and other packages
ii  upower                                        0.9.15-3git1                            abstraction for power management
ii  upstart                                       1.5-0ubuntu7                            event-based init daemon
ii  ure                                           3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment
ii  ureadahead                                    0.100.0-12                              Read required files in advance
ii  usb-creator-common                            0.2.38                                  create a startup disk using a CD or disc image (common files)
ii  usb-creator-gtk                               0.2.38                                  create a startup disk using a CD or disc image (for GNOME)
ii  usb-modeswitch                                1.2.3+repack0-1ubuntu2                  mode switching tool for controlling "flip flop" USB devices
ii  usb-modeswitch-data                           20120120-0ubuntu1                       mode switching data for usb-modeswitch
ii  usbmuxd                                       1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices
ii  usbutils                                      1:005-1                                 Linux USB utilities
ii  util-linux                                    2.20.1-1ubuntu3                         Miscellaneous system utilities
ii  uuid-runtime                                  2.20.1-1ubuntu3                         runtime components for the Universally Unique ID library
ii  vbetool                                       1.1-2ubuntu1                            run real-mode video BIOS code to alter hardware state
ii  vcdimager                                     0.7.23-4.1ubuntu1                       A VideoCD (VCD) image mastering and ripping tool
ii  vim-common                                    2:7.3.429-2ubuntu2.1                    Vi IMproved - Common files
ii  vim-tiny                                      2:7.3.429-2ubuntu2.1                    Vi IMproved - enhanced vi editor - compact version
ii  virtuoso-minimal                              6.1.4+dfsg1-0ubuntu1                    high-performance database - core dependency package
ii  virtuoso-opensource-6.1-bin                   6.1.4+dfsg1-0ubuntu1                    high-performance database - binaries
ii  virtuoso-opensource-6.1-common                6.1.4+dfsg1-0ubuntu1                    high-performance database - common files
ii  vlc                                           2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer
ii  vlc-data                                      2.0.3-0ubuntu0.12.04.1                  Common data for VLC
ii  vlc-nox                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer (without X support)
ii  vlc-plugin-notify                             2.0.3-0ubuntu0.12.04.1                  LibNotify plugin for VLC
ii  vlc-plugin-pulse                              2.0.3-0ubuntu0.12.04.1                  PulseAudio plugin for VLC
ii  vym                                           2.0.3-1                                 mindmapping tool
ii  wamerican                                     7.1-1                                   American English dictionary words for /usr/share/dict
ii  wbritish                                      7.1-1                                   British English dictionary words for /usr/share/dict
ii  wget                                          1.13.4-2ubuntu1                         retrieves files from the web
ii  whiptail                                      0.52.11-2ubuntu10                       Displays user-friendly dialog boxes from shell scripts
rc  winbind                                       2:3.6.3-2ubuntu2.3                      Samba nameservice integration server
ii  wine                                          1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (meta-package)
ii  wine-gecko1.4                                 1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine1.4                                       1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.4-common                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4-i386                                  1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                                    0.0+20120308                            Microsoft Windows Compatibility Layer (winetricks)
ii  wireless-regdb                                2011.04.28-1ubuntu3                     wireless regulatory database
ii  wireless-tools                                30~pre9-5ubuntu2                        Tools for manipulating Linux Wireless Extensions
ii  wodim                                         9:1.1.11-2ubuntu2                       command line CD/DVD writing tool
ii  wordnet                                       1:3.0-26.1                              electronic lexical database of English language
ii  wordnet-base                                  1:3.0-26.1                              electronic lexical database of English language (base data)
ii  wordnet-sense-index                           1:3.0-26.1                              electronic lexical database of English language (index.sense)
ii  wpasupplicant                                 0.7.3-6ubuntu2.1                        client support for WPA and WPA2 (IEEE 802.11i)
ii  x11-apps                                      7.6+5ubuntu1                            X applications
ii  x11-common                                    1:7.6+12ubuntu1                         X Window System (X.Org) infrastructure
ii  x11-session-utils                             7.6+2                                   X session utilities
ii  x11-utils                                     7.6+4ubuntu0.1                          X11 utilities
ii  x11-xfs-utils                                 7.6+1                                   X font server utilities
ii  x11-xkb-utils                                 7.6+4                                   X11 XKB utilities
ii  x11-xserver-utils                             7.6+3                                   X server utilities
ii  xauth                                         1:1.0.6-1                               X authentication utility
ii  xbitmaps                                      1.1.1-1                                 Base X bitmaps
rc  xchat                                         2.8.8-3ubuntu12                         IRC client for X similar to AmIRC
ii  xchat-common                                  2.8.8-3ubuntu12                         Common files for X-Chat
ii  xcursor-themes                                1.0.3-1                                 Base X cursor themes
ii  xdg-user-dirs                                 0.14-0ubuntu2                           tool to manage well known user directories
ii  xdg-user-dirs-gtk                             0.9-0ubuntu1                            tool to manage well known user directories (Gtk extension)
ii  xdg-utils                                     1.1.0~rc1-2ubuntu6                      desktop integration utilities from freedesktop.org
ii  xfce-keyboard-shortcuts                       4.8.1-1                                 xfce keyboard shortcuts configuration
ii  xfce4-appfinder                               4.8.0-3                                 Application finder for the Xfce4 Desktop Environment
ii  xfce4-cpugraph-plugin                         1.0.1-2                                 CPU load graph plugin for the Xfce4 panel
ii  xfce4-datetime-plugin                         0.6.1-3ubuntu1                          date and time plugin for the Xfce4 panel
ii  xfce4-dict                                    0.6.0-5                                 Dictionary plugin for Xfce4 panel
ii  xfce4-indicator-plugin                        0.4.0-0ubuntu2                          plugin to display information from applications in the Xfce4 panel
ii  xfce4-mailwatch-plugin                        1.1.0-5                                 mail watcher plugin for the Xfce4 panel
ii  xfce4-netload-plugin                          1.1.0-1                                 network load monitor plugin for the Xfce4 panel
ii  xfce4-notes                                   1.7.7-2ubuntu1                          Notes application for the Xfce4 desktop
ii  xfce4-notes-plugin                            1.7.7-2ubuntu1                          Notes plugin for the Xfce4 desktop
ii  xfce4-notifyd                                 0.2.2-1                                 simple, visually-appealing notification daemon for Xfce
ii  xfce4-panel                                   4.8.6-2ubuntu2                          panel for Xfce4 desktop environment
ii  xfce4-places-plugin                           1.2.0-3                                 quick access to folders, documents and removable media
ii  xfce4-power-manager                           1.0.11-0ubuntu2                         power manager for Xfce desktop
ii  xfce4-power-manager-data                      1.0.11-0ubuntu2                         power manager for Xfce desktop, arch-indep files
ii  xfce4-quicklauncher-plugin                    1.9.4-9                                 rapid launcher plugin for the Xfce4 panel
ii  xfce4-screenshooter                           1.8.0-2                                 screenshots utility for Xfce
ii  xfce4-session                                 4.8.3-0ubuntu2                          Xfce4 Session Manager
ii  xfce4-settings                                4.8.3-1ubuntu3                          graphical application for managing Xfce settings
ii  xfce4-systemload-plugin                       1:1.0.0-1ubuntu1                        system load monitor plugin for the Xfce4 panel
ii  xfce4-taskmanager                             1.0.0-2                                 process manager for the Xfce4 Desktop Environment
ii  xfce4-terminal                                0.4.8-1ubuntu1                          Xfce terminal emulator
ii  xfce4-utils                                   4.8.3-1ubuntu2                          Various tools for Xfce
ii  xfce4-verve-plugin                            1.0.0-1                                 Verve (command line) plugin for Xfce panel
ii  xfce4-volumed                                 0.1.13-2ubuntu1                         volume keys daemon
ii  xfce4-weather-plugin                          0.7.4-3                                 weather information plugin for the Xfce4 panel
ii  xfce4-xkb-plugin                              0.5.4.3-1ubuntu1                        xkb layout switch plugin for the Xfce4 panel
ii  xfconf                                        4.8.1-1                                 utilities for managing settings in Xfce
ii  xfdesktop4                                    4.8.3-2ubuntu7                          xfce desktop background, icons and root menu manager
ii  xfdesktop4-data                               4.8.3-2ubuntu7                          xfce desktop background, icons and root menu (common files)
ii  xfonts-base                                   1:1.0.3                                 standard fonts for X
ii  xfonts-encodings                              1:1.0.4-1ubuntu1                        Encodings for X.Org fonts
ii  xfonts-mathml                                 4ubuntu1                                Type1 Symbol font for MathML
ii  xfonts-scalable                               1:1.0.3-1                               scalable fonts for X
ii  xfonts-utils                                  1:7.6+1                                 X Window System font utility programs
ii  xfwm4                                         4.8.3-1ubuntu1.1                        window manager of the Xfce project
ii  xinit                                         1.3.1-1                                 X server initialisation tool
ii  xinput                                        1.5.99.1-0ubuntu2                       Runtime configuration and test of XInput devices
ii  xkb-data                                      2.5-1ubuntu1.3                          X Keyboard Extension (XKB) configuration data
ii  xml-core                                      0.13                                    XML infrastructure and XML catalog file support
ii  xorg                                          1:7.6+12ubuntu1                         X.Org X Window System
ii  xorg-docs-core                                1:1.6-1ubuntu2                          Core documentation for the X.org X Window System
ii  xplanet                                       1.2.1-4.1                               planetary body renderer
ii  xplanet-images                                1.2.1-4.1                               imagery for xplanet
rc  xscreensaver                                  5.15-2ubuntu1                           Automatic screensaver for X
ii  xscreensaver-data                             5.15-2ubuntu1                           data files to be shared among screensaver frontends
ii  xscreensaver-gl                               5.15-2ubuntu1                           GL(Mesa) screen hacks for xscreensaver
ii  xserver-common                                2:1.11.4-0ubuntu10.8                    common files used by various X servers
ii  xserver-xorg                                  1:7.6+12ubuntu1                         X.Org X server
ii  xserver-xorg-core                             2:1.11.4-0ubuntu10.8                    Xorg X server - core server
ii  xserver-xorg-input-all                        1:7.6+12ubuntu1                         X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                      1:2.7.0-0ubuntu1.2                      X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                      1:1.7.1-1build3                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics                  1.6.2-1ubuntu1~precise2                 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                    1:12.9.0-0ubuntu0.1                     X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                      1:0.14.0-0ubuntu2.1                     X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                        1:7.6+12ubuntu1                         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                        1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus                     1:1.3.2-4build1                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                      1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                      2.11.13-2build1                         X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel                      2:2.17.0-1ubuntu4.2                     X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                     6.9.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                        1:1.4.13.dfsg-4build2                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                   1:1.2.5-2build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau                    1:0.0.16+git20111201+b5534a1-1build2    X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome                 1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                        0.0.16-2                                X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                       6.8.1-5build2                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                     1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                         1:0.6.3-4build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage                     1:2.3.3-1ubuntu1                        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion              1:1.7.5-1build2                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                        1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                     1:0.9.4-2build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                       1:1.4.3-4build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                    1:1.3.4-2build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                       1:2.3.0-7build2                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                     1:12.0.1-1ubuntu1.1                     X.Org X server -- VMware display driver
ii  xsltproc                                      1.1.26-8ubuntu1.2                       XSLT 1.0 command line processor
ii  xterm                                         271-1ubuntu2.1                          X terminal emulator
ii  xubuntu-artwork                               12.04.11                                Xubuntu themes and artwork
ii  xubuntu-default-settings                      12.04.11                                default settings for the Xubuntu desktop
ii  xubuntu-desktop                               2.152                                   Xubuntu desktop system
ii  xubuntu-docs                                  11.10.0                                 xubuntu documentation
ii  xubuntu-icon-theme                            12.04.11                                Xubuntu icon theme
ii  xubuntu-restricted-addons                     12                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-restricted-extras                     57                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-wallpapers                            12.04.11                                Xubuntu wallpapers
ii  xul-ext-ubufox                                2.6-0ubuntu0.12.04.1                    Ubuntu-specific configuration defaults and apt support for Firefox
ii  xz-lzma                                       5.1.1alpha+20110809-3                   XZ-format compression utilities - compatibility commands
ii  xz-utils                                      5.1.1alpha+20110809-3                   XZ-format compression utilities
ii  yelp                                          3.4.1-0ubuntu1                          Help browser for GNOME
ii  yelp-xsl                                      3.4.1-1                                 XSL stylesheets for the yelp help browser
ii  zeitgeist                                     0.9.0-1ubuntu1                          event logging framework
ii  zeitgeist-core                                0.9.0-1ubuntu1                          event logging framework - engine
ii  zeitgeist-datahub                             0.8.2-1ubuntu2                          event logging framework - passive logging daemon
ii  zenity                                        3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts
ii  zenity-common                                 3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts (common files)
ii  zip                                           3.0-4                                   Archiver for .zip files
ii  zlib1g                                        1:1.2.3.4.dfsg-3ubuntu4                 compression library - runtime

```

**DPKG List of Installed Packages (after Puppet runs)**
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                                 Description
+++-=============================================-=======================================-=================================================================================================================================================
rc  abiword                                       2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration
ii  abiword-common                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- common files
ii  accountsservice                               0.6.15-2ubuntu9.4                       query and manipulate user account information
ii  acl                                           2.2.51-5ubuntu1                         Access control list utilities
ii  acpi-support                                  0.140                                   scripts for handling many ACPI events
ii  acpid                                         1:2.0.10-1ubuntu3                       Advanced Configuration and Power Interface event daemon
ii  adduser                                       3.113ubuntu2                            add and remove users and groups
rc  aisleriot                                     1:3.2.3.2-0ubuntu1                      Solitaire card games
rc  akonadi-backend-mysql                         1.7.2-0ubuntu1                          MySQL storage backend for Akonadi
rc  akonadi-server                                1.7.2-0ubuntu1                          Akonadi PIM storage service
ii  alacarte                                      0.13.2-2ubuntu4                         easy GNOME menu editing tool
ii  alsa-base                                     1.0.25+dfsg-0ubuntu1                    ALSA driver configuration files
ii  alsa-utils                                    1.0.25-1ubuntu5                         Utilities for configuring and using ALSA
ii  anacron                                       2.3-14ubuntu1                           cron-like program that doesn't go by time
ii  app-install-data                              0.12.04.4                               Ubuntu applications (data files)
ii  app-install-data-partner                      12.12.04.1                              Application Installer (data files for partner applications/repositories)
ii  apparmor                                      2.7.102-0ubuntu3.7                      User-space parser utility for AppArmor
ii  apport                                        2.0.1-0ubuntu15.1                       automatically generate crash reports for debugging
ii  apport-gtk                                    2.0.1-0ubuntu15.1                       GTK+ frontend for the apport crash report system
ii  apport-symptoms                               0.16.1                                  symptom scripts for apport
ii  apt                                           0.8.16~exp12ubuntu10.7                  commandline package manager
ii  apt-transport-https                           0.8.16~exp12ubuntu10.7                  https download transport for APT
ii  apt-utils                                     0.8.16~exp12ubuntu10.7                  package managment related utility programs
ii  apt-xapian-index                              0.44ubuntu5                             maintenance and search tools for a Xapian index of Debian packages
ii  aptdaemon                                     0.43+bzr805-0ubuntu7                    transaction based package management service
ii  aptdaemon-data                                0.43+bzr805-0ubuntu7                    data files for clients
ii  artha                                         1.0.2-1ubuntu1                          Handy off-line thesaurus based on WordNet
ii  aspell                                        0.60.7~20110707-1                       GNU Aspell spell-checker
ii  aspell-en                                     6.0-0-6ubuntu2                          English dictionary for GNU Aspell
ii  at                                            3.1.13-1ubuntu1                         Delayed job execution and batch processing
ii  at-spi2-core                                  2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface (dbus core)
ii  audacity                                      2.0.0-1ubuntu0.1                        fast, cross-platform audio editor
ii  audacity-data                                 2.0.0-1ubuntu0.1                        fast, cross-platform audio editor (data)
ii  augeas-lenses                                 0.10.0-0ubuntu4                         Set of lenses needed by libaugeas0 to parse config files
ii  avahi-autoipd                                 0.6.30-5ubuntu2                         Avahi IPv4LL network address configuration daemon
ii  avahi-daemon                                  0.6.30-5ubuntu2                         Avahi mDNS/DNS-SD daemon
ii  avahi-utils                                   0.6.30-5ubuntu2                         Avahi browsing, publishing and discovery utilities
ii  avogadro-data                                 1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Data Files)
ii  banshee                                       2.4.1-3ubuntu1~precise2                 Media Management and Playback application
ii  banshee-extension-soundmenu                   2.4.1-3ubuntu1~precise2                 Media Management and Playback application - sound menu extension
ii  base-files                                    6.5ubuntu6.4                            Debian base system miscellaneous files
ii  base-passwd                                   3.5.24                                  Debian base system master password and group files
ii  bash                                          4.2-2ubuntu2                            GNU Bourne Again SHell
ii  bash-completion                               1:1.3-1ubuntu8                          programmable completion for the bash shell
ii  bc                                            1.06.95-2                               The GNU bc arbitrary precision calculator language
ii  bind9-host                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Version of 'host' bundled with BIND 9.X
ii  binfmt-support                                2.0.8                                   Support for extra binary formats
ii  binutils                                      2.22-6ubuntu1                           GNU assembler, linker and binary utilities
ii  bison                                         1:2.5.dfsg-2.1                          YACC-compatible parser generator
ii  blender                                       2.62-1                                  Very fast and versatile 3D modeller/renderer
ii  blt                                           2.4z-4.2ubuntu1                         the BLT extension library for Tcl/Tk - run-time package
ii  blueman                                       1.23-0ubuntu2.1                         A Graphical bluetooth manager
ii  bluez                                         4.98-2ubuntu7                           Bluetooth tools and daemons
ii  bluez-alsa                                    4.98-2ubuntu7                           Bluetooth ALSA support
ii  bluez-cups                                    4.98-2ubuntu7                           Bluetooth printer driver for CUPS
ii  brasero                                       3.4.1-0ubuntu1.1                        CD/DVD burning application for GNOME
ii  brasero-cdrkit                                3.4.1-0ubuntu1.1                        cdrkit extensions for the Brasero burning application
ii  brasero-common                                3.4.1-0ubuntu1.1                        Common files for the Brasero CD burning application and library
ii  brltty                                        4.3-1ubuntu5                            Access software for a blind person using a braille display
ii  brltty-x11                                    4.3-1ubuntu5                            Access software for a blind person using a braille display - X11 drivers
ii  bsdmainutils                                  8.2.3ubuntu1                            collection of more utilities from FreeBSD
ii  bsdutils                                      1:2.20.1-1ubuntu3                       Basic utilities from 4.4BSD-Lite
ii  bsh                                           2.0b4-12build1                          Java scripting environment (BeanShell) Version 2
ii  bsh-gcj                                       2.0b4-12build1                          Java scripting environment (BeanShell) Version 2 (native code)
ii  build-essential                               11.5ubuntu2.1                           Informational list of build-essential packages
ii  busybox-initramfs                             1:1.18.5-1ubuntu4.1                     Standalone shell setup for initramfs
ii  busybox-static                                1:1.18.5-1ubuntu4.1                     Standalone rescue shell with tons of builtin utilities
ii  bzip2                                         1.0.6-1                                 high-quality block-sorting file compressor - utilities
ii  ca-certificates                               20111211                                Common CA certificates
ii  ca-certificates-java                          20110912ubuntu6                         Common CA certificates (JKS keystore)
ii  cabextract                                    1.4-1                                   Microsoft Cabinet file unpacker
rc  catfish                                       0.3.2-2ubuntu1                          file search tool that support several different engines
rc  charmap.app                                   0.2-11                                  Character map for GNUstep
ii  cheese                                        3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam
ii  cheese-common                                 3.4.1-0ubuntu2.1                        Common files for the Cheese tool to take pictures and videos
ii  chromium-browser                              20.0.1132.47~r144678-0ubuntu0.12.04.1   Chromium browser
ii  chromium-browser-l10n                         20.0.1132.47~r144678-0ubuntu0.12.04.1   chromium-browser language packages
ii  chromium-codecs-ffmpeg                        20.0.1132.47~r144678-0ubuntu0.12.04.1   Free ffmpeg codecs for the Chromium Browser
ii  clamav                                        0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - command-line interface
ii  clamav-base                                   0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - base package
ii  clamav-freshclam                              0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - virus database update utility
ii  cli-common                                    0.8.2                                   common files between all CLI packages
ii  cmap-adobe-japan1                             0+20090930-2                            CMaps for Adobe-Japan1
ii  colord                                        0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- system daemon
ii  command-not-found                             0.2.46ubuntu6                           Suggest installation of packages in interactive bash sessions
ii  command-not-found-data                        0.2.46ubuntu6                           Set of data files for command-not-found.
ii  conky                                         1.8.1-6                                 highly configurable system monitor (transitional package)
ii  conky-std                                     1.8.1-6                                 highly configurable system monitor (default version)
ii  console-setup                                 1.70ubuntu5                             console font and keymap setup program
ii  consolekit                                    0.4.5-2                                 framework for defining and tracking users, sessions and seats
ii  coreutils                                     8.13-3ubuntu3.2                         GNU core utilities
ii  cpio                                          2.11-7ubuntu3                           GNU cpio -- a program to manage archives of files
ii  cpp                                           4:4.6.3-1ubuntu5                        GNU C preprocessor (cpp)
ii  cpp-4.6                                       4.6.3-1ubuntu5                          GNU C preprocessor
ii  crda                                          1.1.2-1ubuntu1                          wireless Central Regulatory Domain Agent
ii  cron                                          3.0pl1-120ubuntu4                       process scheduling daemon
ii  cron-apt                                      0.9.0                                   automatic update of packages using apt-get
ii  cryptsetup-bin                                2:1.4.1-2ubuntu4                        disk encryption support - command line tools
ii  cups                                          1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - server
ii  cups-bsd                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - common files
ii  cups-filters                                  1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters
ii  cups-ppdc                                     1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation utilities
ii  curl                                          7.22.0-3ubuntu4                         Get a file from an HTTP, HTTPS or FTP server
ii  dash                                          0.5.7-2ubuntu2                          POSIX-compliant shell
ii  dbus                                          1.4.18-1ubuntu1.3                       simple interprocess messaging system (daemon and utilities)
ii  dbus-x11                                      1.4.18-1ubuntu1.3                       simple interprocess messaging system (X11 deps)
ii  dc                                            1.06.95-2                               The GNU dc arbitrary precision reverse-polish calculator
ii  dconf-gsettings-backend                       0.12.0-0ubuntu1.1                       simple configuration storage system - GSettings back-end
ii  dconf-service                                 0.12.0-0ubuntu1.1                       simple configuration storage system - D-Bus service
ii  dcraw                                         8.99-1build1                            decode raw digital camera images
ii  debconf                                       1.5.42ubuntu1                           Debian configuration management system
ii  debconf-i18n                                  1.5.42ubuntu1                           full internationalization support for debconf
ii  debconf-utils                                 1.5.42ubuntu1                           debconf utilities
ii  debianutils                                   4.2.1ubuntu2                            Miscellaneous utilities specific to Debian
ii  default-jre                                   1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime
ii  default-jre-headless                          1:1.6-43ubuntu2                         Standard Java or Java compatible Runtime (headless)
ii  desktop-file-utils                            0.20-0ubuntu3                           Utilities for .desktop files
ii  devede                                        3.21.0-1                                simple application to create Video DVDs
ii  dia                                           0.97.2-5                                Diagram editor
ii  dia-common                                    0.97.2-5                                Diagram editor (common files)
ii  dia-libs                                      0.97.2-5                                Diagram editor (library files)
ii  dictionaries-common                           1.12.1ubuntu2                           Common utilities for spelling dictionary tools
ii  diffutils                                     1:3.2-1ubuntu1                          File comparison utilities
ii  dmidecode                                     2.11-4                                  SMBIOS/DMI table decoder
ii  dmsetup                                       2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  dmz-cursor-theme                              0.4.3                                   Style neutral, scalable cursor theme
ii  dnsmasq-base                                  2.59-4                                  Small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                      1:9.8.1.dfsg.P1-4ubuntu0.5              Clients provided with BIND
ii  doc-base                                      0.10.3                                  utilities to manage online documentation
ii  docbook-xml                                   4.5-7ubuntu1                            standard XML documentation system for software and systems
ii  docbook-xsl                                   1.76.1+dfsg-1ubuntu1                    stylesheets for processing DocBook XML to various output formats
ii  dosfstools                                    3.0.12-1ubuntu1                         utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                          1.16.1.2ubuntu7                         Debian package management system
ii  dpkg-dev                                      1.16.1.2ubuntu7                         Debian package development tools
ii  drgeo                                         1.1.0-9                                 An interactive geometry software
ii  drgeo-doc                                     1.5-6                                   The Dr. Geo online user manual
ii  dvd+rw-tools                                  7.1-10                                  DVD+-RW/R tools
ii  dvdauthor                                     0.7.0-1.1build1                         create DVD-Video file system
ii  e2fslibs                                      1.42-1ubuntu2                           ext2/ext3/ext4 file system libraries
ii  e2fsprogs                                     1.42-1ubuntu2                           ext2/ext3/ext4 file system utilities
ii  earth3d                                       1.0.5-3                                 Map client displaying a 3D model of the world
ii  ed                                            1.5-3                                   classic UNIX line editor
ii  eject                                         2.1.5+deb1+cvs20081104-9                ejects CDs and operates CD-Changers under Linux
ii  electric                                      8.10-2                                  electrical CAD system
ii  enchant                                       1.6.0-7                                 Wrapper for various spell checker engines (binary programs)
ii  esound-common                                 0.2.41-10build3                         Enlightened Sound Daemon - Common files
ii  espeak                                        1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer
ii  espeak-data                                   1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: speech data files
ii  evince                                        3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer
ii  evince-common                                 3.4.0-0ubuntu1.4                        Document (PostScript, PDF) viewer - common files
ii  exo-utils                                     0.6.2-4                                 Utility files for libexo
ii  f-spot                                        0.8.2-4                                 personal photo management application
ii  facter                                        1.6.17-1puppetlabs1                     Ruby module for collecting simple facts about a host operating system
ii  fakeroot                                      1.18.2-1                                tool for simulating superuser privileges
ii  ffmpeg                                        4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder (transitional package)
ii  file                                          5.09-2                                  Determines file type using "magic" numbers
ii  file-roller                                   3.4.1-0ubuntu1                          archive manager for GNOME
ii  findutils                                     4.4.2-4ubuntu1                          utilities for finding files--find, xargs
ii  firefox                                       18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla
ii  firefox-globalmenu                            18.0+build1-0ubuntu0.12.04.3            Unity appmenu integration for Firefox
ii  firefox-gnome-support                         18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla - GNOME support
ii  firefox-locale-en                             18.0+build1-0ubuntu0.12.04.3            English language pack for Firefox
ii  flashplugin-installer                         11.2.202.261ubuntu0.12.04.1             Adobe Flash Player plugin installer
ii  flex                                          2.5.35-10ubuntu3                        A fast lexical analyzer generator.
ii  fontconfig                                    2.8.0-3ubuntu9.1                        generic font configuration library - support binaries
ii  fontconfig-config                             2.8.0-3ubuntu9.1                        generic font configuration library - configuration
ii  fonts-droid                                   20101110+git-2                          handheld device font with extensive style and language support
ii  fonts-horai-umefont                           434-1                                   Japanese TrueType font, Ume-font
ii  fonts-kacst                                   2.01+mry-3                              KACST free TrueType Arabic fonts
ii  fonts-kacst-one                               5.0+svn11846-2                          TrueType font designed for Arabic language
ii  fonts-khmeros-core                            5.0-5ubuntu1                            KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                                     0.0.20060226-8                          TrueType font for Lao language
ii  fonts-liberation                              1.07.0-2ubuntu0.1                       Fonts with the same metrics as Times, Arial and Courier
ii  fonts-nanum                                   3.010-2                                 Nanum Korean fonts
ii  fonts-opensymbol                              2:102.2+LibO3.5.4-0ubuntu1.1            OpenSymbol TrueType font
ii  fonts-sil-gentium                             20081126:1.02-12                        extended Unicode Latin font ("a typeface for the nations")
ii  fonts-sil-gentium-basic                       1.1-5                                   smart Unicode font families (Basic and Book Basic) based on Gentium
ii  fonts-takao-pgothic                           003.02.01-5ubuntu1                      Japanese TrueType font set, Takao P Gothic Fonts
ii  fonts-thai-tlwg                               1:0.4.17-1ubuntu1                       Thai fonts maintained by TLWG (meta package)
ii  fonts-tlwg-garuda                             1:0.4.17-1ubuntu1                       Thai Garuda font
ii  fonts-tlwg-kinnari                            1:0.4.17-1ubuntu1                       Thai Kinnari font
ii  fonts-tlwg-loma                               1:0.4.17-1ubuntu1                       Thai Loma font
ii  fonts-tlwg-mono                               1:0.4.17-1ubuntu1                       Thai TlwgMono font
ii  fonts-tlwg-norasi                             1:0.4.17-1ubuntu1                       Thai Norasi font
ii  fonts-tlwg-purisa                             1:0.4.17-1ubuntu1                       Thai Purisa font
ii  fonts-tlwg-sawasdee                           1:0.4.17-1ubuntu1                       Thai Sawasdee font
ii  fonts-tlwg-typewriter                         1:0.4.17-1ubuntu1                       Thai TlwgTypewriter font
ii  fonts-tlwg-typist                             1:0.4.17-1ubuntu1                       Thai TlwgTypist font
ii  fonts-tlwg-typo                               1:0.4.17-1ubuntu1                       Thai TlwgTypo font
ii  fonts-tlwg-umpush                             1:0.4.17-1ubuntu1                       Thai Umpush font
ii  fonts-tlwg-waree                              1:0.4.17-1ubuntu1                       Thai Waree font
ii  fonts-unfonts-core                            1.0.3.is.1.0.2-080608-5ubuntu1          Un series Korean TrueType fonts
ii  foomatic-db-compressed-ppds                   20120322-0ubuntu1                       OpenPrinting printer support - Compressed PPDs derived from the database
ii  foomatic-db-engine                            4.0.8-2ubuntu1                          OpenPrinting printer support - programs
ii  foomatic-filters                              4.0.16-0ubuntu0.2                       OpenPrinting printer support - filters
ii  freepats                                      20060219-1                              Free patch set for MIDI audio synthesis
ii  frei0r-plugins                                1.1.22git20091109-1.1ubuntu1            minimalistic plugin API for video effects, plugins collection
ii  friendly-recovery                             0.2.25                                  Make recovery more user-friendly
ii  ftp                                           0.17-25                                 classical file transfer client
ii  fuse                                          2.8.6-2ubuntu2                          Filesystem in Userspace
ii  g++                                           4:4.6.3-1ubuntu5                        GNU C++ compiler
ii  g++-4.6                                       4.6.3-1ubuntu5                          GNU C++ compiler
ii  gcalctool                                     6.4.1.1-0ubuntu3                        GNOME desktop calculator
ii  gcc                                           4:4.6.3-1ubuntu5                        GNU C compiler
ii  gcc-4.6                                       4.6.3-1ubuntu5                          GNU C compiler
ii  gcc-4.6-base                                  4.6.3-1ubuntu5                          GCC, the GNU Compiler Collection (base package)
ii  gcj-4.6-base                                  4.6.3-1ubuntu2                          GCC, the GNU Compiler Collection (gcj base package)
ii  gcj-4.6-jre-lib                               4.6.3-1ubuntu2                          Java runtime library for use with gcj (jar files)
ii  gconf-service                                 3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf-service-backend                         3.2.5-0ubuntu2                          GNOME configuration database system (D-Bus service)
ii  gconf2                                        3.2.5-0ubuntu2                          GNOME configuration database system (support tools)
ii  gconf2-common                                 3.2.5-0ubuntu2                          GNOME configuration database system (common files)
ii  gdb                                           7.4-2012.04-0ubuntu2.1                  The GNU Debugger
ii  gedit                                         3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment
ii  gedit-common                                  3.4.1-0ubuntu1                          official text editor of the GNOME desktop environment (support files)
ii  gelemental                                    1.2.0-7ubuntu1                          Periodic Table viewer
ii  genisoimage                                   9:1.1.11-2ubuntu2                       Creates ISO-9660 CD-ROM filesystem images
ii  geoip-database                                20111220-1                              IP lookup command line tools that use the GeoIP library (country database)
ii  gettext                                       0.18.1.1-5ubuntu3                       GNU Internationalization utilities
ii  gettext-base                                  0.18.1.1-5ubuntu3                       GNU Internationalization utilities for the base system
ii  ghostscript                                   9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF
ii  ghostscript-cups                              9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - CUPS filters
ii  ghostscript-x                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - X11 support
ii  gigolo                                        0.4.1-3                                 frontend to manage connections to remote filesystems using GIO/GVfs
ii  gimp                                          2.6.12-1ubuntu1.2                       The GNU Image Manipulation Program
ii  gimp-data                                     2.6.12-1ubuntu1.2                       Data files for GIMP
ii  gimp-help-common                              2.6.1-1                                 Data files for the GIMP documentation
ii  gimp-help-en                                  2.6.1-1                                 Documentation for the GIMP (English)
ii  gir1.2-appindicator3-0.1                      0.4.92-0ubuntu1                         Typelib files for libappindicator3-1.
ii  gir1.2-atk-1.0                                2.4.0-0ubuntu1                          ATK accessibility toolkit (GObject introspection)
ii  gir1.2-atspi-2.0                              2.4.2-0ubuntu0.1                        Assistive Technology Service Provider (GObject introspection)
ii  gir1.2-dbusmenu-glib-0.4                      0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-glib4
ii  gir1.2-dbusmenu-gtk-0.4                       0.6.2-0ubuntu0.1                        typelib file for libdbusmenu-gtk4
ii  gir1.2-dee-1.0                                1.0.10-0ubuntu1                         GObject introspection data for the Dee library
ii  gir1.2-freedesktop                            1.32.0-1                                Introspection data for some FreeDesktop components
ii  gir1.2-gdkpixbuf-2.0                          2.26.1-1                                GDK Pixbuf library - GObject-Introspection
ii  gir1.2-glib-2.0                               1.32.0-1                                Introspection data for GLib, GObject, Gio and GModule
ii  gir1.2-gmenu-3.0                              3.4.0-0ubuntu1                          GObject introspection data for the GNOME menu library
ii  gir1.2-gst-plugins-base-0.10                  0.10.36-1ubuntu0.1                      Description: GObject introspection data for the GStreamer Plugins Base library
ii  gir1.2-gstreamer-0.10                         0.10.36-1ubuntu1                        Description: GObject introspection data for the GStreamer library
ii  gir1.2-gtk-2.0                                2.24.10-0ubuntu6                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                                3.4.2-0ubuntu0.5                        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtksource-3.0                          3.4.2-0ubuntu1                          gir files for the GTK+ syntax highlighting widget
ii  gir1.2-gudev-1.0                              175-0ubuntu9.2                          libgudev-1.0 introspection data
ii  gir1.2-javascriptcoregtk-3.0                  1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the GTK+-based JavaScriptCore library
ii  gir1.2-launchpad-integration-3.0              0.1.56.1                                library for launchpad integration (gir files)
ii  gir1.2-notify-0.7                             0.7.5-1                                 sends desktop notifications to a notification daemon (Introspection files)
ii  gir1.2-pango-1.0                              1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text - gir bindings
ii  gir1.2-peas-1.0                               1.2.0-1ubuntu1                          Application plugin library (introspection files)
ii  gir1.2-rb-3.0                                 2.96-0ubuntu4.2                         GObject introspection data for the rhythmbox music player
ii  gir1.2-soup-2.4                               2.38.1-1                                GObject introspection data for the libsoup HTTP library
ii  gir1.2-unity-5.0                              5.12.0-0ubuntu1.1                       GObject introspection data for the Unity library
ii  gir1.2-vte-2.90                               1:0.32.1-0ubuntu1                       GObject introspection data for the VTE library
ii  gir1.2-webkit-3.0                             1.8.3-0ubuntu0.12.04.1                  GObject introspection data for the WebKit library
ii  gir1.2-wnck-3.0                               3.4.0-0ubuntu1                          GObject introspection data for the WNCK library
ii  gksu                                          2.0.2-6ubuntu1                          graphical frontend to su
ii  glib-networking                               2.32.1-1ubuntu2                         network-related giomodules for GLib
ii  glib-networking-common                        2.32.1-1ubuntu2                         network-related giomodules for GLib - data files
ii  glib-networking-services                      2.32.1-1ubuntu2                         network-related giomodules for GLib - D-Bus services
rc  gmusicbrowser                                 1.1.9-1                                 graphic jukebox for large collections of mp3/ogg/flac/mpc files
ii  gnome-accessibility-themes                    3.4.1-0ubuntu1.2                        accessibility themes for the GNOME desktop
ii  gnome-desktop-data                            1:2.32.1-0ubuntu9                       Common files for GNOME desktop apps
ii  gnome-desktop3-data                           3.4.2-0ubuntu0.1                        Common files for GNOME desktop apps
ii  gnome-games-data                              1:3.4.1-0ubuntu2.1                      data files for the GNOME games
ii  gnome-icon-theme                              3.4.0-0ubuntu1.1                        GNOME Desktop icon theme (small subset)
ii  gnome-keyring                                 3.2.2-2ubuntu4                          GNOME keyring services (daemon and tools)
ii  gnome-system-tools                            3.0.0-2ubuntu1                          Cross-platform configuration utilities for GNOME
ii  gnome-time-admin                              3.0.0-2ubuntu1                          GNOME Time Administration Tool
ii  gnome-user-guide                              3.4.1-1                                 GNOME user's guide
ii  gnome-video-effects                           0.4.0-1                                 GNOME Video Effects
rc  gnomine                                       1:3.4.1-0ubuntu2.1                      popular minesweeper puzzle game for GNOME
rc  gnumeric                                      1.10.17-1ubuntu2                        spreadsheet application for GNOME - main program
ii  gnupg                                         1.4.11-3ubuntu2.1                       GNU privacy guard - a free PGP replacement
rc  gnustep-base-common                           1.22.1-2ubuntu2                         GNUstep Base library - common files
rc  gnustep-base-runtime                          1.22.1-2ubuntu2                         GNUstep Base library - daemons and tools
rc  gnustep-common                                2.6.1-1                                 Common files for the core GNUstep environment
ii  google-chrome-stable                          23.0.1271.97-r171054                    The web browser from Google
rc  google-earth-stable                           7.0.1.8244-r0                           Explore, search and discover the planet
ii  gpgv                                          1.4.11-3ubuntu2.1                       GNU privacy guard - signature verification tool
ii  gpsd                                          3.4-2                                   Global Positioning System - daemon
ii  grep                                          2.10-1                                  GNU grep, egrep and fgrep
ii  groff-base                                    1.21-7                                  GNU troff text-formatting system (base system components)
ii  growisofs                                     7.1-10                                  DVD+-RW/R recorder
ii  grub-common                                   1.99-21ubuntu3.7                        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                         0.6                                     GRUB gfxpayload blacklist
ii  grub-pc                                       1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                   1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                  1.99-21ubuntu3.7                        GRand Unified Bootloader (common files for version 2)
ii  gs-cjk-resource                               1.20100103-3                            Resource files for gs-cjk, ghostscript CJK-TrueType extension
ii  gsettings-desktop-schemas                     3.4.1-0ubuntu1                          GSettings deskop-wide schemas
ii  gsfonts                                       1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1     Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                                   0.22                                    Make Ghostscript fonts available to X11
ii  gstreamer0.10-alsa                            0.10.36-1ubuntu0.1                      GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                          0.10.13-1                               FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                     0.10.15.debian-1ubuntu1                 Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gnomevfs                        0.10.36-1ubuntu0.1                      GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                         0.10.17-2                               non-linear editing module for GStreamer
ii  gstreamer0.10-nice                            0.1.1-2ubuntu1                          ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad                     0.10.22.3-2ubuntu2.1                    GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse          0.10.21-1                               GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base                    0.10.36-1ubuntu0.1                      GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps               0.10.36-1ubuntu0.1                      GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good                    0.10.31-1ubuntu1                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                    0.10.18.3-1ubuntu1                      GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio                      0.10.31-1ubuntu1                        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                           0.10.36-1ubuntu1                        Tools for use with GStreamer
ii  gstreamer0.10-x                               0.10.36-1ubuntu0.1                      GStreamer plugins for X11 and Pango
ii  gthumb                                        3:2.14.3-0ubuntu1                       image viewer and browser
ii  gthumb-data                                   3:2.14.3-0ubuntu1                       image viewer and browser - arch-independent files
ii  gtk2-engines                                  1:2.20.2-1ubuntu1                       theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                          0.98.2-0ubuntu1                         cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                           2.24.10-0ubuntu6                        pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-unico                            1.0.2-0ubuntu1                          Unico Gtk+ 3 theme engine
ii  gucharmap                                     1:3.4.1.1-0ubuntu1                      Unicode character picker and font browser
ii  guile-1.6-libs                                1.6.8-10ubuntu4                         Main Guile libraries
ii  guile-1.8-libs                                1.8.8+1-6ubuntu2                        Core Guile libraries
ii  gvfs                                          1.12.1-0ubuntu1.1                       userspace virtual filesystem - GIO module
ii  gvfs-backends                                 1.12.1-0ubuntu1.1                       userspace virtual filesystem - backends
ii  gvfs-bin                                      1.12.1-0ubuntu1.1                       userspace virtual filesystem - binaries
ii  gvfs-common                                   1.12.1-0ubuntu1.1                       userspace virtual filesystem - common data files
ii  gvfs-daemons                                  1.12.1-0ubuntu1.1                       userspace virtual filesystem - servers
ii  gvfs-fuse                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - fuse server
ii  gvfs-libs                                     1.12.1-0ubuntu1.1                       userspace virtual filesystem - private libraries
ii  gzip                                          1.4-1ubuntu2                            GNU compression utilities
ii  hdparm                                        9.37-0ubuntu3.1                         tune hard disk parameters for high performance
ii  heirloom-mailx                                12.5-1build1                            feature-rich BSD mail(1)
ii  hicolor-icon-theme                            0.12-1ubuntu2                           default fallback theme for FreeDesktop.org icon themes
ii  hiera                                         1.1.2-1puppetlabs1                      A simple pluggable Hierarchical Database.
ii  hostname                                      3.06ubuntu1                             utility to set/show the host name or domain name
ii  hplip                                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                    3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - data files
ii  humanity-icon-theme                           0.5.3.11                                Humanity Icon theme
ii  hunspell-en-us                                20070829-4ubuntu3                       English_american dictionary for hunspell
ii  hwdata                                        0.233-1ubuntu1                          hardware identification / configuration data
ii  ibus                                          1.4.1-3ubuntu1                          Intelligent Input Bus - core
ii  ibus-gtk                                      1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3                                     1.4.1-3ubuntu1                          Intelligent Input Bus - GTK+3 support
ii  ibus-pinyin                                   1.4.0-1                                 Pinyin engine for IBus
ii  ibus-pinyin-db-android                        1.4.0-1                                 Pinyin engine for IBus - Android database
ii  ibus-table                                    1.3.9.20110827-1ubuntu1                 table engine for IBus
ii  icc-profiles-free                             2.0.1+dfsg-1                            ICC color profiles for use with color profile aware software
ii  icedtea-6-jre-cacao                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre-jamvm                           6b24-1.11.5-0ubuntu1~12.04.1            Alternative JVM for OpenJDK, using JamVM
ii  icedtea-netx                                  1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icedtea-netx-common                           1.2-2ubuntu1.3                          NetX - implementation of the Java Network Launching Protocol (JNLP)
ii  icoutils                                      0.29.1-2                                Create and extract MS Windows icons and cursors
ii  ifupdown                                      0.7~beta2ubuntu8                        high level tools to configure network interfaces
ii  im-switch                                     1.20ubuntu5.1                           Input method switch framework
ii  imagemagick                                   8:6.6.9.7-5ubuntu3.2                    image manipulation programs
ii  imagemagick-common                            8:6.6.9.7-5ubuntu3.2                    image manipulation programs -- infrastructure
ii  indicator-application                         0.5.0-0ubuntu1                          Application Indicators
ii  indicator-application-gtk2                    0.5.0-0ubuntu1                          Application Indicators
ii  indicator-sound                               0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  indicator-sound-gtk2                          0.8.5.0-0ubuntu2.1                      System sound indicator.
ii  info                                          4.13a.dfsg.1-8ubuntu2                   Standalone GNU Info documentation browser
ii  initramfs-tools                               0.99ubuntu13                            tools for generating an initramfs
ii  initramfs-tools-bin                           0.99ubuntu13                            binaries used by initramfs-tools
ii  initscripts                                   2.88dsf-13.10ubuntu11.1                 scripts for initializing and shutting down the system
ii  inkscape                                      0.48.3.1-1ubuntu1                       vector-based drawing program
ii  inputattach                                   1:1.4.2-1                               utility to connect serial-attached peripherals to the input subsystem
ii  insserv                                       1.14.0-2.1ubuntu2                       Tool to organize boot sequence using LSB init.d script dependencies
ii  install-info                                  4.13a.dfsg.1-8ubuntu2                   Manage installed documentation in info format
ii  iproute                                       20111117-1ubuntu2                       networking and traffic control tools
ii  iptables                                      1.4.12-1ubuntu4                         administration tools for packet filtering and NAT
ii  iputils-arping                                3:20101006-1ubuntu1                     Tool to send ICMP echo requests to an ARP address
ii  iputils-ping                                  3:20101006-1ubuntu1                     Tools to test the reachability of network hosts
ii  iputils-tracepath                             3:20101006-1ubuntu1                     Tools to trace the network path to a remote host
ii  irqbalance                                    0.56-1ubuntu4                           Daemon to balance interrupts for SMP systems
ii  isc-dhcp-client                               4.1.ESV-R4-0ubuntu5.5                   ISC DHCP client
ii  isc-dhcp-common                               4.1.ESV-R4-0ubuntu5.5                   common files used by all the isc-dhcp* packages
ii  iso-codes                                     3.31-1                                  ISO language, territory, currency, script codes and their translations
ii  iw                                            3.2-1                                   tool for configuring Linux wireless devices
ii  java-common                                   0.43ubuntu2                             Base of all Java packages
ii  java-wrappers                                 0.1.24                                  wrappers for java executables
ii  jockey-common                                 0.9.7-0ubuntu7.4                        user interface and desktop integration for driver management
ii  jockey-gtk                                    0.9.7-0ubuntu7.4                        GNOME user interface and desktop integration for driver management
ii  kalgebra                                      4:4.8.4-0ubuntu0.1                      algebraic graphing calculator for KDE
ii  kalgebra-common                               4:4.8.4-0ubuntu0.1                      contains files common for kalgebra and kalgebramobile
ii  kalzium                                       4:4.8.5-0ubuntu0.1                      periodic table and chemistry tools for KDE
ii  kalzium-data                                  4:4.8.5-0ubuntu0.1                      data files for Kalzium
ii  kate-data                                     4:4.8.5-0ubuntu0.1                      shared data files for kate
ii  katepart                                      4:4.8.5-0ubuntu0.1                      kate KPart
ii  kbd                                           1.15.2-3ubuntu4                         Linux console font and keytable utilities
ii  kbruch                                        4:4.8.2-0ubuntu1                        fraction learning aid for KDE
ii  kde-runtime                                   4:4.8.5-0ubuntu0.1                      runtime components from the official KDE release
ii  kde-runtime-data                              4:4.8.5-0ubuntu0.1                      shared data files for the KDE base runtime module
ii  kdeedu-kvtml-data                             4:4.8.5-0ubuntu0.1                      kvtml files for kdeedu programs
ii  kdelibs-bin                                   4:4.8.5-0ubuntu0.1                      core executables for KDE Applications
ii  kdelibs5-data                                 4:4.8.5-0ubuntu0.1                      core shared data for all KDE Applications
ii  kdelibs5-plugins                              4:4.8.5-0ubuntu0.1                      core plugins for KDE Applications
rc  kdepim-runtime                                4:4.8.5-0ubuntu0.1                      Runtime components for akonadi-kde
ii  kdoctools                                     4:4.8.5-0ubuntu0.1                      various tools for accessing application documentation
ii  kerneloops-daemon                             0.12+git20090217-1ubuntu19              kernel oops tracker
ii  keyboard-configuration                        1.70ubuntu5                             system-wide keyboard preferences
ii  kig                                           4:4.8.4-0ubuntu0.1                      interactive geometry tool for KDE
ii  kino                                          1.3.4-1.3                               Non-linear editor for Digital Video data
ii  klibc-utils                                   1.5.25-1ubuntu2                         small utilities built with klibc for early boot
ii  kmplot                                        4:4.8.2-0ubuntu1                        mathematical function plotter for KDE
ii  kolourpaint4                                  4:4.8.4-0ubuntu0.1                      simple image editor and drawing application
ii  krb5-locales                                  1.10+dfsg~beta1-2ubuntu0.3              Internationalization support for MIT Kerberos
ii  krosspython                                   4:4.8.2-0ubuntu1                        Python module for Kross
ii  kstars                                        4:4.8.5-0ubuntu0.1                      desktop planetarium for KDE
ii  kstars-data                                   4:4.8.5-0ubuntu0.1                      data files for KStars desktop planetarium
ii  ktouch                                        4:4.8.2-0ubuntu1                        touch typing tutor for KDE
ii  ktouch-data                                   4:4.8.2-0ubuntu1                        data files for ktouch
ii  kturtle                                       4:4.8.2-0ubuntu1                        Logo educational programming environment for KDE
ii  kubuntu-debug-installer                       11.10ubuntu1                            Debug package installer for Kubuntu
ii  kwordquiz                                     4:4.8.3-0ubuntu0.1                      flashcard learning program for KDE
ii  language-pack-en                              1:12.04+20120801                        translation updates for language English
ii  language-pack-en-base                         1:12.04+20120801                        translations for language English
ii  language-pack-gnome-en                        1:12.04+20120801                        GNOME translation updates for language English
ii  language-pack-gnome-en-base                   1:12.04+20120801                        GNOME translations for language English
ii  language-selector-common                      0.79                                    Language selector for Ubuntu
ii  language-selector-gnome                       0.79                                    Language selector for Ubuntu
ii  laptop-detect                                 0.13.7ubuntu2                           attempt to detect a laptop
ii  launchpad-integration                         0.1.56.1                                launchpad integration
rc  leafpad                                       0.8.18.1-2                              GTK+ based simple text editor
ii  less                                          444-1ubuntu1                            pager program similar to more
ii  liba52-0.7.4                                  0.7.4-16build1                          library for decoding ATSC A/52 streams
ii  libaa1                                        1.4p5-39ubuntu1                         ASCII art library
ii  libaacs0                                      0.3.0-4                                 free-and-libre implementation of AACS
ii  libabiword-2.9                                2.9.2+svn20120213-1                     efficient, featureful word processor with collaboration -- shared library
ii  libaccountsservice0                           0.6.15-2ubuntu9.4                       query and manipulate user account information - shared libraries
ii  libacl1                                       2.2.51-5ubuntu1                         Access control list shared library
rc  libakonadi-calendar4                          4:4.8.5-0ubuntu0.1                      library providing calendar helpers for Akonadi items
rc  libakonadi-contact4                           4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kabc4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kcal4                              4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kde4                               4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-kmime4                             4:4.8.5-0ubuntu0.1                      library for using the Akonadi PIM data server
rc  libakonadi-notes4                             4:4.8.5-0ubuntu0.1                      library providing notes helpers for Akonadi items
rc  libakonadiprotocolinternals1                  1.7.2-0ubuntu1                          libraries for the Akonadi PIM storage service
ii  libalgorithm-diff-perl                        1.19.02-2                               module to find differences between files
ii  libalgorithm-diff-xs-perl                     0.04-2build2                            module to find differences between files (XS accelerated)
ii  libalgorithm-merge-perl                       0.08-2                                  Perl module for three-way merge of textual data
ii  libanalitza4abi1                              4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions
ii  libanalitzagui4abi1                           4:4.8.4-0ubuntu0.1                      library to work with mathematical expressions - GUI routines
ii  libao-common                                  1.1.0-1ubuntu2                          Cross Platform Audio Output Library (Common files)
ii  libao4                                        1.1.0-1ubuntu2                          Cross Platform Audio Output Library
ii  libappindicator1                              0.4.92-0ubuntu1                         Application Indicators
ii  libappindicator3-1                            0.4.92-0ubuntu1                         Application Indicators
ii  libapt-inst1.4                                0.8.16~exp12ubuntu10.7                  deb package format runtime library
ii  libapt-pkg4.12                                0.8.16~exp12ubuntu10.7                  package managment runtime library
ii  libarchive12                                  3.0.3-6ubuntu1                          Multi-format archive and compression library (shared library)
ii  libart-2.0-2                                  2.3.21-1ubuntu0.1                       Library of functions for 2D graphics - runtime files
ii  libart2.0-cil                                 2.24.2-1                                CLI binding for libart 2.3
ii  libasn1-8-heimdal                             1.6~git20120311.dfsg.1-2                Heimdal Kerberos - ASN.1 library
ii  libasound2                                    1.0.25-1ubuntu10.1                      shared library for ALSA applications
ii  libasound2-plugins                            1.0.25-1ubuntu1                         ALSA library additional plugins
ii  libaspell15                                   0.60.7~20110707-1                       GNU Aspell spell-checker runtime library
ii  libass4                                       0.10.0-3                                library for SSA/*** subtitles rendering
ii  libasyncns0                                   0.8-4                                   Asynchronous name service query library
ii  libatasmart4                                  0.18-3                                  ATA S.M.A.R.T. reading and parsing library
ii  libatk-wrapper-java                           0.30.4-0ubuntu2                         An ATK implementation for Java using JNI
ii  libatk-wrapper-java-jni                       0.30.4-0ubuntu2                         An ATK implementation for Java using JNI (jni bindings)
ii  libatk1.0-0                                   2.4.0-0ubuntu1                          ATK accessibility toolkit
ii  libatk1.0-data                                2.4.0-0ubuntu1                          Common files for the ATK accessibility toolkit
ii  libatkmm-1.6-1                                2.22.6-1ubuntu1                         C++ wrappers for ATK accessibility toolkit (shared libraries)
ii  libatspi2.0-0                                 2.4.2-0ubuntu0.1                        Assistive Technology Service Provider Interface - shared library
ii  libattica0.3                                  0.3.0-0ubuntu2                          a Qt library that implements the Open Collaboration Services API
ii  libattr1                                      1:2.4.46-5ubuntu1                       Extended attribute shared library
ii  libaudclient2                                 3.2.1-2                                 audacious dbus remote control library
ii  libaudio-scrobbler-perl                       0.01-2.1                                perl interface to audioscrobbler.com/last.fm
ii  libaudio2                                     1.9.3-4                                 Network Audio System - shared libraries
ii  libaudiofile1                                 0.3.3-2                                 Open-source version of SGI's audiofile library
ii  libaugeas-ruby1.8                             0.3.0-1.1ubuntu4                        Augeas bindings for the Ruby language
ii  libaugeas0                                    0.10.0-0ubuntu4                         Augeas configuration editing library and API
ii  libav-tools                                   4:0.8.4-0ubuntu0.12.04.1                Multimedia player, server, encoder and transcoder
ii  libavahi-client3                              0.6.30-5ubuntu2                         Avahi client library
ii  libavahi-common-data                          0.6.30-5ubuntu2                         Avahi common data files
ii  libavahi-common3                              0.6.30-5ubuntu2                         Avahi common library
ii  libavahi-core7                                0.6.30-5ubuntu2                         Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                                0.6.30-5ubuntu2                         Avahi glib integration library
ii  libavc1394-0                                  0.5.3-1ubuntu2                          control IEEE 1394 audio/video devices
ii  libavcodec-extra-53                           4:0.8.4ubuntu0.12.04.1                  Libav codec library
rc  libavcodec53                                  4:0.8.4-0ubuntu0.12.04.1                Libav codec library
ii  libavdevice53                                 4:0.8.4-0ubuntu0.12.04.1                Libav device handling library
ii  libavfilter2                                  4:0.8.4-0ubuntu0.12.04.1                Libav video filtering library
ii  libavformat-extra-53                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libavformat53                                 4:0.8.4-0ubuntu0.12.04.1                Libav file format library
ii  libavogadro1                                  1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (library)
ii  libavutil-extra-51                            4:0.8.4ubuntu0.12.04.1                  Libav utility library
rc  libavutil51                                   4:0.8.4-0ubuntu0.12.04.1                Libav utility library
ii  libbabl-0.0-0                                 0.0.22-1.1                              Dynamic, any to any, pixel format conversion library
ii  libbind9-80                                   1:9.8.1.dfsg.P1-4ubuntu0.5              BIND9 Shared Library used by BIND
ii  libbison-dev                                  1:2.5.dfsg-2.1                          YACC-compatible parser generator - development library
ii  libblas3gf                                    1.2.20110419-2ubuntu1                   Basic Linear Algebra Reference implementations, shared library
ii  libblkid1                                     2.20.1-1ubuntu3                         block device id library
ii  libbluetooth3                                 4.98-2ubuntu7                           Library to use the BlueZ Linux Bluetooth stack
ii  libbluray1                                    1:0.2.1+git20111208.63e308d-3           Blu-ray disc playback support library (shared library)
ii  libbonobo2-0                                  2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library
ii  libbonobo2-common                             2.32.1-0ubuntu1.1                       Bonobo CORBA interfaces library -- support files
ii  libbonoboui2-0                                2.24.5-0ubuntu1.1                       The Bonobo UI library
ii  libbonoboui2-common                           2.24.5-0ubuntu1.1                       The Bonobo UI library -- common files
rc  libboost-program-options1.46.1                1.46.1-7ubuntu3                         program options library for C++
ii  libboost-python1.46.1                         1.46.1-7ubuntu3                         Boost.Python Library
ii  libbrasero-media3-1                           3.4.1-0ubuntu1.1                        CD/DVD burning library for GNOME - runtime
ii  libbrlapi0.5                                  4.3-1ubuntu5                            braille display access via BRLTTY - shared library
ii  libbsd0                                       0.3.0-2                                 utility functions from BSD systems - shared library
ii  libburn4                                      1.1.8-1                                 library to provide CD/DVD writing functions
ii  libbz2-1.0                                    1.0.6-1                                 high-quality block-sorting file compressor library - runtime
ii  libc-bin                                      2.15-0ubuntu10.3                        Embedded GNU C Library: Binaries
ii  libc-dev-bin                                  2.15-0ubuntu10.3                        Embedded GNU C Library: Development binaries
ii  libc6                                         2.15-0ubuntu10.3                        Embedded GNU C Library: Shared libraries
ii  libc6-dev                                     2.15-0ubuntu10.3                        Embedded GNU C Library: Development Libraries and Header Files
ii  libcaca0                                      0.99.beta17-2.1ubuntu2                  colour ASCII art library
ii  libcairo-gobject2                             1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library (GObject library)
ii  libcairo-perl                                 1.081-1build2                           Perl interface to the Cairo graphics library
ii  libcairo2                                     1.10.2-6.1ubuntu3                       The Cairo 2D vector graphics library
ii  libcairomm-1.0-1                              1.10.0-1ubuntu1                         C++ wrappers for Cairo (shared libraries)
ii  libcanberra-gtk3-0                            0.28-3ubuntu3                           GTK+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module                       0.28-3ubuntu3                           translates GTK3 widgets signals to event sounds
ii  libcanberra-pulse                             0.28-3ubuntu3                           PulseAudio backend for libcanberra
ii  libcanberra0                                  0.28-3ubuntu3                           simple abstract interface for playing event sounds
ii  libcap-ng0                                    0.6.6-1ubuntu1                          An alternate POSIX capabilities library
ii  libcap2                                       1:2.22-1ubuntu3                         support for getting/setting POSIX.1e capabilities
ii  libcap2-bin                                   1:2.22-1ubuntu3                         basic utility programs for using capabilities
ii  libcapi20-3                                   1:3.12.20071127-0ubuntu11               libraries for CAPI support
ii  libcdaudio1                                   0.99.12p2-10build1                      library for controlling a CD-ROM when playing audio CDs
ii  libcddb2                                      1.3.2-3fakesync1                        library to access CDDB data - runtime files
ii  libcdio-cdda1                                 0.83-1                                  library to read and control digital audio CDs
ii  libcdio-paranoia1                             0.83-1                                  library to read digital audio CDs with error correction
ii  libcdio13                                     0.83-1                                  library to read and control CD-ROM
ii  libcdparanoia0                                3.10.2+debian-10ubuntu1                 audio extraction tool for sampling CDs (library)
ii  libcdt4                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - cdt library
ii  libcelt0-0                                    0.7.1-1                                 The CELT codec runtime library
ii  libcfitsio3                                   3.290-1ubuntu1                          shared library for I/O with FITS format data files
ii  libcheese-gtk21                               3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - widgets
ii  libcheese3                                    3.4.1-0ubuntu2.1                        tool to take pictures and videos from your webcam - base library
ii  libck-connector0                              0.4.5-2                                 ConsoleKit libraries
ii  libclamav6                                    0.97.6+dfsg-1ubuntu0.12.04.1            anti-virus utility for Unix - library
ii  libclass-isa-perl                             0.36-3                                  report the search path for a class's ISA tree
ii  libcln6                                       1.3.2-1.1                               Class Library for Numbers (C++)
ii  libclucene0ldbl                               0.9.21b-2                               library for full-featured text search engine (runtime)
ii  libclutter-1.0-0                              1.10.6-1~precise1                       Open GL based interactive canvas library
ii  libclutter-1.0-common                         1.10.6-1~precise1                       Open GL based interactive canvas library (common files)
ii  libclutter-gst-1.0-0                          1.5.4-0ubuntu2                          Open GL based interactive canvas library GStreamer elements
ii  libclutter-gtk-1.0-0                          1.2.0-0ubuntu1                          Open GL based interactive canvas library GTK+ widget
ii  libclutter-imcontext-0.1-0                    0.1.4-2build1                           Open GL based interactive canvas library IMContext framework
ii  libcluttergesture-0.0.2-0                     0.0.2.1-2ubuntu3                        Open GL based interactive canvas library Gesture framework
ii  libcmis-0.2-0                                 0.1.0-1                                 CMIS protocol client library
ii  libcogl-common                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer (common files)
ii  libcogl-pango0                                1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcogl9                                      1.10.0-0ubuntu2                         Object oriented GL/GLES Abstraction/Utility Layer
ii  libcolamd2.7.1                                1:3.4.0-2ubuntu3                        column approximate minimum degree ordering library for sparse matrices
ii  libcolord1                                    0.1.16-2ubuntu0.1                       system service to manage device colour profiles -- runtime
ii  libcomerr2                                    1.42-1ubuntu2                           common error description library
ii  libconfig-inifiles-perl                       2.68-1ubuntu0.12.04.1                   Read .ini-style configuration files
ii  libcroco3                                     0.6.5-1                                 Cascading Style Sheet (CSS) parsing and manipulation toolkit
ii  libcrypt-passwdmd5-perl                       1.3-10                                  interoperable MD5-based crypt() for perl
ii  libcryptsetup4                                2:1.4.1-2ubuntu4                        disk encryption support - shared library
ii  libcrystalhd3                                 1:0.0~git20110715.fdd2f19-4.1           Crystal HD Video Decoder (shared library)
ii  libcups2                                      1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Core library
ii  libcupscgi1                                   1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - CGI library
ii  libcupsdriver1                                1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Driver library
ii  libcupsfilters1                               1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2                                 1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1                                  1.5.3-0ubuntu6                          Common UNIX Printing System(tm) - PPD manipulation library
ii  libcurl3                                      7.22.0-3ubuntu4                         Multi-protocol file transfer library (OpenSSL)
ii  libcurl3-gnutls                               7.22.0-3ubuntu4                         Multi-protocol file transfer library (GnuTLS)
ii  libdaemon0                                    0.14-2                                  lightweight C library for daemons - runtime library
ii  libdatrie1                                    0.2.5-3                                 Double-array trie library
ii  libdb5.1                                      5.1.25-11build1                         Berkeley v5.1 Database Libraries [runtime]
ii  libdbus-1-3                                   1.4.18-1ubuntu1.3                       simple interprocess messaging system (library)
ii  libdbus-glib-1-2                              0.98-1ubuntu1                           simple interprocess messaging system (GLib-based shared library)
ii  libdbus-glib1.0-cil                           0.5.0-3build1                           CLI implementation of D-Bus (GLib mainloop integration)
ii  libdbus1.0-cil                                0.7.0-4                                 CLI implementation of D-Bus
ii  libdbusmenu-glib4                             0.6.2-0ubuntu0.1                        library for passing menus over DBus
ii  libdbusmenu-gtk3-4                            0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk4                              0.6.2-0ubuntu0.1                        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-qt2                               0.9.2-0ubuntu1                          Qt implementation of the DBusMenu protocol
ii  libdc1394-22                                  2.2.0-2                                 high level programming interface for IEEE1394 digital camera
ii  libdca0                                       0.0.5-5                                 decoding library for DTS Coherent Acoustics streams
ii  libdconf0                                     0.12.0-0ubuntu1.1                       simple configuration storage system - runtime library
ii  libdee-1.0-4                                  1.0.10-0ubuntu1                         model to synchronize mutiple instances over DBus - shared lib
ii  libdevmapper-event1.02.1                      2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdevmapper1.02.1                            2:1.02.48-4ubuntu7.1                    The Linux Kernel Device Mapper userspace library
ii  libdigest-crc-perl                            0.18-1                                  Perl module providing generic CRC functions
ii  libdirac-encoder0                             1.0.2-4build1                           open and royalty free high quality codec - encoder library
ii  libdirectfb-1.2-9                             1.2.10.0-4.3ubuntu1                     direct frame buffer graphics - shared libraries
ii  libdiscid0                                    0.2.2-3                                 Library for creating MusicBrainz DiscIDs
ii  libdjvulibre-text                             3.5.24-9                                Linguistic support files for libdjvulibre
ii  libdjvulibre21                                3.5.24-9                                Runtime support for the DjVu image format
ii  libdlrestrictions1                            0.14.2ubuntu5                           library that implements library compatibility checks for dlopen()
ii  libdmapsharing-3.0-2                          2.9.14-1                                DMAP client and server library - runtime
rc  libdmtx0a                                     0.7.2-1build2                           Data Matrix barcodes (runtime library)
ii  libdns81                                      1:9.8.1.dfsg.P1-4ubuntu0.5              DNS Shared Library used by BIND
ii  libdotconf1.0                                 1.0.13-3                                Configuration file parser library - runtime files
ii  libdpkg-perl                                  1.16.1.2ubuntu7                         Dpkg perl modules
ii  libdrm-intel1                                 2.4.32-1ubuntu1                         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                              2.4.32-1ubuntu1                         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                                2.4.32-1ubuntu1                         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2                                       2.4.32-1ubuntu1                         Userspace interface to kernel DRM services -- runtime
ii  libdv4                                        1.0.0-3ubuntu1                          software library for DV format digital video (runtime lib)
ii  libdvbpsi7                                    0.2.2-1                                 library for MPEG TS and DVB PSI tables decoding and generating
ii  libdvdcss2                                    1.2.12-0.0medibuntu1                    Simple foundation for reading DVDs - runtime libraries
ii  libdvdnav4                                    4.2.0-1                                 DVD navigation library
ii  libdvdread4                                   4.2.0-1ubuntu3                          library for reading DVDs
ii  libebml3                                      1.2.2-2                                 access library for the EBML format (shared library)
ii  libedit2                                      2.11-20080614-3ubuntu2                  BSD editline and history libraries
ii  libelemental0                                 1.2.0-7ubuntu1                          Periodic Table viewer (data and shared library)
ii  libelf1                                       0.152-1ubuntu3                          library to read and write ELF files
ii  libenca0                                      1.13-4                                  Extremely Naive Charset Analyser - shared library files
ii  libenchant1c2a                                1.6.0-7                                 Wrapper library for various spell checker engines (runtime libs)
ii  libencode-locale-perl                         1.02-2                                  utility to determine the locale encoding
ii  libept1.4.12                                  1.0.6~exp1ubuntu1                       High-level library for managing Debian package information
ii  libesd0                                       0.2.41-10build3                         Enlightened Sound Daemon - Shared libraries
ii  libespeak1                                    1.46.02-0ubuntu1                        Multi-lingual software speech synthesizer: shared library
ii  libevent-2.0-5                                2.0.16-stable-1                         Asynchronous event notification library
ii  libevince3-3                                  3.4.0-0ubuntu1.4                        Document (PostScript, PDF) rendering library
ii  libexempi3                                    2.2.0-1                                 library to parse XMP metadata (Library)
ii  libexif12                                     0.6.20-2ubuntu0.1                       library to parse EXIF files
ii  libexiv2-11                                   0.22-2                                  EXIF/IPTC metadata manipulation library
ii  libexo-1-0                                    0.6.2-4                                 Library with extensions for Xfce
ii  libexo-common                                 0.6.2-4                                 libexo common files
ii  libexo-helpers                                0.6.2-4                                 libexo helpers
ii  libexpat1                                     2.0.1-7.2ubuntu1.1                      XML parsing C library - runtime library
ii  libexttextcat-data                            3.2.0-1ubuntu1                          Language detection library - data files
ii  libexttextcat0                                3.2.0-1ubuntu1                          Language detection library
ii  libfaac0                                      1.28-0ubuntu2                           AAC audio encoder (library)
ii  libfaad2                                      2.7-7                                   freeware Advanced Audio Decoder - runtime files
ii  libfarstream-0.1-0                            0.1.2-0ubuntu1                          Audio/Video communications framework: core library
ii  libffi6                                       3.0.11~rc1-5                            Foreign Function Interface library runtime
ii  libfftw3-3                                    3.3-1ubuntu1                            library for computing Fast Fourier Transforms
ii  libfile-basedir-perl                          0.03-1fakesync1                         Perl module to use the freedesktop basedir specification
ii  libfile-copy-recursive-perl                   0.38-1                                  Perl extension for recursively copying files and directories
ii  libfile-desktopentry-perl                     0.04-3                                  Perl module to handle freedesktop .desktop files
ii  libfile-listing-perl                          6.03-1                                  module to parse directory listings
ii  libfile-mimeinfo-perl                         0.15-2                                  Perl module to determine file types
ii  libfl-dev                                     2.5.35-10ubuntu3                        static library for flex (a fast lexical analyzer generator).
ii  libflac++6                                    1.2.1-6                                 Free Lossless Audio Codec - C++ runtime library
ii  libflac8                                      1.2.1-6                                 Free Lossless Audio Codec - runtime C library
ii  libflickrnet2.2-cil                           1:2.2.0-3build1                         Flickr.Net API Library
ii  libflite1                                     1.4-release-4                           Small run-time speech synthesis engine - shared libraries
ii  libfont-afm-perl                              1.20-1                                  Font::AFM - Interface to Adobe Font Metrics files
ii  libfontconfig1                                2.8.0-3ubuntu9.1                        generic font configuration library - runtime
ii  libfontenc1                                   1:1.1.0-1                               X11 font encoding library
ii  libframe6                                     2.2.4-0ubuntu0.12.04.1                  Touch Frame Library
ii  libfreetype6                                  2.4.8-1ubuntu2                          FreeType 2 font engine, shared library files
ii  libfribidi0                                   0.19.2-1                                Free Implementation of the Unicode BiDi algorithm
ii  libfs6                                        2:1.0.3-1                               X11 Font Services library
ii  libfuse2                                      2.8.6-2ubuntu2                          Filesystem in Userspace (library)
ii  libgail-3-0                                   3.4.2-0ubuntu0.5                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgail18                                     2.24.10-0ubuntu6                        GNOME Accessibility Implementation Library -- shared libraries
ii  libgarcon-1-0                                 0.1.11-0ubuntu1                         freedesktop.org compliant menu implementation for Xfce
ii  libgarcon-common                              0.1.11-0ubuntu1                         common files for libgarcon menu implementation
ii  libgavl1                                      1.2.0-4                                 low level audio and video library - runtime files
ii  libgc1c2                                      1:7.1-8ubuntu0.12.04.1                  conservative garbage collector for C and C++
ii  libgcc1                                       1:4.6.3-1ubuntu5                        GCC support library
ii  libgcj-bc                                     4.6.3-1ubuntu5                          Link time only library for use with gcj
ii  libgcj-common                                 1:4.6.3-1ubuntu5                        Java runtime library (common files)
ii  libgcj12                                      4.6.3-1ubuntu2                          Java runtime library for use with gcj
ii  libgck-1-0                                    3.2.2-2ubuntu4                          Glib wrapper library for PKCS#11 - runtime
ii  libgconf-2-4                                  3.2.5-0ubuntu2                          GNOME configuration database system (shared libraries)
ii  libgconf2-4                                   3.2.5-0ubuntu2                          GNOME configuration database system (dummy package)
ii  libgconf2.0-cil                               2.24.2-1                                CLI binding for GConf 2.24
ii  libgcr-3-1                                    3.2.2-2ubuntu4                          Library for Crypto UI related task - runtime
ii  libgcr-3-common                               3.2.2-2ubuntu4                          Library for Crypto UI related task - common files
ii  libgcrypt11                                   1.5.0-3ubuntu0.1                        LGPL Crypto library - runtime library
ii  libgd2-xpm                                    2.0.36~rc1~dfsg-6ubuntu2                GD Graphics Library version 2
ii  libgdata1.9-cil                               1.9.0.0-1                               Google GData CLI client library
ii  libgdbm3                                      1.8.3-10                                GNU dbm database routines (runtime version)
ii  libgdiplus                                    2.10-3                                  interface library for System.Drawing of Mono
ii  libgdk-pixbuf2.0-0                            2.26.1-1                                GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                       2.26.1-1                                GDK Pixbuf library - data files
ii  libgdome2-0                                   0.8.1+debian-4.1build1                  DOM level2 library for accessing XML files
ii  libgdome2-cpp-smart0c2a                       0.2.6-6build2                           C++ bindings for GDome2 DOM implementation
ii  libgdu0                                       3.0.2-2ubuntu7                          GObject based Disk Utility Library
ii  libgee2                                       0.6.4-1                                 GObject based collection library
ii  libgegl-0.0-0                                 0.0.22-2ubuntu3                         Generic Graphics Library
ii  libgeis1                                      2.2.9.2-0ubuntu1                        Gesture engine interface support
ii  libgeoclue0                                   0.12.0-1ubuntu12                        C API for GeoClue
ii  libgeoip1                                     1.4.8+dfsg-2                            non-DNS IP-to-country resolver library
ii  libgettextpo0                                 0.18.1.1-5ubuntu3                       GNU Internationalization library
ii  libgfortran3                                  4.6.3-1ubuntu5                          Runtime library for GNU Fortran applications
ii  libgif4                                       4.1.6-9ubuntu1                          library for GIF images (library)
ii  libgimp2.0                                    2.6.12-1ubuntu1.2                       Libraries for the GNU Image Manipulation Program
ii  libgirepository-1.0-1                         1.32.0-1                                Library for handling GObject introspection data (runtime library)
ii  libgkeyfile1.0-cil                            0.1-2ubuntu2                            GObject-based wrapper library for GKeyFile -- CLI bindings
ii  libgksu2-0                                    2.0.13~pre1-5ubuntu2                    library providing su and sudo functionality
ii  libgl1-mesa-dri                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                               8.0.4-0ubuntu0.2                        free implementation of the OpenGL API -- GLX runtime
ii  libglade2-0                                   1:2.6.4-1ubuntu1.1                      library to load .glade files at runtime
ii  libglade2.0-cil                               2.12.10-2ubuntu4                        CLI binding for the Glade libraries 2.6
ii  libglapi-mesa                                 8.0.4-0ubuntu0.2                        free implementation of the GL API -- shared library
ii  libglew1.5                                    1.5.7.is.1.5.2-1ubuntu4                 The OpenGL Extension Wrangler - runtime environment
ii  libglew1.6                                    1.6.0-4                                 OpenGL Extension Wrangler - runtime environment
ii  libglib-perl                                  2:1.241-1                               interface to the GLib and GObject libraries
ii  libglib2.0-0                                  2.32.3-0ubuntu1                         GLib library of C routines
ii  libglib2.0-bin                                2.32.3-0ubuntu1                         Programs for the GLib library
ii  libglib2.0-cil                                2.12.10-2ubuntu4                        CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                               2.32.3-0ubuntu1                         Common files for GLib library
ii  libglibmm-2.4-1c2a                            2.32.0-0ubuntu1                         C++ wrapper for the GLib toolkit (shared libraries)
ii  libglu1-mesa                                  8.0.4-0ubuntu0.2                        Mesa OpenGL utility library (GLU)
ii  libgme0                                       0.5.5-2                                 Playback library for video game music files - shared library
ii  libgmime-2.6-0                                2.6.7-1                                 MIME message parser and creator library - runtime
ii  libgmp10                                      2:5.0.2+dfsg-2ubuntu1                   Multiprecision arithmetic library
ii  libgnome-bluetooth8                           3.2.2-0ubuntu5                          GNOME Bluetooth tools - support library
ii  libgnome-desktop-3-2                          3.4.2-0ubuntu0.1                        Utility library for loading .desktop files - runtime files
ii  libgnome-keyring-common                       3.2.2-2                                 GNOME keyring services library - data files
ii  libgnome-keyring0                             3.2.2-2                                 GNOME keyring services library
ii  libgnome-keyring1.0-cil                       1.0.0-3build1                           CLI library to access the GNOME Keyring daemon
ii  libgnome-menu-3-0                             3.4.0-0ubuntu1                          GNOME implementation of the freedesktop menu specification
ii  libgnome-menu2                                3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  libgnome-vfs2.0-cil                           2.24.2-1                                CLI binding for GnomeVFS 2.24
ii  libgnome2-0                                   2.32.1-2ubuntu1.1                       The GNOME library - runtime files
ii  libgnome2-bin                                 2.32.1-2ubuntu1.1                       The GNOME library - binary files
ii  libgnome2-common                              2.32.1-2ubuntu1.1                       The GNOME library - common files
ii  libgnome2.24-cil                              2.24.2-1                                CLI binding for GNOME 2.24
ii  libgnomecanvas2-0                             2.30.3-1ubuntu1.1                       powerful object-oriented display engine - runtime files
ii  libgnomecanvas2-common                        2.30.3-1ubuntu1.1                       powerful object-oriented display engine - common files
ii  libgnomeui-0                                  2.24.5-2ubuntu2                         GNOME user interface library - runtime files
ii  libgnomeui-common                             2.24.5-2ubuntu2                         GNOME user interface library - common files
ii  libgnomevfs2-0                                1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (runtime libraries)
ii  libgnomevfs2-common                           1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                            1:2.24.4-1ubuntu2.1                     GNOME Virtual File System (extra modules)
rc  libgnustep-base1.22                           1.22.1-2ubuntu2                         GNUstep Base library
rc  libgnustep-gui0.20                            0.20.0-2                                GNUstep GUI Library
ii  libgnutls26                                   2.12.14-5ubuntu3.1                      GNU TLS library - runtime library
ii  libgoffice-0.8-8                              0.8.17-1                                Document centric objects library - runtime files
ii  libgoffice-0.8-8-common                       0.8.17-1                                Document centric objects library - common files
ii  libgomp1                                      4.6.3-1ubuntu5                          GCC OpenMP (GOMP) support library
ii  libgoocanvas-common                           0.15-1                                  translations for goocanvas
ii  libgoocanvas3                                 0.15-1                                  canvas widget for GTK+ that uses the cairo 2D library
ii  libgpg-error0                                 1.10-2ubuntu1                           library for common error values and messages in GnuPG components
ii  libgphoto2-2                                  2.4.13-1ubuntu1.2                       gphoto2 digital camera library
ii  libgphoto2-l10n                               2.4.13-1ubuntu1.2                       gphoto2 digital camera library - localized messages
ii  libgphoto2-port0                              2.4.13-1ubuntu1.2                       gphoto2 digital camera port library
ii  libgpm2                                       1.20.4-4                                General Purpose Mouse - shared library
ii  libgpod-common                                0.8.2-4                                 common files for libgpod
ii  libgpod4                                      0.8.2-4                                 library to read and write songs and artwork to an iPod
ii  libgps20                                      3.4-2                                   Global Positioning System - library
ii  libgrail5                                     3.0.6-0ubuntu0.12.04.01                 Gesture Recognition And Instantiation Library
ii  libgraph4                                     2.26.3-10ubuntu1                        rich set of graph drawing tools - graph library
ii  libgrip0                                      0.3.5-0ubuntu1~12.04.1                  provides multitouch gestures to GTK+ apps
ii  libgs9                                        9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - Library
ii  libgs9-common                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - common files
ii  libgsf-1-114                                  1.14.21-2                               Structured File Library - runtime version
ii  libgsf-1-common                               1.14.21-2                               Structured File Library - common files
ii  libgsl0ldbl                                   1.15+dfsg-1build1                       GNU Scientific Library (GSL) -- library package
ii  libgsm1                                       1.0.13-3                                Shared libraries for GSM speech compressor
ii  libgssapi-krb5-2                              1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgssapi3-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - GSSAPI support library
ii  libgssdp-1.0-3                                0.12.1-2                                GObject-based library for SSDP
ii  libgstreamer-perl                             0.16-1build1                            Perl interface to the GStreamer media processing framework
ii  libgstreamer-plugins-bad0.10-0                0.10.22.3-2ubuntu2.1                    GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0               0.10.36-1ubuntu0.1                      GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                            0.10.36-1ubuntu1                        Core GStreamer libraries and elements
ii  libgtk-3-0                                    3.4.2-0ubuntu0.5                        GTK+ graphical user interface library
ii  libgtk-3-bin                                  3.4.2-0ubuntu0.5                        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                               3.4.2-0ubuntu0.5                        common files for the GTK+ graphical user interface library
ii  libgtk-sharp-beans-cil                        2.14.1-2build2                          Supplementary CLI bindings for GTK 2.14+
ii  libgtk2-notify-perl                           0.05-3build1                            Perl interface to libnotify
ii  libgtk2-perl                                  2:1.223-1build3                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2-trayicon-perl                         0.06-1build2                            Perl interface to fill the system tray
ii  libgtk2.0-0                                   2.24.10-0ubuntu6                        GTK+ graphical user interface library
ii  libgtk2.0-bin                                 2.24.10-0ubuntu6                        programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                 2.12.10-2ubuntu4                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                              2.24.10-0ubuntu6                        common files for the GTK+ graphical user interface library
ii  libgtkmathview0c2a                            0.8.0-7                                 rendering engine for MathML documents
ii  libgtkmm-2.4-1c2a                             1:2.24.2-1ubuntu1                       C++ wrappers for GTK+ (shared libraries)
ii  libgtkmm-3.0-1                                3.4.0-0ubuntu1                          C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview-3.0-0                        3.4.2-0ubuntu1                          shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview-3.0-common                   3.4.2-0ubuntu1                          common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                                  2.0.16-1ubuntu5                         a spell-checking addon for GTK's TextView widget
ii  libgtop2-7                                    2.28.4-2                                gtop system monitoring library (shared)
ii  libgtop2-common                               2.28.4-2                                gtop system monitoring library (common)
ii  libgucharmap-2-90-7                           1:3.4.1.1-0ubuntu1                      Unicode browser widget library (shared library)
ii  libgudev-1.0-0                                1:175-0ubuntu9.2                        GObject-based wrapper library for libudev
ii  libgudev1.0-cil                               0.1-2build1                             GObject-based wrapper library for libudev -- CLI bindings
ii  libguile-ltdl-1                               1.6.8-10ubuntu4                         Guile's patched version of libtool's libltdl
ii  libgupnp-1.0-4                                0.18.1-2                                GObject-based library for UPnP
ii  libgupnp-igd-1.0-4                            0.2.1-2                                 library to handle UPnP IGD port mapping
ii  libgutenprint2                                5.2.8~pre1-0ubuntu2.1                   runtime for the Gutenprint printer driver library
ii  libgvc5                                       2.26.3-10ubuntu1                        rich set of graph drawing tools - gvc library
ii  libhcrypto4-heimdal                           1.6~git20120311.dfsg.1-2                Heimdal Kerberos - crypto library
ii  libheimbase1-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - Base library
ii  libheimntlm0-heimdal                          1.6~git20120311.dfsg.1-2                Heimdal Kerberos - NTLM support library
ii  libhpmud0                                     3.12.2-1ubuntu3.1                       HP Multi-Point Transport Driver (hpmud) run-time libraries
ii  libhsqldb-java                                1.8.0.10-9ubuntu2                       Java SQL database engine
ii  libhtml-form-perl                             6.00-1                                  module that represents an HTML form element
ii  libhtml-format-perl                           2.10-1                                  module for transforming HTML into various formats
ii  libhtml-parser-perl                           3.69-1build1                            collection of modules that parse HTML text documents
ii  libhtml-tagset-perl                           3.20-2                                  Data tables pertaining to HTML
ii  libhtml-tree-perl                             4.2-1                                   Perl module to represent and create HTML syntax trees
ii  libhttp-cookies-perl                          6.00-2                                  HTTP cookie jars
ii  libhttp-daemon-perl                           6.00-1                                  simple http server class
ii  libhttp-date-perl                             6.00-1                                  module of date conversion routines
ii  libhttp-message-perl                          6.01-1                                  perl interface to HTTP style messages
ii  libhttp-negotiate-perl                        6.00-2                                  implementation of content negotiation
ii  libhunspell-1.3-0                             1.3.2-4                                 spell checker and morphological analyzer (shared library)
ii  libhx509-5-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - X509 support library
ii  libhyphen0                                    2.8.3-1                                 ALTLinux hyphenation library - shared library
ii  libibus-1.0-0                                 1.4.1-3ubuntu1                          Intelligent Input Bus - shared library
ii  libical0                                      0.48-1ubuntu3                           iCalendar library implementation in C (runtime)
ii  libice6                                       2:1.0.7-2build1                         X11 Inter-Client Exchange library
ii  libicu48                                      4.8.1.1-3                               International Components for Unicode
ii  libid3tag0                                    0.15.1b-10build2                        ID3 tag reading library from the MAD project
ii  libidl-common                                 0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files (common files)
ii  libidl0                                       0.8.14-0.2ubuntu2                       library for parsing CORBA IDL files
ii  libidn11                                      1.23-2                                  GNU Libidn library, implementation of IETF IDN specifications
ii  libido-0.1-0                                  0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libido3-0.1-0                                 0.3.4-0ubuntu1                          Shared library providing extra gtk menu items for display in
ii  libiec61883-0                                 1.2.0-0.1ubuntu1                        an partial implementation of IEC 61883
ii  libieee1284-3                                 0.2.11-10build1                         cross-platform library for parallel port access
ii  libijs-0.35                                   0.35-8                                  IJS raster image transport protocol: shared library
ii  libilmbase6                                   1.0.1-3build2                           several utility libraries from ILM used by OpenEXR
ii  libimlib2                                     1.4.4-1build1                           powerful image loading and rendering library
ii  libimobiledevice2                             1.1.1-4                                 Library for communicating with the iPhone and iPod Touch
ii  libindi-data                                  0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared data
ii  libindi0                                      0.8-1ubuntu1                            Instrument-Neutral Device Interface library -- shared library
ii  libindicate-gtk3                              0.6.92-0ubuntu1                         library for raising indicators via DBus - GTK+ bindings
ii  libindicate5                                  0.6.92-0ubuntu1                         library for raising indicators via DBus
ii  libindicator-messages-status-provider1        0.6.0-0ubuntu2                          indicator status provider - shared library
ii  libindicator3-7                               0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libindicator7                                 0.5.0-0ubuntu1                          panel indicator applet - shared library
ii  libio-socket-inet6-perl                       2.69-2                                  object interface for AF_INET6 domain sockets
ii  libio-socket-ssl-perl                         1.53-1                                  Perl module implementing object oriented interface to SSL sockets
ii  libisc83                                      1:9.8.1.dfsg.P1-4ubuntu0.5              ISC Shared Library used by BIND
ii  libisccc80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Command Channel Library used by BIND
ii  libisccfg82                                   1:9.8.1.dfsg.P1-4ubuntu0.5              Config File Handling Library used by BIND
ii  libiso9660-8                                  0.83-1                                  library to work with ISO9660 filesystems
ii  libisofs6                                     1.1.6-1ubuntu1                          library to create ISO9660 images
ii  libiw30                                       30~pre9-5ubuntu2                        Wireless tools - library
ii  libjack-jackd2-0                              1.9.8~dfsg.1-1ubuntu1                   JACK Audio Connection Kit (libraries)
ii  libjasper1                                    1.900.1-13                              JasPer JPEG-2000 runtime library
ii  libjava3d-java                                1.5.2+dfsg-5                            Java 3D API (java library)
ii  libjava3d-jni                                 1.5.2+dfsg-5                            Java3D API (java jni library)
ii  libjavascriptcoregtk-1.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjavascriptcoregtk-3.0-0                    1.8.3-0ubuntu0.12.04.1                  Javascript engine library for GTK+
ii  libjbig2dec0                                  0.11-1ubuntu1                           JBIG2 decoder library - shared libraries
ii  libjline-java                                 1.0-1                                   Java library for handling console input
ii  libjpeg-progs                                 8c-2ubuntu7                             Programs for manipulating JPEG files (dependency package)
ii  libjpeg-turbo-progs                           1.1.90+svn733-0ubuntu4.1                Programs for manipulating JPEG files
ii  libjpeg-turbo8                                1.1.90+svn733-0ubuntu4.1                IJG JPEG compliant runtime library.
ii  libjpeg8                                      8c-2ubuntu7                             Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjs-jquery                                  1.7.1-1ubuntu1                          JavaScript library for dynamic web applications
ii  libjson-glib-1.0-0                            0.14.2-1                                GLib JSON manipulation library
ii  libjson-ruby                                  1.6.3-1                                 Transitional package for ruby-json
ii  libjson0                                      0.9-1ubuntu1                            JSON manipulation library - shared library
ii  libjte1                                       1.19-1                                  Jigdo Template Export - runtime library
ii  libk5crypto3                                  1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Crypto Library
rc  libkabc4                                      4:4.8.5-0ubuntu0.1                      library for handling address book data
rc  libkalarmcal2                                 4:4.8.5-0ubuntu0.1                      library for handling alarm calendar data
ii  libkate1                                      0.4.1-1                                 Kate is a codec for karaoke and text encapsulation
ii  libkatepartinterfaces4                        4:4.8.5-0ubuntu0.1                      kate part library
rc  libkcal4                                      4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalcore4                                  4:4.8.5-0ubuntu0.1                      library for handling calendar data
rc  libkcalutils4                                 4:4.8.5-0ubuntu0.1                      library with utility functions for the handling of calendar data
ii  libkcmutils4                                  4:4.8.5-0ubuntu0.1                      utility classes for using KCM modules
ii  libkde3support4                               4:4.8.5-0ubuntu0.1                      KDE 3 Support Library for the KDE 4 Platform
ii  libkdeclarative5                              4:4.8.5-0ubuntu0.1                      Declarative library for plasma
ii  libkdecore5                                   4:4.8.5-0ubuntu0.1                      KDE Platform Core Library
ii  libkdeedu-data                                4:4.8.5-0ubuntu0.1                      data files for libkdeedu
ii  libkdesu5                                     4:4.8.5-0ubuntu0.1                      Console-mode Authentication Library for the KDE Platform
ii  libkdeui5                                     4:4.8.5-0ubuntu0.1                      KDE Platform User Interface Library
ii  libkdewebkit5                                 4:4.8.5-0ubuntu0.1                      KDE WebKit Library
ii  libkdnssd4                                    4:4.8.5-0ubuntu0.1                      DNS-SD Protocol Library for the KDE Platform
ii  libkeduvocdocument4                           4:4.8.5-0ubuntu0.1                      library for reading and writing vocabulary files
ii  libkemoticons4                                4:4.8.5-0ubuntu0.1                      utility classes to deal with emoticon themes
ii  libkeybinder0                                 0.2.2-3build1                           registers global key bindings for applications
ii  libkeyutils1                                  1.5.2-2                                 Linux Key Management Utilities (library)
ii  libkfile4                                     4:4.8.5-0ubuntu0.1                      File Selection Dialog Library for KDE Platform
rc  libkholidays4                                 4:4.8.5-0ubuntu0.1                      holidays calculation library
ii  libkhtml5                                     4:4.8.5-0ubuntu0.1                      KHTML Web Content Rendering Engine
ii  libkidletime4                                 4:4.8.5-0ubuntu0.1                      library to provide information about idle time
rc  libkimap4                                     4:4.8.5-0ubuntu0.1                      library for handling IMAP data
ii  libkio5                                       4:4.8.5-0ubuntu0.1                      Network-enabled File Management Library for the KDE Platform
ii  libkjsapi4                                    4:4.8.5-0ubuntu0.1                      KJS API Library for the KDE Development Platform
ii  libkjsembed4                                  4:4.8.5-0ubuntu0.1                      library for binding JavaScript objects to QObjects
rc  libkldap4                                     4:4.8.5-0ubuntu0.1                      library for accessing LDAP
ii  libklibc                                      1.5.25-1ubuntu2                         minimal libc subset for use with initramfs
rc  libkmbox4                                     4:4.8.5-0ubuntu0.1                      library for handling mbox mailboxes
ii  libkmediaplayer4                              4:4.8.5-0ubuntu0.1                      KMediaPlayer Interface for the KDE Platform
rc  libkmime4                                     4:4.8.5-0ubuntu0.1                      library for handling MIME data
rc  libknewstuff2-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v2 Library for the KDE Platform
ii  libknewstuff3-4                               4:4.8.5-0ubuntu0.1                      "Get Hot New Stuff" v3 Library for the KDE Platform
ii  libknotifyconfig4                             4:4.8.5-0ubuntu0.1                      library for configuring KDE Notifications
ii  libkntlm4                                     4:4.8.5-0ubuntu0.1                      NTLM Authentication Library for the KDE Platform
ii  libkparts4                                    4:4.8.5-0ubuntu0.1                      Framework for the KDE Platform Graphical Components
ii  libkpathsea5                                  2009-11ubuntu2                          TeX Live: path search library for TeX (runtime part)
rc  libkpimidentities4                            4:4.8.5-0ubuntu0.1                      library for managing user identities
rc  libkpimtextedit4                              4:4.8.5-0ubuntu0.1                      library that provides a textedit with PIM-specific features
rc  libkpimutils4                                 4:4.8.5-0ubuntu0.1                      library for dealing with email addresses
ii  libkprintutils4                               4:4.8.5-0ubuntu0.1                      utility classes to deal with printing
ii  libkpty4                                      4:4.8.5-0ubuntu0.1                      Pseudo Terminal Library for the KDE Platform
ii  libkrb5-26-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - libraries
ii  libkrb5-3                                     1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries
ii  libkrb5support0                               1.10+dfsg~beta1-2ubuntu0.3              MIT Kerberos runtime libraries - Support library
rc  libkresources4                                4:4.8.5-0ubuntu0.1                      KDE Resource framework library
ii  libkrosscore4                                 4:4.8.5-0ubuntu0.1                      Kross Core Library
ii  libktexteditor4                               4:4.8.5-0ubuntu0.1                      KTextEditor interfaces for the KDE Platform
ii  libkunitconversion4                           4:4.8.5-0ubuntu0.1                      Unit Conversion library for the KDE Platform
ii  liblapack3gf                                  3.3.1-1                                 library of linear algebra routines 3 - shared version
ii  liblaunchpad-integration-3.0-1                0.1.56.1                                library for launchpad integration
ii  liblaunchpad-integration-common               0.1.56.1                                library for launchpad integration common data
ii  liblaunchpad-integration1                     0.1.56.1                                library for launchpad integration
ii  liblcms1                                      1.19.dfsg-1ubuntu3                      Little CMS color management library
ii  liblcms2-2                                    2.2+git20110628-2ubuntu3                Little CMS 2 color management library
ii  libldap-2.4-2                                 2.4.28-1.1ubuntu4.2                     OpenLDAP libraries
ii  liblightdm-gobject-1-0                        1.2.1-0ubuntu1.1                        LightDM GObject client library
ii  liblightdm-qt-2-0                             1.2.1-0ubuntu1.1                        LightDM Qt client library
ii  liblink-grammar4                              4.7.4-2                                 Carnegie Mellon University's link grammar parser (libraries)
ii  liblircclient0                                0.9.0-0ubuntu1                          infra-red remote control support - client library
ii  libllvm3.0                                    3.0-4ubuntu1                            Low-Level Virtual Machine (LLVM), runtime library
ii  liblocale-gettext-perl                        1.05-7build1                            module using libc functions for internationalization in Perl
ii  liblockfile-bin                               1.09-3                                  support binaries for and cli utilities based on liblockfile
ii  liblockfile1                                  1.09-3                                  NFS-safe locking library
ii  libloudmouth1-0                               1.4.3-8                                 Lightweight C Jabber library
ii  liblqr-1-0                                    0.4.1-1.1                               converts plain array images into multi-size representation
ii  libltdl7                                      2.4.2-1ubuntu1                          A system independent dlopen wrapper for GNU libtool
ii  liblua5.1-0                                   5.1.4-12ubuntu1                         Shared library for the Lua interpreter version 5.1
ii  liblvm2app2.2                                 2.02.66-4ubuntu7.1                      LVM2 application library
ii  liblwp-mediatypes-perl                        6.01-1                                  module to guess media type for a file or a URL
ii  liblwp-protocol-https-perl                    6.02-1                                  https driver for LWP::UserAgent
ii  liblwres80                                    1:9.8.1.dfsg.P1-4ubuntu0.5              Lightweight Resolver Library used by BIND
ii  liblzma5                                      5.1.1alpha+20110809-3                   XZ-format compression library
ii  liblzo2-2                                     2.06-1                                  data compression library
ii  libmad0                                       0.15.1b-7ubuntu1                        MPEG audio decoder library
ii  libmagic1                                     5.09-2                                  File type determination library using "magic" numbers
ii  libmagick++4                                  8:6.6.9.7-5ubuntu3.2                    object-oriented C++ interface to ImageMagick
ii  libmagickcore4                                8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library
ii  libmagickcore4-extra                          8:6.6.9.7-5ubuntu3.2                    low-level image manipulation library - extra codecs
ii  libmagickwand4                                8:6.6.9.7-5ubuntu3.2                    image manipulation library
ii  libmailtools-perl                             2.08-1                                  Manipulate email in perl programs
rc  libmailtransport4                             4:4.8.5-0ubuntu0.1                      mail transport service library
ii  libmarblewidget13                             4:4.8.5-0ubuntu0.1                      Marble globe widget library
ii  libmatroska5                                  1.3.0-1                                 extensible open standard audio/video container format (shared library)
ii  libmeanwhile1                                 1.0.2-4ubuntu1                          open implementation of the Lotus Sametime Community Client protocol
ii  libmhash2                                     0.9.9.9-1                               Library for cryptographic hashing and message authentication
rc  libmicroblog4                                 4:4.8.5-0ubuntu0.1                      library for using the Microblog Akonadi Resource
ii  libmimic0                                     1.0.4-2.1build1                         A video codec for Mimic V2.x content
ii  libminiupnpc8                                 1.6-3ubuntu1                            UPnP IGD client lightweight library
ii  libmjpegtools-1.9                             1:1.9.0-0.5ubuntu7                      MJPEG video capture/editting/playback MPEG encoding
ii  libmlt++3                                     0.7.6+git20120204-2                     MLT multimedia framework C++ wrapper (runtime)
ii  libmlt-data                                   0.7.6+git20120204-2                     multimedia framework (data)
ii  libmlt4                                       0.7.6+git20120204-2                     multimedia framework (runtime)
ii  libmms0                                       0.6.2-2                                 MMS stream protocol library - shared library
ii  libmng1                                       1.0.10-3                                Multiple-image Network Graphics library
ii  libmodplug1                                   1:0.8.8.4-1                             shared libraries for mod music based on ModPlug
ii  libmono-addins-gui0.2-cil                     0.6.2-2                                 GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                         0.6.2-2                                 addin framework for extensible CLI applications/libraries
ii  libmono-cairo4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono Cairo library (for CLI 4.0)
ii  libmono-corlib4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono core library (for CLI 4.0)
ii  libmono-data-tds4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Data Library (for CLI 4.0)
ii  libmono-i18n-west4.0-cil                      2.10.8.1-1ubuntu2.2                     Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono I18N base library (for CLI 4.0)
ii  libmono-posix4.0-cil                          2.10.8.1-1ubuntu2.2                     Mono.Posix library (for CLI 4.0)
ii  libmono-security4.0-cil                       2.10.8.1-1ubuntu2.2                     Mono Security library (for CLI 4.0)
ii  libmono-sharpzip4.84-cil                      2.10.8.1-1ubuntu2.2                     Mono SharpZipLib library (for CLI 4.0)
ii  libmono-simd4.0-cil                           2.10.8.1-1ubuntu2.2                     Mono SIMD (for CLI 4.0)
ii  libmono-sqlite4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono Sqlite library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil           2.10.8.1-1ubuntu2.2                     Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-core4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Core library (for CLI 4.0)
ii  libmono-system-data4.0-cil                    2.10.8.1-1ubuntu2.2                     Mono System.Data library (for CLI 4.0)
ii  libmono-system-drawing4.0-cil                 2.10.8.1-1ubuntu2.2                     Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-enterpriseservices4.0-cil      2.10.8.1-1ubuntu2.2                     Mono System.EnterpriseServices library (for CLI 4.0)
ii  libmono-system-security4.0-cil                2.10.8.1-1ubuntu2.2                     Mono System.Security library (for CLI 4.0)
ii  libmono-system-transactions4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Transactions library (for CLI 4.0)
ii  libmono-system-web-applicationservices4.0-cil 2.10.8.1-1ubuntu2.2                     Mono System.Web.ApplicationServices library (for CLI 4.0)
ii  libmono-system-web-services4.0-cil            2.10.8.1-1ubuntu2.2                     Mono System.Web.Services (for CLI 4.0)
ii  libmono-system-web4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Web library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                     2.10.8.1-1ubuntu2.2                     Mono System.Xml library (for CLI 4.0)
ii  libmono-system4.0-cil                         2.10.8.1-1ubuntu2.2                     Mono System libraries (for CLI 4.0)
ii  libmono-web4.0-cil                            2.10.8.1-1ubuntu2.2                     Mono.Web library (for CLI 4.0)
ii  libmono-zeroconf1.0-cil                       0.9.0-3                                 CLI library for multicast DNS service discovery
ii  libmount1                                     2.20.1-1ubuntu3                         block device id library
ii  libmp3lame0                                   3.99.3+repack1-1                        MP3 encoding library
ii  libmpc2                                       0.9-4                                   multiple precision complex floating-point library
ii  libmpcdec6                                    2:0.1~r459-1ubuntu1                     MusePack decoder - library
ii  libmpeg2-4                                    0.4.1-3                                 MPEG1 and MPEG2 video decoder library
ii  libmpfr4                                      3.1.0-3ubuntu2                          multiple precision floating-point computation
ii  libmpg123-0                                   1.12.1-3.2ubuntu1                       MPEG layer 1/2/3 audio decoder -- runtime library
ii  libmtdev1                                     1.1.0-2ubuntu1                          Multitouch Protocol Translation Library - shared library
ii  libmtp-common                                 1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) common files
ii  libmtp-runtime                                1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) runtime tools
ii  libmtp9                                       1.1.3-1ubuntu0.1                        Media Transfer Protocol (MTP) library
ii  libmusicbrainz3-6                             3.0.2-2.1                               library to access the MusicBrainz.org database
ii  libmx-1.0-2                                   1.4.3-0ubuntu1                          toolkit for the Moblin user experience
ii  libmysqlclient18                              5.5.28-0ubuntu0.12.04.3                 MySQL database client library
ii  libmythes-1.2-0                               2:1.2.2-1                               simple thesaurus library
ii  libnautilus-extension1a                       1:3.4.2-0ubuntu6                        libraries for nautilus components - runtime version
ii  libncurses5                                   5.9-4                                   shared libraries for terminal handling
ii  libncursesw5                                  5.9-4                                   shared libraries for terminal handling (wide character support)
ii  libndesk-dbus1.0-cil                          0.6.0-5                                 CLI implementation of D-Bus
ii  libneon27-gnutls                              0.29.6-1                                HTTP and WebDAV client library (GnuTLS enabled)
ii  libnepomuk4                                   4:4.8.5-0ubuntu0.1                      Nepomuk Meta Data Library
ii  libnepomukdatamanagement4                     4:4.8.5-0ubuntu0.1                      Basic Nepomuk data manipulation interface
ii  libnepomukquery4a                             4:4.8.5-0ubuntu0.1                      Nepomuk Query Library for the KDE Platform
ii  libnepomuksync4                               4:4.8.5-0ubuntu0.1                      Nepomuk sync interface for the Backup and Sync service
ii  libnepomukutils4                              4:4.8.5-0ubuntu0.1                      Nepomuk Utility Library
ii  libnet-dbus-perl                              1.0.0-1build1                           Extension for the DBus bindings
ii  libnet-http-perl                              6.02-1                                  module providing low-level HTTP connection client
ii  libnet-ssleay-perl                            1.42-1build1                            Perl module for Secure Sockets Layer (SSL)
ii  libnetfilter-conntrack3                       0.9.1-1ubuntu1                          Netfilter netlink-conntrack library
ii  libnetpbm10                                   2:10.0-15                               Graphics conversion tools shared libraries
ii  libnettle4                                    2.4-1                                   low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52                                   0.52.11-2ubuntu10                       Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnfnetlink0                                 1.0.0-1                                 Netfilter netlink library
ii  libnice10                                     0.1.1-2ubuntu1                          ICE library (shared library)
ii  libnih-dbus1                                  1.0.3-4ubuntu9                          NIH D-Bus Bindings Library
ii  libnih1                                       1.0.3-4ubuntu9                          NIH Utility Library
ii  libnl-3-200                                   3.2.3-2ubuntu2                          library for dealing with netlink sockets
ii  libnl-genl-3-200                              3.2.3-2ubuntu2                          library for dealing with netlink sockets - generic netlink
ii  libnl-route-3-200                             3.2.3-2ubuntu2                          library for dealing with netlink sockets - route interface
ii  libnm-glib-vpn1                               0.9.4.0-0ubuntu4.1                      network management framework (GLib VPN shared library)
ii  libnm-glib4                                   0.9.4.0-0ubuntu4.1                      network management framework (GLib shared library)
ii  libnm-gtk-common                              0.9.4.1-0ubuntu2                        network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                    0.9.4.1-0ubuntu2                        network management framework (GNOME dialogs for wifi and mobile)
ii  libnm-util2                                   0.9.4.0-0ubuntu4.1                      network management framework (shared library)
ii  libnotify-bin                                 0.7.5-1                                 sends desktop notifications to a notification daemon (Utilities)
ii  libnotify0.4-cil                              0.4.0~r3032-4                           CLI library for desktop notifications
ii  libnotify4                                    0.7.5-1                                 sends desktop notifications to a notification daemon
ii  libnova-0.12-2                                0.12.2-0ubuntu2                         astronomical library
ii  libnspr4                                      4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnspr4-0d                                   4.8.9-1ubuntu2.3                        NetScape Portable Runtime Library
ii  libnss-mdns                                   0.10-3.2                                NSS module for Multicast DNS name resolution
ii  libnss3                                       3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libnss3-1d                                    3.13.1.with.ckbi.1.88-1ubuntu6.1        Network Security Service libraries
ii  libntrack-qt4-1                               016-1ubuntu1                            Qt 4 API for ntrack
ii  libntrack0                                    016-1ubuntu1                            lightweight connectivity tracking library
rc  libobjc3                                      4.6.3-1ubuntu5                          Runtime library for GNU Objective-C applications
ii  libodbc1                                      2.2.14p2-5ubuntu3                       ODBC library for Unix
ii  libofa0                                       0.9.3-4                                 Library for acoustic fingerprinting
ii  libogg0                                       1.2.2~dfsg-1ubuntu1                     Ogg bitstream library
ii  liboil0.3                                     0.3.17-2ubuntu3                         Library of Optimized Inner Loops
ii  liboobs-1-5                                   3.0.0-1                                 GObject based interface to system-tools-backends - shared library
ii  libopenal-data                                1:1.13-4ubuntu3                         Software implementation of the OpenAL API (data files)
ii  libopenal1                                    1:1.13-4ubuntu3                         Software implementation of the OpenAL API (shared library)
ii  libopenbabel4                                 2.3.0+dfsg-3ubuntu3                     Chemical toolbox library
ii  libopencc1                                    0.3.0-1                                 simplified-traditional chinese conversion library - runtime
ii  libopencore-amrnb0                            0.1.2-1                                 Adaptive Multi Rate speech codec - shared library
ii  libopencore-amrwb0                            0.1.2-1                                 Adaptive Multi-Rate - Wideband speech codec - shared library
ii  libopencv-calib3d2.3                          2.3.1-7                                 computer vision Camera Calibration library
ii  libopencv-core2.3                             2.3.1-7                                 computer vision core library
ii  libopencv-features2d2.3                       2.3.1-7                                 computer vision Feature Detection and Descriptor Extraction library
ii  libopencv-flann2.3                            2.3.1-7                                 computer vision Clustering and Search in Multi-Dimensional spaces library
ii  libopencv-highgui2.3                          2.3.1-7                                 computer vision High-level GUI and Media I/O library
ii  libopencv-imgproc2.3                          2.3.1-7                                 computer vision Image Processing library
ii  libopencv-objdetect2.3                        2.3.1-7                                 computer vision Object Detection library
ii  libopenexr6                                   1.6.1-4.1                               runtime files for the OpenEXR image library
ii  libopenjpeg2                                  1.3+dfsg-4                              JPEG 2000 image compression/decompression library
ii  libopenobex1                                  1.5-2build1                             OBEX protocol library
ii  libopenspc0                                   0.3.99a-2                               library for playing SPC files
ii  liborbit2                                     1:2.14.19-0.1ubuntu1                    libraries for ORBit2 - a CORBA ORB
ii  liborc-0.4-0                                  1:0.4.16-1ubuntu2                       Library of Optimized Inner Loops Runtime Compiler
ii  libotr2                                       3.2.0-4ubuntu0.1                        Off-the-Record Messaging library
ii  libots0                                       0.5.0-2.1                               Open Text Summarizer (library)
ii  libp11-kit0                                   0.12-2ubuntu1                           Library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpam-cap                                    1:2.22-1ubuntu3                         PAM module for implementing capabilities
ii  libpam-ck-connector                           0.4.5-2                                 ConsoleKit PAM module
ii  libpam-gnome-keyring                          3.2.2-2ubuntu4                          PAM module to unlock the GNOME keyring upon login
ii  libpam-modules                                1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                            1.1.3-7ubuntu2                          Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                                1.1.3-7ubuntu2                          Runtime support for the PAM library
ii  libpam0g                                      1.1.3-7ubuntu2                          Pluggable Authentication Modules library
ii  libpango-perl                                 1.222-1build1                           Perl module to layout and render international text
ii  libpango1.0-0                                 1.30.0-0ubuntu3.1                       Layout and rendering of internationalized text
ii  libpangomm-1.4-1                              2.28.4-1ubuntu1                         C++ Wrapper for pango (shared libraries)
ii  libpaper-utils                                1.1.24+nmu1build1                       library for handling paper characteristics (utilities)
ii  libpaper1                                     1.1.24+nmu1build1                       library for handling paper characteristics
ii  libparted0debian1                             2.3-8ubuntu5.1                          disk partition manipulator - shared library
ii  libpathplan4                                  2.26.3-10ubuntu1                        rich set of graph drawing tools - pathplan library
ii  libpcap0.8                                    1.1.1-10                                system interface for user-level packet capture
ii  libpci3                                       1:3.1.8-2ubuntu5                        Linux PCI Utilities (shared library)
ii  libpciaccess0                                 0.12.902-1                              Generic PCI access library for X
ii  libpcre3                                      8.12-4                                  Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcsclite1                                  1.7.4-2ubuntu2                          Middleware to access a smart card using PC/SC (library)
ii  libpeas-1.0-0                                 1.2.0-1ubuntu1                          Application plugin library
ii  libpeas-common                                1.2.0-1ubuntu1                          Application plugin library (common files)
ii  libperl5.14                                   5.14.2-6ubuntu2.2                       shared Perl library
ii  libphonon4                                    4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - core library
ii  libpipeline1                                  1.2.1-1                                 pipeline manipulation library
ii  libpixman-1-0                                 0.24.4-1                                pixel-manipulation library for X and cairo
ii  libplasma3                                    4:4.8.5-0ubuntu0.1                      Plasma Library for the KDE Platform
ii  libplist1                                     1.8-1                                   Library for handling Apple binary and XML property lists
ii  libplymouth2                                  0.8.2-2ubuntu30                         graphical boot animation and logger - shared libraries
ii  libpng12-0                                    1.2.46-3ubuntu4                         PNG library - runtime
ii  libpolkit-agent-1-0                           0.104-1ubuntu1                          PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0                         0.104-1ubuntu1                          PolicyKit backend API
ii  libpolkit-gobject-1-0                         0.104-1ubuntu1                          PolicyKit Authorization API
ii  libpolkit-qt-1-1                              0.103.0-1                               PolicyKit-qt-1 library
ii  libpoppler-glib8                              0.18.4-1ubuntu3                         PDF rendering library (GLib-based shared library)
ii  libpoppler19                                  0.18.4-1ubuntu3                         PDF rendering library
ii  libpopt0                                      1.16-3ubuntu1                           lib for parsing cmdline parameters
ii  libportaudio2                                 19+svn20111121-1                        Portable audio I/O - shared library
ii  libportsmf0                                   0.1~svn20101010-3                       Portable Standard Midi File Library
ii  libpostproc-extra-52                          4:0.8.4ubuntu0.12.04.1                  Libav video postprocessing library
rc  libpostproc52                                 4:0.8.4-0ubuntu0.12.04.1                Libav video postprocessing library
rc  libprison0                                    1.0+dfsg-1                              barcode API for Qt
ii  libproxy1                                     0.4.7-0ubuntu4.1                        automatic proxy configuration management library (shared)
ii  libpulse-mainloop-glib0                       1:1.1-0ubuntu15.1                       PulseAudio client libraries (glib support)
ii  libpulse0                                     1:1.1-0ubuntu15.1                       PulseAudio client libraries
ii  libpulsedsp                                   1:1.1-0ubuntu15.1                       PulseAudio OSS pre-load library
ii  libpurple-bin                                 1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library - extra utilities
ii  libpurple0                                    1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging library
ii  libpython2.7                                  2.7.3-0ubuntu3.1                        Shared Python runtime library (version 2.7)
ii  libpython3.2                                  3.2.3-0ubuntu3.2                        Shared Python runtime library (version 3.2)
ii  libqalculate5                                 0.9.7-6ubuntu2                          Powerful and easy to use desktop calculator - library
ii  libqapt-runtime                               1.3.1-0ubuntu2                          Runtime components for the QApt library
ii  libqapt1                                      1.3.1-0ubuntu2                          QApt library package
ii  libqca2                                       2.0.3-2                                 libraries for the Qt Cryptographic Architecture
ii  libqimageblitz4                               1:0.0.6-4                               QImageBlitz image effects library
rc  libqrencode3                                  3.1.1-1ubuntu1                          QR Code encoding library
ii  libqt3-mt                                     3:3.3.8-b-8ubuntu3                      Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-dbus                                   4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus module
ii  libqt4-declarative                            4:4.8.1-0ubuntu4.3                      Qt 4 Declarative module
ii  libqt4-designer                               4:4.8.1-0ubuntu4.3                      Qt 4 designer module
ii  libqt4-help                                   4:4.8.1-0ubuntu4.3                      Qt 4 help module
ii  libqt4-network                                4:4.8.1-0ubuntu4.3                      Qt 4 network module
ii  libqt4-opengl                                 4:4.8.1-0ubuntu4.3                      Qt 4 OpenGL module
ii  libqt4-qt3support                             4:4.8.1-0ubuntu4.3                      Qt 3 compatibility library for Qt 4
ii  libqt4-script                                 4:4.8.1-0ubuntu4.3                      Qt 4 script module
ii  libqt4-scripttools                            4:4.8.1-0ubuntu4.3                      Qt 4 script tools module
ii  libqt4-sql                                    4:4.8.1-0ubuntu4.3                      Qt 4 SQL module
ii  libqt4-sql-mysql                              4:4.8.1-0ubuntu4.3                      Qt 4 MySQL database driver
ii  libqt4-svg                                    4:4.8.1-0ubuntu4.3                      Qt 4 SVG module
ii  libqt4-test                                   4:4.8.1-0ubuntu4.3                      Qt 4 test module
ii  libqt4-xml                                    4:4.8.1-0ubuntu4.3                      Qt 4 XML module
ii  libqt4-xmlpatterns                            4:4.8.1-0ubuntu4.3                      Qt 4 XML patterns module
ii  libqtassistantclient4                         4.6.3-3ubuntu2                          Qt Assistant client library (runtime)
ii  libqtcore4                                    4:4.8.1-0ubuntu4.3                      Qt 4 core module
ii  libqtgui4                                     4:4.8.1-0ubuntu4.3                      Qt 4 GUI module
ii  libqthreads-12                                1.6.8-10ubuntu4                         QuickThreads library for Guile
ii  libqtwebkit4                                  2.2.1-1ubuntu4                          Web content engine library for Qt
ii  libquadmath0                                  4.6.3-1ubuntu5                          GCC Quad-Precision Math Library
ii  libquicktime2                                 2:1.2.3-4build2                         library for reading and writing Quicktime files
ii  libquvi-scripts                               0.4.2-1                                 library for parsing video download links (Lua scripts)
ii  libquvi7                                      0.4.0-1                                 library for parsing video download links (runtime libraries)
ii  libraptor2-0                                  2.0.6-1                                 Raptor 2 RDF syntax library
ii  librarian0                                    0.8.1-5                                 Documentation meta-data library (library package)
ii  librasqal3                                    0.9.28-1                                Rasqal RDF query library
ii  libraw1394-11                                 2.0.7-1ubuntu1                          library for direct access to IEEE 1394 bus (aka FireWire)
ii  librdf0                                       1.0.14-1                                Redland Resource Description Framework (RDF) library
ii  libreadline5                                  5.2-11                                  GNU readline and history libraries, run-time libraries
ii  libreadline6                                  6.2-8                                   GNU readline and history libraries, run-time libraries
ii  libreoffice                                   1:3.5.4-0ubuntu1.1                      office productivity suite
ii  libreoffice-base                              1:3.5.4-0ubuntu1.1                      office productivity suite -- database
ii  libreoffice-base-core                         1:3.5.4-0ubuntu1.1                      office productivity suite -- shared library
ii  libreoffice-calc                              1:3.5.4-0ubuntu1.1                      office productivity suite -- spreadsheet
ii  libreoffice-common                            1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent files
ii  libreoffice-core                              1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-dependent files
ii  libreoffice-draw                              1:3.5.4-0ubuntu1.1                      office productivity suite -- drawing
ii  libreoffice-emailmerge                        1:3.5.4-0ubuntu1.1                      office productivity suite -- email mail merge
ii  libreoffice-filter-mobiledev                  1:3.5.4-0ubuntu1.1                      office productivity suite -- mobile devices filters
ii  libreoffice-gnome                             1:3.5.4-0ubuntu1.1                      office productivity suite -- GNOME integration
ii  libreoffice-gtk                               1:3.5.4-0ubuntu1.1                      office productivity suite -- GTK+ integration
ii  libreoffice-impress                           1:3.5.4-0ubuntu1.1                      office productivity suite -- presentation
ii  libreoffice-java-common                       1:3.5.4-0ubuntu1.1                      office productivity suite -- arch-independent Java support files
ii  libreoffice-math                              1:3.5.4-0ubuntu1.1                      office productivity suite -- equation editor
ii  libreoffice-style-human                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Human symbol style
ii  libreoffice-style-tango                       1:3.5.4-0ubuntu1.1                      office productivity suite -- Tango symbol style
ii  libreoffice-writer                            1:3.5.4-0ubuntu1.1                      office productivity suite -- word processor
ii  libresid-builder0c2a                          2.1.1-12                                SID chip emulation class based on resid
ii  librhythmbox-core5                            2.96-0ubuntu4.2                         support library for the rhythmbox music player
ii  libroken18-heimdal                            1.6~git20120311.dfsg.1-2                Heimdal Kerberos - roken support library
ii  librsvg2-2                                    2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (runtime)
ii  librsvg2-common                               2.36.1-0ubuntu1                         SAX-based renderer library for SVG files (extra runtime)
ii  librtmp0                                      2.4~20110711.gitc28f1bab-1              toolkit for RTMP streams (shared library)
ii  libruby                                       4.8                                     Transitional package for libruby1.8
ii  libruby1.8                                    1.8.7.352-2ubuntu1.1                    Libraries necessary to run Ruby 1.8
ii  libsamplerate0                                0.1.8-4                                 Audio sample rate conversion library
ii  libsane                                       1.0.22-7ubuntu1                         API library for scanners
ii  libsane-common                                1.0.22-7ubuntu1                         API library for scanners -- documentation and support files
ii  libsane-hpaio                                 3.12.2-1ubuntu3.1                       HP SANE backend for multi-function peripherals
ii  libsasl2-2                                    2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - authentication abstraction library
ii  libsasl2-modules                              2.1.25.dfsg1-3ubuntu0.1                 Cyrus SASL - pluggable authentication modules
ii  libschroedinger-1.0-0                         1.0.11-1                                library for encoding/decoding of Dirac video streams
ii  libsdl-image1.2                               1.2.10-3                                image loading library for Simple DirectMedia Layer 1.2
ii  libsdl1.2debian                               1.2.14-6.4ubuntu3                       Simple DirectMedia Layer
ii  libselinux1                                   2.1.0-4.1ubuntu1                        SELinux runtime shared libraries
ii  libsensors4                                   1:3.3.1-2ubuntu1                        library to read temperature/voltage/fan sensors
ii  libservlet2.5-java                            6.0.35-1ubuntu3.1                       Servlet 2.5 and JSP 2.1 Java API classes
ii  libsexy2                                      0.1.11-2build2                          collection of additional GTK+ widgets - library
ii  libsgutils2-2                                 1.33-1                                  utilities for devices using the SCSI command set (shared libraries)
ii  libshadow-ruby1.8                             1.4.1-8build1                           Interface of shadow password for Ruby 1.8
ii  libshout3                                     2.2.2-7ubuntu1                          MP3/Ogg Vorbis broadcast streaming library
ii  libsidplay1                                   1.36.59-5                               SID (MOS 6581) emulation library
ii  libsidplay2                                   2.1.1-12                                SID (MOS 6581) emulation library
ii  libsigc++-2.0-0c2a                            2.2.10-0ubuntu2                         type-safe Signal Framework for C++ - runtime
ii  libslang2                                     2.2.4-3ubuntu1                          S-Lang programming library - runtime version
ii  libslp1                                       1.2.1-7.8ubuntu1                        OpenSLP libraries
ii  libslv2-9                                     0.6.6+dfsg1-1                           library for simple use of LV2 plugins
ii  libsm6                                        2:1.2.0-2build1                         X11 Session Management library
ii  libsmbclient                                  2:3.6.3-2ubuntu2.3                      shared library for communication with SMB/CIFS servers
ii  libsndfile1                                   1.0.25-4                                Library for reading/writing audio files
ii  libsnmp-base                                  5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) MIBs and documentation
ii  libsnmp15                                     5.4.3~dfsg-2.4ubuntu1.1                 SNMP (Simple Network Management Protocol) library
ii  libsocket6-perl                               0.23-1build2                            Perl extensions for IPv6
ii  libsolid4                                     4:4.8.5-0ubuntu0.1                      Solid Library for KDE Platform
ii  libsonic0                                     0.1.17-1.1                              Simple library to speed up or slow down speech
ii  libsoprano4                                   2.7.5+dfsg.1-0ubuntu1                   libraries for the Soprano RDF framework
ii  libsoundtouch0                                1.6.0-2build1                           Sound stretching library
ii  libsoup-gnome2.4-1                            2.38.1-1                                HTTP library implementation in C -- GNOME support library
ii  libsoup2.4-1                                  2.38.1-1                                HTTP library implementation in C -- Shared library
ii  libsox-fmt-alsa                               14.3.2-3                                SoX alsa format I/O library
ii  libsox-fmt-base                               14.3.2-3                                Minimal set of SoX format libraries
ii  libsox1b                                      14.3.2-3                                SoX library of audio effects and processing
ii  libspandsp2                                   0.0.6~pre18-2build1                     Telephony signal processing library
ii  libspectre1                                   0.2.6-1build1                           Library for rendering PostScript documents
ii  libspeechd2                                   0.7.1-6ubuntu3                          Speech Dispatcher: Shared libraries
ii  libspeex1                                     1.2~rc1-3ubuntu2                        The Speex codec runtime library
ii  libspeexdsp1                                  1.2~rc1-3ubuntu2                        The Speex extended runtime library
ii  libsqlite3-0                                  3.7.9-2ubuntu1.1                        SQLite 3 shared library
ii  libss2                                        1.42-1ubuntu2                           command-line interface parsing library
ii  libssh-4                                      0.5.2-1ubuntu0.12.04.1                  tiny C SSH library
ii  libssl1.0.0                                   1.0.1-4ubuntu5.5                        SSL shared libraries
ii  libstartup-notification0                      0.12-1ubuntu1                           library for program launch feedback (shared library)
ii  libstdc++6                                    4.6.3-1ubuntu5                          GNU Standard C++ Library v3
ii  libstdc++6-4.6-dev                            4.6.3-1ubuntu5                          GNU Standard C++ Library v3 (development files)
ii  libstlport4.6ldbl                             4.6.2-7                                 STLport C++ class library
ii  libstreamanalyzer0                            0.7.7-1.1ubuntu3                        streamanalyzer library for Strigi Desktop Search
ii  libstreams0                                   0.7.7-1.1ubuntu3                        streams library for for Strigi Desktop Search
ii  libsvga1                                      1:1.4.3-31                              console SVGA display libraries
ii  libswitch-perl                                2.16-2                                  switch statement for Perl
ii  libswscale-extra-2                            4:0.8.4ubuntu0.12.04.1                  Libav video software scaling library
rc  libswscale2                                   4:0.8.4-0ubuntu0.12.04.1                Libav video scaling library
ii  libsysfs2                                     2.1.0+repack-1                          interface library to sysfs
ii  libt1-5                                       5.1.2-3.4ubuntu1                        Type 1 font rasterizer library - runtime
ii  libtag1-vanilla                               1.7-1ubuntu5                            audio meta-data library - vanilla flavour
ii  libtag1c2a                                    1.7-1ubuntu5                            audio meta-data library
ii  libtagc0                                      1.7-1ubuntu5                            audio meta-data library - C bindings
ii  libtaglib2.0-cil                              2.0.4.0-1                               CLI library for accessing audio and video files metadata
ii  libtalloc2                                    2.0.7-3                                 hierarchical pool based memory allocator
ii  libtar0                                       1.2.11-8                                C library for manipulating tar archives
ii  libtasn1-3                                    2.10-1ubuntu1.1                         Manage ASN.1 structures (runtime)
ii  libtdb1                                       1.2.9-4                                 Trivial Database - shared library
ii  libtelepathy-glib0                            0.18.0-1ubuntu1                         Telepathy framework - GLib library
ii  libtext-charwidth-perl                        0.04-7build1                            get display widths of characters on the terminal
ii  libtext-iconv-perl                            1.7-5                                   converts between character sets in Perl
ii  libtext-wrapi18n-perl                         0.06-7                                  internationalized substitute of Text::Wrap
ii  libthai-data                                  0.1.16-3                                Data files for Thai language support library
ii  libthai0                                      0.1.16-3                                Thai language support library
ii  libtheora0                                    1.1.1+dfsg.1-3ubuntu2                   The Theora Video Compression Codec
ii  libthreadweaver4                              4:4.8.5-0ubuntu0.1                      ThreadWeaver Library for the KDE Platform
ii  libthunarx-2-0                                1.2.3-3ubuntu2                          extension library for thunar
ii  libtidy-0.99-0                                20091223cvs-1ubuntu2                    HTML syntax checker and reformatter - library
ii  libtie-ixhash-perl                            1.21-2                                  ordered associative arrays for Perl
ii  libtiff4                                      3.9.5-2ubuntu1.4                        Tag Image File Format (TIFF) library
ii  libtimedate-perl                              1.2000-1                                collection of modules to manipulate date/time information
ii  libtinfo5                                     5.9-4                                   shared low-level terminfo library for terminal handling
ii  libtommath0                                   0.42.0-1                                multiple-precision integer library [runtime]
ii  libtotem-plparser17                           3.4.1-1                                 Totem Playlist Parser library - runtime files
ii  libts-0.0-0                                   1.0-10                                  touch screen library
ii  libtumbler-1-0                                0.1.24-0ubuntu1                         library for tumbler, a D-Bus thumbnailing service
ii  libtwolame0                                   0.3.13-1build1                          MPEG Audio Layer 2 encoding library
ii  libudev0                                      175-0ubuntu9.2                          udev library
ii  libunique-1.0-0                               1.1.6-4                                 Library for writing single instance applications - shared libraries
ii  libunistring0                                 0.9.3-5                                 Unicode string library for C
ii  libunity9                                     5.12.0-0ubuntu1.1                       binding to get places into the launcher - shared library
ii  libupnp3                                      1:1.6.6-5.1                             Portable SDK for UPnP Devices, version 1.6 (shared libraries)
ii  libupower-glib1                               0.9.15-3git1                            abstraction for power management - shared library
ii  liburi-perl                                   1.59-1                                  module to manipulate and access URI strings
ii  libusb-0.1-4                                  2:0.1.12-20                             userspace USB programming library
ii  libusb-1.0-0                                  2:1.0.9~rc3-2ubuntu1                    userspace USB programming library
ii  libusbmuxd1                                   1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libutempter0                                  1.1.5-4                                 A privileged helper for utmp/wtmp updates (runtime)
ii  libutouch-evemu1                              1.0.9-0ubuntu1                          KernelInput Event Device Emulation Library
ii  libutouch-frame1                              2.2.3-0ubuntu1                          Touch Frame Library
ii  libutouch-geis1                               2.2.9-0ubuntu3                          Gesture engine interface support
ii  libutouch-grail1                              3.0.5-0ubuntu1                          Gesture Recognition And Instantiation Library
ii  libuuid-perl                                  0.02-4ubuntu1                           Perl extension for using UUID interfaces as defined in e2fsprogs
ii  libuuid1                                      2.20.1-1ubuntu3                         Universally Unique ID library
ii  libv4l-0                                      0.8.6-1ubuntu2                          Collection of video4linux support libraries
ii  libv4lconvert0                                0.8.6-1ubuntu2                          Video4linux frame format conversion library
ii  libva-x11-1                                   1.0.15-4                                Video Acceleration (VA) API for Linux -- X11 runtime
ii  libva1                                        1.0.15-4                                Video Acceleration (VA) API for Linux -- runtime
ii  libvamp-hostsdk3                              2.1-1                                   helper library for Vamp hosts written in C++
ii  libvcdinfo0                                   0.7.23-4.1ubuntu1                       library to extract information from VideoCD
ii  libvdpau1                                     0.4.1-3ubuntu1.1                        Video Decode and Presentation API for Unix (libraries)
ii  libvecmath-java                               1.5.2-3                                 javax.vecmath vector math package
ii  libvirtodbc0                                  6.1.4+dfsg1-0ubuntu1                    high-performance database - ODBC libraries
ii  libvisual-0.4-0                               0.4.0-4                                 Audio visualization framework
ii  libvisual-0.4-plugins                         0.4.0.dfsg.1-7                          Audio visualization framework plugins
ii  libvlc5                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer library
ii  libvlccore5                                   2.0.3-0ubuntu0.12.04.1                  base library for VLC and its modules
ii  libvo-aacenc0                                 0.1.1-2                                 VisualOn AAC encoder library
ii  libvo-amrwbenc0                               0.1.1-2                                 VisualOn AMR-WB encoder library
ii  libvorbis0a                                   1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Decoder library)
ii  libvorbisenc2                                 1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (Encoder library)
ii  libvorbisfile3                                1.3.2-1ubuntu3                          The Vorbis General Audio Compression Codec (High Level API)
ii  libvpx1                                       1.0.0-1                                 VP8 video codec (shared library)
ii  libvte-2.90-9                                 1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - runtime files
ii  libvte-2.90-common                            1:0.32.1-0ubuntu1                       Terminal emulator widget for GTK+ 3.0 - common files
ii  libvte-common                                 1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.x - common files
ii  libvte9                                       1:0.28.2-3ubuntu2                       Terminal emulator widget for GTK+ 2.0 - runtime files
ii  libwavpack1                                   4.60.1-2                                audio codec (lossy and lossless) - library
ii  libwbclient0                                  2:3.6.3-2ubuntu2.3                      Samba winbind client library
ii  libwebkitgtk-1.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0                            1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                       1.8.3-0ubuntu0.12.04.1                  Web content engine library for GTK+ - data files
ii  libwildmidi-config                            0.2.3.4-2.1                             software MIDI player configuration
ii  libwildmidi1                                  0.2.3.4-2.1                             software MIDI player library
ii  libwind0-heimdal                              1.6~git20120311.dfsg.1-2                Heimdal Kerberos - stringprep implementation
ii  libwmf-bin                                    0.2.8.4-10ubuntu1                       Windows metafile conversion tools
ii  libwmf0.2-7                                   0.2.8.4-10ubuntu1                       Windows metafile conversion library
ii  libwnck-3-0                                   3.4.0-0ubuntu1                          Window Navigator Construction Kit - runtime files
ii  libwnck-3-common                              3.4.0-0ubuntu1                          Window Navigator Construction Kit - common files
ii  libwnck-common                                1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - common files
ii  libwnck22                                     1:2.30.7-0ubuntu1                       Window Navigator Construction Kit - runtime files
ii  libwpd-0.9-9                                  0.9.4-1                                 Library for handling WordPerfect documents (shared library)
ii  libwpg-0.2-2                                  0.2.1-1                                 WordPerfect graphics import/convert library (shared library)
ii  libwps-0.2-2                                  0.2.4-1                                 Works text file format import filter library (shared library)
ii  libwrap0                                      7.6.q-21                                Wietse Venema's TCP wrappers library
ii  libwv-1.2-4                                   1.2.9-2                                 Library for accessing Microsoft Word documents
ii  libwww-perl                                   6.03-1                                  simple and consistent interface to the world-wide web
ii  libwww-robotrules-perl                        6.01-1                                  database of robots.txt-derived permissions
ii  libwxbase2.8-0                                2.8.12.1-6ubuntu2                       wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxgtk2.8-0                                 2.8.12.1-6ubuntu2                       wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libx11-6                                      2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-data                                   2:1.4.99.1-0ubuntu2                     X11 client-side library
ii  libx11-xcb1                                   2:1.4.99.1-0ubuntu2                     Xlib/XCB interface library
ii  libx264-120                                   2:0.120.2151+gita3f4407-2               x264 video coding library
ii  libx86-1                                      1.1+ds1-7ubuntu1                        x86 real-mode library
ii  libxapian22                                   1.2.8-1                                 Search engine library
ii  libxatracker1                                 8.0.4-0ubuntu0.2                        X acceleration library -- runtime
ii  libxau6                                       1:1.0.6-4                               X11 authorisation library
ii  libxaw7                                       2:1.0.9-3ubuntu1                        X11 Athena Widget library
ii  libxcb-composite0                             1.8.1-1ubuntu0.1                        X C Binding, composite extension
ii  libxcb-dri2-0                                 1.8.1-1ubuntu0.1                        X C Binding, dri2 extension
ii  libxcb-glx0                                   1.8.1-1ubuntu0.1                        X C Binding, glx extension
ii  libxcb-keysyms1                               0.3.8-1build1                           utility libraries for X C Binding -- keysyms
ii  libxcb-randr0                                 1.8.1-1ubuntu0.1                        X C Binding, randr extension
ii  libxcb-render0                                1.8.1-1ubuntu0.1                        X C Binding, render extension
ii  libxcb-shape0                                 1.8.1-1ubuntu0.1                        X C Binding, shape extension
ii  libxcb-shm0                                   1.8.1-1ubuntu0.1                        X C Binding, shm extension
ii  libxcb-util0                                  0.3.8-2                                 utility libraries for X C Binding -- atom, aux and event
ii  libxcb-xv0                                    1.8.1-1ubuntu0.1                        X C Binding, xv extension
ii  libxcb1                                       1.8.1-1ubuntu0.1                        X C Binding
ii  libxcomposite1                                1:0.4.3-2build1                         X11 Composite extension library
ii  libxcursor1                                   1:1.1.12-1                              X cursor management library
ii  libxdamage1                                   1:1.1.3-2build1                         X11 damaged region extension library
ii  libxdmcp6                                     1:1.1.0-4                               X11 Display Manager Control Protocol library
ii  libxerces2-java                               2.11.0-4                                Validating XML parser for Java with DOM level 3 support
ii  libxext6                                      2:1.3.0-3build1                         X11 miscellaneous extension library
ii  libxfce4ui-1-0                                4.8.1-1                                 widget library for Xfce
ii  libxfce4util-bin                              4.8.2-1                                 tools for libxfce4util
ii  libxfce4util-common                           4.8.2-1                                 common files for libxfce4util
ii  libxfce4util4                                 4.8.2-1                                 Utility functions library for Xfce4
ii  libxfcegui4-4                                 4.8.1-5ubuntu1                          Basic GUI C functions for Xfce4
ii  libxfconf-0-2                                 4.8.1-1                                 Client library for Xfce4 configure interface
ii  libxfixes3                                    1:5.0-4ubuntu4                          X11 miscellaneous 'fixes' extension library
ii  libxfont1                                     1:1.4.4-1                               X11 font rasterisation library
ii  libxft2                                       2.2.0-3ubuntu2                          FreeType-based font drawing library for X
ii  libxi6                                        2:1.6.0-0ubuntu2                        X11 Input extension library
ii  libxinerama1                                  2:1.1.1-3build1                         X11 Xinerama extension library
ii  libxkbfile1                                   1:1.0.7-1ubuntu0.1                      X11 keyboard file manipulation library
ii  libxklavier16                                 5.2.1-1ubuntu1                          X Keyboard Extension high-level API
ii  libxml-commons-external-java                  1.4.01-2                                XML Commons external code - DOM, SAX, and JAXP, etc
ii  libxml-commons-resolver1.1-java               1.2-7                                   XML entity and URI resolver library
ii  libxml-parser-perl                            2.41-1build1                            Perl module for parsing XML files
ii  libxml-twig-perl                              1:3.39-1ubuntu1                         Perl module for processing huge XML documents in tree mode
ii  libxml-xpath-perl                             1.13-7                                  Perl module for processing XPath
ii  libxml2                                       2.7.8.dfsg-5.1ubuntu4.3                 GNOME XML library
ii  libxml2-utils                                 2.7.8.dfsg-5.1ubuntu4.3                 XML utilities
ii  libxmmsclient6                                0.8+dfsg-2                              XMMS2 - client library
ii  libxmu6                                       2:1.1.0-3                               X11 miscellaneous utility library
ii  libxmuu1                                      2:1.1.0-3                               X11 miscellaneous micro-utility library
ii  libxp6                                        1:1.0.1-2                               X Printing Extension (Xprint) client library
ii  libxpm4                                       1:3.5.9-4                               X11 pixmap library
ii  libxrandr2                                    2:1.3.2-2                               X11 RandR extension library
ii  libxrender1                                   1:0.9.6-2build1                         X Rendering Extension client library
ii  libxres1                                      2:1.0.5-1                               X11 Resource extension library
ii  libxslt1.1                                    1.1.26-8ubuntu1.2                       XSLT 1.0 processing library - runtime library
ii  libxss1                                       1:1.2.1-2                               X11 Screen Saver extension library
ii  libxt6                                        1:1.1.1-2build1                         X11 toolkit intrinsics library
ii  libxtst6                                      2:1.2.0-4                               X11 Testing -- Record extension library
ii  libxv1                                        2:1.0.6-2build1                         X11 Video extension library
ii  libxvidcore4                                  2:1.3.2-6                               Open source MPEG-4 video codec (library)
ii  libxvmc1                                      2:1.0.6-1ubuntu2                        X11 Video extension library
ii  libxxf86dga1                                  2:1.1.2-1                               X11 Direct Graphics Access extension library
ii  libxxf86vm1                                   1:1.1.1-2build1                         X11 XFree86 video mode extension library
ii  libyajl1                                      1.0.12-2                                Yet Another JSON Library
ii  libyaml-tiny-perl                             1.50-1                                  Perl module for reading and writing YAML files
ii  libyelp0                                      3.4.1-0ubuntu1                          Library for the GNOME help browser
ii  libzbar0                                      0.10+doc-7build2                        bar code scanner and decoder (library)
ii  libzeitgeist-1.0-1                            0.3.18-1ubuntu1                         library to access Zeitgeist - shared library
ii  libzephyr4                                    3.0.1-1                                 Project Athena's notification service - non-Kerberos libraries
ii  libzvbi-common                                0.2.33-4                                Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0                                      0.2.33-4                                Vertical Blanking Interval decoder (VBI) - runtime files
ii  lightdm                                       1.2.1-0ubuntu1.1                        Display Manager
ii  lightdm-gtk-greeter                           1.1.5-0ubuntu1.1                        LightDM GTK+ Greeter
ii  lightdm-kde-greeter                           0.1.1-0ubuntu0.1                        LightDM KDE greeter
ii  link-grammar-dictionaries-en                  4.7.4-2                                 Carnegie Mellon University's link grammar parser (English dictionary)
ii  linux-firmware                                1.79.1                                  Firmware for Linux kernel drivers
ii  linux-generic                                 3.2.0.35.40                             Complete Generic Linux kernel
ii  linux-headers-3.2.0-35                        3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic                3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                         3.2.0.35.40                             Generic Linux kernel headers
ii  linux-image-3.2.0-29-generic                  3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic                  3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic                  3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic                  3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                           3.2.0.35.40                             Generic Linux kernel image
ii  linux-libc-dev                                3.2.0-35.55                             Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu1                    base package for ALSA and OSS sound systems
ii  locales                                       2.13+git20120306-3                      common files for locale support
ii  lockfile-progs                                0.1.16                                  Programs for locking and unlocking files and mailboxes
ii  login                                         1:4.1.4.2+svn3283-3ubuntu5.1            system login tools
ii  logrotate                                     3.7.8-6ubuntu5                          Log rotation utility
ii  lp-solve                                      5.5.0.13-7                              Solve (mixed integer) linear programming problems
ii  lsb-base                                      4.0-0ubuntu20.2                         Linux Standard Base 4.0 init script functionality
ii  lsb-release                                   4.0-0ubuntu20.2                         Linux Standard Base version reporting utility
ii  lshw                                          02.15-2                                 information about hardware configuration
ii  lsof                                          4.81.dfsg.1-1build1                     List open files
ii  ltrace                                        0.5.3-2.1ubuntu2                        Tracks runtime library calls in dynamically linked programs
ii  lynx-cur                                      2.8.8dev.9-2ubuntu0.12.04.1             Text-mode WWW Browser with NLS support (development version)
ii  m4                                            1.4.16-2ubuntu1                         a macro processing language
rc  mahjongg                                      1:3.4.1-0ubuntu2.1                      classic Eastern tile game for GNOME
ii  make                                          3.81-8.1ubuntu1.1                       An utility for Directing compilation.
ii  makedev                                       2.3.1-89ubuntu2                         creates device files in /dev
ii  man-db                                        2.6.1-2ubuntu1                          on-line manual pager
ii  manpages                                      3.35-0.1ubuntu1                         Manual pages about using a GNU/Linux system
ii  manpages-dev                                  3.35-0.1ubuntu1                         Manual pages about using GNU/Linux for development
ii  marble                                        4:4.8.5-0ubuntu0.1                      globe and map widget
ii  marble-data                                   4:4.8.5-0ubuntu0.1                      data files for Marble
ii  marble-plugins                                4:4.8.5-0ubuntu0.1                      plugins for Marble
ii  mawk                                          1.3.3-17                                a pattern scanning and text processing language
ii  media-player-info                             16-1                                    Media player identification files
ii  melt                                          0.7.6+git20120204-2                     command line media player and video editor
ii  memtest86+                                    4.20-1.1ubuntu1                         thorough real-mode memory tester
ii  mencoder                                      2:1.0~rc4.dfsg1+svn34540-1              MPlayer's Movie Encoder
ii  mime-support                                  3.51-1ubuntu1                           MIME files 'mime.types' & 'mailcap', and support programs
ii  miscfiles                                     1.4.2.dfsg.1-9                          Dictionaries and other interesting files
ii  mlocate                                       0.23.1-1ubuntu2                         quickly find files on the filesystem based on their name
ii  mobile-broadband-provider-info                20120410-0ubuntu1                       database of mobile broadband service providers
ii  modemmanager                                  0.5.2.0-0ubuntu2                        D-Bus service for managing modems
ii  module-init-tools                             3.16-1ubuntu2                           tools for managing Linux kernel modules
ii  mono-4.0-gac                                  2.10.8.1-1ubuntu2.2                     Mono GAC tool (for CLI 4.0)
ii  mono-gac                                      2.10.8.1-1ubuntu2.2                     Mono GAC tool
ii  mono-runtime                                  2.10.8.1-1ubuntu2.2                     Mono runtime
ii  mount                                         2.20.1-1ubuntu3                         Tools for mounting and manipulating filesystems
ii  mountall                                      2.36.3                                  filesystem mounting tool
ii  mpg321                                        0.2.13-4ubuntu1                         Simple and lightweight command line MP3 player
ii  mplayer                                       2:1.0~rc4.dfsg1+svn34540-1              movie player for Unix-like systems
ii  mscompress                                    0.3-3.1                                 Microsoft "compress.exe/expand.exe" compatible (de)compressor
ii  mtools                                        4.0.12-1                                Tools for manipulating MSDOS files
ii  mtr-tiny                                      0.80-1ubuntu1                           Full screen ncurses traceroute tool
ii  multiarch-support                             2.15-0ubuntu10.3                        Transitional package to ensure multiarch compatibility
ii  mysql-common                                  5.5.28-0ubuntu0.12.04.3                 MySQL database common files, e.g. /etc/mysql/my.cnf
ii  nano                                          2.2.6-1                                 small, friendly text editor inspired by Pico
ii  nautilus                                      1:3.4.2-0ubuntu6                        file manager and graphical shell for GNOME
ii  nautilus-data                                 1:3.4.2-0ubuntu6                        data files for nautilus
ii  nautilus-sendto                               3.0.1-2ubuntu2                          integrates Evolution and Pidgin into the Nautilus file manager
ii  ncurses-base                                  5.9-4                                   basic terminal type definitions
ii  ncurses-bin                                   5.9-4                                   terminal-related programs and man pages
ii  net-tools                                     1.60-24.1ubuntu2                        The NET-3 networking toolkit
ii  netbase                                       4.47ubuntu1                             Basic TCP/IP networking system
ii  netcat-openbsd                                1.89-4ubuntu1                           TCP/IP swiss army knife
ii  netpbm                                        2:10.0-15                               Graphics conversion tools between image formats
ii  network-manager                               0.9.4.0-0ubuntu4.1                      network management framework (daemon and userspace tools)
ii  network-manager-gnome                         0.9.4.1-0ubuntu2                        network management framework (GNOME frontend)
ii  network-manager-pptp                          0.9.4.0-0ubuntu1                        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                    0.9.4.0-0ubuntu1                        network management framework (PPTP plugin GNOME GUI)
ii  ntfs-3g                                       1:2012.1.15AR.1-1ubuntu1.2              read/write NTFS driver for FUSE
ii  ntpdate                                       1:4.2.6.p3+dfsg-1ubuntu3.1              client for setting system time from NTP servers
ii  ntrack-module-libnl-0                         016-1ubuntu1                            libnl based ntrack module
ii  numlockx                                      1.2-2                                   enable NumLock in X11 sessions
ii  nvidia-common                                 1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  obex-data-server                              0.4.6-0ubuntu1                          D-Bus service for OBEX client and server side functionality
ii  odbcinst                                      2.2.14p2-5ubuntu3                       Helper program for accessing odbc ini files
ii  odbcinst1debian2                              2.2.14p2-5ubuntu3                       Support library for accessing odbc ini files
rc  onboard                                       0.97.0-0ubuntu4                         Simple On-screen Keyboard
ii  oneconf                                       0.2.8.1                                 synchronize your configuration data over the network
ii  openjdk-6-jre                                 6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                        6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                             6b24-1.11.5-0ubuntu1~12.04.1            OpenJDK Java runtime (architecture independent libraries)
ii  openprinting-ppds                             20120322-0ubuntu1                       OpenPrinting printer support - PostScript PPD files
ii  openshot                                      1.4.0-1ubuntu1                          Create and edit videos and movies
ii  openshot-doc                                  1.4.0-1ubuntu1                          Help manual for OpenShot Video Editor
ii  openssh-client                                1:5.9p1-5ubuntu1                        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                                1:5.9p1-5ubuntu1                        secure shell (SSH) server, for secure access from remote machines
ii  openssl                                       1.0.1-4ubuntu5.5                        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  os-prober                                     1.51ubuntu3                             utility to detect other OSes on a set of drives
ii  oxygen-icon-theme                             4:4.8.3-0ubuntu0.1                      Oxygen icon theme
ii  p7zip-full                                    9.20.1~dfsg.1-4                         7z and 7za file archivers with high compression ratio
ii  parley                                        4:4.8.5-0ubuntu0.1                      vocabulary trainer for KDE
ii  parley-data                                   4:4.8.5-0ubuntu0.1                      data files for the Parley vocabulary trainer
ii  parted                                        2.3-8ubuntu5.1                          disk partition manipulator
ii  passwd                                        1:4.1.4.2+svn3283-3ubuntu5.1            change and administer password and group data
ii  pastebinit                                    1.3-2ubuntu2.1                          command-line pastebin client
ii  patch                                         2.6.1-3                                 Apply a diff file to an original
ii  pavucontrol                                   0.99.2-1build1                          PulseAudio Volume Control
ii  pbis-open                                     7.0.1.918                               Authentication services for Active Directory domains
ii  pbis-open-gui                                 7.0.1.918                               Desktop utility for joining Active Directory domains
ii  pbis-open-legacy                              7.0.1.918                               Provides symbolic links from the older command names and paths in Likewise Open to the new names and paths in PowerBroker Identity Services Open.
ii  pciutils                                      1:3.1.8-2ubuntu5                        Linux PCI Utilities
ii  pcmciautils                                   018-6                                   PCMCIA utilities for Linux 2.6
ii  perl                                          5.14.2-6ubuntu2.2                       Larry Wall's Practical Extraction and Report Language
ii  perl-base                                     5.14.2-6ubuntu2.2                       minimal Perl system
ii  perl-modules                                  5.14.2-6ubuntu2.2                       Core Perl modules
ii  perlmagick                                    8:6.6.9.7-5ubuntu3.2                    Perl interface to the ImageMagick graphics routines
ii  phonon                                        4:4.7.0really4.6.0-0ubuntu1             multimedia framework from KDE - metapackage
ii  phonon-backend-gstreamer                      4:4.7.0really4.6.2-0ubuntu0.1           Phonon GStreamer 0.10.x backend
rc  pidgin                                        1:2.10.3-0ubuntu1.1                     graphical multi-protocol instant messaging client for X
ii  pidgin-data                                   1:2.10.3-0ubuntu1.1                     multi-protocol instant messaging client - data files
ii  pidgin-microblog                              0.3.0-3                                 Microblogging plugins for Pidgin
ii  pitivi                                        0.15.2-0ubuntu0.1                       non-linear audio/video editor using GStreamer
ii  pkg-config                                    0.26-1ubuntu1                           manage compile and link flags for libraries
ii  plasma-scriptengine-javascript                4:4.8.5-0ubuntu0.1                      JavaScript script engine for Plasma
ii  plymouth                                      0.8.2-2ubuntu30                         graphical boot animation and logger - main package
ii  plymouth-label                                0.8.2-2ubuntu30                         graphical boot animation and logger - label control
ii  plymouth-theme-ubuntu-text                    0.8.2-2ubuntu30                         graphical boot animation and logger - ubuntu-logo theme
ii  plymouth-theme-xubuntu-logo                   12.04.11                                graphical boot animation and logger - xubuntu-logo theme
ii  plymouth-theme-xubuntu-text                   12.04.11                                graphical boot animation and logger - xubuntu-text theme
ii  pm-utils                                      1.4.1-9                                 utilities and scripts for power management
ii  policykit-1                                   0.104-1ubuntu1                          framework for managing administrative policies and privileges
ii  policykit-1-gnome                             0.105-1ubuntu3.1                        GNOME authentication agent for PolicyKit-1
ii  policykit-desktop-privileges                  0.10                                    run common desktop actions without password
ii  poppler-data                                  0.4.5-2                                 Encoding data for the poppler PDF rendering library
ii  poppler-utils                                 0.18.4-1ubuntu3                         PDF utilities (based on Poppler)
ii  popularity-contest                            1.53ubuntu1                             Vote for your favourite packages automatically
ii  powermgmt-base                                1.31                                    Common utils and configs for power management
ii  ppp                                           2.4.5-5ubuntu1                          Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                                     2.3.18+nmu3ubuntu1                      A text menu based utility for configuring ppp
ii  pppoeconf                                     1.20ubuntu1                             configures PPPoE/ADSL connections
ii  pptp-linux                                    1.7.2-6                                 Point-to-Point Tunneling Protocol (PPTP) Client
ii  printer-driver-c2esp                          23-1                                    printer driver for Kodak ESP AiO color inkjet Series
ii  printer-driver-foo2zjs                        20111202dfsg0-1ubuntu1                  printer driver for ZjStream-based printers
ii  printer-driver-gutenprint                     5.2.8~pre1-0ubuntu2.1                   printer drivers for CUPS
ii  printer-driver-hpcups                         3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  printer-driver-hpijs                          3.12.2-1ubuntu3.1                       HP Linux Printing and Imaging - gs IJS driver (hpijs)
ii  printer-driver-min12xxw                       0.0.9-6ubuntu1                          printer driver for KonicaMinolta PagePro 1[234]xxW
ii  printer-driver-pnm2ppa                        1.13+nondbs-0ubuntu1                    printer driver for HP-GDI printers
ii  printer-driver-postscript-hp                  3.12.2-1ubuntu3.1                       HP Printers PostScript Descriptions
ii  printer-driver-ptouch                         1.3-3ubuntu0.1                          printer driver Brother P-touch label printers
ii  printer-driver-pxljr                          1.3+repack0-2                           printer driver for HP Color LaserJet 35xx/36xx
ii  printer-driver-sag-gdi                        0.1-3                                   printer driver for Ricoh Aficio SP 1000s/SP 1100s
ii  printer-driver-splix                          2.0.0+svn300-1.1ubuntu2                 Driver for Samsung and Xerox SPL2 and SPLc laser printers
ii  procps                                        1:3.2.8-11ubuntu6                       /proc file system utilities
ii  psmisc                                        22.15-2ubuntu1.1                        utilities that use the proc file system
ii  pulseaudio                                    1:1.1-0ubuntu15.1                       PulseAudio sound server
ii  pulseaudio-module-x11                         1:1.1-0ubuntu15.1                       X11 module for PulseAudio sound server
ii  pulseaudio-utils                              1:1.1-0ubuntu15.1                       Command line tools for the PulseAudio sound server
iU  puppet                                        3.0.2-1puppetlabs1                      Centralized configuration management - agent startup and compatibility scripts
ii  puppet-common                                 3.0.2-1puppetlabs1                      Centralized configuration management
ii  python                                        2.7.3-0ubuntu2                          interactive high-level object-oriented language (default version)
ii  python-appindicator                           0.4.92-0ubuntu1                         Python bindings for libappindicator
ii  python-apport                                 2.0.1-0ubuntu15.1                       apport crash report handling library
ii  python-apt                                    0.8.3ubuntu7                            Python interface to libapt-pkg
ii  python-apt-common                             0.8.3ubuntu7                            Python interface to libapt-pkg (locales)
ii  python-aptdaemon                              0.43+bzr805-0ubuntu7                    Python module for the server and client of aptdaemon
ii  python-aptdaemon.gtk3widgets                  0.43+bzr805-0ubuntu7                    Python GTK+ 3 widgets to run an aptdaemon client
ii  python-avogadro                               1.0.3-1ubuntu4                          Molecular Graphics and Modelling System (Python module)
ii  python-cairo                                  1.8.8-1ubuntu3                          Python bindings for the Cairo vector graphics library
ii  python-chardet                                2.0.1-2build1                           universal character encoding detector
ii  python-configobj                              4.7.2+ds-3build1                        simple but powerful config file reader and writer for Python
ii  python-crypto                                 2.4.1-1ubuntu0.1                        cryptographic algorithms and protocols for Python
ii  python-cups                                   1.9.61-0ubuntu2                         Python bindings for CUPS
ii  python-cupshelpers                            1.3.8+20120201-0ubuntu8.1               Python modules for printer configuration with CUPS
ii  python-dbus                                   1.0.0-1ubuntu1                          simple interprocess messaging system (Python interface)
ii  python-dbus-dev                               1.0.0-1ubuntu1                          main loop integration development files for python-dbus
ii  python-debian                                 0.1.21ubuntu1                           Python modules to work with Debian-related data formats
ii  python-debtagshw                              1.9+git20120320-0ubuntu1                Match debtags hardware:: tags against the actual hardware
ii  python-defer                                  1.0.2+bzr481-1                          Small framework for asynchronous programming
ii  python-gconf                                  2.28.1+dfsg-1                           Python bindings for the GConf configuration database system
ii  python-gdbm                                   2.7.3-1ubuntu1                          GNU dbm database support for Python
ii  python-gi                                     3.2.2-1~precise                         Python 2.x bindings for gobject-introspection libraries
ii  python-gi-cairo                               3.2.2-1~precise                         Python Cairo bindings for the GObject library
ii  python-glade2                                 2.24.0-3                                GTK+ bindings: Glade support
ii  python-gmenu                                  3.0.1-0ubuntu7                          GNOME implementation of the freedesktop menu specification
ii  python-gnomekeyring                           2.32.0+dfsg-1                           Python bindings for the GNOME keyring library
ii  python-gnupginterface                         0.3.2-9.1ubuntu3                        Python interface to GnuPG (GPG)
ii  python-gobject                                3.2.2-1~precise                         Python 2.x bindings for GObject - transitional package
ii  python-gobject-2                              2.28.6-10ubuntu1                        deprecated static Python bindings for the GObject library
ii  python-gst0.10                                0.10.22-3ubuntu0.1                      generic media-playing framework (Python bindings)
ii  python-gtk2                                   2.24.0-3                                Python bindings for the GTK+ widget set
ii  python-httplib2                               0.7.2-1ubuntu2                          comprehensive HTTP client library written for Python
ii  python-ibus                                   1.4.1-3ubuntu1                          Intelligent Input Bus - Python support
ii  python-imaging                                1.1.7-4                                 Python Imaging Library
ii  python-keyring                                0.9.2-0ubuntu0.12.04.2                  store and access your passwords safely
ii  python-launchpad-integration                  0.1.56.1                                library for launchpad integration
ii  python-launchpadlib                           1.9.12-1                                Launchpad web services client library
ii  python-lazr.restfulclient                     0.12.0-1ubuntu1                         client for lazr.restful-based web services
ii  python-lazr.uri                               1.0.3-1                                 library for parsing, manipulating, and generating URIs
ii  python-libxml2                                2.7.8.dfsg-5.1ubuntu4.3                 Python bindings for the GNOME XML library
ii  python-lxml                                   2.3.2-1                                 pythonic binding for the libxml2 and libxslt libraries
ii  python-mako                                   0.5.0-1                                 fast and lightweight templating for the Python platform
ii  python-markupsafe                             0.15-1                                  XML/HTML/XHTML Markup safe string for Python
ii  python-minimal                                2.7.3-0ubuntu2                          minimal subset of the Python language (default version)
ii  python-mlt3                                   0.7.6+git20120204-2                     multimedia framework (python bindings)
ii  python-notify                                 0.1.1-3                                 Python bindings for libnotify
ii  python-numpy                                  1:1.6.1-6ubuntu1                        Numerical Python adds a fast array facility to the Python language
ii  python-oauth                                  1.0.1-3build1                           Python library implementing of the OAuth protocol
ii  python-openssl                                0.12-1ubuntu2                           Python wrapper around the OpenSSL library
ii  python-pam                                    0.4.2-12.2ubuntu4                       A Python interface to the PAM library
ii  python-pexpect                                2.3-1ubuntu2                            Python module for automating interactive applications
ii  python-piston-mini-client                     0.7.2+bzr57-0ubuntu1                    library for writing clients for Django's Piston REST APIs
ii  python-pkg-resources                          0.6.24-1ubuntu1                         Package Discovery and Resource Access using pkg_resources
ii  python-problem-report                         2.0.1-0ubuntu15.1                       Python library to handle problem reports
ii  python-pycurl                                 7.19.0-4ubuntu3                         Python bindings to libcurl
ii  python-pygoocanvas                            0.14.1-1ubuntu6                         GooCanvas Python bindings
ii  python-qt4                                    4.9.1-2ubuntu1                          Python bindings for Qt4
ii  python-renderpm                               2.5-1.1build1                           python low level render interface
ii  python-reportlab                              2.5-1.1build1                           ReportLab library to create PDF documents using Python
ii  python-reportlab-accel                        2.5-1.1build1                           C coded extension accelerator for the ReportLab Toolkit
ii  python-serial                                 2.5-2.1build1                           pyserial - module encapsulating access for the serial port
ii  python-simplejson                             2.3.2-1                                 simple, fast, extensible JSON encoder/decoder for Python
ii  python-sip                                    4.13.2-1                                Python/C++ bindings generator runtime library
ii  python-smbc                                   1.0.13-0ubuntu1                         Python bindings for Samba clients (libsmbclient)
ii  python-software-properties                    0.82.7.3                                manage the repositories that you install software from
ii  python-support                                1.0.14ubuntu2                           automated rebuilding support for Python modules
ii  python-tk                                     2.7.3-1ubuntu1                          Tkinter - Writing Tk applications with Python
ii  python-twisted-bin                            11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-core                           11.1.0-1ubuntu2                         Event-based framework for internet applications
ii  python-twisted-web                            11.1.0-1                                HTTP protocol implementation together with clients and servers
ii  python-ubuntu-sso-client                      3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - Python library
ii  python-uniconvertor                           1.1.4-1ubuntu1                          Universal vector graphics translator
ii  python-uno                                    1:3.5.4-0ubuntu1.1                      Python-UNO bridge
ii  python-virtkey                                0.60.0-0ubuntu5                         Library to emulate keyboard keypresses.
ii  python-wadllib                                1.3.0-2                                 Python library for navigating WADL files
ii  python-xapian                                 1.2.8-1                                 Xapian search engine interface for Python
ii  python-xdg                                    0.19-3ubuntu2                           Python library to access freedesktop.org standards
ii  python-xkit                                   0.4.2.3build1                           library for the manipulation of the xorg.conf
ii  python-zeitgeist                              0.9.0-1ubuntu1                          event logging framework - Python bindings
ii  python-zope.interface                         3.6.1-1ubuntu3                          Interfaces for Python
ii  python2.7                                     2.7.3-0ubuntu3.1                        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                             2.7.3-0ubuntu3.1                        Minimal subset of the Python language (version 2.7)
ii  python3.2                                     3.2.3-0ubuntu3.2                        Interactive high-level object-oriented language (version 3.2)
ii  python3.2-minimal                             3.2.3-0ubuntu3.2                        Minimal subset of the Python language (version 3.2)
ii  qapt-batch                                    1.3.1-0ubuntu2                          Batch package manager for KDE
ii  qdbus                                         4:4.8.1-0ubuntu4.3                      Qt 4 D-Bus tool
ii  radeontool                                    1.6.2-1.1                               utility to control ATI Radeon backlight functions on laptops
ii  rarian-compat                                 0.8.1-5                                 Documentation meta-data library (compatibility tools)
ii  readline-common                               6.2-8                                   GNU readline and history libraries, common files
ii  resolvconf                                    1.63ubuntu16                            name server information handler
ii  rfkill                                        0.4-1ubuntu2                            tool for enabling and disabling wireless devices
ii  rhythmbox                                     2.96-0ubuntu4.2                         music player and organizer for GNOME
ii  rhythmbox-data                                2.96-0ubuntu4.2                         data files for rhythmbox
ii  rhythmbox-mozilla                             2.96-0ubuntu4.2                         Rhythmbox Mozilla plugin
ii  rhythmbox-plugin-cdrecorder                   2.96-0ubuntu4.2                         burning plugin for rhythmbox music player
ii  rhythmbox-plugin-zeitgeist                    2.96-0ubuntu4.2                         zeitgeist plugin for rhythmbox music player
ii  rhythmbox-plugins                             2.96-0ubuntu4.2                         plugins for rhythmbox music player
ii  ristretto                                     0.3.6-0ubuntu1                          lightweight picture-viewer for the Xfce desktop environment
ii  rsync                                         3.0.9-1ubuntu1                          fast, versatile, remote (and local) file-copying tool
ii  rsyslog                                       5.8.6-1ubuntu8                          reliable system and kernel logging daemon
ii  rtkit                                         0.10-2                                  Realtime Policy and Watchdog Daemon
ii  ruby                                          4.8                                     Transitional package for ruby1.8
ii  ruby-json                                     1.6.3-1                                 JSON library for Ruby
ii  ruby1.8                                       1.8.7.352-2ubuntu1.1                    Interpreter of object-oriented scripting language Ruby 1.8
ii  samba-common                                  2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  samba-common-bin                              2:3.6.3-2ubuntu2.3                      common files used by both the Samba server and client
ii  sane-utils                                    1.0.22-7ubuntu1                         API library for scanners -- utilities
ii  screensaver-default-images                    0.2-1                                   Wallpapers for image processing screensavers
ii  scribus                                       1.4.0.dfsg+r17300-1ubuntu1              Open Source Desktop Page Layout - stable branch
ii  sed                                           4.2.1-9                                 The GNU sed stream editor
ii  sensible-utils                                0.0.6ubuntu2                            Utilities for sensible alternative selection
ii  sessioninstaller                              0.20+bzr128-0ubuntu1.2                  APT based installer using PackageKit's session DBus API
ii  sgml-base                                     1.26+nmu1ubuntu1                        SGML infrastructure and SGML catalog file support
ii  sgml-data                                     2.0.6                                   common SGML and XML data
ii  shared-desktop-ontologies                     0.8.1-1                                 shared ontologies for semantic searching
ii  shared-mime-info                              1.0-0ubuntu4.1                          FreeDesktop.org shared MIME database and spec
ii  shimmer-themes                                1.3.0-0ubuntu1                          Gtk+ themes from Shimmer Project
ii  simple-scan                                   3.4.1-0ubuntu1.1                        Simple Scanning Utility
ii  smbclient                                     2:3.6.3-2ubuntu2.3                      command-line SMB/CIFS clients for Unix
ii  software-center                               5.2.7                                   Utility for browsing, installing, and removing software
ii  software-center-aptdaemon-plugins             0.1.2                                   The aptdaemon plugins for software-center
ii  software-properties-common                    0.82.7.3                                manage the repositories that you install software from (common)
ii  software-properties-gtk                       0.82.7.3                                manage the repositories that you install software from (gtk)
ii  soprano-daemon                                2.7.5+dfsg.1-0ubuntu1                   daemon for the Soprano RDF framework
ii  sound-theme-freedesktop                       0.7.pristine-2                          freedesktop.org sound theme
ii  speech-dispatcher                             0.7.1-6ubuntu3                          Common interface to speech synthesizers
ii  ssh-import-id                                 2.10-0ubuntu1                           securely retrieve an SSH public key and install it locally
ii  ssl-cert                                      1.0.28ubuntu0.1                         simple debconf wrapper for OpenSSL
ii  step                                          4:4.8.5-0ubuntu0.1                      interactive physical simulator for KDE
ii  strace                                        4.5.20-2.3ubuntu1                       A system call tracer
ii  sudo                                          1.8.3p1-1ubuntu3.3                      Provide limited super user privileges to specific users
ii  synaptic                                      0.75.9ubuntu1                           Graphical package manager
ii  syslinux                                      2:4.05+dfsg-2                           collection of boot loaders
ii  syslinux-common                               2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies
ii  system-config-printer-common                  1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-gnome                   1.3.8+20120201-0ubuntu8.1               Printer configuration GUI
ii  system-config-printer-udev                    1.3.8+20120201-0ubuntu8.1               Printer auto-configuration facility based on udev
ii  system-tools-backends                         2.10.2-1ubuntu1                         System Tools to manage computer configuration -- scripts
ii  sysv-rc                                       2.88dsf-13.10ubuntu11.1                 System-V-like runlevel change mechanism
ii  sysvinit-utils                                2.88dsf-13.10ubuntu11.1                 System-V-like utilities
ii  tar                                           1.26-4ubuntu1                           GNU version of the tar archiving utility
ii  tcl8.5                                        8.5.11-1ubuntu1                         Tcl (the Tool Command Language) v8.5 - run-time files
ii  tcpd                                          7.6.q-21                                Wietse Venema's TCP wrapper utilities
ii  tcpdump                                       4.2.1-1ubuntu2                          command-line network traffic analyzer
ii  telnet                                        0.17-36build1                           The telnet client
ii  thunar                                        1.2.3-3ubuntu2                          File Manager for Xfce
ii  thunar-archive-plugin                         0.3.0-4                                 Archive plugin for Thunar file manager
ii  thunar-data                                   1.2.3-3ubuntu2                          Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                      0.2.0-1                                 Media tags plugin for Thunar file manager
ii  thunar-volman                                 0.6.1-0ubuntu1                          Thunar extension for volumes management
rc  thunderbird                                   16.0.2+build1-0ubuntu0.12.04.1          Email, RSS and newsgroup client with integrated spam filter
ii  tilem                                         0.973-1                                 TilEm, a TI 83+ emulator
ii  time                                          1.7-23.1                                The GNU time program for measuring cpu resource usage
ii  tk8.5                                         8.5.11-1                                Tk toolkit for Tcl and X11, v8.5 - run-time files
ii  toshset                                       1.76-2                                  Access much of the Toshiba laptop hardware interface
rc  transmission-gtk                              2.51-0ubuntu1                           lightweight BitTorrent client (GTK interface)
ii  tree                                          1.5.3-2                                 displays directory tree, in color
ii  tsconf                                        1.0-10                                  touch screen library common files
ii  ttf-dejavu                                    2.33-2ubuntu1                           Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra
ii  ttf-dejavu-core                               2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-dejavu-extra                              2.33-2ubuntu1                           Vera font family derivate with additional characters
ii  ttf-droid                                     20101110+git-2                          transitional dummy package
ii  ttf-freefont                                  20100919-1                              Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                          1:0.5.11ubuntu1                         Core collection of free fonts for languages of India
ii  ttf-lyx                                       2.0.2-1ubuntu2                          TrueType versions of some TeX fonts
ii  ttf-mscorefonts-installer                     3.4ubuntu3                              Installer for Microsoft TrueType core fonts
ii  ttf-punjabi-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Punjabi language
ii  ttf-sil-gentium-basic                         1.1-5                                   transitional dummy package
ii  ttf-ubuntu-font-family                        0.80-0ubuntu2                           Ubuntu Font Family, sans-serif typeface hinted for clarity
ii  ttf-umefont                                   434-1                                   transitional dummy package
ii  ttf-unfonts-core                              1.0.3.is.1.0.2-080608-5ubuntu1          transitional dummy package
ii  ttf-wqy-microhei                              0.2.0-beta-1ubuntu1                     A droid derived Sans-Seri style CJK font
ii  tumbler                                       0.1.24-0ubuntu1                         D-Bus thumbnailing service
ii  tumbler-common                                0.1.24-0ubuntu1                         D-Bus thumbnailing service (common files)
ii  tzdata                                        2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data
ii  tzdata-java                                   2012e-0ubuntu0.12.04.1                  time zone and daylight-saving time data for use by java runtimes
ii  ubuntu-extras-keyring                         2010.09.27                              GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring                                2011.11.21.1                            GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                                1.267                                   Minimal core of Ubuntu
ii  ubuntu-restricted-addons                      12                                      Commonly used restricted packages for Ubuntu
ii  ubuntu-sso-client                             3.0.2-0ubuntu3                          Ubuntu Single Sign-On client
ii  ubuntu-sso-client-gtk                         3.0.2-0ubuntu3                          Ubuntu Single Sign-On client - GTK+ frontend
ii  ubuntu-standard                               1.267                                   The Ubuntu standard system
ii  ucf                                           3.0025+nmu2ubuntu1                      Update Configuration File: preserve user changes to config files.
ii  udev                                          175-0ubuntu9.2                          rule-based device node and kernel event manager
ii  udisks                                        1.0.4-5ubuntu2.1                        storage media interface
ii  ufw                                           0.31.1-1                                program for managing a Netfilter firewall
ii  unattended-upgrades                           0.76ubuntu1                             automatic installation of security upgrades
ii  unixodbc                                      2.2.14p2-5ubuntu3                       Basic ODBC tools
ii  uno-libs3                                     3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment -- public shared libraries
ii  unrar                                         1:4.0.3-1                               Unarchiver for .rar files (non-free version)
ii  unzip                                         6.0-4ubuntu1                            De-archiver for .zip files
ii  update-inetd                                  4.41                                    inetd configuration file updater
ii  update-manager                                1:0.156.14.11                           GNOME application that manages apt updates
ii  update-manager-core                           1:0.156.14.11                           manage release upgrades
ii  update-notifier                               0.119ubuntu8.6                          Daemon which notifies about package updates
ii  update-notifier-common                        0.119ubuntu8.6                          Files shared between update-notifier and other packages
ii  upower                                        0.9.15-3git1                            abstraction for power management
ii  upstart                                       1.5-0ubuntu7                            event-based init daemon
ii  ure                                           3.5.4-0ubuntu1.1                        LibreOffice UNO runtime environment
ii  ureadahead                                    0.100.0-12                              Read required files in advance
ii  usb-creator-common                            0.2.38                                  create a startup disk using a CD or disc image (common files)
ii  usb-creator-gtk                               0.2.38                                  create a startup disk using a CD or disc image (for GNOME)
ii  usb-modeswitch                                1.2.3+repack0-1ubuntu2                  mode switching tool for controlling "flip flop" USB devices
ii  usb-modeswitch-data                           20120120-0ubuntu1                       mode switching data for usb-modeswitch
ii  usbmuxd                                       1.0.7-2                                 USB multiplexor daemon for iPhone and iPod Touch devices
ii  usbutils                                      1:005-1                                 Linux USB utilities
ii  util-linux                                    2.20.1-1ubuntu3                         Miscellaneous system utilities
ii  uuid-runtime                                  2.20.1-1ubuntu3                         runtime components for the Universally Unique ID library
ii  vbetool                                       1.1-2ubuntu1                            run real-mode video BIOS code to alter hardware state
ii  vcdimager                                     0.7.23-4.1ubuntu1                       A VideoCD (VCD) image mastering and ripping tool
ii  vim-common                                    2:7.3.429-2ubuntu2.1                    Vi IMproved - Common files
ii  vim-tiny                                      2:7.3.429-2ubuntu2.1                    Vi IMproved - enhanced vi editor - compact version
ii  virtuoso-minimal                              6.1.4+dfsg1-0ubuntu1                    high-performance database - core dependency package
ii  virtuoso-opensource-6.1-bin                   6.1.4+dfsg1-0ubuntu1                    high-performance database - binaries
ii  virtuoso-opensource-6.1-common                6.1.4+dfsg1-0ubuntu1                    high-performance database - common files
ii  vlc                                           2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer
ii  vlc-data                                      2.0.3-0ubuntu0.12.04.1                  Common data for VLC
ii  vlc-nox                                       2.0.3-0ubuntu0.12.04.1                  multimedia player and streamer (without X support)
ii  vlc-plugin-notify                             2.0.3-0ubuntu0.12.04.1                  LibNotify plugin for VLC
ii  vlc-plugin-pulse                              2.0.3-0ubuntu0.12.04.1                  PulseAudio plugin for VLC
ii  vym                                           2.0.3-1                                 mindmapping tool
ii  wamerican                                     7.1-1                                   American English dictionary words for /usr/share/dict
ii  wbritish                                      7.1-1                                   British English dictionary words for /usr/share/dict
ii  wget                                          1.13.4-2ubuntu1                         retrieves files from the web
ii  whiptail                                      0.52.11-2ubuntu10                       Displays user-friendly dialog boxes from shell scripts
rc  winbind                                       2:3.6.3-2ubuntu2.3                      Samba nameservice integration server
ii  wine                                          1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (meta-package)
ii  wine-gecko1.4                                 1.4.0-0ubuntu2                          Microsoft Windows compatibility layer (embedded web browser)
ii  wine1.4                                       1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.4-common                                1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (transitional package)
ii  wine1.4-i386                                  1.4-0ubuntu4.1                          Microsoft Windows Compatibility Layer (32-bit support)
ii  winetricks                                    0.0+20120308                            Microsoft Windows Compatibility Layer (winetricks)
ii  wireless-regdb                                2011.04.28-1ubuntu3                     wireless regulatory database
ii  wireless-tools                                30~pre9-5ubuntu2                        Tools for manipulating Linux Wireless Extensions
ii  wodim                                         9:1.1.11-2ubuntu2                       command line CD/DVD writing tool
ii  wordnet                                       1:3.0-26.1                              electronic lexical database of English language
ii  wordnet-base                                  1:3.0-26.1                              electronic lexical database of English language (base data)
ii  wordnet-sense-index                           1:3.0-26.1                              electronic lexical database of English language (index.sense)
ii  wpasupplicant                                 0.7.3-6ubuntu2.1                        client support for WPA and WPA2 (IEEE 802.11i)
ii  x11-apps                                      7.6+5ubuntu1                            X applications
ii  x11-common                                    1:7.6+12ubuntu1                         X Window System (X.Org) infrastructure
ii  x11-session-utils                             7.6+2                                   X session utilities
ii  x11-utils                                     7.6+4ubuntu0.1                          X11 utilities
ii  x11-xfs-utils                                 7.6+1                                   X font server utilities
ii  x11-xkb-utils                                 7.6+4                                   X11 XKB utilities
ii  x11-xserver-utils                             7.6+3                                   X server utilities
ii  xauth                                         1:1.0.6-1                               X authentication utility
ii  xbitmaps                                      1.1.1-1                                 Base X bitmaps
rc  xchat                                         2.8.8-3ubuntu12                         IRC client for X similar to AmIRC
ii  xchat-common                                  2.8.8-3ubuntu12                         Common files for X-Chat
ii  xcursor-themes                                1.0.3-1                                 Base X cursor themes
ii  xdg-user-dirs                                 0.14-0ubuntu2                           tool to manage well known user directories
ii  xdg-user-dirs-gtk                             0.9-0ubuntu1                            tool to manage well known user directories (Gtk extension)
ii  xdg-utils                                     1.1.0~rc1-2ubuntu6                      desktop integration utilities from freedesktop.org
ii  xfce-keyboard-shortcuts                       4.8.1-1                                 xfce keyboard shortcuts configuration
ii  xfce4-appfinder                               4.8.0-3                                 Application finder for the Xfce4 Desktop Environment
ii  xfce4-cpugraph-plugin                         1.0.1-2                                 CPU load graph plugin for the Xfce4 panel
ii  xfce4-datetime-plugin                         0.6.1-3ubuntu1                          date and time plugin for the Xfce4 panel
ii  xfce4-dict                                    0.6.0-5                                 Dictionary plugin for Xfce4 panel
ii  xfce4-indicator-plugin                        0.4.0-0ubuntu2                          plugin to display information from applications in the Xfce4 panel
ii  xfce4-mailwatch-plugin                        1.1.0-5                                 mail watcher plugin for the Xfce4 panel
ii  xfce4-netload-plugin                          1.1.0-1                                 network load monitor plugin for the Xfce4 panel
ii  xfce4-notes                                   1.7.7-2ubuntu1                          Notes application for the Xfce4 desktop
ii  xfce4-notes-plugin                            1.7.7-2ubuntu1                          Notes plugin for the Xfce4 desktop
ii  xfce4-notifyd                                 0.2.2-1                                 simple, visually-appealing notification daemon for Xfce
ii  xfce4-panel                                   4.8.6-2ubuntu2                          panel for Xfce4 desktop environment
ii  xfce4-places-plugin                           1.2.0-3                                 quick access to folders, documents and removable media
ii  xfce4-power-manager                           1.0.11-0ubuntu2                         power manager for Xfce desktop
ii  xfce4-power-manager-data                      1.0.11-0ubuntu2                         power manager for Xfce desktop, arch-indep files
ii  xfce4-quicklauncher-plugin                    1.9.4-9                                 rapid launcher plugin for the Xfce4 panel
ii  xfce4-screenshooter                           1.8.0-2                                 screenshots utility for Xfce
ii  xfce4-session                                 4.8.3-0ubuntu2                          Xfce4 Session Manager
ii  xfce4-settings                                4.8.3-1ubuntu3                          graphical application for managing Xfce settings
ii  xfce4-systemload-plugin                       1:1.0.0-1ubuntu1                        system load monitor plugin for the Xfce4 panel
ii  xfce4-taskmanager                             1.0.0-2                                 process manager for the Xfce4 Desktop Environment
ii  xfce4-terminal                                0.4.8-1ubuntu1                          Xfce terminal emulator
ii  xfce4-utils                                   4.8.3-1ubuntu2                          Various tools for Xfce
ii  xfce4-verve-plugin                            1.0.0-1                                 Verve (command line) plugin for Xfce panel
ii  xfce4-volumed                                 0.1.13-2ubuntu1                         volume keys daemon
ii  xfce4-weather-plugin                          0.7.4-3                                 weather information plugin for the Xfce4 panel
ii  xfce4-xkb-plugin                              0.5.4.3-1ubuntu1                        xkb layout switch plugin for the Xfce4 panel
ii  xfconf                                        4.8.1-1                                 utilities for managing settings in Xfce
ii  xfdesktop4                                    4.8.3-2ubuntu7                          xfce desktop background, icons and root menu manager
ii  xfdesktop4-data                               4.8.3-2ubuntu7                          xfce desktop background, icons and root menu (common files)
ii  xfonts-base                                   1:1.0.3                                 standard fonts for X
ii  xfonts-encodings                              1:1.0.4-1ubuntu1                        Encodings for X.Org fonts
ii  xfonts-mathml                                 4ubuntu1                                Type1 Symbol font for MathML
ii  xfonts-scalable                               1:1.0.3-1                               scalable fonts for X
ii  xfonts-utils                                  1:7.6+1                                 X Window System font utility programs
ii  xfwm4                                         4.8.3-1ubuntu1.1                        window manager of the Xfce project
ii  xinit                                         1.3.1-1                                 X server initialisation tool
ii  xinput                                        1.5.99.1-0ubuntu2                       Runtime configuration and test of XInput devices
ii  xkb-data                                      2.5-1ubuntu1.3                          X Keyboard Extension (XKB) configuration data
ii  xml-core                                      0.13                                    XML infrastructure and XML catalog file support
ii  xorg                                          1:7.6+12ubuntu1                         X.Org X Window System
ii  xorg-docs-core                                1:1.6-1ubuntu2                          Core documentation for the X.org X Window System
ii  xplanet                                       1.2.1-4.1                               planetary body renderer
ii  xplanet-images                                1.2.1-4.1                               imagery for xplanet
rc  xscreensaver                                  5.15-2ubuntu1                           Automatic screensaver for X
ii  xscreensaver-data                             5.15-2ubuntu1                           data files to be shared among screensaver frontends
ii  xscreensaver-gl                               5.15-2ubuntu1                           GL(Mesa) screen hacks for xscreensaver
ii  xserver-common                                2:1.11.4-0ubuntu10.8                    common files used by various X servers
ii  xserver-xorg                                  1:7.6+12ubuntu1                         X.Org X server
ii  xserver-xorg-core                             2:1.11.4-0ubuntu10.8                    Xorg X server - core server
ii  xserver-xorg-input-all                        1:7.6+12ubuntu1                         X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                      1:2.7.0-0ubuntu1.2                      X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                      1:1.7.1-1build3                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics                  1.6.2-1ubuntu1~precise2                 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                    1:12.9.0-0ubuntu0.1                     X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                      1:0.14.0-0ubuntu2.1                     X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                        1:7.6+12ubuntu1                         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                        1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus                     1:1.3.2-4build1                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                      1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                      2.11.13-2build1                         X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel                      2:2.17.0-1ubuntu4.2                     X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                     6.9.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                        1:1.4.13.dfsg-4build2                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                   1:1.2.5-2build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau                    1:0.0.16+git20111201+b5534a1-1build2    X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome                 1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                        0.0.16-2                                X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                       6.8.1-5build2                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                     1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                         1:0.6.3-4build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage                     1:2.3.3-1ubuntu1                        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion              1:1.7.5-1build2                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                        1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                     1:0.9.4-2build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                       1:1.4.3-4build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                    1:1.3.4-2build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                       1:2.3.0-7build2                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                     1:12.0.1-1ubuntu1.1                     X.Org X server -- VMware display driver
ii  xsltproc                                      1.1.26-8ubuntu1.2                       XSLT 1.0 command line processor
ii  xterm                                         271-1ubuntu2.1                          X terminal emulator
ii  xubuntu-artwork                               12.04.11                                Xubuntu themes and artwork
ii  xubuntu-default-settings                      12.04.11                                default settings for the Xubuntu desktop
ii  xubuntu-desktop                               2.152                                   Xubuntu desktop system
ii  xubuntu-docs                                  11.10.0                                 xubuntu documentation
ii  xubuntu-icon-theme                            12.04.11                                Xubuntu icon theme
ii  xubuntu-restricted-addons                     12                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-restricted-extras                     57                                      Commonly used restricted packages for Xubuntu
ii  xubuntu-wallpapers                            12.04.11                                Xubuntu wallpapers
ii  xul-ext-ubufox                                2.6-0ubuntu0.12.04.1                    Ubuntu-specific configuration defaults and apt support for Firefox
ii  xz-lzma                                       5.1.1alpha+20110809-3                   XZ-format compression utilities - compatibility commands
ii  xz-utils                                      5.1.1alpha+20110809-3                   XZ-format compression utilities
ii  yelp                                          3.4.1-0ubuntu1                          Help browser for GNOME
ii  yelp-xsl                                      3.4.1-1                                 XSL stylesheets for the yelp help browser
ii  zeitgeist                                     0.9.0-1ubuntu1                          event logging framework
ii  zeitgeist-core                                0.9.0-1ubuntu1                          event logging framework - engine
ii  zeitgeist-datahub                             0.8.2-1ubuntu2                          event logging framework - passive logging daemon
ii  zenity                                        3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts
ii  zenity-common                                 3.4.0-0ubuntu4                          Display graphical dialog boxes from shell scripts (common files)
ii  zip                                           3.0-4                                   Archiver for .zip files
ii  zlib1g                                        1:1.2.3.4.dfsg-3ubuntu4                 compression library - runtime

```

---

### Post by Kirk Schnable on 2013-01-09
**The Cron-Apt Run Log**
The Puppet related error is because I moved the init script on this computer to prevent Puppet from running and make a controlled environment.  It is not part of the problem.
```

Date: Wed, 09 Jan 2013 13:41:13 -0600
To: root
Subject: CRON-APT completed on 1405lab01 [/etc/cron-apt/config]
User-Agent: Heirloom mailx 12.5 6/20/10
MIME-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Transfer-Encoding: 7bit

CRON-APT RUN [/etc/cron-apt/config]: Wed Jan  9 13:38:37 CST 2013
CRON-APT ACTION: 3-download
CRON-APT LINE: /usr/bin/apt-get -o quiet=1 dist-upgrade -y -o APT::Get::Show-Upgraded=true
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  facter firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  flashplugin-installer grub-common grub-pc grub-pc-bin grub2-common hiera
  libnautilus-extension1a man-db mountall nautilus nautilus-data puppet
  puppet-common software-center unattended-upgrades
20 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.8 MB of archives.
After this operation, 3993 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mountall i386 2.36.3 [70.2 kB]
Get:2 http://apt.puppetlabs.com/ precise/main facter all 1.6.17-1puppetlabs1 [49.3 kB]
Get:3 http://apt.puppetlabs.com/ precise/main hiera all 1.1.2-1puppetlabs1 [17.1 kB]
Get:4 http://apt.puppetlabs.com/ precise/main puppet all 3.0.2-1puppetlabs1 [68.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main man-db i386 2.6.1-2ubuntu1 [742 kB]
Get:6 http://apt.puppetlabs.com/ precise/main puppet-common all 3.0.2-1puppetlabs1 [830 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-globalmenu i386 18.0+build1-0ubuntu0.12.04.3 [50.3 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox i386 18.0+build1-0ubuntu0.12.04.3 [23.7 MB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-gnome-support i386 18.0+build1-0ubuntu0.12.04.3 [9256 B]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en i386 18.0+build1-0ubuntu0.12.04.3 [490 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse flashplugin-installer i386 11.2.202.261ubuntu0.12.04.1 [7528 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc i386 1.99-21ubuntu3.7 [140 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin i386 1.99-21ubuntu3.7 [876 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common i386 1.99-21ubuntu3.7 [94.2 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common i386 1.99-21ubuntu3.7 [2097 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libnautilus-extension1a i386 1:3.4.2-0ubuntu6 [51.1 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main nautilus-data all 1:3.4.2-0ubuntu6 [63.4 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main nautilus i386 1:3.4.2-0ubuntu6 [843 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main software-center all 5.2.7 [625 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unattended-upgrades all 0.76ubuntu1 [24.7 kB]
Preconfiguring packages ...
Fetched 30.8 MB in 9s (3149 kB/s)
(Reading database ... 185624 files and directories currently installed.)
Preparing to replace mountall 2.36 (using .../mountall_2.36.3_i386.deb) ...
Unpacking replacement mountall ...
Preparing to replace man-db 2.6.1-2 (using .../man-db_2.6.1-2ubuntu1_i386.deb) ...
Unpacking replacement man-db ...
Preparing to replace facter 1.6.16-1puppetlabs1 (using .../facter_1.6.17-1puppetlabs1_all.deb) ...
Unpacking replacement facter ...
Preparing to replace firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_18.0+build1-0ubuntu0.12.04.3_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 17.0.1+build1-0ubuntu0.12.04.1 (using .../firefox_18.0+build1-0ubuntu0.12.04.3_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-gnome-support_18.0+build1-0ubuntu0.12.04.3_i386.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_18.0+build1-0ubuntu0.12.04.3_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace flashplugin-installer 11.2.202.258ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.261ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace grub-pc 1.99-21ubuntu3.4 (using .../grub-pc_1.99-21ubuntu3.7_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 1.99-21ubuntu3.4 (using .../grub-pc-bin_1.99-21ubuntu3.7_i386.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 1.99-21ubuntu3.4 (using .../grub2-common_1.99-21ubuntu3.7_i386.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 1.99-21ubuntu3.4 (using .../grub-common_1.99-21ubuntu3.7_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu5 (using .../libnautilus-extension1a_1%3a3.4.2-0ubuntu6_i386.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu5 (using .../nautilus-data_1%3a3.4.2-0ubuntu6_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu5 (using .../nautilus_1%3a3.4.2-0ubuntu6_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace hiera 1.1.1-1puppetlabs1 (using .../hiera_1.1.2-1puppetlabs1_all.deb) ...
Unpacking replacement hiera ...
Preparing to replace puppet 3.0.1-1puppetlabs1 (using .../puppet_3.0.2-1puppetlabs1_all.deb) ...
Unpacking replacement puppet ...
Preparing to replace puppet-common 3.0.1-1puppetlabs1 (using .../puppet-common_3.0.2-1puppetlabs1_all.deb) ...
Unpacking replacement puppet-common ...
Preparing to replace software-center 5.2.6 (using .../software-center_5.2.7_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace unattended-upgrades 0.76 (using .../unattended-upgrades_0.76ubuntu1_all.deb) ...
Unpacking replacement unattended-upgrades ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.261.orig.tar.gz
Installing from local file /tmp/tmpLgpxQF.gz
Flash Plugin installed.
Processing triggers for install-info ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Setting up mountall (2.36.3) ...
Setting up man-db (2.6.1-2ubuntu1) ...
Updating database of manual pages ...
Setting up facter (1.6.17-1puppetlabs1) ...
Setting up firefox (18.0+build1-0ubuntu0.12.04.3) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (18.0+build1-0ubuntu0.12.04.3) ...
Setting up firefox-gnome-support (18.0+build1-0ubuntu0.12.04.3) ...
Setting up firefox-locale-en (18.0+build1-0ubuntu0.12.04.3) ...
Setting up flashplugin-installer (11.2.202.261ubuntu0.12.04.1) ...
Setting up grub-common (1.99-21ubuntu3.7) ...
Installing new version of config file /etc/grub.d/10_linux ...
Setting up grub2-common (1.99-21ubuntu3.7) ...
Setting up grub-pc-bin (1.99-21ubuntu3.7) ...
Setting up grub-pc (1.99-21ubuntu3.7) ...
/usr/sbin/grub-probe: error: cannot stat `/dev/disk/by-id/ata-Maxtor_6E040L0_E1V41MYE'.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu6) ...
Setting up nautilus-data (1:3.4.2-0ubuntu6) ...
Setting up nautilus (1:3.4.2-0ubuntu6) ...
Setting up hiera (1.1.2-1puppetlabs1) ...
Installing new version of config file /etc/hiera.yaml ...
Setting up puppet-common (3.0.2-1puppetlabs1) ...
Setting up puppet (3.0.2-1puppetlabs1) ...

Configuration file `/etc/init.d/puppet'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** puppet (Y/I/N/O/D/Z) [default=N] ? dpkg: error processing puppet (--configure):
 EOF on stdin at conffile prompt
Setting up software-center (5.2.7) ...
No apport report written because MaxReports is reached already
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Updating software catalog...this may take a moment.
Software catalog update was successful.
Setting up unattended-upgrades (0.76ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 puppet
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**Packages Installed By Puppet (based on Diff of 2 files)**
```


> debian-archive-keyring				install
> debian-keyring					install
117,118d118
< default-jre					install
< default-jre-headless				install
146d145
< electric					install
209a209,210
> gcj-4.6-jre					install
> gcj-4.6-jre-headless				install
210a212,213
> gcj-jre						install
> gcj-jre-headless				install
344,346c347
< icedtea-6-jre-cacao				install
< icedtea-6-jre-jamvm				install
< icedtea-netx					install
---
> icedtea-7-jre-jamvm				install
655a657
> libgcj12-awt					install
1458a1461,1462
> notify-osd					install
> notify-osd-icons				install
1469,1471c1473,1475
< openjdk-6-jre					install
< openjdk-6-jre-headless				install
< openjdk-6-jre-lib				install
---
> openjdk-7-jre					install
> openjdk-7-jre-headless				install
> openjdk-7-jre-lib				install
1477a1482
> oracle-java7-installer				install

```

**Packages Upgraded By Cron-Apt (based on Diff of 2 files)**
```

< ii  facter                                        1.6.16-1puppetlabs1                     Ruby module for collecting simple facts about a host operating system
---
> ii  facter                                        1.6.17-1puppetlabs1                     Ruby module for collecting simple facts about a host operating system
166,170c166,170
< ii  firefox                                       17.0.1+build1-0ubuntu0.12.04.1          Safe and easy web browser from Mozilla
< ii  firefox-globalmenu                            17.0.1+build1-0ubuntu0.12.04.1          Unity appmenu integration for Firefox
< ii  firefox-gnome-support                         17.0.1+build1-0ubuntu0.12.04.1          Safe and easy web browser from Mozilla - GNOME support
< ii  firefox-locale-en                             17.0.1+build1-0ubuntu0.12.04.1          English language pack for Firefox
< ii  flashplugin-installer                         11.2.202.258ubuntu0.12.04.1             Adobe Flash Player plugin installer
---
> ii  firefox                                       18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla
> ii  firefox-globalmenu                            18.0+build1-0ubuntu0.12.04.3            Unity appmenu integration for Firefox
> ii  firefox-gnome-support                         18.0+build1-0ubuntu0.12.04.3            Safe and easy web browser from Mozilla - GNOME support
> ii  firefox-locale-en                             18.0+build1-0ubuntu0.12.04.3            English language pack for Firefox
> ii  flashplugin-installer                         11.2.202.261ubuntu0.12.04.1             Adobe Flash Player plugin installer
291c291
< ii  grub-common                                   1.99-21ubuntu3.4                        GRand Unified Bootloader (common files)
---
> ii  grub-common                                   1.99-21ubuntu3.7                        GRand Unified Bootloader (common files)
293,295c293,295
< ii  grub-pc                                       1.99-21ubuntu3.4                        GRand Unified Bootloader, version 2 (PC/BIOS version)
< ii  grub-pc-bin                                   1.99-21ubuntu3.4                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
< ii  grub2-common                                  1.99-21ubuntu3.4                        GRand Unified Bootloader (common files for version 2)
---
> ii  grub-pc                                       1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS version)
> ii  grub-pc-bin                                   1.99-21ubuntu3.7                        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
> ii  grub2-common                                  1.99-21ubuntu3.7                        GRand Unified Bootloader (common files for version 2)
335c335
< ii  hiera                                         1.1.1-1puppetlabs1                      A simple pluggable Hierarchical Database.
---
> ii  hiera                                         1.1.2-1puppetlabs1                      A simple pluggable Hierarchical Database.
990c990
< ii  libnautilus-extension1a                       1:3.4.2-0ubuntu5                        libraries for nautilus components - runtime version
---
> ii  libnautilus-extension1a                       1:3.4.2-0ubuntu6                        libraries for nautilus components - runtime version
1421c1421
< ii  man-db                                        2.6.1-2                                 on-line manual pager
---
> ii  man-db                                        2.6.1-2ubuntu1                          on-line manual pager
1442c1442
< ii  mountall                                      2.36                                    filesystem mounting tool
---
> ii  mountall                                      2.36.3                                  filesystem mounting tool
1451,1452c1451,1452
< ii  nautilus                                      1:3.4.2-0ubuntu5                        file manager and graphical shell for GNOME
< ii  nautilus-data                                 1:3.4.2-0ubuntu5                        data files for nautilus
---
> ii  nautilus                                      1:3.4.2-0ubuntu6                        file manager and graphical shell for GNOME
> ii  nautilus-data                                 1:3.4.2-0ubuntu6                        data files for nautilus
1544,1545c1544,1545
< ii  puppet                                        3.0.1-1puppetlabs1                      Centralized configuration management - agent startup and compatibility scripts
< ii  puppet-common                                 3.0.1-1puppetlabs1                      Centralized configuration management
---
> iU  puppet                                        3.0.2-1puppetlabs1                      Centralized configuration management - agent startup and compatibility scripts
> ii  puppet-common                                 3.0.2-1puppetlabs1                      Centralized configuration management
1665c1665
< ii  software-center                               5.2.6                                   Utility for browsing, installing, and removing software
---
> ii  software-center                               5.2.7                                   Utility for browsing, installing, and removing software
1734c1734
< ii  unattended-upgrades                           0.76                                    automatic installation of security upgrades
---
> ii  unattended-upgrades                           0.76ubuntu1                             automatic installation of security upgrades

```

---

### Post by Kirk Schnable on 2013-01-09
If any other information would be useful, please don't hesitate to ask... I will keep updating this thread as we find out more information.

On the test computer, we rebooted after running Puppet.  The changes made to the computer's packages are outlined above.

The computer boots to a blinking cursor, never shows GRUB, never shows a splash screen.  I believe a GRUB issue is occurring.

---

### Post by Kirk Schnable on 2013-01-09
I am marking this thread as solved, because we determined what the problem was.  As this thread was mainly about troubleshooting\determining how to fix the issue, I will close it.

The problem is related to the automated GRUB update, and our old-style partition layout.


Continued discussion and troubleshooting of that problem will be here:

[http://ubuntuforums.org/showthread.php?p=12447208](http://ubuntuforums.org/showthread.php?p=12447208)

Kirk

---

