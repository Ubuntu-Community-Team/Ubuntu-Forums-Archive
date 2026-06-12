---
title: "Why am i getting these errors and how can i fix them?"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2011-02-21
I get prompted to do an update so i go thru with it, it locked me out of my pc and couldnt boot. i finally got that fix. so someone suggested that next, rather than updating thru the update manager, i instead run sudo apt-get update and sudo apt-get upgrade. the update went fine, but when i do the upgrade, i get this:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.opera.com testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch http://deb.opera.com/opera/dists/lenny/Release  

W: Failed to fetch http://deb.opera.com/opera-beta/dists/testing/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)
```

---

### Post by TimEnid on 2011-02-21
i was able to get rid of some of the error messages regarding opera. i just updated opera manually. but now i still get this
```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
```

---

### Post by Frogs Hair on 2011-02-21
Do as suggested by the message , run this in the terminal. if it doesn't work right away try again.```
sudo apt-get update 
```

---

### Post by TimEnid on 2011-02-22
> **Frogs Hair said:**
> Do as suggested by the message , run this in the terminal. if it doesn't work right away try again.```
sudo apt-get update 
```
tried it several times and still get the same thing.

---

### Post by avocadorange on 2011-02-24
Don't know if you saw this thread but this might help you: [http://ubuntuforums.org/showthread.php?t=1684213&highlight=error+signature+verification](http://ubuntuforums.org/showthread.php?t=1684213&highlight=error+signature+verification)

---

### Post by TimEnid on 2011-02-24
> **avocadorange said:**
> Don't know if you saw this thread but this might help you: [http://ubuntuforums.org/showthread.php?t=1684213&highlight=error+signature+verification](http://ubuntuforums.org/showthread.php?t=1684213&highlight=error+signature+verification)
thanks. but i stated in my second post that i was able to get rid of the opera related messages, by updating opera thru its website. the error message in my second post is what im trying to get rid of now.

---

### Post by tgm4883 on 2011-02-24
As the error message says you have a duplicate entry in sources.list "Duplicate sources.list entry"


Either edit your /etc/apt/sources.list and remove the duplicate entry, or post that file here so we can tell you what to remove.

---

### Post by TimEnid on 2011-02-24
> **tgm4883 said:**
> As the error message says you have a duplicate entry in sources.list "Duplicate sources.list entry"


Either edit your /etc/apt/sources.list and remove the duplicate entry, or post that file here so we can tell you what to remove.
thanks for the response. i will do this tonight. i am not at my home pc right now.

---

### Post by TimEnid on 2011-02-26
> **tgm4883 said:**
> As the error message says you have a duplicate entry in sources.list "Duplicate sources.list entry"


Either edit your /etc/apt/sources.list and remove the duplicate entry, or post that file here so we can tell you what to remove.

so which file am i supposed to be posting? is it this?
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages

if so, this is the file contents of the file, and there is only one file of this type
```
Package: acroread
Source: acroread
Priority: extra
Section: text
Installed-Size: 148904
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: amd64
Version: 9.4.1-1maverick1
Replaces: acroread-debian-files, adobereader-deu, adobereader-enu, adobereader-fr, adobereader-ja
Suggests: libldap2, libgnome-speech7
Provides: adobereader-enu, pdf-viewer
Depends: ia32-libs (>= 20080808), lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.1.1), lib32z1 (>= 1:1.1.4), libc6-i386 (>= 2.3.2), nspluginwrapper, lsb-release
Conflicts: acroread-debian-files, adobereader-deu, adobereader-enu, adobereader-fr, adobereader-ja
Filename: pool/partner/a/acroread/acroread_9.4.1-1maverick1_amd64.deb
Size: 63424398
MD5sum: aa9f930b331d81bfe3507af1efb76456
SHA1: 639924a7fda767666fe974236bd1895494694f7b
Description: Adobe Reader
 Adobe Reader allows you to view navigate and print PDF files. This version
 adds advanced forms support (save), better integration with Adobe Acrobat
 workflows, customizable toolbars and better overall performance.

Package: gstreamer0.10-fluendo-plugins-mp3-partner
Source: gstreamer0.10-fluendo-plugins-partner-x86-64
Priority: extra
Section: sound
Installed-Size: 1256
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: amd64
Version: 7.0.20100316-3
Replaces: gstreamer0.10-fluendo-mp3, gstreamer0.10-fluendo-plugins, gstreamer0.10-fluendo-plugins-mp3, gstreamer0.10-fluendo-plugins-offline
Provides: gstreamer0.10-fluendo-mp3, gstreamer0.10-fluendo-plugins-mp3
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.12.0), libgstreamer0.10-0 (>= 0.10.0), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0, gstreamer0.10-plugins-base (>= 0.10.14)
Conflicts: gstreamer0.10-fluendo-mp3, gstreamer0.10-fluendo-plugins, gstreamer0.10-fluendo-plugins-mp3, gstreamer0.10-fluendo-plugins-offline
Pre-Depends: debconf
Filename: pool/partner/g/gstreamer0.10-fluendo-plugins-partner-x86-64/gstreamer0.10-fluendo-plugins-mp3-partner_7.0.20100316-3_amd64.deb
Size: 319638
MD5sum: efc9c4338b5c3e3d2223bdecb22b81b3
SHA1: 0461c757274720fec9db4b469e347f490133fbfc
Description: MP3 codec support for GStreamer
 The GStreamer multimedia framework is being used in more and more systems,
 ranging from server media processing systems, end-user desktops and various
 embedded and mobile devices. The Fluendo Plugins are a set of plugins for
 GStreamer which implement support for various media formats and hardware.
 These plugins give you an opportunity to quickly and easily add proprietary
 support to their GStreamer-based products.
 .
 This package contains an enhanced mp3 codec.

Package: skype
Source: skype
Priority: extra
Section: net
Installed-Size: 26072
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: amd64
Version: 2.1.0.81-1ubuntu5
Replaces: skype-common, skype-mid
Depends: ia32-libs (>= 2.4), lib32asound2 (>> 1.0.22), lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.2.1), libc6-i386 (>= 2.4)
Conflicts: skype-common, skype-mid
Filename: pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_amd64.deb
Size: 20152192
MD5sum: 883ca46ba6676d1b8aff489ef84ba896
SHA1: a2c566afb4474d7848e2491c8da77fed2c1031f4
Description: VOIP and instant messaging client
 Skype is a little piece of software that lets you make free calls to anyone
 else on Skype, anywhere in the world. And even though the calls are free,
 they are really excellent quality.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call phones and mobiles at pretty cheap rates per minute.
 * Group chat with up to 100 people or conference call with up to nine others.
 * Free to download.

Package: canonical-census
Source: canonical-census
Priority: extra
Section: admin
Installed-Size: 64
Maintainer: Martin Pitt <martin.pitt@canonical.com>
Architecture: all
Version: 0.1
Depends: cron, wget
Filename: pool/partner/c/canonical-census/canonical-census_0.1_all.deb
Size: 2622
MD5sum: 3c3fd82ce7e3fb4f4f5ff421cf15e476
SHA1: bae118b7c2c91af90661f645ff15d9d9d95af97c
Description: send "I am alive" ping to Canonical
 This package installs a daily cron job for surveying how many original OEM
 installs are running in the world. Note that this does not send any
 user specific data; it only transmits the operating system version
 (/var/lib/ubuntu_dist_channel), the machine product name, and a counter how
 many pings were sent.

Package: openbravo-erp
Source: openbravo-erp-openjdk
Priority: extra
Section: web
Installed-Size: 1117456
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: all
Version: 2.50MP-25EU1-1maverick1
Depends: openjdk-6-jdk, postgresql, postgresql-contrib, postgresql-client, ant, ant-optional, tomcat6-common, apache2, libapache2-mod-jk, libtcnative-1, adduser
Filename: pool/partner/o/openbravo-erp-openjdk/openbravo-erp_2.50MP-25EU1-1maverick1_all.deb
Size: 121438674
MD5sum: 85d0bb83cb096af39839d2b5f279c10f
SHA1: 0bb800d940b1c463fefe868648458ea98e24050a
Description: Enterprise Resource Planning solution
 Openbravo is "Everyone's ERP"--a comprehensive, ready to use, web-based open
 source business management solution that automates all of the core business
 processes for small and medium-sized companies, ranging from accounting and
 financial management, to sales, purchasing, inventory management and more.
 .
 Written in Java and offering a choice between Oracle and PostgreSQL
 as database, Openbravo is model-driven, allowing easy extension and
 configuration of the system. The simple, powerful, and consistent browser
 screens do not require any client software installation, are intuitive for
 users to learn, and designed for efficient daily use. The comprehensive
 web service coverage enables easy integration with other applications.
 .
 Openbravo ERP is the foundation of a global ecosystem that is changing the
 way ERP solutions are developed, marketed, and consumed. Its modular
 architecture enables easy creation and deployment of native third
 party extensions, and Openbravo ERP users can complement the core
 functionality, choosing from an ever increasing portfolio of modules
 providing localization capabilities, additional functions and vertical
 specialization. The Openbravo ERP ecosystem provides packaged solutions to
 support all the core business processes shared by most companies, enabling
 Openbravo users to quickly realize the benefits of implementing an ERP and
 allowing them to focus their implementation efforts on the processes that
 provide a true competitive advantage.
 .
 Openbravo Community Edition on Ubuntu is a free and fully functional
 ERP, ready for production usage. Organizations wishing to maximize the
 benefits of their ERP system can also easily activate a Professional
 Edition subscription and enjoy: Full support for both the application and
 technology stack Premium functionality Access to a broader portfolio of
 extensions, including commercial modules and solutions. Get started now,
 and become part of Openbravo's global vision of "Opening ERP's Future".

Package: uex
Source: uex
Priority: extra
Section: editors
Installed-Size: 56152
Maintainer: IDM Computer Solutions, Inc. <idm@idmcomp.com>
Architecture: amd64
Version: 1.2.0.13-1maverick1
Depends: libboost-regex1.42.0 (>= 1.42.0-1), libc6 (>= 2.11), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.18.0), libicu42 (>= 4.2-1), libjpeg62, libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libsm6, libstdc++6 (>= 4.4.0), libtiff4, libx11-6, libxinerama1, libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4)
Filename: pool/partner/u/uex/uex_1.2.0.13-1maverick1_amd64.deb
Size: 21281598
MD5sum: 932f4bc5faec82f00de685ea2ce0d745
SHA1: b0ff8951f01e59e12f62ff26716b361cee4f570a
Description: UltraEdit is a text, hex, and programming language editor
 Features:
 * Code Folding
 * Supports 64-bit file handling
 * Unicode support
 * Disk based text editing and large file handling - supports files in
 excess of 4GB, minimum RAM used even for multi-megabyte files
 * Multiline find and replace dialogs for all searches (Find, Replace,
 Find in Files, Replace in Files)
 * Syntax highlighting - configurable, pre-configured for C/C++, VB, HTML,
 Java, and Perl, multiple wordfiles available for download
 * Project/workspace support
 * Integrated scripting language to automate tasks
 * Configurable keyboard mapping
 * Column/block mode editing
 * Hexadecimal editor allows editing of any binary file, shows binary
 and ASCII view

Package: adobereader-deu
Source: adobereader-deu
Priority: extra
Section: text
Installed-Size: 160900
Maintainer: Brian Thomason <brian.thomason@canonical.com>
Architecture: amd64
Version: 9.4.1-1maverick1
Replaces: acroread, acroread-debian-files, acroread-deu, adobereader-fr, adobereader-ja
Suggests: libldap2, libgnome-speech7
Provides: acroread, acroread-deu, pdf-viewer
Depends: ia32-libs (>= 20080808), lib32gcc1 (>= 1:4.1.1), lib32stdc++6 (>= 4.1.1), lib32z1 (>= 1:1.1.4), libc6-i386 (>= 2.3.2), nspluginwrapper, debconf
Conflicts: acroread, acroread-debian-files, acroread-deu, adobereader-fr, adobereader-ja
Filename: pool/partner/a/adobereader-deu/adobereader-deu_9.4.1-1maverick1_amd64.deb
Size: 69566100
MD5sum: 406ca20c4eacf184b70c25fa4464114e
SHA1: 443cf89b335de3a391c5b417b3fba6d2819eb132
Description: Adobe Reader
 Adobe Reader allows you to view navigate and print PDF files. This version
 adds advanced forms support (save), better integration with Adobe Acrobat
 workflows, customizable toolbars and better overall performance.

Package: centrifydc
Source: centrifydc
Priority: optional
Section: admin
Installed-Size: 27960
Maintainer: Centrify Corporation <support@centrify.com>
Architecture: amd64
Version: 4.4.2-310-0ubuntu2
Depends: libc6 (>= 2.9), libgcc1 (>= 1:4.1.1), libpam0g (>= 0.99.7.1), libstdc++6 (>= 4.1.1), libuuid1 (>= 2.16), debianutils (>= 3)
Conflicts: centrifydc-apache (<< 4.1.0), centrifydc-idmap, centrifydc-krb5 (<< 4.2.0), centrifydc-nis (<< 4.0.0), centrifydc-samba (<< 3.0.26a-4.0.0.000), centrifydc-web (<< 4.1.0)
Filename: pool/partner/c/centrifydc/centrifydc_4.4.2-310-0ubuntu2_amd64.deb
Size: 10739114
MD5sum: 1bc7eb3768993b87a5d63ab2437152bc
SHA1: 9b427d5e345009ad9978fb3ff9d076d0a07d2c69
Description: Centrify Express
 Free Active Directory Integration and single sign-on for Ubuntu - Centrify
 Express is the No. 1 choice of IT professionals for Active Directory-based
 authentication and single sign-on to cross-platform systems.
 .
 Centrify Express is not only the quickest and easiest solution to use and
 deploy for integrating Ubuntu systems with Active Directory, but delivers more
 functionality and more to upgrade to than alternative offerings.  And best of
 all - it is free! For more free tools, information and community support check
 out http://www.centrify.com/express

Package: sun-java6-plugin
Source: sun-java6
Priority: optional
Section: web
Installed-Size: 60
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.24-1build0.10.10.1
Depends: libasound2, libx11-6, libxext6, libxi6, libxt6, libxtst6, sun-java6-bin (>= 6.24-1build0.10.10.1), firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori | google-chrome
Filename: pool/partner/s/sun-java6/sun-java6-plugin_6.24-1build0.10.10.1_amd64.deb
Size: 1866
MD5sum: 9a100442316f9546b01574bddbf2166b
SHA1: 6432c828e6c33028d8b7227044c7dd3d7bb366cd
Description: The Java(TM) Plug-in, Java SE 6
 Java Plug-in enables applets written to the Java Platform 6
 specification to be run in Mozilla and other web browsers.
 Java Plug-in comes with the Java Runtime Environment (JRE).
 .
 This is a metapackage containing dependencies for running Java in
 various browsers.
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.6.0_07
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Name: The Java(TM) Plug-in, Java SE 6

Package: sun-java6-jdk
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 61544
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.24-1build0.10.10.1
Suggests: sun-java6-demo, openjdk-6-doc, sun-java6-source
Provides: java-compiler, java-sdk, java2-compiler, java2-sdk, java5-sdk, java6-sdk
Depends: sun-java6-bin (>= 6.24-1build0.10.10.1), libc6, libx11-6
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Filename: pool/partner/s/sun-java6/sun-java6-jdk_6.24-1build0.10.10.1_amd64.deb
Size: 20407480
MD5sum: c207c106a792f27beff0bf436c1022fb
SHA1: e08aa1db11d882ddbb7fcaeda63e06014b8d9c78
Description: Sun Java(TM) Development Kit (JDK) 6
 The JDK(TM) is a development environment for building applications,
 applets, and components using the Java programming language.
 .
 The JDK includes tools useful for developing and testing programs
 written in the Java programming language and running on the Java
 Platform.
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package

Package: sun-java6-demo
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 28248
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.24-1build0.10.10.1
Replaces: sun-java6-jdk
Suggests: openjdk-6-doc
Depends: sun-java6-jre (>= 6.24-1build0.10.10.1), sun-java6-jdk (>= 6.24-1build0.10.10.1), libc6 (>= 2.2.5)
Enhances: sun-java6-jdk
Filename: pool/partner/s/sun-java6/sun-java6-demo_6.24-1build0.10.10.1_amd64.deb
Size: 12146678
MD5sum: e6632ce8d3cf8f0b8f36ee2962ffc065
SHA1: 74522eb3961312becf950b29297480a9092e978b
Description: Sun Java(TM) Development Kit (JDK) 6 demos and examples
 The JDK(TM) is a development environment for building applications,
 applets, and components using the Java programming language.
 .
 This package contains the examples and demonstration files.

Package: sun-java6-bin
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 82588
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.24-1build0.10.10.1
Recommends: libasound2, libx11-6, libxext6, libxi6, libxt6, libxtst6, libnss-mdns
Suggests: binfmt-support
Depends: sun-java6-jre (>= 6.24-1build0.10.10.1), unixodbc, libc6
Conflicts: binfmt-support (<< 1.1.2)
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Filename: pool/partner/s/sun-java6/sun-java6-bin_6.24-1build0.10.10.1_amd64.deb
Size: 28164010
MD5sum: f2a77f547a6ee8edc7053a7c5ebb5c09
SHA1: dcefd798d040bd8b3eb338aa47309a5afdf6be95
Description: Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 6
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 6
 (package sun-java6-jdk).
 .
 This package contains architecture dependent files.

Package: ia32-sun-java6-bin
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 87044
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 6.24-1build0.10.10.1
Recommends: lib32asound2, lib32nss-mdns, ia32-libs-gtk
Depends: sun-java6-jre (>= 6.24-1build0.10.10.1), ia32-libs, libc6-i386, debconf (>= 0.5) | debconf-2.0
Filename: pool/partner/s/sun-java6/ia32-sun-java6-bin_6.24-1build0.10.10.1_amd64.deb
Size: 29967228
MD5sum: a3332f0c6d34fd337c71c62732e4d3a4
SHA1: 414881fa780b4324484a25978878c7ddac994d0e
Description: Sun Java(TM) Runtime Environment (JRE) 6 (32-bit)
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 6
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 6
 (package sun-java6-jdk).
 .
 This package contains architecture dependent files for ia32.

Package: sun-java6-source
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 18712
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 6.24-1build0.10.10.1
Replaces: sun-java6-src
Depends: sun-java6-jdk (>= 6.24-1build0.10.10.1)
Conflicts: sun-java6-src
Filename: pool/partner/s/sun-java6/sun-java6-source_6.24-1build0.10.10.1_all.deb
Size: 17916674
MD5sum: aa00c781f172c9ffb79c1025d3f7ef2e
SHA1: 94e6107148edd32a34e8540e510bf1d1d6b9a9e7
Description: Sun Java(TM) Development Kit (JDK) 6 source files
 The JDK(TM) is a development environment for building applications,
 applets, and components using the Java programming language.
 .
 This package contains the Java programming language source
 files (src.zip) for all classes that make up the Java core API.

Package: sun-java6-jre
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 14188
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 6.24-1build0.10.10.1
Recommends: gsfonts-x11
Replaces: ia32-sun-java6-bin, sun-java6-bin
Suggests: sun-java6-plugin | ia32-sun-java6-plugin, sun-java6-fonts, ttf-baekmuk | ttf-unfonts | ttf-unfonts-core, ttf-kochi-gothic | ttf-sazanami-gothic, ttf-kochi-mincho | ttf-sazanami-mincho, ttf-arphic-uming
Provides: java-runtime, java-runtime-headless, java-virtual-machine, java2-runtime, java2-runtime-headless, java5-runtime, java5-runtime-headless, java6-runtime, java6-runtime-headless
Depends: java-common (>= 0.24), locales, sun-java6-bin (>= 6.24-1build0.10.10.1) | ia32-sun-java6-bin (>= 6.24-1build0.10.10.1)
Conflicts: j2se-common
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Filename: pool/partner/s/sun-java6/sun-java6-jre_6.24-1build0.10.10.1_all.deb
Size: 6385978
MD5sum: cbe958e75e1fa196e4b9d70910c07165
SHA1: 615afea333f63c311f2d8229358ba659e3741433
Description: Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 6
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 6
 (package sun-java6-jdk).
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package
 .
 This package contains architecture independent files.

Package: sun-java6-javadb
Source: sun-java6
Priority: optional
Section: java
Installed-Size: 30800
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 6.24-1build0.10.10.1
Depends: sun-java6-jdk (>= 6.24-1build0.10.10.1)
Enhances: sun-java6-jdk
Filename: pool/partner/s/sun-java6/sun-java6-javadb_6.24-1build0.10.10.1_all.deb
Size: 10791550
MD5sum: c8cb291e8f5bb3b901a707d9e4addb88
SHA1: 58ef231edfb3109f6520bddd39277951bdbbc2cb
Description: Java(TM) DB, Sun Microsystems' distribution of Apache Derby
 Java DB is Sun's supported distribution of the open source Apache
 Derby 100% Java technology database. It is fully transactional, secure,
 easy-to-use, standards-based -- SQL, JDBC API, and Java EE -- yet small,
 only 2MB.
 .
 This package adds the optional Java DB to your JDK 6 installation.
 .
 For more information, check out the Java DB website:
 http://developers.sun.com/prodtech/javadb/

Package: sun-java6-fonts
Source: sun-java6
Priority: optional
Section: fonts
Installed-Size: 112
Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Architecture: all
Version: 6.24-1build0.10.10.1
Provides: ttf-lucida
Depends: sun-java6-jre (>= 6.24-1build0.10.10.1), defoma
Conflicts: ttf-lucida
Filename: pool/partner/s/sun-java6/sun-java6-fonts_6.24-1build0.10.10.1_all.deb
Size: 1882
MD5sum: 02fca52487618b2c4984e708d678e751
SHA1: 3a706a3ece53374e379c8db07d8ced054109d4c3
Description: Lucida TrueType fonts (from the Sun JRE)
 The Lucida fonts are included in the sun-java6-jre package.
 This package makes the fonts available to defoma.

```

---

### Post by TimEnid on 2011-02-26
and here is my sourcelist
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.canonical.com/ maverick partner
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

---

### Post by tgm4883 on 2011-02-26
> **TimEnid said:**
> and here is my sourcelist
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.canonical.com/ maverick partner
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

It's a duplicate line in sources.list, so remove this line then apt-get update.

```
deb http://archive.canonical.com/ maverick partner
```

---

### Post by TimEnid on 2011-02-26
> **tgm4883 said:**
> It's a duplicate line in sources.list, so remove this line then apt-get update.

```
deb http://archive.canonical.com/ maverick partner
```

not sure which one to delete, as none of them are exactly identical
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

i removed that first line and then ran update and still get this
```
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
```

---

### Post by tgm4883 on 2011-02-26
> **TimEnid said:**
> its not letting me edit it.

Look, I'm sure you are a reasonably intelligent person and can function in normal day to day activities, but this isn't that difficult. I can't hold your hand though every little error you get, especially since you don't post the actual errors. 

Unless something really bizarre is happening on your system (which I doubt, but don't know since you posted no error message), this is a really easy one to solve. A simple Google search (or some proactive thinking) would probably resolve it in about 3 minutes). 

I'm 99% confident that I know exactly what you are doing when you are receiving this error message. I just can't bring myself to give you the answer right now. Maybe when I get back home later I'll be in a better place to answer this. 

I really do try to help everyone that I can on here, but I just can't do it today. Maybe it's because I'm not in the best of moods today, maybe it's because you just happen to be the straw that broke the camels back. There seems to be a lot more people that simply don't even try to fix something before running for help.

If you have some learning disability then I apologize, as you have a legit reason for being unable to figure it out. If this is the case, then this post is directed at all of the other users out there that can't take the time to read and figure out simple issues like this. I'm not asking everyone to research for hours to resolve difficult issues. I would however appreciate users taking 5 minutes to do a google search and resolving issues on their own. 

I really am sorry for the tone of this post, but I just can't do this anymore.

---

### Post by TimEnid on 2011-02-26
> **tgm4883 said:**
> Look, I'm sure you are a reasonably intelligent person and can function in normal day to day activities, but this isn't that difficult. I can't hold your hand though every little error you get, especially since you don't post the actual errors. 

Unless something really bizarre is happening on your system (which I doubt, but don't know since you posted no error message), this is a really easy one to solve. A simple Google search (or some proactive thinking) would probably resolve it in about 3 minutes). 

I'm 99% confident that I know exactly what you are doing when you are receiving this error message. I just can't bring myself to give you the answer right now. Maybe when I get back home later I'll be in a better place to answer this. 

I really do try to help everyone that I can on here, but I just can't do it today. Maybe it's because I'm not in the best of moods today, maybe it's because you just happen to be the straw that broke the camels back. There seems to be a lot more people that simply don't even try to fix something before running for help.

If you have some learning disability then I apologize, as you have a legit reason for being unable to figure it out. If this is the case, then this post is directed at all of the other users out there that can't take the time to read and figure out simple issues like this. I'm not asking everyone to research for hours to resolve difficult issues. I would however appreciate users taking 5 minutes to do a google search and resolving issues on their own. 

I really am sorry for the tone of this post, but I just can't do this anymore.

understandable, but if you look at my previous post again, you will see that comment is no longer there. I figured that part out on my own.

also, i feel what you are saying, but you have the decision of coming in this post. i didnt force you, so if you dont feel like helping, simple solution: stop replying. thanks for your help anyway. 

silly me, thinking i could come here and get help:P

lastly, if you look at some of my previous posts, any issues i had, i was able to comprehend and sometimes even figure things out on my own.

---

### Post by Old_Grey_Wolf on 2011-02-26
> **TimEnid said:**
> and here is my sourcelist
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://archive.canonical.com/ maverick partner
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

Delete the third line from the bottom. It is "deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner".

---

### Post by TimEnid on 2011-02-26
> **Old_Gray_Wolf said:**
> Delete the third line from the bottom. It is "deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner".

thank you for your help. it is much appreciated. that fixed it.

---

### Post by Old_Grey_Wolf on 2011-02-26
> **TimEnid said:**
> thank you for your help. it is much appreciated. that fixed it.

That is exactly what tgm4883 told you to do in response #11. That was just before he exceeded his threshold of frustration.

---

### Post by TimEnid on 2011-02-26
> **Old_Gray_Wolf said:**
> That is exactly what tgm4883 told you to do in response #11. That was just before he exceeded his threshold of frustration.

there was a misunderstanding on my part. apologies.

---

