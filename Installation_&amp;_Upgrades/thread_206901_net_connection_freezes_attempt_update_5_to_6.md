---
title: "net connection freezes attempt update 5 to 6"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by john_spiral on 2006-06-30
Hi,

I'm posting this from a now working connection (ADSL USB) connection (ubuntu 5). If I attempt to update from ubuntu 5 to 6 via the Update Manager my connection freezes and I need to unplug and replug my modem (BT Voyager 105) looks like the upgrade database , if there is such a thing, is corrupt.

I had the same problem attempting the update via a shell.

I'm dialling up with the eciadsl (linux usb adsl modem connection software) tool via the shell.

any ideas?

---

### Post by john_spiral on 2006-07-01
More info:

If I click the update icon near the clock, it analyses my system and give me the following message

**Cannot install all available updates.**

Some updates require the removal of futher software. Use the  function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

**The following updates will be skipped:**

[FONT="Arial Narrow"]acpi-support
apt
apt-utils
aptitude
aspell
base-files
bc
bind9-host
bluez-pcmcia-support
bluez-pin
bluez-utils
bsh
bug-buddy
capplets-data
contact-lookup-applet
coreutils
cpp
cpp-4.0
cron
cupsys
cupsys-bsd
cupsys-client
cupsys-driver-gimpprint
dbus
dbus-1-utils
dmsetup
dnsutils
dpkg
dselect
dvd+rw-tools
eject
eog
evince
evolution
evolution-data-server
evolution-exchange
evolution-plugins
evolution-webcal
fetchmail
file-roller
firefox
firefox-gnome-support
fontconfig
foomatic-db-gimp-print
g++
g++-4.0
gaim
gaim-data
gcalctool
gcc
gcc-4.0
gcc-4.0-base
gconf-editor
gconf2
gdb
gdm
gedit
gedit-common
gij
gij-4.0
gksu
gnome-about
gnome-app-install
gnome-applets
gnome-applets-data
gnome-btdownload
gnome-control-center
gnome-cups-manager
gnome-doc-utils
gnome-games
gnome-games-data
gnome-media
gnome-menus
gnome-netstatus-applet
gnome-nettool
gnome-panel
gnome-panel-data
gnome-pilot
gnome-pilot-conduits
gnome-session
gnome-spell
gnome-system-monitor
gnome-system-tools
gnome-terminal
gnome-terminal-data
gnome-utils
gnome-volume-manager
gnupg
groff-base
gs-esp
gstreamer0.8-gnomevfs
gstreamer0.8-misc
gstreamer0.8-vorbis
gthumb
gtkhtml3.8
gucharmap
guile-1.6-libs
hal
hal-device-manager
hpijs
hplip-data
hplip-ppds
ijsgimpprint
imake
initramfs-tools
irssi-text
java-gcj-compat
language-pack-en-base
language-pack-gnome-en-base
language-selector
language-support-en
lftp
libaspell15
libbind9-0
libbonoboui2-0
libbonoboui2-common
libc6
libc6-dev
libc6-i686
libcupsimage2
libcupsys2-gnutls10
libcurl3
libdjvulibre15
libebook1.2-5
libecal1.2-3
libedata-book1.2-2
libedata-cal1.2-1
libedataserverui1.2-6
libeel2-2
libfontenc1
libfs6
libgc1c2
libgcc1
libgcj-common
libgcj6
libgconf2-4
libgda2-3
libgda2-common
libgl1-mesa
libgl1-mesa-dri
libglu1-mesa
libgnome-desktop-2
libgnome-menu2
libgnome2-0
libgnome2-common
libgnomecups1.0-1
libgnomeprint2.2-0
libgnomeprint2.2-data
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-common
libgstreamer-gconf0.8-0
libgtkhtml3.8-15
libgucharmap4
libhal-storage1
libhal1
libice6
libidl0
libisccc0
libisccfg1
libldap2
liblpint-bonobo0
libmetacity0
libnautilus-extension1
libneon24
libopenal0
libpam-modules
libpam-runtime
libpanel-applet2-0
libpq4
libpt-plugins-alsa
libpt-plugins-v4l
libpt-plugins-v4l2
libraptor1
librasqal0
librdf0
libreadline4
libreadline5
librsvg2-2
librsvg2-common
libsasl2
libsasl2-modules
libselinux1
libsm6
libsoup2.2-8
libstdc++6
libstdc++6-4.0-dev
libx11-6
libxau6
libxaw7
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxi6
libxinerama1
libxkbfile1
libxml2-utils
libxmu6
libxmuu1
libxp6
libxpm4
libxrandr2
libxres1
libxss1
libxt6
libxtrap6
libxtst6
libxv1
libxxf86dga1
libxxf86misc1
libxxf86vm1
linux-image-386
linux-restricted-modules-386
locales
logrotate
lshw
lvm-common
lvm2
mdadm
metacity
mozilla-firefox-locale-en-gb
nautilus
nautilus-cd-burner
nautilus-sendto
notification-daemon
openoffice.org2
openoffice.org2-base
openoffice.org2-calc
openoffice.org2-draw
openoffice.org2-evolution
openoffice.org2-gnome
openoffice.org2-impress
openoffice.org2-math
openoffice.org2-writer
openssh-client
parted
pmount
python-glade2
python-gtk2
python-mysqldb
python-netcdf
python-parted
python-soappy
python-uno
python2.4
python2.4-apt
python2.4-crypto
python2.4-dbus
python2.4-examples
python2.4-gdbm
python2.4-glade2
python2.4-gnome2
python2.4-gnome2-extras
python2.4-gtk2
python2.4-id3lib
python2.4-ldap
python2.4-librdf
python2.4-minimal
python2.4-mysqldb
python2.4-pycurl
python2.4-pyopenssl
python2.4-tk
rdesktop
rhythmbox
rss-glx
samba-common
serpentine
smbclient
sound-juicer
synaptic
tcpdump
totem
totem-gstreamer
tsclient
ubuntu-artwork
ubuntu-desktop
ubuntu-minimal
ubuntu-standard
udev
update-manager
update-notifier
usplash
vim
vim-common
vino
w3m
wget
wvdial
xchat
xchat-common
xdpyinfo
xfonts-100dpi
xfonts-75dpi
xfonts-base
xfonts-scalable
xkeyboard-config
xrdb
xserver-xorg
xserver-xorg-core
xserver-xorg-driver-apm
xserver-xorg-driver-ark
xserver-xorg-driver-ati
xserver-xorg-driver-chips
xserver-xorg-driver-cirrus
xserver-xorg-driver-cyrix
xserver-xorg-driver-dummy
xserver-xorg-driver-fbdev
xserver-xorg-driver-glint
xserver-xorg-driver-i128
xserver-xorg-driver-i740
xserver-xorg-driver-i810
xserver-xorg-driver-imstt
xserver-xorg-driver-mga
xserver-xorg-driver-newport
xserver-xorg-driver-nsc
xserver-xorg-driver-nv
xserver-xorg-driver-rendition
xserver-xorg-driver-s3
xserver-xorg-driver-s3virge
xserver-xorg-driver-savage
xserver-xorg-driver-sis
xserver-xorg-driver-tdfx
xserver-xorg-driver-tga
xserver-xorg-driver-trident
xserver-xorg-driver-tseng
xserver-xorg-driver-v4l
xserver-xorg-driver-vesa
xserver-xorg-driver-vga
xserver-xorg-driver-via
xserver-xorg-driver-vmware
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-calcomp
xserver-xorg-input-digitaledge
xserver-xorg-input-dmc
xserver-xorg-input-dynapro
xserver-xorg-input-elographics
xserver-xorg-input-fpit
xserver-xorg-input-hyperpen
xserver-xorg-input-magellan
xserver-xorg-input-microtouch
xserver-xorg-input-mutouch
xserver-xorg-input-palmax
xserver-xorg-input-penmount
xserver-xorg-input-spaceorb
xserver-xorg-input-summa
xserver-xorg-input-tek4957
xserver-xorg-input-void
xserver-xorg-input-wacom
xterm
xvncviewer
yelp[/FONT]

I choose 'Install updates' and my adsl connection freezes on 
alsa-utils 80 out of 548. 

followed by the following error message:

[FONT="Arial Narrow"]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.10-1ubuntu14_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.10-1ubuntu14_i386.deb)
  Connection timed out [IP: 146.137.96.7 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.3-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.3-0ubuntu2_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.3-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.3-0ubuntu2_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.0.3-6ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.0.3-6ubuntu7_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.3-6ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.0.3-6ubuntu7_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dosfstools/dosfstools_2.11-2.1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dosfstools/dosfstools_2.11-2.1ubuntu1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3-1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext-base_0.14.5-2ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext-base_0.14.5-2ubuntu3_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grepmap/grepmap_1.1.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grepmap/grepmap_1.1.0-1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-tools/net-tools_1.60-16ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-tools/net-tools_1.60-16ubuntu2_i386.deb)
  
[/FONT]

I need to plug uplug my modem to get it working again.


running sudo apt-get dist-upgrade from the term has the connection freeze on the following stage:

Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-25-386 2.6.15-25.43 [21.6MB]
3% [6 locales 3199447/3283kB 97%] [9 linux-image-2.6.15-25-386 3199771/21.6MB 1

If I use firefox to browse the [http://security.ubuntu.com](http://security.ubuntu.com) site my connection also freezes?

I've re-installed the eciadsl dialler from source.

My connection is running fine under Win XP.

any suggestions?

---

