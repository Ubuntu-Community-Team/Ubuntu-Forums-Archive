---
title: "add extra programs to ubuntu 13.??"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Adrian_Moncloa on 2015-08-24
I installed Ubuntu 13 point something successfully.  However, there was an option that was unchecked that asked if you wanted to include extra programs in your installation.  I left it unchecked and am now wondering if you can add this functionality from the command line. Thanks in advance.

---

### Post by sammiev on 2015-08-24
You will need to move up to the 14 LTS version or to at least 12 LTS. 

13 is now dead and will not get updates.

See [this]("http://www.ubuntu.com/info/release-end-of-life") for more info.

---

### Post by Adrian_Moncloa on 2015-08-30
Sorry for the misinformation.  I had actually installed ubuntu-14.04.3-desktop-i386 but I still did not add the extra programs during installation.  Any idea how I can add them from the command line?
Thanks in advance.

---

### Post by v3.xx on 2015-08-30
The extra package sources are in the gui, if thats what you mean.

```
software-properties-gtk
```

[ATTACH=CONFIG]264123[/ATTACH]

---

### Post by flaymond on 2015-08-31
Hi there. Welcome to Ubuntu Forums.


Do you mean the 'install this third-party software' in the installation session ?

[ATTACH=CONFIG]264124[/ATTACH]

then try this to install - 

```
sudo apt-get install libmpeg3-dev
```

or if you want more than that -

```
sudo apt-get install ubuntu-restricted-extras
```

This one install Flash, codecs and another bunch of propietary softwares. This is useful if you want to run a lot of videos with different formats, and Flash for your web browser to run Flash programs. (swf)

or you mean you want to install more programs?

This can be accomplished by running - 

```
sudo apt-get install **program-name**
```

What program to install? You can find a lot by typing -

```
apt-cache search ***name ***
```

Example - I want to look for browser

```
alex@scope:~$ apt-cache search browser
auctex - integrated document editing environment for TeX etc.
ca-certificates - Common CA certificates
cups-browsed - OpenPrinting CUPS Filters - cups-browsed
devhelp - GNOME developers help program
devhelp-common - Common files for devhelp and its library
devscripts - scripts to make the life of a Debian Package maintainer easier
doxygen - Documentation system for C, C++, Java, Python and other languages
doxygen-dbg - Debug symbols for doxygen
doxygen-doc - Documentation for doxygen
doxygen-latex - Documentation system for C, C++, Java, Python and other languages
emacs24 - GNU Emacs editor (with GTK+ user interface)
emacs24-nox - GNU Emacs editor (without X support)
firefox - Safe and easy web browser from Mozilla
firefox-dbg - Safe and easy web browser from Mozilla - debug symbols
firefox-dev - Safe and easy web browser from Mozilla - development files
firefox-globalmenu - Safe and easy web browser from Mozilla (transitional package)
gimp - The GNU Image Manipulation Program
gimp-help-de - Documentation for the GIMP (German)
gimp-help-en - Documentation for the GIMP (English)
gimp-help-es - Documentation for the GIMP (Spanish)
gimp-help-fr - Documentation for the GIMP (French)
gimp-help-it - Documentation for the GIMP (Italian)
gimp-help-ko - Documentation for the GIMP (Korean)
gimp-help-nl - Documentation for the GIMP (Dutch)
gimp-help-nn - Documentation for the GIMP (Norwegian)
gimp-help-pl - Documentation for the GIMP (Polish)
gimp-help-ru - Documentation for the GIMP (Russian)
gimp-help-sv - Documentation for the GIMP (Swedish)
gir1.2-gucharmap-2.90 - GObject introspection data for the Unicode browser widget library
gir1.2-webkit-1.0 - Web content engine library for GTK+ - GObject introspection data
gir1.2-webkit-3.0 - Web content engine library for GTK+ - GObject introspection data
gir1.2-webkit2-3.0 - WebKit2 API layer for WebKitGTK+ - GObject introspection data
gucharmap - Unicode character picker and font browser
hevea - translates from LaTeX to HTML, info, or text
icedtea-7-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
icedtea-plugin - web browser plugin to execute Java applets (dependency package)
info - Standalone GNU Info documentation browser
libbatik-java - xml.apache.org SVG Library
libdevhelp-3-2 - Library providing documentation browser functionality
libdevhelp-dev - Library providing documentation browser functionality (development)
libgd-dbg - Debug symbols for GD Graphics Library
libgd-dev - GD Graphics Library (development version)
libgd3 - GD Graphics Library
libgucharmap-2-90-7 - Unicode browser widget library (shared library)
libgucharmap-2-90-dev - Unicode browser widget library (development headers)
libjs-jquery-tablesorter - Flexible client-side table sorting
libjs-raphael - JavaScript library to work with vector graphics
libjs-underscore - JavaScript's functional programming helper library
libjs-yui3-common - Yahoo User Interface Library v3 (common files)
libjs-yui3-debug - Yahoo User Interface Library v3 (debug files)
libjs-yui3-full - Yahoo User Interface Library v3 (full, uncompressed files)
libjs-yui3-min - Yahoo User Interface Library v3 (minified files)
libkhtml5 - KHTML Web Content Rendering Engine
libmono-webbrowser2.0-cil - Mono Web Browser library (for CLI 2.0)
libmono-webbrowser4.0-cil - Mono Web Browser library (for CLI 4.0)
libnet-ssleay-perl - Perl module for Secure Sockets Layer (SSL)
liboxideqt-qmlplugin - Web browser engine library for Qt (QML plugin)
libqt5webkit5 - Web content engine library for Qt
libqt5webkit5-dbg - Web content engine library for Qt - debugging symbols
libqt5webkit5-dev - Web content engine library for Qt - development files
libqt5webkit5-qmlwebkitplugin - Qt WebKit QML plugin
libqtwebkit-dev - Web content engine library for Qt - development files
libqtwebkit4 - Web content engine library for Qt
libqtwebkit4-dbg - Web content engine library for Qt - debugging symbols
libtidy-0.99-0 - HTML syntax checker and reformatter - library
libtidy-dev - HTML syntax checker and reformatter - development
libwebkit-cil-dev - CLI binding for the WebKit library - development package
libwebkit1.1-cil - CLI binding for the WebKit library
libwebkit2gtk-3.0-25 - WebKit2 API layer for WebKitGTK+
libwebkit2gtk-3.0-25-dbg - WebKit2 API layer for WebKitGTK+ - debugging symbols
libwebkit2gtk-3.0-dev - WebKit2 API layer for WebKitGTK+ - development files
libwebkitgtk-1.0-0 - Web content engine library for GTK+
libwebkitgtk-1.0-0-dbg - Web content engine library for GTK+ - debugging symbols
libwebkitgtk-1.0-common - Web content engine library for GTK+ - data files
libwebkitgtk-3.0-0 - Web content engine library for GTK+
libwebkitgtk-3.0-0-dbg - Web content engine library for GTK+ - debugging symbols
libwebkitgtk-3.0-common - Web content engine library for GTK+ - data files
libwebkitgtk-3.0-dev - Web content engine library for GTK+ - development files
libwebkitgtk-common-dev - Web content engine library for GTK+ - common development files
libwebkitgtk-dev - Web content engine library for GTK+ - development files
libyelp-dev - Library for the GNOME help browser (development)
libyelp0 - Library for the GNOME help browser
lynx - Text-mode WWW Browser (transitional package)
lynx-cur - Text-mode WWW Browser with NLS support (development version)
man-db - on-line manual pager
monodoc-browser - MonoDoc GTK+ based viewer
monodoc-webkit-manual - compiled XML documentation for webkit-sharp
munin - network-wide graphing framework (grapher/gatherer)
nginx-core - nginx web/proxy server (core version)
nut-cgi - network UPS tools - web interface
oxideqt-codecs - Web browser engine library for Qt (codecs)
oxideqt-codecs-dbg - Web browser engine library for Qt (Debug symbols)
oxideqt-codecs-extra - Web browser engine library for Qt (codecs)
oxideqt-codecs-extra-dbg - Web browser engine library for Qt (Debug symbols)
oxideqt-dbg - Web browser engine library for Qt (Debug symbols)
python-gnome2-doc - Python bindings for the GNOME desktop environment
python-gtk2-doc - Python bindings for the GTK+ widget set - documentation
python-html5lib - HTML parser/tokenizer based on the WHATWG HTML5 specification (Python 2)
python-requests - elegant and simple HTTP library for Python, built for human beings
python-utidylib - Python wrapper for TidyLib
python3-pyqt5.qtwebkit - Python 3 bindings for Qt5's WebKit module
python3-pyqt5.qtwebkit-dbg - Python 3 bindings for Qt5's WebKit module (debug extensions)
python3-requests - elegant and simple HTTP library for Python3, built for human beings
qtdeclarative5-ubuntu-ui-extras-browser-plugin - Ubuntu web browser QML plugin
qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets - Ubuntu web browser QML plugin assets
rhythmbox-mozilla - Rhythmbox Mozilla plugin
sensible-utils - Utilities for sensible alternative selection
tidy - HTML syntax checker and reformatter
tidy-doc - HTML syntax checker and reformatter - documentation
totem-mozilla - Totem Mozilla plugin
ubuntu-defaults-builder - create Ubuntu customization packages
ubuntu-docs - Ubuntu Desktop Guide
unity-scope-gmusicbrowser - gmusicbrowser scope for Unity
w3m - WWW browsable pager with excellent tables/frames support
webaccounts-extension-common - Ubuntu Online Accounts browser extension - common files
webbrowser-app - Ubuntu web browser
x11-apps - X applications
xdg-utils - desktop integration utilities from freedesktop.org
xfonts-mathml - Type1 Symbol font for MathML
yelp - Help browser for GNOME
yelp-xsl - XSL stylesheets for the yelp help browser
axe - Text editor for X
flashplugin-installer - Adobe Flash Player plugin installer
mp3fs - FUSE filesystem for transcoding FLAC to MP3 on the fly
mythbrowser - A web browser for MythTV
mythnetvision - A Internet Video Player plugin for MythTV
othman - electronic Quran browser
pepperflashplugin-nonfree - Pepper Flash Player - browser plugin
squeak-plugin-image - The Squeak Smalltalk System (image and changes file)
w3-recs - Recommendations of the World Wide Web Consortium (W3C)
wine-gecko2.21 - Microsoft Windows compatibility layer (embedded web browser)
389-admin - 389 Directory Administration Server
ajaxterm - Web based terminal written in Python
akregator - RSS/Atom feed aggregator
alevt - X11 Teletext/Videotext browser
alice - Web browser (WebKit or Gecko) based IRC client
ams - Realtime modular synthesizer for ALSA
amule-gnome-support - ed2k links handling support for GNOME web browsers
anon-proxy - Proxy to surf the web anonymously
arora - simple cross platform web browser
aspectj - aspect-oriented extension for Java - tools
autopsy - graphical interface to SleuthKit
aview - A high quality ASCII art image viewer and video player
betaradio - Internet radio of Taiwan
bluedevil - KDE Bluetooth stack
bluefish - advanced Gtk+ HTML editor
browser-history - User daemon that tracks URLs looked at and logs them
browser-plugin-gnash - GNU Shockwave Flash (SWF) player - Plugin for Mozilla and derivatives
browser-plugin-libreoffice - office productivity suite -- Mozilla plugin
browser-plugin-lightspark - High-performance SWF player - Mozilla Plugin (experimental)
browser-plugin-packagekit - Plugin to install missing plugins using PackageKit
browser-plugin-spice - XPI client for interacting with SPICE servers
browser-plugin-vlc - multimedia plugin for web browsers based on VLC
buffy - Heavy duty browser for mail folders
buffycli - Text mode alternative to Buffy
buxon - SIOC forums browser
c-cpp-reference - C and C++ programming reference
cdargs - bookmarks and browsing for the cd command
cervisia - graphical CVS client
ch5m3d - create and visualize 3-dimensional drawings of simple molecules
chimera2 - Web browser for X
chromium-browser-dbg - chromium-browser debug symbols
chromium-chromedriver - WebDriver driver for the Chromium Browser
cloudprint - Server for Google Cloud Print
codeblocks - Code::Blocks integrated development environment (IDE)
codeblocks-dbg - Code::Blocks debugging libraries
codeblocks-dev - Code::Blocks development files (SDK)
collabtive - Web-based project management software
comix - GTK Comic Book Viewer
compass-breakpoint-plugin - really simple media queries with Sass
compass-fancy-buttons-plugin - Compass plugin implementing fancy CSS3 buttons
compass-layoutgala-plugin - Compass plugin implementing the Layout-gala CSS styles
cricket - Program for collection and display of time-series data
d-feet - D-Bus object browser, viewer and debugger
darkstat - network traffic analyzer
dbndns - Debian fork of djbdns, a collection of Domain Name System tools
dbus-java-bin - simple interprocess messaging system (Java Binaries)
dcmtk-www - OFFIS DICOM toolkit worklist www server application
ddns3-client - Issues dynamic DNS v3 requests
desktop-webmail - Webmail for Linux Desktops
desproxy - tunnel TCP traffic through a HTTP proxy
dianara - client for the pump.io federated social network
dillo - Small and fast web browser
djbdns - a collection of Domain Name System tools
djview-plugin - Browser plugin for the DjVu image format
doc-central - web-based documentation browser
dolibarr - Web based software to manage a small company or foundation
dooble - WebKit based browser written is Qt 4
doublecmd-help-en - Documentation for Double Commander (English)
doublecmd-help-ru - Documentation for Double Commander (Russian)
doublecmd-help-uk - Documentation for Double Commander (Ukrainian)
doxygen-gui - GUI configuration tool for doxygen
dpkg-www - Web based Debian package browser
drgeo-doc - Dr. Geo online user manual
drpython - simple and customizable editor for the Python language
drupal7-mod-drucall - WebRTC SIP module for the Drupal CMS
drupal7-mod-jscommunicator - Browser-based messaging, phone and video chat application
drupal7-mod-jssip - Browser-based messaging, phone and video chat application
dsc-statistics-presenter - DNS Statistics Collector - Presenter component
dsniff - Various tools to sniff network traffic for cleartext insecurities
dvb-apps - Digital Video Broadcasting (DVB) applications
dwb - lightweight WebKit browser
dwww - Read all on-line documentation with a WWW browser
easytag - viewing, editing and writing ID3 tags
ecb - code browser for Emacs supporting several languages
edfbrowser - viewer for biosignal storage files such as bdf and edf
editmoin - edit MoinMoin wiki pages with your favourite editor
edubuntu-docs - The Ubuntu Documentation Project - Edubuntu Documentation
eekboek-gui - Graphical User Interface for EekBoek
elinks - advanced text-mode WWW browser
elinks-data - advanced text-mode WWW browser - data files
elinks-doc - advanced text-mode WWW browser - documentation
elinks-lite - advanced text-mode WWW browser (transition package)
emacs23 - The GNU Emacs editor (with GTK+ user interface)
emacs23-lucid - The GNU Emacs editor
emacs23-nox - The GNU Emacs editor (without X support)
emacs24-lucid - GNU Emacs editor
epiphany-browser - Intuitive GNOME web browser
epiphany-browser-data - Data files for the GNOME web browser
epiphany-browser-dbg - Debugging symbols for the GNOME web browser
eric - full featured Python IDE
esteid - Estonian national ID card support (meta-package)
ezmlm-browse - Web browser for ezmlm-idx archives
fex - web service for transferring very large files
filetea - Web-based file sharing system
firefox-mozsymbols - Safe and easy web browser from Mozilla - Breakpad symbols
firefox-testsuite - Safe and easy web browser from Mozilla - testsuite
fonts-lyx - TrueType versions of some TeX fonts used by LyX
fonts-mathjax - JavaScript display engine for LaTeX and MathML (fonts)
fonts-mathjax-extras - JavaScript display engine for LaTeX and MathML (extra fonts)
forg - Graphical Gopher Browser
fpm2 - password manager with GTK+ 2.x GUI
freemind-browser - Java Applet for publishing Mindmaps produced with FreeMind
frescobaldi - Qt4 LilyPond sheet music editor
fsniper - Monitors for new files and runs a rule based task
fsviewer-icons - icons for fsviewer to make it look more like the NeXT FileViewer
gambas3-gb-db-form - Gambas database bound controls
gambas3-gb-qt4-webkit - Gambas WebKit component
garmin-plugin - browser plugin for communication with the fitness websites
gbemol - Graphical frontend for the Music Player Daemon (MPD)
gbrowse - GMOD Generic Genome Browser
gcu-plugin - GNOME chemistry utils (browser plugin)
geany-plugin-addons - miscellanous plugins for Geany
geany-plugin-devhelp - DevHelp plugin for Geany
geany-plugin-geniuspaste - GeniusPaste plugin for Geany
geany-plugin-treebrowser - tree browser plugin for Geany
gecko-mediaplayer - Multimedia plug-in for Gecko browsers
gecrit - simple, easy-to-use Python IDE
gedit-source-code-browser-plugin - source code class and function browser plugin for Gedit
geeqie - image viewer using GTK+
geeqie-common - data files for Geeqie
geeqie-dbg - debug symbols for Geeqie
gimmix - graphical music player daemon (MPD) client using GTK+2
gitg - git repository viewer
gkrellxmms2 - GKrellM plugin to control xmms2
global - Source code search and browse tools
gman - small man(1) front-end for X
gmpc - Gnome Music Player Client (graphical interface to MPD)
gmpc-data - Gnome Music Player Client - data files
gmpc-dbg - Gnome Music Player Client - debugging symbols
gmpc-dev - Gnome Music Player Client (plugin development files)
gmpc-plugins - Plugins for the GNOME Music Player Client
gmusicbrowser - graphical jukebox for large music collections
gnash - GNU Shockwave Flash (SWF) player
gnash-common - GNU Shockwave Flash (SWF) player - Common files/libraries
gnash-cygnal - GNU Shockwave Flash (SWF) player - Media server
gnash-dbg - GNU Shockwave Flash (SWF) player - Debug symbols
gnash-dev - GNU Shockwave Flash (SWF) player - Development files
gnash-doc - GNU Shockwave Flash (SWF) player - API documentation
gnash-ext-fileio - GNU Shockwave Flash (SWF) player - Fileio extension
gnash-ext-lirc - GNU Shockwave Flash (SWF) player - LIRC extension
gnash-ext-mysql - GNU Shockwave Flash (SWF) player - MySQL extension
gnash-tools - GNU Shockwave Flash (SWF) player - Command-line Tools
gnat-gps - integrated development environment for C and Ada
gnome-api-docs - API reference documentation for the GNOME libraries
gnome-core - GNOME Desktop Environment -- essential components
gnome-mplayer - GTK+ interface for MPlayer
gnome-mplayer-dbg - GTK+ interface for MPlayer (debugging symbols)
gnu-smalltalk-browser - GNU Smalltalk browser
gnucash-docs - Documentation for gnucash, a personal finance tracking program
gnuit - GNU Interactive Tools, a file browser/viewer and process viewer/killer
goaccess - log analyzer and interactive viewer for the Apache Webserver
goplay - games (and more) package browser using DebTags
gotmail - utility to download email from a Hotmail or MSN account
gplanarity - simple puzzle game involving untangling planar graphs
gt5 - shell program to display visual disk usage with navigation
gthumb - image viewer and browser
gthumb-data - image viewer and browser - arch-independent files
gthumb-dbg - image viewer and browser - debugging symbols
gthumb-dev - image viewer and browser - development files
gtkcookie - editor for cookie files
gtml - HTML pre-processor
guacamole - HTML5 web application for accessing remote desktops
guacamole-tomcat - Tomcat-based Guacamole install with VNC support
gurlchecker - graphical websites checker
gxmms2 - XMMS2 client for the GNOME desktop
haxe - Web-oriented universal programming language
hbro - minimal KISS-compliant web browser
hoteldruid - web-based property management system for hotels or B&Bs
html2wml - converts HTML pages to WML (WAP) or i-mode pages
httest - HTTP test tool
httrack - Copy websites to your computer (Offline browser)
hv3 - Lightweight web browser
icedtea-6-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
imgsizer - Adds WIDTH and HEIGHT attributes to IMG tags in HTML files
info2www - Read info files with a WWW browser
isoqlog - Mail Transport Agent log analysis program
java2html - Highlight Java and C++ sources for WWW presentation
jd - simple browser for "2ch-style" web forum sites
jed - editor for programmers (textmode version)
jed-extra - collection of useful Jed modes and utilities
jedit - Plugin-based editor for programmers
jplayer - jQuery plugin that plays and controls audio files in a webpage
jpoker - javascript online poker client
js-of-ocaml - OCaml bytecode to JavaScript compiler (compiler)
jscommunicator-web-phone - Basic SIP video-phone web page using WebRTC
jsmath - TeX equations in HTML documents
jsmath-fonts - raster fonts for jsMath
jsmath-fonts-sprite - raster fonts for jsMath plugin spriteImageFonts
jsxgraph - Interactive Geometry with JavaScript
juffed-plugins - Lightweight Qt 4 text editor - plugins
junior-internet - Debian Jr. Internet tools
jwchat - full featured, web-based Jabber chat client
jxplorer - Java LDAP Browser
kde-plasma-desktop - KDE Plasma Desktop and minimal set of applications
kde-plasma-netbook - KDE Plasma Netbook and minimal set of applications
kdevelop - integrated development environment for KDE
kdevelop-data - data files for the KDevelop IDE
kdevelop-dbg - debugging symbols for KDevelop
kdevelop-dev - development files for the KDevelop IDE
kdevelop-l10n - localization files for the KDevelop IDE
kdevelop-php - PHP plugin for KDevelop
kdevelop-php-docs - PHP documentation plugin for KDevelop
kgmailnotifier - Gmail notifier applet for the KDE Plasma Workspace
king - interactive system for three-dimensional vector graphics
klash - GNU Shockwave Flash (SWF) player - Standalone player for KDE
klipper - clipboard manager
konq-plugins - plugins for Konqueror, the KDE file/web/document browser
konqueror - advanced file manager, web browser and document viewer
konqueror-nsplugins - Netscape plugin support for Konqueror
konqueror-plugin-gnash - GNU Shockwave Flash (SWF) player - Plugin for Konqueror
kpart-webkit - WebKit KPart
kpart-webkit-dbg - WebKit KPart - debugging symbols
kpartsplugin - Netscape-compatible plugin to embed KDE file-viewers into browser
lazarus-doc - IDE for Free Pascal - documentation dependency package
lazarus-doc-1.0.10 - IDE for Free Pascal - documentation
ldap-account-manager - webfrontend for managing accounts in an LDAP directory
ledgersmb - financial accounting and ERP program
letodms - document management system based on PHP and MySQL
libapache2-authcookie-perl - Perl Authentication and Authorization via cookies
libapache2-mod-upload-progress - upload progress support for the Apache web server
libaws-bin - Ada Web Server utilities
libaws-dbg - Debugging symbols for the Ada Web Server shared library
libaws-doc - Ada Web Server documentation
libaws2.10.2 - Ada Web Server shared library
libaws2.10.2-dev - Ada Web Server development files
libbio-samtools-perl - Perl interface to SamTools library for DNA sequencing
libbrowser-open-perl - Perl module to open a browser in a given URL
libcgi-application-plugin-captcha-perl - module providing CAPTCHA support in CGI::Application
libcgi-application-plugin-protectcsrf-perl - plugin to generate and verify anti-CSRF challenges
libcgic-dev - C library for developing CGI applications
libcgic2 - C library for developing CGI applications
libcodeblocks0 - Code::Blocks shared library
libcurses-ui-perl - curses-based OO user interface framework for Perl
libdap11 - Open-source Project for a Network Data Access Protocol library
libdata-showtable-perl - Perl module to print arrays of data in a formatted listing
libdomain-publicsuffix-perl - module for parsing a domain to determine the public suffix
libds-admin-serv0 - Libraries for the 389 Directory Administration Server
libgd-ocaml - OCaml interface to the GD library -- runtime files
libgd-ocaml-dev - OCaml interface to the GD library -- developpement files
libgd-tools - GD command line tools and example code
libgdl-3-5 - GNOME DevTool libraries
libgdl-3-common - GNOME DevTool libraries - common files
libgdl-3-dbg - GNOME DevTool libraries - debug files
libgdl-3-dev - GNOME DevTool libraries - development files
libgdl-3-doc - GNOME DevTool libraries - documentation
libghc-hbro-contrib-dev - third-party extensions to hbro
libghc-hbro-contrib-doc - third-party extensions to hbro; documentation
libghc-hbro-contrib-prof - third-party extensions to hbro; profiling libraries
libghc-hbro-dev - minimal KISS-compliant web browser
libghc-hbro-doc - minimal KISS-compliant web browser; documentation
libghc-hbro-prof - minimal KISS-compliant web browser; profiling libraries
libghc-wai-handler-launch-dev - WAI handler for launching in a web browser
libghc-wai-handler-launch-doc - Short description of wai-handler-launch; documentation
libghc-wai-handler-launch-prof - Short description of wai-handler-launch; profiling libraries
libghc-webkit-dev - Binding to the Webkit library
libghc-webkit-doc - Binding to the Webkit library; documentation
libghc-webkit-prof - Binding to the Webkit library; profiling libraries
libgnustep-gui0.22 - GNUstep GUI Library
libgtk2-gst - GTK+ bindings and environment for GNU Smalltalk
libhtml-clean-perl - Cleans up HTML code for web browsers, not humans
libhtml-defang-perl - cleans HTML and CSS of scripting, executable contents and XSS attacks
libhtml-display-perl - module for displaying HTML locally in a browser
libhtml-formattext-withlinks-perl - Perl module to convert HTML to text with links as footnotes
libhtml-prettyprinter-perl - module that generates nice HTML files from HTML syntax trees
libhtml-widgets-selectlayers-perl - Perl extension for selectable HTML layers
libhtmlunit-core-js-java - GUI-Less browser for Java programs - JavaScript engine
libhtmlunit-java - GUI-Less browser for Java programs
libhttp-browserdetect-perl - module to extract system data from an HTTP User Agent string
libhttp-recorder-perl - Perl module to record interaction with websites
libhttpunit-java - automated web site testing toolkit
libhttpunit-java-doc - documentation for libhttpunit-java
libitext-java - Java Library to create and manipulate PDF on the fly
libitext-java-gcj - Java Library to create and manipulate PDF on the fly
libitext1-java - Java Library to generate PDF on the Fly
libitext5-java - Java Library to create and manipulate PDF on the fly
libitext5-java-doc - Java Library to create and manipulate PDF on the fly (documentation)
libjabsorb-java - Java to Javascript object request broker
libjboss-profiler-java - JBoss Profiler
libjcm-java - Java Components for Mathematics
libjcm-java-doc - Documentation for Java Components for Mathematics
libjenkins-htmlunit-core-js-java - Jenkins branch of the HtmlUnit Core JS Interpreter
libjenkins-htmlunit-java - Jenkins branch of HtmlUnit browser testing for web apps
libjenkins-htmlunit-java-doc - Documentation for Jenkins HtmlUnit
libjgrapht0.6-java-doc - javadoc-generated API of libjgrapht-java
libjs-angularjs - lets you write client-side web applications as if you had a smarter browser
libjs-asciimathml - a library to render high quality mathematical formulas in a browser
libjs-async - higher-order functions and common patterns for asynchronous Javascript
libjs-backbone - some Backbone for JavaScript applications - browser library
libjs-bignumber - Arbitrary-precision decimal and non-decimal arithmetic (client)
libjs-coffeescript - client-side interpreter for the CoffeeScript language
libjs-cssom - CSS parser written in pure JavaScript
libjs-d3 - JavaScript visualization library for HTML and SVG
libjs-ejs - Embedded JavaScript templates (client support)
libjs-excanvas - HTML5 Canvas for Internet Explorer
libjs-extjs - cross-browser JavaScript library
libjs-extjs-doc - cross-browser JavaScript library (docs)
libjs-flotr - plotting library for the Prototype Framework
libjs-gordon - Open source flash runtime written in pure javascript
libjs-highlight - JavaScript library for syntax highlighting
libjs-htmlparser - forgiving HTML/XML/RSS Parser in Javascript
libjs-ie7 - help Internet Explorer behave like a standards-compliant browser
libjs-img.srcset - fast JavaScript polyfill for img srcset
libjs-impress - JavaScript library to make animated presentations
libjs-inherits - Exposes inherits function from Node.js environment
libjs-jac - JavaScript Jabber Client Library
libjs-jquery-jgrowl - notification system for jquery
libjs-jquery-jplayer - HTML5 Audio & Video for jQuery with a Flash fallback
libjs-jquery-jush - jQuery Syntax Highlighter
libjs-jquery-lazyload - Lazy Load Plugin for jQuery
libjs-jquery-mousewheel - jQuery Mousewheel Plugin
libjs-jquery-reflection - jQuery plugin to add reflection effects to images in webpages
libjs-jscommunicator - Browser-based messaging, phone and video chat application
libjs-json - JSON encoders/decoders implemented in JavaScript
libjs-jssip - JavaScript implementation of a WebRTC SIP video phone
libjs-jstorage - store data locally with JavaScript
libjs-leaflet - JavaScript library for mobile-friendly interactive maps
libjs-less - the LESS CSS meta-language - Javascript library
libjs-mathjax - JavaScript display engine for LaTeX and MathML
libjs-mathjax-doc - JavaScript display engine for LaTeX and MathML (documentation)
libjs-modernizr - JavaScript library to detect HTML5 and CSS3 features in the user's browser
libjs-mootools - compact JavaScript framework
libjs-node-uuid - simple, fast generation of RFC4122 UUIDs - JavaScript library
libjs-of-ocaml - OCaml bytecode to JavaScript compiler (runtime)
libjs-of-ocaml-dev - OCaml bytecode to JavaScript compiler (development files)
libjs-of-ocaml-doc - OCaml bytecode to JavaScript compiler (documentation)
libjs-openlayers - JavaScript library for displaying map data in web browsers
libjs-openlayers-doc - documentation for OpenLayers
libjs-polymaps - JavaScript library for image- and vector-tiled maps
libjs-qunit - JavaScript Unit Testing framework
libjs-semver - Semantic Versioning for Node.js
libjs-sipml5 - JavaScript implementation of a WebRTC SIP video phone
libjs-sipml5-doc - JavaScript implementation of a WebRTC SIP video phone - API docs
libjs-traverse - recursively traverse objects in Javascript
libjs-twitter-bootstrap - HTML, CSS and JS toolkit from Twitter
libjs-twitter-bootstrap-docs - HTML, CSS and JS toolkit from Twitter (documentation)
libjs-underscore.logger - cross-browser and Node empowered logging - browser library
libjs-unorm - Common JS Unicode Normalizer (client/browser)
libjs-xmlextras - creates a common interface to use of the XML objects provided by IE and Mozilla
libjs-yui - Yahoo User Interface Library
libjs-zeparser - Javascript library for parsing Javascript code
libjsoup-java - Java HTML parser that makes sense of real-world HTML soup
libjsoup-java-doc - Documentation for jsoup HTML Parser
liblingua-preferred-perl - Perl module which allows language content negotiation
libnetx-java - An open-source JNLP client
libpacparser-dev - library to parse proxy auto-config files (development files)
libpacparser1 - library to parse proxy auto-config files
libpadre-plugin-datawalker-perl - simple Perl data structure browser Padre
libphp-snoopy - Snoopy is a PHP class that simulates a web browser
libplack-middleware-crossorigin-perl - Plack middleware adding headers to allow CORS
libplack-middleware-file-sass-perl - Sass and SCSS support for all Plack-based PSGI frameworks
libpod-webserver-perl - a miniature web server for reading Pod in web browsers
libqtpropertybrowser3 - Qt Property Browser Library - runtime
libqtpropertybrowser3-dev - Qt Property Browser Library - development
libqtwebkit-qmlwebkitplugin - Qt WebKit QML plugin
libqupzilla-dev - development files for qupzilla's shared library
libqupzilla1 - shared library and header files for qupzilla
libreoffice - office productivity suite (metapackage)
libsession-storage-secure-perl - module implementing a secure way to encode session data
libspork-perl - create slide presentations with Kwiki markup
libstoken1 - Software Token for cryptographic authentication - shared library
libtggraphlayout-java-doc - Javadoc generated API for libtggraphlayout-java
libtk-pod-perl - Tk Pod browser widget with hypertext capability
libtyxml-ocaml - typed XML in OCaml (plugins)
libtyxml-ocaml-dev - typed XML in OCaml (development files)
libtyxml-ocaml-doc - typed XML in OCaml (documentation)
libv8-3.14-dbg - V8 JavaScript engine - debugging symbols
libv8-3.14-dev - V8 JavaScript engine - development files for 3.14 branch
libv8-3.14.5 - V8 JavaScript engine - runtime library
libv8-dev - V8 JavaScript engine - development files for latest branch
libweb-id-perl - implementation of WebID (a.k.a. FOAF+SSL)
libwine-gecko-2.21 - Windows API implementation - web browser module
libwine-gecko-dbg-2.21 - Windows API implementation - web browser debug build
libwww-mechanize-shell-perl - interactive shell for WWW::Mechanize
libwwwbrowser-perl - Platform independent means to start a WWW browser
libwx-perl-datawalker-perl - Perl data structure browser
libwxsmithlib-dev - wxSmith development files (Code::Blocks plugin for RAD GUI editing)
libwxsmithlib0 - wxSmith shared library (Code::Blocks plugin for RAD GUI editing)
libxfce4util-dev - Development files for libxfce4util6
libxfcegui4-dev - Development files for libxfcegui4-4
libxfconf-0-dev - Development files for libxfconf
lightdm-remote-session-uccsconfigure - Session and configuration to login to configure UCCS
lightspark - High-performance SWF player (experimental)
lightspark-dbg - High-performance SWF player (experimental) - Debug symbols
links - Web browser running in text mode
links2 - Web browser running in both graphics and text mode
luakit - fast and small web browser extensible by Lua
man2html - browse man pages in your web browser
maptransfer - upload/download maps to/from a VALVe game server (Client)
maptransfer-server - upload/download maps to/from a VALVe game server (Server)
matchbox-desktop - desktop application launcher for resource-limited systems
mediatomb - UPnP MediaServer (main package)
midori - fast, lightweight graphical web browser
midori-dbg - fast, lightweight graphical web browser (debug symbols)
mldonkey-server - Door to the 'donkey' network
monit - utility for monitoring and managing daemons or similar programs
monodevelop - Development Environment for GNOME
monodoc-http - MonoDoc http based viewer
morla - GTK+ RDF editor
motion - V4L capture program supporting motion detection
mozilla-plugin-gnash - dummy package for renaming to browser-plugin-gnash
namebench - DNS benchmark utility
ncmpc - ncurses-based audio player
ncview - A X11 visual browser for NetCDF format files
netrik - text mode WWW browser with vi like keybindings
netsurf - Small web browser with CSS support - Transition package
netsurf-common - Small web browser with CSS support common files
netsurf-fb - Small web browser with CSS support for framebuffers
netsurf-gtk - Small web browser with CSS support for GTK
newbiedoc - Debian documentation FOR newbies BY newbies
nginx-extras - nginx web/proxy server (extended version)
nginx-full - nginx web/proxy server (standard version)
nginx-naxsi - nginx web/proxy server (version with naxsi)
ninja-build - small build system closest in spirit to Make
ninja-build-doc - documentation for ninja-build
nitrogen - wallpaper browser and changing utility for X
node-almond - minimal AMD API implementation for use in optimized browser builds
node-async - higher-order functions and common patterns for asynchronous Javascript
node-htmlparser - forgiving HTML/XML/RSS Parser in Javascript for NodeJS
node-inherits - Exposes inherits function from Node.js environment
node-jsv - extendable, fully compliant JSON schema validator for NodeJS
node-log4js - Conversion of the log4js framework to work with Node.js
node-mirror - content aggregator for NodeJS
node-node-uuid - simple, fast generation of RFC4122 UUIDs - Node module
node-requirejs - JavaScript file and module loader
node-topcube - spawn a child webkit window from Node.js
node-underscore - JavaScript's functional programming helper library - NodeJS
node-underscore.logger - cross-browser and Node empowered logging - Node module
node-xmlhttprequest - XMLHttpRequest for Node
nova-consoleauth - OpenStack Compute - Console Authenticator
novnc - HTML5 VNC client - daemon and programs
ntop - display network usage in web browser
ntop-data - display network usage in a web browser (data files)
ntop-dbg - display network usage in web browser (debug symbols)
octave-vrml - VRML functions for Octave
op-panel - switchboard type application for the Asterisk PBX
oxideqmlscene - Web browser engine library for Qt (QML application runner)
password-gorilla - cross-platform password manager
perl-doc-html - Perl documentation suitable for viewing with a web browser
pgn2web - convert PGN chess game files into webpages
photon - a static HTML gallery generator
php-horde-browser - Horde Browser API
php-horde-groupware - Horde Groupware
php-horde-trean - Web-based bookmarks application
php-horde-webmail - Horde Groupware Webmail Edition
phpldapadmin - web based interface for administering LDAP servers
phpunit-selenium - Selenium RC integration for PHPUnit
pilot - Simple file browser from Alpine, a text-based email client
pinfo - An alternative info-file viewer
plasma-active-webbrowser - web browser for the KDE Plasma Active workspace
plasma-runners-addons - additional runners for Plasma and Krunner
plotdrop - A minimal GNOME frontend to GNUPlot
podbrowser - Documentation browser for Perl
poedit - gettext catalog editor
poedit-dbg - gettext catalog editor (debug)
pop3browser - Allows to check a pop3 mailbox before downloading any mail
postgresql-autodoc - Utility to create a PostgreSQL database schema overview in HTML, DOT and XML
prank - Probabilistic Alignment Kit for DNA, codon and amino-acid sequences
proxytrack - Build HTTP Caches using archived websites copied by HTTrack
psensor-server - Psensor server for monitoring hardware sensors remotely
pycode-browser - environment to teach with Python code snippets
pykaraoke - free CDG/MIDI/MPEG karaoke player
pyneighborhood - PyGTK2 SAMBA browser
pypibrowser - graphical interface for browsing the Python Package Index
pysolfc - collection of more than 1000 solitaire card games
python-albatross - Toolkit for Stateful Web Applications
python-albatross-doc - documentation for the Albatross Web Toolkit
python-bleach - whitelist-based HTML-sanitizing library
python-django-localeurl - Django application allows the language be set in the URL
python-django-tinymce - replacement text widget for Django web framework
python-django-websocket - Websocket support for django
python-gtk-gnash - GNU Shockwave Flash (SWF) player - Python bindings
python-htseq - high-throughput genome sequencing read analysis utilities
python-livereload - Refresh the browser automatically when a file has been updated
python-livereload-doc - Refresh the browser automatically when a file has been updated (documentation)
python-mechanize - stateful programmatic web browsing
python-nevow - Web application templating system for Python and Twisted
python-novnc - HTML5 VNC client - libraries
python-pacparser - Python module to parse proxy auto-config files
python-publicsuffix - get a public suffix for a domain name using the Public Suffix List
python-socketio - Socket.IO server based on the gevent pywsgi server
python-socketio-doc - documentation for gevent-socketio
python-sockjs-tornado - server side counterpart of SockJS-client browser library - Python 2.x
python-txws - Python module to add Websocket support to the Twisted framework
python-w3lib - Collection of web-related functions for Python (Python 2)
python-webflash - Portable flash messages for Python WSGI applications
python-webkit - WebKit/Gtk Python bindings
python-webkit-dev - WebKit/Gtk Python bindings: development files
python-weboob-core - Weboob, Web Out Of Browsers - core library
python-websocket - WebSocket client library for python
python-webunit - Unit testing for web apps with code that acts like a web browser.
python-wsgilog - WSGI logging and event reporting middleware
python-zope.app.exception - Zope 3 exception views
python-zope.app.principalannotation - Bootstrap subscriber and add menu item for zope.principalannotation
python-zope.app.publisher - Zope 3 views, resources and menus
python-zope.app.security - ZMI Views For Zope3 Security Components
python-zope.browser - Shared Zope Toolkit browser components
python-zope.browsermenu - Browser menu implementation for Zope
python-zope.browserpage - ZCML directives for configuring browser views for Zope
python-zope.browserresource - Browser resources implementation for Zope
python-zope.ptresource - Page template resource plugin for zope.browserresource
python-zope.publisher - Zope publisher publishes Python objects on the web
python-zope.testbrowser - Programmable browser for functional black-box tests
python3-html5lib - HTML parser/tokenizer based on the WHATWG HTML5 specification (Python 3)
python3-sockjs-tornado - server side counterpart of SockJS-client browser library - Python 3.x
python3-w3lib - Collection of web-related functions for Python (Python 3)
pyvnc2swf - screen recording tool with Flash (SWF) output
qasconfig - ALSA configuration browser
qashctl - mixer for ALSA's High level Control Interface
qasmixer - ALSA mixer for the desktop
qastools-common - QasTools common files
qbzr - Graphical interface for Bazaar using the Qt toolkit
qmmp - feature-rich audio player with support of many formats
qupzilla - lightweight web browser based on libqtwebkit
r-base-html - GNU R html docs for statistical computing system functions
r-bioc-genomicfeatures - GNU R tools for making and manipulating transcript centric annotations
r-bioc-hilbertvis - GNU R package to visualise long vector data
r-bioc-rtracklayer - GNU R interface to genome browsers and their annotation tracks
rebuildd - build daemon aiming at rebuilding Debian packages
rekonq - KDE web browser based on Webkit
remuco-gmusicbrowser - duplex remote control for media players - gmusicbrowser adapter
rhythmbox-radio-browser - Internet radio browser plugin for rhythmbox
roundcube - skinnable AJAX based webmail solution for IMAP servers - metapackage
roundcube-core - skinnable AJAX based webmail solution for IMAP servers
roundcube-plugins - skinnable AJAX based webmail solution for IMAP servers - plugins
roundcube-plugins-extra - skinnable AJAX based webmail solution - extra plugins
ruby-bcat - pipe to browser utility
ruby-http-accept-language - Ruby library that finds out which locale the user prefers
ruby-http-cookie - Ruby library to handle HTTP Cookies based on RFC 6265
ruby-multipart-post - multipart form post accessory for Net::HTTP
ruby-rchardet - Character encoding auto-detection for Ruby
ruby-upr - Upload Progress for Rack
sbcl-source - Source code files for SBCL
scribus-doc - non-free documentation for Scribus
scribus-ng-doc - non-free documentation for Developmental Scribus branch
semanticscuttle - Self-hosted and web-based social bookmark manager
shellinabox - publish command line shell through AJAX interface
sipdialer - reSIProcate SIP stack - click-to-call utility
sipml5-web-phone - Basic SIP video-phone web page based on WebRTC
smb2www - SMB/CIFS network client with a web interface
smb4k - Samba (SMB) share advanced browser for KDE
smbc - samba-commander - curses based samba network browser
smtube - YouTube videos browser
sozi - inkscape extension for creating animated presentations
spe - Stani's Python Editor
spice-html5 - Spice Web client which runs entirely within a modern browser
sql-ledger - Web based double-entry accounting program
sqlitebrowser - GUI editor for SQLite databases
squid-cgi - Full featured Web Proxy cache (HTTP proxy) - control CGI
squirrelmail - Webmail for nuts
squirrelmail-quicksave - SquirrelMail plugin: Auto-save messages while composing
streamtuner2 - Browser for Internet Radio Stations
subcommander - Graphical client for Subversion
subcommander-doc - User guide for subcommander
sugar-browse-activity - web browsing activity for the Sugar graphical shell
sugar-firefox-activity - Mozilla Firefox browser for the Sugar desktop
surf - simple web browser
surfraw - fast unix command line interface to WWW
surfraw-extra - extra surfraw search tools with heavy dependencies
sweeper - history and temporary file cleaner
swfdec-mozilla - dummy package for transition to browser-plugin-gnash
tdfsb - 3D filesystem browser
tea - graphical text editor with syntax highlighting
telegnome - graphical teletext viewer
telepathy-specification - Telepathy D-Bus specification
tickr - GTK-based highly graphically-customizable Feed Ticker
tig - ncurses-based Git repository browser
tinymce - platform independent web based Javascript/HTML WYSIWYG editor
tkcvs - Graphical front-end to CVS and Subversion
tkdesk - Tk/tcl based X11 Desktop/File manager
tkinfo - Tcl/Tk Info browser
tkmib - SNMP (Simple Network Management Protocol) MIB browser
tor - anonymizing overlay network for TCP
tora - graphical toolkit for database developers and administrators
tora-dbg - graphical toolkit for database developers and administrators - debugging symbols
torrentflux - web based, feature-rich BitTorrent download manager
trac-graphviz - Graphs printing plugin for Trac
tribler - Python based Bittorrent/Internet TV application
tt-rss - Tiny Tiny RSS - web-based news feed (RSS/Atom) aggregator
ttb - (Dutch) teletekst browser for the desktop
turses - Twitter client for the console
ubuntu-kylin-docs - Ubuntu Kylin Desktop Guide
ubuntu-online-tour - Experience Ubuntu in your web browser
unburden-home-dir - Remove or move cache files automatically from user's home
unhtml - Remove the markup tags from an HTML file
unity-chromium-extension - Unity WebApp extension for the chromium browser
unixodbc-bin - Graphical tools for ODBC management and browsing
urlview - Extracts URLs from text
uzbl - Lightweight Webkit browser following the UNIX philosophy
vdetelweb - Telnet and Web interface for VDE 2.x
vidalia - controller GUI for Tor
view3dscene - VRML / X3D browser, and a viewer for other 3D model formats
viewvc - web interface for CVS and/or Subversion repositories
viewvc-query - utility to query CVS and Subversion commit database
vim-scripts - plugins for vim, adding bells and whistles
vokoscreen - easy to use screencast creator
vuze - Multimedia BitTorrent client
w3m-el - simple Emacs interface of w3m
w3m-el-snapshot - simple Emacs interface of w3m (development version)
wapua - Web browser for WAP WML pages
web2ldap - Full-featured web-based LDAPv3 client
webalizer - web server log analysis program
webbrowser-app-autopilot - Ubuntu web browser autopilot tests
webdruid - Web server log file analysis tool
webhttrack - Copy websites to your computer, httrack with a Web interface
widemargin - bible reading and study application
wikipedia2text - displays Wikipedia articles on the command line
woof - share files through HTTP protocol
wulf2html - filter for generating HTML logs from wulflogger data
wxmaxima - GUI for the computer algebra system Maxima
wysihtml-el - Almost real-time previewing system for HTML and DocBook
x2goplugin - X2Go Client (Qt4) as browser plugin
xemacs21 - highly customizable text editor
xemacs21-bin - highly customizable text editor -- support binaries
xemacs21-gnome-mule - highly customizable text editor -- transitional package
xemacs21-gnome-mule-canna-wnn - highly customizable text editor -- transitional package
xemacs21-gnome-nomule - highly customizable text editor -- transitional package
xemacs21-mule - highly customizable text editor -- Mule binary
xemacs21-mule-canna-wnn - highly customizable text editor -- Mule binary compiled with Canna and Wnn
xemacs21-nomule - highly customizable text editor -- Non-mule binary
xemacs21-support - highly customizable text editor -- architecture independent support files
xemacs21-supportel - highly customizable text editor -- non-required library files
xenwatch - Virtualization utilities, mostly for Xen
xfce4-dict - Dictionary plugin for Xfce4 panel
xfonts-kapl - APL fonts for A+ development
xine-plugin - xine-based media player plugin for Mozilla browsers
xjed - editor for programmers (x11 version)
xmotd - a message of the day browser for X
xqf - X-based Quake Server Browser
xubuntu-docs - xubuntu documentation
xul-ext-deejayd-webui - Deejayd web user interface XUL extension
xul-ext-y-u-no-validate - browser extension to make security exceptions temporary by default
xxxterm - Minimalist's web browser
yarssr - RSS reader for the notification area
yorick-doc - documentation for the Yorick interpreted language
youtranslate - graphical translator which makes use of online services
zescrow-client - back up eCryptfs Encrypted Home or Encrypted Private Configuration
zeya - web music server
liboxideqtcore0 - Web browser engine library for Qt (core library and components)
liboxideqtquick0 - Web browser engine library for Qt (QtQuick library)
oxideqt-chromedriver - Web browser engine library for Qt (chromedriver build)
python-html5lib-whl - HTML parser/tokenizer based on the WHATWG HTML5 specification
python-requests-whl - elegant and simple HTTP library for Python, built for human beings
xul-ext-ubufox - Ubuntu modifications for Firefox
chromium-browser - Chromium web browser, open-source version of Chrome
chromium-browser-l10n - chromium-browser language packages
chromium-codecs-ffmpeg - Free ffmpeg codecs for the Chromium Browser
chromium-codecs-ffmpeg-extra - Extra ffmpeg codecs for the Chromium Browser

```

or simply launch Ubuntu Software Center at your left menubar/taskbar.

Thanks.

---

### Post by Bucky Ball on 2015-08-31
Software and Updates> Other Software tab> Tick 'Canonical Partners' and 'Independent' (don't check the 'source' repos: you don't need them). On the 'Ubuntu Software' tab tick 'Proprietary drivers for devices'. That's it.

---

### Post by grahammechanical on 2015-08-31
Ticking the box "Install third party software" will install third party also called proprietary audio and video codecs. It will also install a proprietary video driver. We can install all these things after the installation is complete.

InterProg has shown you how to install Ubuntu Restricted Extras from the command line. The package is also in the Ubuntu software Centre.

To install a proprietary video driver go to System Settings>Software & Updates>Additional drivers tab. You will need to be connected to the internet and to give the utility time to do its search. You should be offered a selection of 4 drivers.

Then you will have everything that you would have received if you had ticked the box "Install third party software."

Regards.

---

