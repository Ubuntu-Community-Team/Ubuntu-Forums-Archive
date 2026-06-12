---
title: "Upgrade problems..."
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by DarkDancer on 2006-06-20
(I'm in Breezy btw)

Ok, I went to the Update magager, which said that "New distribution release 'dapper' is available". I hit the Upgrade button and the upgrade begins, but then gives me the error:

> Invalid package information

After your package information was updated the essential package 'ubuntu-base' can not be found anymore.
This indicates a serious error, please report this as a bug.

I did a search here for "Invalid package information" and found this post:

[http://ubuntuforums.org/showthread.php?t=189461&highlight=invalid+package+information](http://ubuntuforums.org/showthread.php?t=189461&highlight=invalid+package+information)

I changed (as per the post) all the references in /etc/apt/sources.list from breezy to dapper and ran synaptec, it did a lot of things getting packages, removing them, then finished. I rebooted and checked Update Manager again to see if the upgrade message for dapper was still there.First (after doing the system check, it says:

Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

Here's a copy of my sources.list.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

What should I do next?

The following updates will be skipped:
3ddesktop
amule
amule-utils
audacity
beep-media-player
beep-media-player-dev
dvdauthor
easytag
firestarter
gdesklets
gftp
gftp-text
gnomebaker
gstreamer0.8-a52dec
gstreamer0.8-aa
gstreamer0.8-alsa
gstreamer0.8-artsd
gstreamer0.8-audiofile
gstreamer0.8-caca
gstreamer0.8-cdio
gstreamer0.8-cdparanoia
gstreamer0.8-dv
gstreamer0.8-dvd
gstreamer0.8-esd
gstreamer0.8-faac
gstreamer0.8-faad
gstreamer0.8-festival
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
gstreamer0.8-plugin-apps
gstreamer0.8-sdl
gstreamer0.8-sid
gstreamer0.8-speex
gstreamer0.8-swfdec
gstreamer0.8-theora
gstreamer0.8-tools
gstreamer0.8-vorbis
gstreamer0.8-x
ifrename
jpilot
kinoplus
libdirectfb-0.9-22
libfaac0
libgnutls11
libgstreamer-gconf0.8-0
libgstreamer-plugins0.8-0
libgstreamer0.8-0
libgtk-perl
libgtk-pixbuf-perl
libmp4v2-0
libmysqlclient14
libneon24
libopenal0
libreadline4
libswfdec0.3
libvcdinfo0
libwxgtk2.4-1
libwxgtk2.6-0
libxine1c2
mencoder-586
menu
mjpegtools
python-gst
python-wxgtk2.6
rar
sox
streamtuner
totem-xine
transcode
vcdimager
vlc
vlc-plugin-arts
wxvlc
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-calcomp
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

If I tell that to close, the message about the new dstribution Dapper is still there, and if I try to upgrade from there, the same thing happens as the first time.

---

### Post by DarkDancer on 2006-06-20
Here's a copy of my sources.list.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by wbmj on 2006-06-20
It looks to me like you're missing the main and restricted repositories

---

### Post by DarkDancer on 2006-06-20
Ok, how do I fix it?

---

### Post by DarkDancer on 2006-06-20
Wait, I think I figured it out........... back in a bit.

---

### Post by SpacePony on 2006-06-20
Did you try doing the > Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely. stuff?

For what it's worth, this is my sources.list contents:

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release Candidate i386 (20060525)]/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.


## All officially supported packages, including security- and other updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

---

### Post by DarkDancer on 2006-06-20
WEee! I am Dappered, unfortunately I am in 640 x 480 and stuc there...everything is HUGE! ;)

---

