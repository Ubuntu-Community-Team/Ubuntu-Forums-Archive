---
title: "Gnome removal"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by aaron27 on 2015-09-10
I have Ubuntu 12.04 LTS server on a virtual machine and Gnome has broken  one of our apps, I need to remove Gnome completely - I can find  instructions to remove unity but not Gnome.

---

### Post by grahammechanical on 2015-09-10
What did you install? ubuntu-desktop? gnome-session-fallback? gnome-core? gnome-desktop-environment? Here is a list of all the gnome related packages in Ubuntu 12.04 desktop. I have no idea how many of them are default in a 12.04 server install.

[http://packages.ubuntu.com/precise/gnome/](http://packages.ubuntu.com/precise/gnome/)

Regards.

---

### Post by aaron27 on 2015-09-11
None of them are default as far as I know and I just ran: 

```

sudo apt-get update

sudo apt-get install gnome

```

I am assuming this is the complete Gnome package.

so would a purge command then remove the package?

---

### Post by MAFoElffen on 2015-09-11
FYI:
Source Package: meta-gnome3 (1:3.0+6ubuntu3) [universe]

The following binary packages are built from this source package:
gnome  || The GNOME Desktop Environment, with extra components

Unfortunately ubuntu-desktop uses portions of gnome-desktop-environment as elements of itself...

I only have a few minutes before I go to work. I've started a list for you. These are dependent packages that are installed with those two desktops... If you go through that list, first delete gnome-desktop-environment packages that have a match with an ubuntu- desktop. The delte the remaining ubuntu-desktop packages. What should be left over is packages from gnome-desktop-environment that are not in ubuntu desktop. Someone might want to verify that before you start removing them...
```

abiword (>= 2.8) (gnome-desktop)
alacarte (>= 0.13.2) (gnome-desktop)
alsa-base (ubuntu-desktop)
alsa-utils (ubuntu-desktop)
anacron (ubuntu-desktop)
at-spi2-core (ubuntu-desktop)
avahi-daemon (gnome-desktop)
baobab (ubuntu-desktop)
bc (ubuntu-desktop)
ca-certificates (ubuntu-desktop)
checkbox-gui (ubuntu-desktop)
cheese (>= 3.0) (gnome-desktop)
cups-pk-helper (>= 0.1.2) (gnome-desktop)
desktop-base (gnome-desktop)
dmz-cursor-theme (ubuntu-desktop)
doc-base (ubuntu-desktop)
ekiga (>= 3.2) (gnome-desktop)
eog (ubuntu-desktop)
epiphany-extensions (>= 3.0) (gnome-desktop)
evince (ubuntu-desktop)
evolution (>= 3.0) (gnome-desktop)
evolution-plugins (>= 3.0) (gnome-desktop)
file-roller (>= 3.0) (gnome-desktop)
file-roller (ubuntu-desktop)
fonts-dejavu-core (ubuntu-desktop)
fonts-freefont-ttf (ubuntu-desktop)
foomatic-db-compressed-ppds (ubuntu-desktop)
gedit (>= 3.0) (gnome-desktop)
gedit (ubuntu-desktop)
gedit-plugins (>= 3.0) (gnome-desktop)
genisoimage (ubuntu-desktop)
ghostscript-x (ubuntu-desktop)
gimp (>= 2.6) (gnome-desktop)
gnome-applets (>= 2.91) (gnome-desktop)
gnome-calculator (ubuntu-desktop)
gnome-core (= 1:3.0+6ubuntu3) (gnome-desktop)
gnome-font-viewer (ubuntu-desktop)
gnome-games (>= 1:3.0) (gnome-desktop)
gnome-media (>= 2.91) (gnome-desktop)
gnome-menus (ubuntu-desktop)
gnome-nettool (>= 3.0) (gnome-desktop)
gnome-power-manager (ubuntu-desktop)
gnome-screenshot (ubuntu-desktop)
gnome-session-canberra (ubuntu-desktop)
gnome-system-log (ubuntu-desktop)
gnome-system-monitor (ubuntu-desktop)
gnote (gnome-desktop)
gnumeric (>= 1.10) (gnome-desktop)
gstreamer0.10-alsa (ubuntu-desktop)
gstreamer0.10-ffmpeg (>= 0.10.12) (gnome-desktop)
gstreamer0.10-plugins-base-apps (ubuntu-desktop)
gstreamer0.10-plugins-ugly (>= 0.10.18) (gnome-desktop)
gstreamer0.10-pulseaudio (ubuntu-desktop)
gstreamer1.0-alsa (ubuntu-desktop)
gstreamer1.0-plugins-base-apps (ubuntu-desktop)
gstreamer1.0-pulseaudio (ubuntu-desktop)
gucharmap (ubuntu-desktop)
gvfs-bin (gnome-desktop)
gvfs-bin (ubuntu-desktop)
hamster-applet (>= 2.91.2) (gnome-desktop)
inkscape (>= 0.48) (gnome-desktop)
inputattach (ubuntu-desktop)
language-selector-gnome (ubuntu-desktop)
libatk-adaptor (ubuntu-desktop)
libgtk2-perl (>= 1:1.130) (gnome-desktop)
libnotify-bin (ubuntu-desktop)
libpam-systemd (ubuntu-desktop)
libreoffice-gnome (gnome-desktop)
libreoffice-gnome (gnome-desktop)
libsasl2-modules (ubuntu-desktop)
libxp6 (ubuntu-desktop)
lightdm (ubuntu-desktop)
memtest86+ (ubuntu-desktop)
nautilus (ubuntu-desktop)
nautilus-sendto (>= 3.0) (gnome-desktop)
nautilus-sendto (ubuntu-desktop)
notify-osd (ubuntu-desktop)
openprinting-ppds (ubuntu-desktop)
printer-driver-pnm2ppa (ubuntu-desktop)
pulseaudio (ubuntu-desktop)
rfkill (ubuntu-desktop)
rhythmbox (>= 2.90) (gnome-desktop)
rhythmbox-plugin-cdrecorder (gnome-desktop)
rhythmbox-plugins (gnome-desktop)
seahorse (>= 3.0) (gnome-desktop)
seahorse (ubuntu-desktop)
shotwell (gnome-desktop)
simple-scan (gnome-desktop)
software-center (ubuntu-desktop)
software-properties-gtk (ubuntu-desktop)
sound-juicer (>= 2.32.1+20110330) (gnome-desktop)
ssh-askpass-gnome (ubuntu-desktop)
system-config-printer-gnome (ubuntu-desktop)
telepathy-gabble (gnome-desktop)
telepathy-salut (gnome-desktop)
tomboy (>= 1.6) (gnome-desktop)
totem-mozilla (gnome-desktop)
totem-plugins (gnome-desktop)
transmission-gtk (gnome-desktop)
ubuntu-artwork (ubuntu-desktop)
ubuntu-drivers-common (ubuntu-desktop)
ubuntu-extras-keyring (ubuntu-desktop)
ubuntu-release-upgrader-gtk (ubuntu-desktop)
ubuntu-session (ubuntu-desktop)
ubuntu-settings (ubuntu-desktop)
ubuntu-sounds (ubuntu-desktop)
ubuntu-sso-client-qt (ubuntu-desktop)
unity (ubuntu-desktop)
unity-control-center (ubuntu-desktop)
unity-greeter (ubuntu-desktop)
unzip (ubuntu-desktop)
update-manager (ubuntu-desktop)
update-notifier (ubuntu-desktop)
vinagre (>= 3.0) (gnome-desktop)
wireless-tools (ubuntu-desktop)
wpasupplicant (ubuntu-desktop)
xdg-user-dirs (ubuntu-desktop)
xdg-user-dirs-gtk (gnome-desktop)
xdg-user-dirs-gtk (ubuntu-desktop)
xdiagnose (ubuntu-desktop)
xkb-data (ubuntu-desktop)
xorg (ubuntu-desktop)
yelp (ubuntu-desktop)
zenity (ubuntu-desktop)
zip (ubuntu-desktop)

```

Off to work for me...

---

### Post by MAFoElffen on 2015-09-12
Home now. Above list and instructions translate to:
```

sudo apt-get remove abiword alacarte avahi-daemon cheese
sudo apt-get remove cups-pk-helper desktop-base ekiga epiphany-extensions
sudo apt-get remove evolution evolution-plugins gedit-plugins gimp
sudo apt-get remove gnome-applets gnome-core gnome-games gnome-media
sudo apt-get remove gnome-nettool gnote gnumeric gstreamer0.10-ffmpeg
sudo apt-get remove gstreamer0.10-plugins-ugly hamster-applet inkscape
sudo apt-get remove libgtk2-perl libreoffice-gnome libreoffice-gnome
sudo apt-get remove rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins
sudo apt-get remove shotwell simple-scan sound-juicer telepathy-gabble
sudo apt-get remove telepathy-salut tomboy totem-mozilla totem-plugins
sudo apt-get remove transmission-gtk vinagre

```

---

