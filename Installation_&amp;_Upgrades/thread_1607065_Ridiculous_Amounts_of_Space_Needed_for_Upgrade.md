---
title: "Ridiculous Amounts of Space Needed for Upgrade?"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by genjix on 2010-10-27
When I first installed Kubuntu, I asked around how much space would be needed for /. The consensus was that generally around 3 GB should be enough. I tripled that to be sure to 10 GB.

Now I want to upgrade to maverick df shows I'm using 8 GB of 10 GB, and the upgrade claims to need a further 1.5 GB on top of the 2 GB free (I don't have enough space). WTF FOR???

6GB of that is in usr, although not in any one particular package. Why is it requiring so much excessive hard-disk space? This is just dumb. I have no idea what is hogging all those 8 GB as I just have vanilla KDE and a few programs installed.

> genjix@l:/usr$ du -sh
6.1G    .
genjix@l:/usr$ du -sh *
441M    bin
4.0K    games
155M    include
1.9G    lib
278M    lib32
0       lib64
2.2M    local
39M     sbin
2.9G    share
423M    src
genjix@l:/usr$ du -sh share/* | grep -i G|M
M: command not found
genjix@l:/usr$ du -sh share/* | grep -i "G|M"
genjix@l:/usr$ du -sh share/* | egrep -i "G|M"
25M     share/app-install
36K     share/application-registry
16M     share/apps
2.2M    share/aptitude
1.4M    share/asymptote
1.7M    share/autoconf
1008K   share/automake-1.11
972K    share/awesome
20K     share/binfmts
8.0K    share/binfmt-support
6.9M    share/blender
1.1M    share/bug
18M     share/calibre
728K    share/cli-common
16K     share/cmake
3.0M    share/cmake-2.8
1.1M    share/color
2.4M    share/command-not-found
192K    share/common-licenses
48K     share/computerjanitor
8.0K    share/config.kcfg
1.3M    share/consolefonts
13M     share/cups
208K    share/defoma
16K     share/dictionaries-common
1.1G    share/doc
20K     share/dpkg
8.0K    share/e2fsprogs
62M     share/emacs
2.4M    share/emacs23
348K    share/emoticons
68K     share/ffmpeg
2.3M    share/file
120M    share/fonts
1.5M    share/foo2qpdl
1.8M    share/foo2zjs
109M    share/foomatic
1.8M    share/gccxml-0.9
312K    share/gconf
48K     share/gcr0
72K     share/gdb
24K     share/gdebi
1.3M    share/GeoIP
1.6M    share/gettext
2.9M    share/ghostscript
6.2M    share/gimp
5.3M    share/gir-1.0
72K     share/git-core
8.0K    share/gksu
44K     share/glade3
52K     share/glib-2.0
5.9M    share/gnome
20K     share/gnome-2.0
16K     share/gnome-control-center
52K     share/gnome-keyring
16K     share/gnupg
244K    share/GNUstep
140K    share/graphviz
1.6M    share/groff
2.9M    share/grub
620K    share/gtk-doc
1.8M    share/guile
5.3M    share/gutenprint
96K     share/gvfs
1.6M    share/hal
13M     share/hplip
22M     share/i18n
152M    share/icons
6.6M    share/idl
172K    share/ImageMagick-6.5.7
4.0K    share/im-switch
7.1M    share/info
224K    share/initramfs-tools
48M     share/inkscape
3.6M    share/irssi
1.9M    share/javazi
110M    share/kde4
16K     share/keyrings
412K    share/kubuntu-default-settings
88K     share/language-selector
44K     share/language-support
2.3M    share/latex2html
52K     share/launchpad-integration
28K     share/libgksu
736K    share/libgphoto2
32K     share/libparse-debianchangelog-perl
1.1M    share/libtool
20K     share/lighttpd
6.4M    share/lilypond
1.2M    share/lintian
15M     share/lmms
70M     share/locale
12M     share/locale-langpack
27M     share/lyx
7.0M    share/m17n
228K    share/macchanger
45M     share/man
12K     share/man-db
324K    share/menu
868K    share/mercurial
5.0M    share/mime
2.0M    share/mime-info
12K     share/mimelink
1.6M    share/mimelnk
288K    share/minitube
448K    share/misc
3.5M    share/mlt
8.0K    share/mono
48K     share/mono-1.0
12K     share/mozilla
16K     share/mplayer
136K    share/myspell
2.3M    share/mysql
16K     share/mysql-common
20K     share/netpbm
20K     share/notification-daemon
8.0K    share/nvidia-common
116K    share/omf
640K    share/ontology
48K     share/OpenGTL
6.2M    share/openoffice
760K    share/org-mode
184K    share/PackageKit
44K     share/pam
24K     share/pam-configs
24M     share/perl
5.6M    share/perl5
560K    share/pixmaps
56K     share/pkgconfig
144K    share/pkg-kde-tools
24K     share/pnm2ppa
308K    share/poker-engine
47M     share/ppd
83M     share/pyshared
79M     share/qt4
44K     share/recovery-mode
45M     share/ri
256K    share/roxterm
8.0K    share/rsyslog
380K    share/samba
1.1M    share/sgml
16K     share/sgml-base
12K     share/sgml-data
7.5M    share/skype
2.2M    share/snmp
3.6M    share/sounds
1.7M    share/speedcrunch
452K    share/strigi
3.7M    share/swig1.3
1.2M    share/synaptic
652K    share/system-config-printer
14M     share/tcltk
152K    share/templates
56K     share/terminfo
256K    share/tex-common
139M    share/texmf
146M    share/texmf-texlive
100K    share/themes
12K     share/unattended-upgrades
252K    share/update-manager
16K     share/util-macros
24M     share/vim
9.5M    share/virtualbox
1.9M    share/vlc
44K     share/w3m
104M    share/wallpapers
2.5M    share/webkit-1.0
8.7M    share/wine
12M     share/wireshark
5.5M    share/X11
60K     share/xemacs
1.1M    share/xine
7.5M    share/xml
12K     share/xml-core
12K     share/xserver-xorg
6.1M    share/zoneinfo


This really annoys me, as when I wanted to install I specifically asked many people on the [forums]("http://ubuntuforums.org/showthread.php?t=1416807"), on IRC and in real life.

Any suggestions?

---

### Post by Mark Phelps on 2010-10-27
Sorry I can't answer your question with specifics, but in general, any installer or major upgrade action needs to install interim files and software on the machine -- which you will notice when, during the end of the installation/upgrade it often displays some text along the lines of "cleaning up temporary files" -- or something like that.

And while, I wouldn't have guessed that such TEMP space would amount to 1.5GB, I also wouldn't be terribly surprised if it did.

---

