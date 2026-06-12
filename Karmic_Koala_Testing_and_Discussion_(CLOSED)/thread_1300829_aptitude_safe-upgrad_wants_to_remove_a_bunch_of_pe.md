---
title: "aptitude safe-upgrad wants to remove a bunch of perl related packages"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by viper8 on 2009-10-25
I clean installed Karmic-RC.  Now I go to get some updates and aptitude  is wanting to remove a bunch of perl related packages...any ideas?  

FYI, using Update Manager it doesn't mention that it will remove packages, but how will it behave if I choose "Install Updates"?  I use command line 100% of the time for updates 100% of the time so I'm not too familiar with Update Manager.

I have perl 5.10.0-24ubuntu4 installed.



# aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be **REMOVED**:
  libarchive-zip-perl{u} libclass-methodmaker-perl{u} libclass-singleton-perl{u} libconvert-binhex-perl{u} libcrypt-ssleay-perl{u} libdate-manip-perl{u} libdatetime-format-strptime-perl{u} libdatetime-locale-perl{u} libdatetime-perl{u} libdatetime-timezone-perl{u} libdigest-hmac-perl{u} libdigest-sha1-perl{u} libemail-address-perl{u} libemail-find-perl{u} libemail-valid-perl{u} libexporter-lite-perl{u} libfcgi-perl{u} libfile-slurp-perl{u} libhtml-fromtext-perl{u} libhtml-tableextract-perl{u} libhttp-cache-transparent-perl{u} libhttp-response-encoding-perl{u} libhttp-server-simple-perl{u} libio-socket-ssl-perl{u} libio-stringy-perl{u} liblingua-preferred-perl{u} liblist-coreutils-perl{u} liblog-tracemessages-perl{u} libmime-tools-perl{u} libnet-dns-perl{u} libnet-domain-tld-perl{u} libnet-ip-perl{u} libnet-libidn-perl{u} libnet-ssleay-perl{u} libossp-uuid-perl{u} libossp-uuid15{u} libparams-validate-perl{u} libregexp-common-perl{u} libsoap-lite-perl{u} libterm-progressbar-perl{u} libtext-bidi-perl{u} libunicode-string-perl{u} libwww-mechanize-perl{u} libxml-dom-perl{u} libxml-libxml-common-perl{u} libxml-libxml-perl{u} libxml-libxslt-perl{u} libxml-namespacesupport-perl{u} libxml-perl{u} libxml-regexp-perl{u} libxml-sax-expat-perl{u} libxml-sax-perl{u} 
The following packages will be **upgraded**:
  apport apport-gtk bsdutils compiz-fusion-plugins-extra couchdb-bin dbus dbus-x11 desktopcouch devicekit-disks e2fslibs e2fsprogs evolution-couchdb friendly-recovery gettext-base gnome-about  gnome-desktop-data gnome-session gnome-session-bin gnome-system-tools gnome-utils grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x ia32-libs language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-selector language-selector-common libblkid1 libcairomm-1.0-1 libcomerr2 libcwidget3 libdbus-1-3 libdjvulibre-text libdjvulibre21 libept0 libexempi3 libgdict-1.0-6 libgmp3c2 libgnome-desktop-2-11 libgnome2-0 libgnome2-common libgstreamer-plugins-base0.10-0 libhunspell-1.2-0 libicu40 libilmbase6 libmp3lame0 libnautilus-extension1 libopenexr6 libpangomm-1.4-1 libpoppler-glib4 libpoppler5 libprotobuf3 librarian0 libsoup-gnome2.4-1 libsoup2.4-1 libss2 libtag1-vanilla libtag1c2a libuuid1 libxapian15 mail-notification memtest86+ mount nautilus nautilus-data ntpdate openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer openssh-client poppler-utils  protobuf-compiler python-apport python-apt python-desktopcouch python-desktopcouch-records python-problem-report python-protobuf python-uno python-xapian rarian-compat ssh-askpass-gnome tasksel tasksel-data telepathy-butterfly ttf-opensymbol tzdata uno-libs3 update-manager update-manager-core ure usb-creator-common usb-creator-gtk util-linux uuid-runtime xserver-xorg-input-vmmouse 
The following packages are RECOMMENDED but will NOT be installed:
  xfonts-mathml 
111 packages upgraded, 0 newly installed, 52 to remove and 0 not upgraded.
Need to get 129MB/129MB of archives. After unpacking 50.4MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

I guess I'm just concerned that if I do go ahead and let it remove the packages that it will break some functionality that requires them...so what do you think?

---

### Post by dino99 on 2009-10-25
well, i don't see any important in the "removed", so let's go. Is your distro a fresh install or an dist-upgrade ? these perl links let me think about dev development or debugging. sources installed ?

Do it & at end run a install -f

---

