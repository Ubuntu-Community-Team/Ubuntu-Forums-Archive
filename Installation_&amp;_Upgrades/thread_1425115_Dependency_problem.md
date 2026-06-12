---
title: "Dependency problem"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by brumb on 2010-03-08
Hi all,

I've been using Ubuntu for years and this is the first time I've had to post. So, er, well done for sorting all my problems so far. Now I have something that seems totally intractable.

Running Karmic amd64 on my shiny new box. Need to install g++, or build essentials.
```
sudo apt-get install g++
```gives
```

The following packages have unmet dependencies.
  g++: Depends: g++-4.4 (>= 4.4.1-1) but it is not going to be installed
E: Broken packages

```When I try to do the same in Synaptic (i.e. select g++ metapackage), it says
```

g++:
 Depends: g++-4.4 but it is not going to be installed

```So I try to install g++-4.4 directly by selecting it alone:
```

g++-4.4:
  Depends: gcc-4.4-base (=4.4.1-4ubuntu8) but 4.4.1-4ubuntu9 is to be installed
  Depends: gcc-4.4 (=4.4.1-4ubuntu8) but 4.4.1-4ubuntu9 is to be installed
 Depends: libstdc++6-4.4-dev but it is not going to be installed

```So the problem appears to be the fact that gcc is the wrong version. So I tried to force gcc back to 4.4.1-4ubuntu8 (using the menus in Synaptic), but nothing happens. So I tried to force gcc-base back to 4.4.1-4ubuntu8, and these are the packages it wants to remove:
```

apt (essential) will be removed
base-files (essential) will be removed
bash (essential) will be removed
e2fsprogs (essential) will be removed
hostname (essential) will be removed
login (essential) will be removed
mount (essential) will be removed
python-minimal (essential) will be removed
util-linux (essential) will be removed
acpi-support will be removed
acpid will be removed
adduser will be removed
aisleriot will be removed
alacarte will be removed
alsa-base will be removed
alsa-utils will be removed
anacron will be removed
ant will be removed
ant-gcj will be removed
ant-optional will be removed
ant-optional-gcj will be removed
apache2 will be removed
apache2-mpm-prefork will be removed
apache2-utils will be removed
apache2.2-bin will be removed
apache2.2-common will be removed
apparmor will be removed
apparmor-utils will be removed
apport will be removed
apport-gtk will be removed
apt-transport-https will be removed
apt-utils will be removed
apt-xapian-index will be removed
aptdaemon will be removed
aptitude will be removed
apturl will be removed
apturl-common will be removed
aspell will be removed
aspell-en will be removed
at will be removed
at-spi will be removed
avahi-autoipd will be removed
avahi-daemon will be removed
bash-completion will be removed
bind9-host will be removed
binfmt-support will be removed
bluetooth will be removed
bluez will be removed
bluez-cups will be removed
bluez-utils will be removed
brasero will be removed
brltty will be removed
brltty-x11 will be removed
bsdmainutils will be removed
byobu will be removed
ca-certificates will be removed
capplets-data will be removed
checkbox will be removed
checkbox-gtk will be removed
cli-common will be removed
command-not-found will be removed
compiz will be removed
compiz-core will be removed
compiz-fusion-plugins-extra will be removed
compiz-fusion-plugins-main will be removed
compiz-gnome will be removed
compiz-plugins will be removed
compiz-wrapper will be removed
compizconfig-backend-gconf will be removed
computer-janitor will be removed
computer-janitor-gtk will be removed
console-setup will be removed
consolekit will be removed
couchdb-bin will be removed
cpp will be removed
cpp-4.4 will be removed
cron will be removed
cryptsetup will be removed
cups will be removed
cups-bsd will be removed
cups-client will be removed
cups-driver-gutenprint will be removed
cvs will be removed
dbus will be removed
dbus-x11 will be removed
defoma will be removed
desktopcouch will be removed
devicekit-disks will be removed
dhcp3-client will be removed
dictionaries-common will be removed
dkms will be removed
dmsetup will be removed
dnsutils will be removed
doc-base will be removed
docbook-xml will be removed
dvd+rw-tools will be removed
eclipse will be removed
eclipse-jdt will be removed
eclipse-pde will be removed
eclipse-platform will be removed
eclipse-plugin-cvs will be removed
eclipse-rcp will be removed
ecryptfs-utils will be removed
empathy will be removed
eog will be removed
erlang-base will be removed
erlang-crypto will be removed
erlang-inets will be removed
erlang-mnesia will be removed
erlang-public-key will be removed
erlang-runtime-tools will be removed
erlang-ssl will be removed
erlang-syntax-tools will be removed
erlang-xmerl will be removed
espeak will be removed
evince will be removed
evolution will be removed
evolution-couchdb will be removed
evolution-data-server will be removed
evolution-documentation-en will be removed
evolution-exchange will be removed
evolution-indicator will be removed
evolution-plugins will be removed
evolution-webcal will be removed
f-spot will be removed
fglrx-amdcccle will be removed
fglrx-kernel-source will be removed
file-roller will be removed
firefox will be removed
firefox-3.5 will be removed
firefox-3.5-branding will be removed
firefox-3.5-gnome-support will be removed
firefox-gnome-support will be removed
flashplugin-installer will be removed
flashplugin-nonfree will be removed
fontconfig will be removed
fontconfig-config will be removed
foo2zjs will be removed
foomatic-db will be removed
foomatic-db-engine will be removed
foomatic-filters will be removed
friendly-recovery will be removed
ftp will be removed
fuse-utils will be removed
gcalctool will be removed
gcc will be removed
gcc-4.4 will be removed
gcj-4.4-jre-lib will be removed
gconf-defaults-service will be removed
gconf-editor will be removed
gconf2 will be removed
gconf2-common will be removed
gdebi will be removed
gdebi-core will be removed
gdm will be removed
gdm-guest-session will be removed
gedit will be removed
gettext-base will be removed
ghostscript will be removed
ghostscript-cups will be removed
ghostscript-x will be removed
gimp will be removed
gimp-help-en will be removed
git-core will be removed
gitk will be removed
gksu will be removed
glchess will be removed
glines will be removed
gnect will be removed
gnibbles will be removed
gnobots2 will be removed
gnome-about will be removed
gnome-accessibility-themes will be removed
gnome-applets will be removed
gnome-applets-data will be removed
gnome-blackjack will be removed
gnome-bluetooth will be removed
gnome-codec-install will be removed
gnome-control-center will be removed
gnome-disk-utility will be removed
gnome-doc-utils will be removed
gnome-games will be removed
gnome-games-common will be removed
gnome-icon-theme will be removed
gnome-keyring will be removed
gnome-mag will be removed
gnome-mahjongg will be removed
gnome-media will be removed
gnome-media-common will be removed
gnome-menus will be removed
gnome-nettool will be removed
gnome-orca will be removed
gnome-panel will be removed
gnome-panel-data will be removed
gnome-pilot will be removed
gnome-pilot-conduits will be removed
gnome-power-manager will be removed
gnome-screensaver will be removed
gnome-session will be removed
gnome-session-bin will be removed
gnome-session-canberra will be removed
gnome-settings-daemon will be removed
gnome-sudoku will be removed
gnome-system-monitor will be removed
gnome-system-tools will be removed
gnome-terminal will be removed
gnome-terminal-data will be removed
gnome-themes-selected will be removed
gnome-themes-ubuntu will be removed
gnome-user-guide will be removed
gnome-user-guide-en will be removed
gnome-utils will be removed
gnometris will be removed
gnomine will be removed
gnotravex will be removed
gnotski will be removed
gnupg will be removed
groff-base will be removed
grub-common will be removed
grub-pc will be removed
gsfonts will be removed
gsfonts-x11 will be removed
gstreamer0.10-nice will be removed
gstreamer0.10-plugins-bad will be removed
gstreamer0.10-plugins-bad-multiverse will be removed
gstreamer0.10-plugins-base will be removed
gstreamer0.10-plugins-base-apps will be removed
gstreamer0.10-plugins-good will be removed
gstreamer0.10-plugins-ugly will be removed
gstreamer0.10-pulseaudio will be removed
gstreamer0.10-x will be removed
gtali will be removed
gtk2-engines will be removed
gtk2-engines-murrine will be removed
gtk2-engines-pixbuf will be removed
gucharmap will be removed
gvfs will be removed
gvfs-backends will be removed
gvfs-bin will be removed
gvfs-fuse will be removed
gxine will be removed
hal will be removed
hpijs will be removed
hplip will be removed
hplip-data will be removed
human-theme will be removed
humanity-icon-theme will be removed
hunspell-en-us will be removed
ia32-libs will be removed
iagno will be removed
ibus will be removed
ibus-gtk will be removed
ibus-m17n will be removed
ibus-table will be removed
ifupdown will be removed
indicator-applet will be removed
indicator-applet-session will be removed
indicator-messages will be removed
indicator-session will be removed
initramfs-tools will be removed
initscripts will be removed
jockey-common will be removed
jockey-gtk will be removed
kbd will be removed
kerneloops-daemon will be removed
language-pack-en will be removed
language-pack-en-base will be removed
language-pack-gnome-en will be removed
language-pack-gnome-en-base will be removed
language-selector will be removed
language-selector-common will be removed
language-support-writing-en will be removed
laptop-mode-tools will be removed
latex-xft-fonts will be removed
launchpad-integration will be removed
lftp will be removed
lib32gcc1 will be removed
lib32stdc++6 will be removed
libapache2-mod-php5 will be removed
libapparmor-perl will be removed
libapr1 will be removed
libaprutil1 will be removed
libaprutil1-dbd-sqlite3 will be removed
libaprutil1-ldap will be removed
libart2.0-cil will be removed
libasound2-plugins will be removed
libaspell15 will be removed
libass3 will be removed
libatspi1.0-0 will be removed
libaudio2 will be removed
libavahi-ui0 will be removed
libbind9-50 will be removed
libblkid1 will be removed
libbonobo2-0 will be removed
libbonoboui2-0 will be removed
libboost-date-time1.38.0 will be removed
libboost-thread1.38.0 will be removed
libbrasero-media0 will be removed
libcaca0 will be removed
libcairo-perl will be removed
libcairo2 will be removed
libcairomm-1.0-1 will be removed
libcamel1.2-14 will be removed
libcanberra-gtk-module will be removed
libcanberra-gtk0 will be removed
libcanberra-pulse will be removed
libclass-accessor-perl will be removed
libclutter-1.0-0 will be removed
libclutter-gtk-0.10-0 will be removed
libcompizconfig0 will be removed
libcompress-bzip2-perl will be removed
libcouchdb-glib-1.0-1 will be removed
libcryptui0 will be removed
libcupsppdc1 will be removed
libcurl3 will be removed
libcurl3-gnutls will be removed
libcwidget3 will be removed
libdbusmenu-gtk0 will be removed
libdigest-sha1-perl will be removed
libdirac0c2a will be removed
libdjvulibre21 will be removed
libdns53 will be removed
libebackend1.2-0 will be removed
libebook1.2-9 will be removed
libecal1.2-7 will be removed
libedata-book1.2-2 will be removed
libedata-cal1.2-6 will be removed
libedataserver1.2-11 will be removed
libedataserverui1.2-8 will be removed
libegroupwise1.2-13 will be removed
libempathy-gtk-common will be removed
libempathy-gtk28 will be removed
libempathy30 will be removed
libenchant1c2a will be removed
libept0 will be removed
libequinox-osgi-java will be removed
liberror-perl will be removed
libespeak1 will be removed
libevdocument1 will be removed
libevview1 will be removed
libexchange-storage1.2-3 will be removed
libexempi3 will be removed
libffado1 will be removed
libflickrnet2.2-cil will be removed
libfont-afm-perl will be removed
libfontconfig1 will be removed
libfreebob0 will be removed
libfreezethaw-perl will be removed
libgail-common will be removed
libgail-gnome-module will be removed
libgail18 will be removed
libgc1c2 will be removed
libgcj-bc will be removed
libgcj-common will be removed
libgcj10 will be removed
libgconf2-4 will be removed
libgconf2.0-cil will be removed
libgcr0 will be removed
libgd2-xpm will be removed
libgdata5 will be removed
libgdict-1.0-6 will be removed
libgdiplus will be removed
libgdu-gtk0 will be removed
libgegl-0.0-0 will be removed
libgimp2.0 will be removed
libgksu2-0 will be removed
libgl1-mesa-glx will be removed
libglade2-0 will be removed
libglade2.0-cil will be removed
libglib-perl will be removed
libglibmm-2.4-1c2a will be removed
libglitz-glx1 will be removed
libglu1-mesa will be removed
libgmime2.2a-cil will be removed
libgnome-bluetooth7 will be removed
libgnome-desktop-2-11 will be removed
libgnome-keyring1.0-cil will be removed
libgnome-mag2 will be removed
libgnome-media0 will be removed
libgnome-pilot2 will be removed
libgnome-vfs2.0-cil will be removed
libgnome-window-settings1 will be removed
libgnome2-0 will be removed
libgnome2-canvas-perl will be removed
libgnome2-common will be removed
libgnome2-perl will be removed
libgnome2-vfs-perl will be removed
libgnome2.24-cil will be removed
libgnomecanvas2-0 will be removed
libgnomekbd-common will be removed
libgnomekbd4 will be removed
libgnomekbdui4 will be removed
libgnomepanel2.24-cil will be removed
libgnomeui-0 will be removed
libgnomevfs2-0 will be removed
libgnomevfs2-common will be removed
libgnomevfs2-extra will be removed
libgomp1 will be removed
libgpgme11 will be removed
libgphoto2-2 will be removed
libgpod-common will be removed
libgpod4 will be removed
libgraphviz4 will be removed
libgs8 will be removed
libgstfarsight0.10-0 will be removed
libgtk-vnc-1.0-0 will be removed
libgtk2-perl will be removed
libgtk2.0-0 will be removed
libgtk2.0-bin will be removed
libgtk2.0-cil will be removed
libgtkhtml-editor0 will be removed
libgtkhtml2-0 will be removed
libgtkhtml3.14-19 will be removed
libgtkmm-2.4-1c2a will be removed
libgtksourceview2.0-0 will be removed
libgtkspell0 will be removed
libgucharmap7 will be removed
libgupnp-1.0-2 will be removed
libgupnp-igd-1.0-2 will be removed
libgweather-common will be removed
libgweather1 will be removed
libhtml-format-perl will be removed
libhtml-parser-perl will be removed
libhtml-tagset-perl will be removed
libhtml-tree-perl will be removed
libhunspell-1.2-0 will be removed
libical0 will be removed
libice6 will be removed
libicu40 will be removed
libidl0 will be removed
libilmbase6 will be removed
libindicate-gtk1 will be removed
libio-string-perl will be removed
libisccfg50 will be removed
libjack0 will be removed
libjaxp1.3-java will be removed
liblaunchpad-integration1 will be removed
liblpint-bonobo0 will be removed
libm17n-0 will be removed
libmagickcore2 will be removed
libmagickwand2 will be removed
libmailtools-perl will be removed
libmetacity0 will be removed
libmjpegtools-1.9 will be removed
libmldbm-perl will be removed
libmodplug0c2 will be removed
libmono-addins-gui0.2-cil will be removed
libmono-addins0.2-cil will be removed
libmono-cairo2.0-cil will be removed
libmono-system-web2.0-cil will be removed
libmono2.0-cil will be removed
libmp4v2-0 will be removed
libmusicbrainz4c2a will be removed
libnautilus-extension1 will be removed
libndesk-dbus-glib1.0-cil will be removed
libndesk-dbus1.0-cil will be removed
libnet-dbus-perl will be removed
libnice0 will be removed
libnm-glib2 will be removed
libnm-util1 will be removed
libnotify1 will be removed
libnss-mdns will be removed
libofa0 will be removed
liboobs-1-4 will be removed
libopenexr6 will be removed
liborbit2 will be removed
libpam-ck-connector will be removed
libpam-gnome-keyring will be removed
libpam-modules will be removed
libpam-runtime will be removed
libpam0g will be removed
libpanel-applet2-0 will be removed
libpango-perl will be removed
libpango1.0-0 will be removed
libpango1.0-common will be removed
libpangomm-1.4-1 will be removed
libpaper-utils will be removed
libpaper1 will be removed
libparse-debianchangelog-perl will be removed
libparted1.8-12 will be removed
libperl5.10 will be removed
libpolkit-gtk-1-0 will be removed
libpoppler-glib4 will be removed
libpoppler5 will be removed
libpq5 will be removed
libprotobuf3 will be removed
libpulse-browse0 will be removed
libpulse-mainloop-glib0 will be removed
libpulse0 will be removed
libpurple-bin will be removed
libpurple0 will be removed
libraptor1 will be removed
librarian0 will be removed
librasqal1 will be removed
librdf0 will be removed
librpc-xml-perl will be removed
librsvg2-2 will be removed
librsvg2-common will be removed
libsane will be removed
libsensors3 will be removed
libsexy2 will be removed
libsidplay1 will be removed
libsigc++-2.0-0c2a will be removed
libslp1 will be removed
libsm6 will be removed
libsnmp15 will be removed
libsoundtouch1c2 will be removed
libsoup-gnome2.4-1 will be removed
libspectre1 will be removed
libstartup-notification0 will be removed
libsub-name-perl will be removed
libswt-gtk-3.5-java will be removed
libswt-gtk-3.5-jni will be removed
libtag1-vanilla will be removed
libtag1c2a will be removed
libtelepathy-farsight0 will be removed
libterm-readkey-perl will be removed
libtie-ixhash-perl will be removed
libtimedate-perl will be removed
libtotem-plparser12 will be removed
libunique-1.0-0 will be removed
liburi-perl will be removed
libuuid-perl will be removed
libuuid1 will be removed
libvisual-0.4-plugins will be removed
libvte9 will be removed
libwebkit-1.0-2 will be removed
libwmf0.2-7 will be removed
libwmf0.2-7-gtk will be removed
libwnck22 will be removed
libwpd8c2a will be removed
libwpg-0.1-1 will be removed
libwps-0.1-1 will be removed
libwww-perl will be removed
libxapian15 will be removed
libxaw7 will be removed
libxcomposite1 will be removed
libxcursor1 will be removed
libxdamage1 will be removed
libxerces2-java will be removed
libxext6 will be removed
libxfixes3 will be removed
libxft2 will be removed
libxi6 will be removed
libxine1 will be removed
libxine1-console will be removed
libxine1-misc-plugins will be removed
libxine1-x will be removed
libxinerama1 will be removed
libxklavier15 will be removed
libxml++2.6-2 will be removed
libxml-parser-perl will be removed
libxml-twig-perl will be removed
libxml-xpath-perl will be removed
libxmu6 will be removed
libxp6 will be removed
libxrandr2 will be removed
libxres1 will be removed
libxss1 will be removed
libxt6 will be removed
libxtrap6 will be removed
libxtst6 will be removed
libxv1 will be removed
libxvmc1 will be removed
libxxf86dga1 will be removed
libxxf86misc1 will be removed
libxxf86vm1 will be removed
linux-generic will be removed
linux-image-2.6.31-14-generic will be removed
linux-image-2.6.31-19-generic will be removed
linux-image-generic will be removed
linux-sound-base will be removed
logrotate will be removed
lsb-release will be removed
lshw will be removed
m17n-contrib will be removed
m17n-db will be removed
man-db will be removed
media-player-info will be removed
medibuntu-keyring will be removed
mencoder will be removed
mesa-utils will be removed
metacity will be removed
metacity-common will be removed
mlocate will be removed
module-init-tools will be removed
mousetweaks will be removed
mplayer-nogui will be removed
myspell-en-au will be removed
myspell-en-gb will be removed
myspell-en-za will be removed
nautilus will be removed
nautilus-data will be removed
nautilus-sendto will be removed
nautilus-share will be removed
netbase will be removed
network-manager will be removed
network-manager-gnome will be removed
non-free-codecs will be removed
notify-osd will be removed
nspluginwrapper will be removed
ntfs-3g will be removed
ntfsprogs will be removed
ntpdate will be removed
nvidia-common will be removed
obex-data-server will be removed
oem-config will be removed
oem-config-gtk will be removed
onboard will be removed
openoffice.org-base-core will be removed
openoffice.org-calc will be removed
openoffice.org-core will be removed
openoffice.org-draw will be removed
openoffice.org-emailmerge will be removed
openoffice.org-gnome will be removed
openoffice.org-gtk will be removed
openoffice.org-help-en-gb will be removed
openoffice.org-help-en-us will be removed
openoffice.org-hyphenation will be removed
openoffice.org-hyphenation-en-us will be removed
openoffice.org-impress will be removed
openoffice.org-math will be removed
openoffice.org-thesaurus-en-au will be removed
openoffice.org-thesaurus-en-us will be removed
openoffice.org-writer will be removed
openprinting-ppds will be removed
openssh-client will be removed
openssh-server will be removed
openssl will be removed
parted will be removed
passwd will be removed
pcmciautils will be removed
perl will be removed
perl-modules will be removed
php5 will be removed
php5-mysql will be removed
php5-pgsql will be removed
pm-utils will be removed
pnm2ppa will be removed
policykit-1 will be removed
policykit-1-gnome will be removed
poppler-utils will be removed
popularity-contest will be removed
powermgmt-base will be removed
ppp will be removed
pppconfig will be removed
pppoeconf will be removed
procps will be removed
protobuf-compiler will be removed
psfontmgr will be removed
pulseaudio will be removed
pulseaudio-esound-compat will be removed
pulseaudio-module-bluetooth will be removed
pulseaudio-module-gconf will be removed
pulseaudio-module-udev will be removed
pulseaudio-module-x11 will be removed
pulseaudio-utils will be removed
pxljr will be removed
python will be removed
python-apport will be removed
python-apt will be removed
python-aptdaemon will be removed
python-aptdaemon-gtk will be removed
python-avahi will be removed
python-brlapi will be removed
python-cairo will be removed
python-central will be removed
python-configglue will be removed
python-couchdb will be removed
python-crypto will be removed
python-cups will be removed
python-cupshelpers will be removed
python-dbus will be removed
python-debian will be removed
python-desktopcouch will be removed
python-desktopcouch-records will be removed
python-fstab will be removed
python-gconf will be removed
python-gdbm will be removed
python-glade2 will be removed
python-gmenu will be removed
python-gnome2 will be removed
python-gnomeapplet will be removed
python-gnomecanvas will be removed
python-gnomekeyring will be removed
python-gnupginterface will be removed
python-gobject will be removed
python-gst0.10 will be removed
python-gtk2 will be removed
python-gtkhtml2 will be removed
python-gtksourceview2 will be removed
python-httplib2 will be removed
python-ibus will be removed
python-imaging will be removed
python-launchpad-integration will be removed
python-launchpadlib will be removed
python-lazr-restfulclient will be removed
python-lazr-uri will be removed
python-libxml2 will be removed
python-louis will be removed
python-newt will be removed
python-notify will be removed
python-oauth will be removed
python-openssl will be removed
python-pam will be removed
python-papyon will be removed
python-pkg-resources will be removed
python-problem-report will be removed
python-protobuf will be removed
python-pyatspi will be removed
python-pyicu will be removed
python-pyinotify will be removed
python-pyorbit will be removed
python-rdflib will be removed
python-rsvg will be removed
python-serial will be removed
python-sexy will be removed
python-simplejson will be removed
python-smbc will be removed
python-software-properties will be removed
python-speechd will be removed
python-support will be removed
python-telepathy will be removed
python-twisted-bin will be removed
python-twisted-core will be removed
python-twisted-names will be removed
python-twisted-web will be removed
python-ubuntuone-client will be removed
python-ubuntuone-storageprotocol will be removed
python-uno will be removed
python-virtkey will be removed
python-vte will be removed
python-wadllib will be removed
python-webkit will be removed
python-xapian will be removed
python-xdg will be removed
python-xkit will be removed
python-zope.interface will be removed
raptor-utils will be removed
rarian-compat will be removed
rdesktop will be removed
redland-utils will be removed
reiserfsprogs will be removed
rhythmbox will be removed
rsync will be removed
rsyslog will be removed
samba-common will be removed
samba-common-bin will be removed
same-gnome will be removed
sane-utils will be removed
screen will be removed
screen-resolution-extra will be removed
screensaver-default-images will be removed
seahorse will be removed
sgml-base will be removed
sgml-data will be removed
smartdimmer will be removed
smbclient will be removed
software-center will be removed
software-properties-gtk will be removed
speech-dispatcher will be removed
splix will be removed
sreadahead will be removed
ssh-askpass-gnome will be removed
ssl-cert will be removed
sudo will be removed
sun-java6-bin will be removed
sun-java6-jre will be removed
sun-java6-plugin will be removed
synaptic will be removed
system-config-printer-common will be removed
system-config-printer-gnome will be removed
system-config-printer-udev will be removed
system-tools-backends will be removed
sysv-rc will be removed
tasksel will be removed
tasksel-data will be removed
tcpd will be removed
tcpdump will be removed
telepathy-butterfly will be removed
telepathy-gabble will be removed
telepathy-haze will be removed
telepathy-idle will be removed
telepathy-salut will be removed
telnet will be removed
tomboy will be removed
toshset will be removed
totem will be removed
totem-common will be removed
totem-mozilla will be removed
totem-plugins will be removed
transmission-gtk will be removed
truecrypt will be removed
tsclient will be removed
ttf-dejavu-core will be removed
ttf-freefont will be removed
ttf-indic-fonts-core will be removed
ttf-kacst will be removed
ttf-lao will be removed
ttf-liberation will be removed
ttf-mscorefonts-installer will be removed
ttf-thai-tlwg will be removed
ttf-unfonts-core will be removed
ttf-vlgothic will be removed
ttf-wqy-zenhei will be removed
ubiquity will be removed
ubiquity-casper will be removed
ubiquity-frontend-debconf will be removed
ubiquity-frontend-gtk will be removed
ubufox will be removed
ubuntu-artwork will be removed
ubuntu-desktop will be removed
ubuntu-docs will be removed
ubuntu-keyring will be removed
ubuntu-minimal will be removed
ubuntu-standard will be removed
ubuntu-system-service will be removed
ubuntu-wallpapers will be removed
ubuntuone-client will be removed
ubuntuone-client-gnome will be removed
ucf will be removed
udev will be removed
ufw will be removed
unattended-upgrades will be removed
uno-libs3 will be removed
unrar will be removed
update-inetd will be removed
update-manager will be removed
update-manager-core will be removed
update-notifier will be removed
update-notifier-common will be removed
upstart will be removed
ure will be removed
ureadahead will be removed
usb-creator-common will be removed
usb-creator-gtk will be removed
usplash will be removed
usplash-theme-ubuntu will be removed
uuid-runtime will be removed
vim-gnome will be removed
vim-nox will be removed
vim-runtime will be removed
vinagre will be removed
vino will be removed
w3m will be removed
w64codecs will be removed
wamerican will be removed
watershed will be removed
wbritish will be removed
wget will be removed
wireless-crda will be removed
wpasupplicant will be removed
x-ttcidfont-conf will be removed
x11-apps will be removed
x11-common will be removed
x11-session-utils will be removed
x11-utils will be removed
x11-xfs-utils will be removed
x11-xkb-utils will be removed
x11-xserver-utils will be removed
xauth will be removed
xbitmaps will be removed
xdg-user-dirs-gtk will be removed
xfonts-100dpi will be removed
xfonts-75dpi will be removed
xfonts-base will be removed
xfonts-encodings will be removed
xfonts-mathml will be removed
xfonts-scalable will be removed
xfonts-utils will be removed
xinit will be removed
xinput will be removed
xml-core will be removed
xorg will be removed
xorg-driver-fglrx will be removed
xsane will be removed
xscreensaver-data will be removed
xscreensaver-gl will be removed
xserver-common will be removed
xserver-xorg will be removed
xserver-xorg-core will be removed
xserver-xorg-input-all will be removed
xserver-xorg-input-evdev will be removed
xserver-xorg-input-mouse will be removed
xserver-xorg-input-synaptics will be removed
xserver-xorg-input-vmmouse will be removed
xserver-xorg-input-wacom will be removed
xserver-xorg-video-all will be removed
xserver-xorg-video-apm will be removed
xserver-xorg-video-ark will be removed
xserver-xorg-video-ati will be removed
xserver-xorg-video-chips will be removed
xserver-xorg-video-cirrus will be removed
xserver-xorg-video-fbdev will be removed
xserver-xorg-video-i128 will be removed
xserver-xorg-video-intel will be removed
xserver-xorg-video-mach64 will be removed
xserver-xorg-video-mga will be removed
xserver-xorg-video-neomagic will be removed
xserver-xorg-video-nv will be removed
xserver-xorg-video-openchrome will be removed
xserver-xorg-video-r128 will be removed
xserver-xorg-video-radeon will be removed
xserver-xorg-video-rendition will be removed
xserver-xorg-video-s3 will be removed
xserver-xorg-video-s3virge will be removed
xserver-xorg-video-savage will be removed
xserver-xorg-video-siliconmotion will be removed
xserver-xorg-video-sis will be removed
xserver-xorg-video-sisusb will be removed
xserver-xorg-video-tdfx will be removed
xserver-xorg-video-trident will be removed
xserver-xorg-video-tseng will be removed
xserver-xorg-video-v4l will be removed
xserver-xorg-video-vesa will be removed
xserver-xorg-video-vmware will be removed
xserver-xorg-video-voodoo will be removed
xsplash will be removed
xterm will be removed
xtightvncviewer will be removed
xulrunner-1.9.1 will be removed
xulrunner-1.9.1-gnome-support will be removed
yelp will be removed
zenity will be removed

```This is obviously going to cause some problems in the running of my system.

What to do?

---

### Post by Barriehie on 2010-03-09
See what this produces:
```

sudo aptitude why g++
```

---

### Post by brumb on 2010-03-09
> **Barriehie said:**
> See what this produces:
```

sudo aptitude why g++
```

```

:~$ sudo aptitude why g++
i   xorg-driver-fglrx   Depends fglrx-kernel-source              
i A fglrx-kernel-source Depends dkms                             
i A dkms                Depends make | build-essential | dpkg-dev
p   build-essential     Depends g++ (>= 4:4.3.1)         

```Never heard of the 'why' command before. Not sure I fully understand the man page; does the above mean that if I tried to install the  xorg-driver-fglrx package, g++ would be installed as a dependency?

If it helps at all the xorg-driver-fglrx is all up-to-date.

```

sudo apt-get install -s xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-date-time1.38.0 libboost-thread1.38.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Thanks for your help. Any further ideas much appreciated.

---

### Post by Barriehie on 2010-03-09
From your first post you have broken packages, so:
```

sudo apt-get --fix-broken
```See if that gets you any closer.

---

### Post by brumb on 2010-03-10
Um...
```

:~$ sudo apt-get --fix-broken
apt 0.7.23.1ubuntu2 for amd64 compiled on Oct 15 2009 19:26:30
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

``````

man apt-get
-f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.


``````

:~$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```I'm confused.
I have a working Gentoo install on the same hardware. Any idea how I can build and install stuff onto my Ubuntu installation using the Gentoo's g++?

Thanks for your help.

---

### Post by Barriehie on 2010-03-10
```

sudo apt-get -f install g++
```

---

### Post by brumb on 2010-03-19
Sorry, have been away for a week.

```
:~$ sudo apt-get -f install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  g++: Depends: g++-4.4 (>= 4.4.1-1) but it is not going to be installed
E: Broken packages

```

Same old. I'm at a bit of a loss here.

Is this a bug? I'm reluctant to say the computer is at fault because usually it's not; in fact every problem I have ever encountered with Ubuntu has been entirely of my own making. But this is a relatively fresh install, standard repositories only, and I haven't done any of my normal amateur jiggery pokery yet.

---

### Post by Barriehie on 2010-03-19
> **brumb said:**
> Sorry, have been away for a week.

```
:~$ sudo apt-get -f install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  g++: Depends: g++-4.4 (>= 4.4.1-1) but it is not going to be installed
E: Broken packages

```

Same old. I'm at a bit of a loss here.

Is this a bug? I'm reluctant to say the computer is at fault because usually it's not; in fact every problem I have ever encountered with Ubuntu has been entirely of my own making. But this is a relatively fresh install, standard repositories only, and I haven't done any of my normal amateur jiggery pokery yet.

Last shot from this end:
```

sudo apt-get install g++-4.4
```

---

### Post by dave2008713 on 2010-03-21
hey, I've just meet the same problem!And I fixed it with following command:
```
sudo aptitude install build-essential
```
it will done all the downgrades and installations automatically.
hope it helps, gl.

---

### Post by brumb on 2010-03-27
> **dave2008713 said:**
> hey, I've just meet the same problem!And I fixed it with following command:
```
sudo aptitude install build-essential
```it will done all the downgrades and installations automatically.
hope it helps, gl.

Ah excellent! So it did.

apt-get install build-essential threw an error.
aptitude install build-essential downgraded as required.

Thanks for the help. And thanks to Barriehie for all his suggestions. Ta for persevering.

---

