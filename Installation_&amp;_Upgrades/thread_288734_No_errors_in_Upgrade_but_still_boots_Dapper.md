---
title: "No errors in Upgrade but still boots Dapper"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Alf Stockton on 2006-10-30
I have used :-
sudo sed -e ’s/\sdapper/ edgy/g’ -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg –configure -a

and a reboot but cannot see any differences.

to upgrade to edgy and was not aware of any errors but on reboot I am still in Dapper. Why?

---

### Post by Sef on 2006-10-30
Try this:

System > Administration > Update Manager

then click on install Edgy (upper right.)

or 

command line: ```
gksu "update-manager -c"

```

For more info: [Edgy Release Notes]("https://wiki.ubuntu.com/EdgyReleaseNotes").

---

### Post by Alf Stockton on 2006-10-30
I had tried that but it appears to make no difference. I do however, when trying your suggestion, get a message "Cannot install all available updates" and I get a list of applications that cannot be updated :-
acroread
acroread-plugins
bluefish
bluez-pcmcia-support
bzflag
cupsys-driver-gimpprint
dpkg-dev
efax
efax-gtk
ethereal-common
ffmpeg
foomatic-db-gimp-print
foomatic-db-gutenprint
gdk-imlib11
gfax
gkrellm
gok
gstreamer-tools
gstreamer0.10-ffmpeg
gstreamer0.10-gl
gstreamer0.10-gnonlin
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-dbg
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-sdl
gstreamer0.8-a52dec
gstreamer0.8-aa
gstreamer0.8-alsa
gstreamer0.8-artsd
gstreamer0.8-audiofile
gstreamer0.8-caca
gstreamer0.8-cdio
gstreamer0.8-cdparanoia
gstreamer0.8-dirac
gstreamer0.8-dv
gstreamer0.8-dvd
gstreamer0.8-esd
gstreamer0.8-faac
gstreamer0.8-faad
gstreamer0.8-festival
gstreamer0.8-ffmpeg
gstreamer0.8-flac
gstreamer0.8-gnomevfs
gstreamer0.8-gsm
gstreamer0.8-gtk
gstreamer0.8-hermes
gstreamer0.8-jpeg
gstreamer0.8-lame
gstreamer0.8-mad
gstreamer0.8-mikmod
gstreamer0.8-misc
gstreamer0.8-mms
gstreamer0.8-mpeg2dec
gstreamer0.8-musepack
gstreamer0.8-oss
gstreamer0.8-sdl
gstreamer0.8-sid
gstreamer0.8-speex
gstreamer0.8-swfdec
gstreamer0.8-theora
gstreamer0.8-tools
gstreamer0.8-vorbis
gstreamer0.8-x
gtk2-engines-clearlooks
gtk2-engines-crux
gtk2-engines-highcontrast
gtk2-engines-industrial
gtk2-engines-lighthouseblue
gtk2-engines-mist
gtk2-engines-pixbuf
gtk2-engines-redmond95
gtk2-engines-smooth
gtk2-engines-thinice
gxineplugin
hermes1
hylafax-client
ifplugd
ijsgimpprint
ijsgutenprint
jpilot
jpilot-backup
jpilot-plugins
kismet
lame
liba52-0.7.4
libart2
libc6-dev
libcompfaceg1
libdb1-compat
libdvbpsi4
libdvdread3
libgdchart-gd1-noxpm
libggi2
libglide2
libgnorbagtk0
libgnujaxp-jni
libgnutls12
libgstreamer-gconf0.8-0
libgstreamer-plugins0.8-0
libgstreamer0.8-0
libgtksourceview2.0-cil
libjack0.100.0-0
liblame0
libmjpegtools0c2a
libmms0
libnetcdf3
libsigc++-1.2-5c2
libsmjs1
libssl0.9.7
libswfdec0.3
libtasn1-2
libtasn1-2-dev
libvcdinfo0
libwxgtk2.4-1
libwxgtk2.6-0
libxine-extracodecs
libxine-main1
libxosd2
libxvidcore4
mjpegtools
monodevelop
mplayer
pcmcia-cs
pilot-link
python-gadfly
python-gst
python-htmltmpl
python-kjbuckets
python-netcdf
python-osd
python-parted
python-pgsql
python-soappy
python-stats
python-syck
sane-utils
timidity
timidity-interfaces-extra
totem-xine
vlc
wpagui
x-window-system-core
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-calcomp
xserver-xorg-input-citron
xserver-xorg-input-digitaledge
xserver-xorg-input-dmc
xserver-xorg-input-dynapro
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
xsupplicant
xtightvncviewer

---

