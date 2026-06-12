---
title: "Package List from Dapper, install into Feisty"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2007-05-04
I want to go to Feisty but would like to run this list of packages that I currently have installed in Dapper and was wondering if I simply tell aptitude to install all of these packages will there be any problems? Will aptitude take care of the dependencies and possible issues with whatever is in Feisty by default? Like should I remove gcc+ from the package list and just let build-essential take care of that (it's my understanding that when I installed build-essential, it installed a buynch of development tools?) So it's things like that that I would like some1's opinion on. Also for example, should I remove python2.4 because maybe it's not compatible with Feisty?  

Thank you for anyones help.

acroread
acroread-escript
amarok
amarok-xine
arj
audacity
avidemux
binfmt-support
binutils
bmp-docklet
build-essential
bum
cdda2wav
checkinstall
chkrootkit
clamav
clamav-base
clamav-daemon
clamav-docs
clamav-freshclam
clamtk
cpp
cpp-4.0
dar
dbus
ddrescue
debhelper
devscripts
dh-make
dpatch
dvdauthor
dvdrip
easytag
faac
faad
fakeroot
ffmpeg
g++
g++-4.0
gawk
gcc
gcc-4.0
gcontrol
gdb
gdk-imlib1
gdk-imlib1
gnome-bin
gnome-libs-data
gnome-main-menu
gnomebaker
gparted
gpgp
gtk-sharp2
gtk-sharp2-examples
gtk-sharp2-gapi
gtk2-engines-pixbuf
hddtemp
html2text
iftop
imagemagick
imlib-base
iptraf
kakasi-dic
kamera
kcontrol
kdebase-bin
kdebase-data
kdebase-kio-plugins
kdelibs-bin
kdelibs-data
kdelibs4c2a
kdemultimedia-kio-plugins
kdesktop
kernel-package
kicker
kino
lame
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
lha
lockfile-progs
logcheck
logcheck-database
logtail
mailx
make
mencoder
mencoder-386
menu
menu-xdg
mesa-utils
mjpegtools
module-assistant
mono-classlib-1.0
mono-common
mono-jit
monodoc-base
monodoc-browser
monodoc-gtk2.0-manual
monodoc-manual
mozilla-acroread
mozilla-mplayer
mpeg2dec
mpg321
mpgtx
nmap
ntp
odbcinst1debian1
ogmtools
openssh-server
openssl
p7zip
pgpgpg
pmount
poppler-utils
pwgen
pysdm
python2.4
python2.4-examples
python2.4-gdbm
python2.4-minimal
python2.4-pymad
python2.4-pysqlite2
python2.4-tk
python2.4-xmms
rar
rkhunter
rsnapshot
samba
samba-common
sbackup
sharutils
smart-notifier
smartmontools
smbldap-tools
sox
ssh
ssl-cert
subtitleripper
toolame
traceroute
transcode
tripwire
ttf-opensymbol
unace
unixodbc
unrar
unzoo
usbview
vcdimager
vorbis-tools
xbgmsharp
xcdroast
xchat
xchat-common
xinetd
xinit
xmltv-util
xmms
xmoto
xmoto-data
xvid4conf

---

### Post by thk on 2007-05-04
Take a look at apt's dump/set selections commands.

Or

for pkg in <pkg list goes here>; do apt-get -y install $pkg; done

---

### Post by dannyboy79 on 2007-05-04
> **thk said:**
> Take a look at apt's dump/set selections commands.

Or

for pkg in <pkg list goes here>; do apt-get -y install $pkg; done

this doesn't answer my question but thanks for informing me of what I was already going to do. My question is whether or not the list that I have put here is alright to install right into Feisty or should I remove some stuff like any of the examples that  listed above. you must not have read my post otherwise you wouldn't have responed with this answer.

---

