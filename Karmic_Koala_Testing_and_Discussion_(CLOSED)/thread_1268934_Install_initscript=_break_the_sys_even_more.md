---
title: "Install initscript= break the sys even more?"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by qwerty800 on 2009-09-17
Well, in every karmic topic related to the bug of the 15 sept, people recommends of upgrading initscript.

However, I'm scared of doing that. Here is why:

```
root@ubuntu:/home/user/Bureau# sudo apt-get install initscripts
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xorg-docs-core nvidia-settings nvidia-185-libvdpau nvidia-185-kernel-source check tix tcl8.4 tk8.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support alsa-base bluez-cups brltty brltty-x11 checkbox checkbox-gtk console-setup cups cups-driver-gutenprint cupsys dmsetup foo2zjs foomatic-db foomatic-db-engine
  fuse-utils gdm gdm-guest-session ghostscript-cups gnome-mount gvfs-fuse hal hotkey-setup hpijs hplip hplip-cups indicator-applet-session indicator-session initramfs-tools
  kbd libcanberra-pulse linux-backports-modules-2.6.31-10-generic linux-generic linux-image-2.6.31-10-generic linux-image-2.6.31-5-generic linux-image-2.6.31-6-generic
  linux-image-2.6.31-7-generic linux-image-2.6.31-8-generic linux-image-2.6.31-9-generic linux-image-generic lvm2 media-player-info ntfs-3g openprinting-ppds pcmciautils
  pm-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 rhythmbox splix ubuntu-desktop
  udev usplash usplash-theme-ubuntu watershed wireless-crda xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following packages will be upgraded:
  initscripts
1 upgraded, 0 newly installed, 102 to remove and 0 not upgraded.
Need to get 72.7kB of archives.
After this operation, 654MB disk space will be freed.
Do you want to continue [Y/n]? 

```
My question is: "What will remain of ubuntu after that^ No kernels, no Xorg, no pulse..."

When I try to install the deb package with dpkg, it even says:
> root@ubuntu:/home/user/Bureau# dpkg -i /home/user/Bureau/initscripts_2.87dsf-4ubuntu3_i386.deb
dpkg: regarding .../initscripts_2.87dsf-4ubuntu3_i386.deb containing initscripts:
 **initscripts breaks udev** (<< 146-2~boot6)
  udev (version 146-1) is present and installed.
dpkg: error processing /home/user/Bureau/initscripts_2.87dsf-4ubuntu3_i386.deb (--install):
 installing **initscripts would break udev**, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 /home/user/Bureau/initscripts_2.87dsf-4ubuntu3_i386.deb
I mean, that's some serious suicide, isn't?

The question now is: "What should I do?":(

---

### Post by qwerty800 on 2009-09-17
Bump!

People rerely reads what's not on the first page.

---

### Post by trulan on 2009-09-17
> **qwerty800 said:**
> 
```
1 upgraded, 0 newly installed, 102 to remove and 0 not upgraded.
Need to get 72.7kB of archives.
After this operation, 654MB disk space will be freed.
Do you want to continue [Y/n]? 

```
I mean, that's some serious suicide, isn't?

The question now is: "What should I do?":(
Not that.  Definitely not that.

Just keep checking update manager or running apt-get update until the dependencies clear and initscripts is able to install properly.

---

### Post by Eestlane on 2009-09-18
You could try Synaptic->Edit->Fix broken Packages.

---

### Post by lithorus on 2009-09-18
You should upgrade udev first. I think the sept 15 issues have been resolved now.

---

### Post by dino99 on 2009-09-18
i would say: 

- check your sources.list to be sure you use the good one's, disable all the extra if exist (ppa's)

- run sudo aptitude clean
-     sudo aptitude autoclean
-     sudo aptitude install -f

don't run "sudo apt-get autoremove" now

- run system --> administration --> system janitor
- install gtkorphan & then: system --> administration --> remove orphans
- you can safely remove all the xorg-driver-chip-you-dont-have except the main one (intel, nvidia, ati & vesa)

Then, sudo aptitude update & sudo aptitude safe-upgrade

---

### Post by qwerty800 on 2009-09-18
Well, my major problem is that I just can't do all of this outside of a chroot on a liveusb.

When I try to boot normally, I get uSplash, and when it fades out, I don't even get a console!

There's no prompt!

And no matter how long I wait, that prompt will ONLY appear for 2 seconds after I made Ctrl+Alt+Del...

I don't want to reinstall everything AGAIN!

---

### Post by VMC on 2009-09-18
> **qwerty800 said:**
> Well, my major problem is that I just can't do all of this outside of a chroot on a liveusb.

When I try to boot normally, I get uSplash, and when it fades out, I don't even get a console!

There's no prompt!

And no matter how long I wait, that prompt will ONLY appear for 2 seconds after I made Ctrl+Alt+Del...

I don't want to reinstall everything AGAIN!

Remove the splash command from end of kernel line to see what text messages you get.

---

### Post by qwerty800 on 2009-09-18
See the attachement.

The computer won't go farther than here.

---

### Post by qwerty800 on 2009-09-18
Up!

It getting quite urgent, so please awnser back!:(

---

### Post by VMC on 2009-09-18
> **qwerty800 said:**
> See the attachement.

The computer won't go farther than here.

In your first post you mentioned about initscript. Did you run it? Because right after that is where I see the udev sym errors that you don't have shown. Anything inside here "/etc/initramfs-tools/scripts/init-bottom". Mines empty.

---

### Post by qwerty800 on 2009-09-18
My init-bottom folder is empty too.

What do you mean by "Did you run it?"? I am supposed to run it manually?

---

### Post by VMC on 2009-09-18
> **qwerty800 said:**
> My init-bottom folder is empty too.

What do you mean by "Did you run it?"? I am supposed to run it manually?No. Someone else suggested that you shouldn't. It's as though your init scripts aren't running. Even though I get those symlink errors I progress past the init-bottom.

---

### Post by qwerty800 on 2009-09-19
Well, then...

Can you, or anybody else suggest me a way to fix my system?

---

### Post by dinxter on 2009-09-19
> **qwerty800 said:**
> Well, then...

Can you, or anybody else suggest me a way to fix my system?
all the conflicts that cause the problems you mention in the first post are resolved on an up to date  karmic. it should be as simple as updating then upgrading. 
however, the line
sudo: unable to resolve host ubuntu
makes me wonder what your file
/etc/apt/sources.list
looks like?
i'm thinking something may be wrong in there

---

### Post by dinxter on 2009-09-19
just to add, being able to update and upgrade is important, there have been a lot of changes in boot over the last week and a few problems that need the latest upstart/initscript/hal/udev/etc thats why it should be helpful in curing your boot failure

---

### Post by snooptodd on 2009-09-19
> **dinxter said:**
> all the conflicts that cause the problems you mention in the first post are resolved on an up to date  karmic. it should be as simple as updating then upgrading. 
however, the line
sudo: unable to resolve host ubuntu
makes me wonder what your file
/etc/apt/sources.list
looks like?
i'm thinking something may be wrong in there

The sudo error is weirdness from running in a chroot. I wouldn't worry about it.

To the op, you can try updating and upgrading again. it mite work. 

I will say that problem seriously broke one of my boxes, (I reinstalled.) the other 2 running karmic made it through the upgrade.

---

### Post by qwerty800 on 2009-09-19
**My source.list**
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main #PPA VLC désactivé pour la mise à niveau vers karmic
# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main #PPA VLC (Source) désactivé pour la mise à niveau vers karmic
```

Just to say, when I update, it crashes at 97%: *"Method http has died unexpectedly!"*

On upgrade and dist-upgrade, there's still only one package aviavble.

---

### Post by trulan on 2009-09-19
You're going to have to complete apt-get update successfully before apt-get upgrade is going to do any good.  I don't know how to fix it, but if update is failing, anything else you try is just a waste of time.

---

### Post by qwerty800 on 2009-09-20
Ok, i've been able to solve my update problem [thanks to this link]("http://http://michael-prokop.at/blog/2007/10/27/could-not-set-non-blocking-flag/").

I just remounted my chrooted FS (sda2) with this command:
> mount -o remount,dev /dev/sda2

I'll reboot, and we will see if it works...

---

### Post by qwerty800 on 2009-09-20
I don't understand!

The update worked, upgrade couldn't install Pulse, but that's surely a chroot issue, initscripts were upgraded without completely messing up my system...

So why do I still get the same results? (See [screenshot on post #9]("http://ubuntuforums.org/attachment.php?attachmentid=128979&d=1253296500"))

Man, I swear in front of all of you that, if I manage to fix the "Showdown of the september 15", this will have been my last pre-relase testing!

---

### Post by qwerty800 on 2009-09-21
Up!

(Nooooo!! Triple post!!:shock:)

---

### Post by qwerty800 on 2009-09-22
Awww, com-on!

It's been more than a week, and I don't feel like to reinstalling everything!
:(

---

### Post by qwerty800 on 2009-09-22
Agrh, I can't upgraade my system now, because couchdb is making trouble:

```
root@ubuntu:/# apt-get upgrade -fReading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
  pidgin-libnotify ubuntu-desktop
The following packages will be upgraded:
  aisleriot alacarte at-spi brasero bzr bzrtools couchdb dash eog evince
  evolution evolution-common evolution-couchdb evolution-documentation-en
  evolution-exchange evolution-plugins evolution-webcal f-spot file-roller
  gcalctool gconf-editor gedit gedit-common glchess glines gnect gnibbles
  gnobots2 gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth
  gnome-doc-utils gnome-games gnome-games-common gnome-keyring gnome-mag
  gnome-mahjongg gnome-media gnome-media-common gnome-network-admin gnome-orca
  gnome-power-manager gnome-sudoku gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-utils gnometris gnomine gnotravex
  gnotski gtali gucharmap iagno intltool jackd jockey-common jockey-gtk
  libatk1.0-data libatspi1.0-0 libbrasero-media0 libclutter-1.0-0
  libclutter-1.0-dev libcryptui0 libevdocument1 libevview1
  libexchange-storage1.2-3 libgcr0 libgdict-1.0-6 libglib2.0-data
  libgnome-bluetooth7 libgnome-mag2 libgnome-media0 libgp11-0
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common
  libgucharmap7 libjack0 liboobs-1-4 libpam-gnome-keyring libpangomm-1.4-1
  libtag1-vanilla libtag1c2a libtelepathy-glib0 libtotem-plparser12
  libwebkit-1.0-2 libwebkit-1.0-common linux-headers-2.6.31-10
  linux-headers-2.6.31-10-generic linux-libc-dev mountall mousetweaks
  nautilus-sendto openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer os-prober pulseaudio python-bugbuddy
  python-cupshelpers python-evince python-evolution python-gnome2-desktop
  python-gnomeapplet python-gnomedesktop python-gnomeprint
  python-gtksourceview python-gtop python-mediaprofiles python-metacity
  python-nautilusburn python-pyatspi python-rsvg python-totem-plparser
  python-uno python-wnck quilt same-gnome screen-profiles seahorse
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins ttf-liberation ttf-opensymbol uno-libs3 ure
  vim-common vim-tiny vinagre vino xscreensaver-data xscreensaver-gl
  xserver-xorg-video-ati xserver-xorg-video-radeon xserver-xorg-video-savage
  yelp zenity
159 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
291 not fully installed or removed.
Need to get 0B/148MB of archives.
After this operation, 4428kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 252503 files and directories currently installed.)
Preparing to replace couchdb 0.10.0~svn813472-0ubuntu1 (using .../couchdb_0.10.0~svn813472-0ubuntu2_i386.deb) ...
invoke-rc.d: initscript couchdb, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript couchdb, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript couchdb, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace pulseaudio 1:0.9.17-0ubuntu1 (using .../pulseaudio_1%3a0.9.18-0ubuntu2_i386.deb) ...
invoke-rc.d: initscript pulseaudio, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript pulseaudio, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/pulseaudio_1%3a0.9.18-0ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript pulseaudio, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb
 /var/cache/apt/archives/pulseaudio_1%3a0.9.18-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```
root@ubuntu:/# aptitude hold couchdbReading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  libjack-dev pulseaudio pulseaudio-esound-compat 
  pulseaudio-module-bluetooth pulseaudio-module-gconf 
  pulseaudio-module-udev pulseaudio-module-x11 
The following partially installed packages will be configured:
  anacron apparmor apparmor-utils apport apport-gtk apturl apturl-common 
  avahi-autoipd avahi-daemon avahi-utils bc binfmt-support binutils byobu 
  capplets-data command-not-found command-not-found-data compiz compiz-core 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper 
  couchdb-bin cups-driver-gutenprint dbus dbus-x11 dc desktopcouch 
  devicekit-disks dpkg-dev evolution-data-server 
  evolution-data-server-common evolution-indicator fglrx-modaliases foo2zjs 
  foomatic-db foomatic-db-engine gamin gconf-defaults-service gconf2 
  gconf2-common gdb gdm gdm-guest-session ghostscript ghostscript-cups 
  ghostscript-x gnome-about gnome-accessibility-themes gnome-control-center 
  gnome-desktop-data gnome-disk-utility gnome-icon-theme gnome-menus 
  gnome-panel gnome-panel-data gnome-session gnome-session-bin 
  gnome-session-canberra gnome-settings-daemon gnome-themes-selected gnupg 
  gpgv grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gstreamer0.10-x guile-1.8 guile-1.8-dev 
  guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse hal hdparm hpijs 
  hplip hplip-cups hplip-data ifupdown indicator-messages indicator-session 
  initramfs-tools language-pack-en language-pack-en-base language-pack-fr 
  language-pack-fr-base language-pack-gnome-en language-pack-gnome-en-base 
  language-pack-gnome-fr language-pack-gnome-fr-base language-selector 
  language-selector-common lftp libapparmor-perl libapparmor1 libatasmart4 
  libatk1.0-0 libatk1.0-dev libavahi-client-dev libavahi-client3 
  libavahi-common-data libavahi-common-dev libavahi-common3 
  libavahi-compat-libdnssd1 libavahi-core6 libavahi-glib-dev libavahi-glib1 
  libavahi-gobject0 libavahi-ui0 libcamel1.2-14 libcanberra-dev 
  libcanberra-gtk-dev libcanberra-gtk-module libcanberra-gtk0 
  libcanberra-pulse libcanberra0 libdbus-1-dev libdbusmenu-glib0 
  libdbusmenu-gtk0 libdecoration0 libebackend1.2-0 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 
  libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common 
  libempathy-gtk-common libept0 libexpat1 libexpat1-dev libffado1 libgamin0 
  libgconf2-4 libgconf2-dev libgdata-common libgdata-google1.2-1 
  libgdata1.2-1 libgdata5 libgdu-gtk0 libgdu0 libgl1-mesa-dev 
  libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0 libglib2.0-dev 
  libglibmm-2.4-1c2a libglu1-mesa libglu1-mesa-dev libgnome-desktop-2-11 
  libgnome-keyring-dev libgnome-keyring0 libgnome-menu-dev libgnome-menu2 
  libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgnomekbdui4 
  libgraphviz4 libgs8 libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 
  libgstreamer0.10-0 libgstreamer0.10-dev libgudev-1.0-0 libgutenprint2 
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 
  libindicate3 libnautilus-extension1 libnm-glib2 libnm-util1 libofa0 
  libopenexr6 libpam-smbpass libpanel-applet2-0 libpango1.0-0 
  libpango1.0-common libpango1.0-dev libparted1.8-12 libperl5.10 
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libsmbclient 
  libsqlite3-0 libusplash0 libvte-common libvte9 libwbclient0 
  libwnck-common libwnck22 libxml2 libxml2-dev libxml2-utils linux-firmware 
  linux-image-2.6.31-10-generic mesa-common-dev mesa-utils 
  module-init-tools nautilus nautilus-data network-manager odbcinst1debian1 
  openprinting-ppds parted perl perl-modules procps pulseaudio-utils pxljr 
  python-apport python-avahi python-central python-desktopcouch 
  python-desktopcouch-records python-gconf python-gmenu python-gnome2 
  python-gnomecanvas python-gnomekeyring python-gst0.10 python-libxml2 
  python-problem-report python-qt4 python-qt4-dbus python-ubuntuone-client 
  python-ubuntuone-storageprotocol python-vte python2.5 python2.5-minimal 
  rhythmbox samba samba-common samba-common-bin smbclient smbfs splix 
  sreadahead synaptic tsclient ubuntu-standard ubuntu-xsplash-artwork 
  ubuntuone-client ubuntuone-client-gnome udev ufw unixodbc usb-creator 
  usb-creator-common usb-creator-gtk usplash uuid-runtime wpasupplicant 
  x11-xserver-utils xserver-xorg-video-geode xserver-xorg-video-nv xsplash 
0 packages upgraded, 0 newly installed, 0 to remove and 161 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  pulseaudio-module-udev: Depends: pulseaudio (= 1:0.9.18-0ubuntu2) but 1:0.9.17-0ubuntu1 is installed and it is kept back.
  pulseaudio: Depends: libpulse0 (= 1:0.9.17-0ubuntu1) but 1:0.9.18-0ubuntu2 is installed.
  pulseaudio-module-bluetooth: Depends: pulseaudio (= 1:0.9.18-0ubuntu2) but 1:0.9.17-0ubuntu1 is installed and it is kept back.
  pulseaudio-module-x11: Depends: pulseaudio (= 1:0.9.18-0ubuntu2) but 1:0.9.17-0ubuntu1 is installed and it is kept back.
  pulseaudio-module-gconf: Depends: pulseaudio (= 1:0.9.18-0ubuntu2) but 1:0.9.17-0ubuntu1 is installed and it is kept back.
  libjack-dev: Depends: libjack0 (= 0.116.1-4ubuntu2) but 0.116.1-4ubuntu1 is installed and it is kept back.
  pulseaudio-esound-compat: Depends: pulseaudio (= 1:0.9.18-0ubuntu2) but 1:0.9.17-0ubuntu1 is installed and it is kept back.
E: I wasn't able to locate file for the couchdb package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
libjack-dev

Upgrade the following packages:
pulseaudio [1:0.9.17-0ubuntu1 (now) -> 1:0.9.18-0ubuntu2 (karmic)]

Score is 189

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  libjack-dev{a} 
The following packages will be upgraded:
  pulseaudio 
The following partially installed packages will be configured:
  anacron apparmor apparmor-utils apport apport-gtk apturl apturl-common 
  avahi-autoipd avahi-daemon avahi-utils bc binfmt-support binutils byobu 
  capplets-data command-not-found command-not-found-data compiz compiz-core 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper 
  couchdb-bin cups-driver-gutenprint dbus dbus-x11 dc desktopcouch 
  devicekit-disks dpkg-dev evolution-data-server 
  evolution-data-server-common evolution-indicator fglrx-modaliases foo2zjs 
  foomatic-db foomatic-db-engine gamin gconf-defaults-service gconf2 
  gconf2-common gdb gdm gdm-guest-session ghostscript ghostscript-cups 
  ghostscript-x gnome-about gnome-accessibility-themes gnome-control-center 
  gnome-desktop-data gnome-disk-utility gnome-icon-theme gnome-menus 
  gnome-panel gnome-panel-data gnome-session gnome-session-bin 
  gnome-session-canberra gnome-settings-daemon gnome-themes-selected gnupg 
  gpgv grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gstreamer0.10-x guile-1.8 guile-1.8-dev 
  guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse hal hdparm hpijs 
  hplip hplip-cups hplip-data ifupdown indicator-messages indicator-session 
  initramfs-tools language-pack-en language-pack-en-base language-pack-fr 
  language-pack-fr-base language-pack-gnome-en language-pack-gnome-en-base 
  language-pack-gnome-fr language-pack-gnome-fr-base language-selector 
  language-selector-common lftp libapparmor-perl libapparmor1 libatasmart4 
  libatk1.0-0 libatk1.0-dev libavahi-client-dev libavahi-client3 
  libavahi-common-data libavahi-common-dev libavahi-common3 
  libavahi-compat-libdnssd1 libavahi-core6 libavahi-glib-dev libavahi-glib1 
  libavahi-gobject0 libavahi-ui0 libcamel1.2-14 libcanberra-dev 
  libcanberra-gtk-dev libcanberra-gtk-module libcanberra-gtk0 
  libcanberra-pulse libcanberra0 libdbus-1-dev libdbusmenu-glib0 
  libdbusmenu-gtk0 libdecoration0 libebackend1.2-0 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 
  libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common 
  libempathy-gtk-common libept0 libexpat1 libexpat1-dev libffado1 libgamin0 
  libgconf2-4 libgconf2-dev libgdata-common libgdata-google1.2-1 
  libgdata1.2-1 libgdata5 libgdu-gtk0 libgdu0 libgl1-mesa-dev 
  libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0 libglib2.0-dev 
  libglibmm-2.4-1c2a libglu1-mesa libglu1-mesa-dev libgnome-desktop-2-11 
  libgnome-keyring-dev libgnome-keyring0 libgnome-menu-dev libgnome-menu2 
  libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgnomekbdui4 
  libgraphviz4 libgs8 libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 
  libgstreamer0.10-0 libgstreamer0.10-dev libgudev-1.0-0 libgutenprint2 
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 
  libindicate3 libnautilus-extension1 libnm-glib2 libnm-util1 libofa0 
  libopenexr6 libpam-smbpass libpanel-applet2-0 libpango1.0-0 
  libpango1.0-common libpango1.0-dev libparted1.8-12 libperl5.10 
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libsmbclient 
  libsqlite3-0 libusplash0 libvte-common libvte9 libwbclient0 
  libwnck-common libwnck22 libxml2 libxml2-dev libxml2-utils linux-firmware 
  linux-image-2.6.31-10-generic mesa-common-dev mesa-utils 
  module-init-tools nautilus nautilus-data network-manager odbcinst1debian1 
  openprinting-ppds parted perl perl-modules procps 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 
  pulseaudio-utils pxljr python-apport python-avahi python-central 
  python-desktopcouch python-desktopcouch-records python-gconf python-gmenu 
  python-gnome2 python-gnomecanvas python-gnomekeyring python-gst0.10 
  python-libxml2 python-problem-report python-qt4 python-qt4-dbus 
  python-ubuntuone-client python-ubuntuone-storageprotocol python-vte 
  python2.5 python2.5-minimal rhythmbox samba samba-common samba-common-bin 
  smbclient smbfs splix sreadahead synaptic tsclient ubuntu-standard 
  ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome udev ufw 
  unixodbc usb-creator usb-creator-common usb-creator-gtk usplash 
  uuid-runtime wpasupplicant x11-xserver-utils xserver-xorg-video-geode 
  xserver-xorg-video-nv xsplash 
1 packages upgraded, 0 newly installed, 1 to remove and 160 not upgraded.
Need to get 0B of archives. After unpacking 1577kB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the couchdb package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the couchdb package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```
```
root@ubuntu:/# aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  aptdaemon{a} libindicate-gtk1{a} python-aptdaemon{a} 
  python-aptdaemon-gtk{a} python-webkit{a} software-store{a} 
The following packages will be REMOVED:
  libffado0{u} 
The following packages will be upgraded:
  aisleriot alacarte at-spi brasero bzr bzrtools dash eog evince evolution 
  evolution-common evolution-couchdb evolution-documentation-en 
  evolution-exchange evolution-plugins evolution-webcal f-spot file-roller 
  gcalctool gconf-editor gedit gedit-common glchess glines gnect gnibbles 
  gnobots2 gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth 
  gnome-doc-utils gnome-games gnome-games-common gnome-keyring gnome-mag 
  gnome-mahjongg gnome-media gnome-media-common gnome-network-admin 
  gnome-orca gnome-power-manager gnome-sudoku gnome-system-monitor 
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-utils 
  gnometris gnomine gnotravex gnotski gtali gucharmap iagno intltool jackd 
  jockey-common jockey-gtk libatk1.0-data libatspi1.0-0 libbrasero-media0 
  libclutter-1.0-0 libclutter-1.0-dev libcryptui0 libevdocument1 libevview1 
  libexchange-storage1.2-3 libgcr0 libgdict-1.0-6 libglib2.0-data 
  libgnome-bluetooth7 libgnome-mag2 libgnome-media0 libgp11-0 
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 
  libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common 
  libgucharmap7 libjack0 liboobs-1-4 libpam-gnome-keyring libpangomm-1.4-1 
  libtag1-vanilla libtag1c2a libtelepathy-glib0 libtotem-plparser12 
  libwebkit-1.0-2 libwebkit-1.0-common linux-headers-2.6.31-10 
  linux-headers-2.6.31-10-generic linux-libc-dev mountall mousetweaks 
  nautilus-sendto openoffice.org-base-core openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-style-human 
  openoffice.org-writer os-prober pidgin-libnotify pulseaudio 
  python-bugbuddy python-cupshelpers python-evince python-evolution 
  python-gnome2-desktop python-gnomeapplet python-gnomedesktop 
  python-gnomeprint python-gtksourceview python-gtop python-mediaprofiles 
  python-metacity python-nautilusburn python-pyatspi python-rsvg 
  python-totem-plparser python-uno python-wnck quilt same-gnome 
  screen-profiles seahorse system-config-printer-common 
  system-config-printer-gnome system-config-printer-udev tomboy totem 
  totem-common totem-gstreamer totem-mozilla totem-plugins ttf-liberation 
  ttf-opensymbol ubuntu-desktop uno-libs3 ure vim-common vim-tiny vinagre 
  vino xscreensaver-data xscreensaver-gl xserver-xorg-video-ati 
  xserver-xorg-video-radeon xserver-xorg-video-savage yelp zenity 
The following partially installed packages will be configured:
  anacron apparmor apparmor-utils apport apport-gtk apturl apturl-common 
  avahi-autoipd avahi-daemon avahi-utils bc binfmt-support binutils byobu 
  capplets-data command-not-found command-not-found-data compiz compiz-core 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper 
  couchdb-bin cups-driver-gutenprint dbus dbus-x11 dc desktopcouch 
  devicekit-disks dpkg-dev evolution-data-server 
  evolution-data-server-common evolution-indicator fglrx-modaliases foo2zjs 
  foomatic-db foomatic-db-engine gamin gconf-defaults-service gconf2 
  gconf2-common gdb gdm gdm-guest-session ghostscript ghostscript-cups 
  ghostscript-x gnome-about gnome-accessibility-themes gnome-control-center 
  gnome-desktop-data gnome-disk-utility gnome-icon-theme gnome-menus 
  gnome-panel gnome-panel-data gnome-session gnome-session-bin 
  gnome-session-canberra gnome-settings-daemon gnome-themes-selected gnupg 
  gpgv grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gstreamer0.10-x guile-1.8 guile-1.8-dev 
  guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse hal hdparm hpijs 
  hplip hplip-cups hplip-data ifupdown indicator-messages indicator-session 
  initramfs-tools language-pack-en language-pack-en-base language-pack-fr 
  language-pack-fr-base language-pack-gnome-en language-pack-gnome-en-base 
  language-pack-gnome-fr language-pack-gnome-fr-base language-selector 
  language-selector-common lftp libapparmor-perl libapparmor1 libatasmart4 
  libatk1.0-0 libatk1.0-dev libavahi-client-dev libavahi-client3 
  libavahi-common-data libavahi-common-dev libavahi-common3 
  libavahi-compat-libdnssd1 libavahi-core6 libavahi-glib-dev libavahi-glib1 
  libavahi-gobject0 libavahi-ui0 libcamel1.2-14 libcanberra-dev 
  libcanberra-gtk-dev libcanberra-gtk-module libcanberra-gtk0 
  libcanberra-pulse libcanberra0 libdbus-1-dev libdbusmenu-glib0 
  libdbusmenu-gtk0 libdecoration0 libebackend1.2-0 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 
  libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common 
  libempathy-gtk-common libept0 libexpat1 libexpat1-dev libffado1 libgamin0 
  libgconf2-4 libgconf2-dev libgdata-common libgdata-google1.2-1 
  libgdata1.2-1 libgdata5 libgdu-gtk0 libgdu0 libgl1-mesa-dev 
  libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0 libglib2.0-dev 
  libglibmm-2.4-1c2a libglu1-mesa libglu1-mesa-dev libgnome-desktop-2-11 
  libgnome-keyring-dev libgnome-keyring0 libgnome-menu-dev libgnome-menu2 
  libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgnomekbdui4 
  libgraphviz4 libgs8 libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 
  libgstreamer0.10-0 libgstreamer0.10-dev libgudev-1.0-0 libgutenprint2 
  libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 
  libindicate3 libjack-dev libnautilus-extension1 libnm-glib2 libnm-util1 
  libofa0 libopenexr6 libpam-smbpass libpanel-applet2-0 libpango1.0-0 
  libpango1.0-common libpango1.0-dev libparted1.8-12 libperl5.10 
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libsmbclient 
  libsqlite3-0 libusplash0 libvte-common libvte9 libwbclient0 
  libwnck-common libwnck22 libxml2 libxml2-dev libxml2-utils linux-firmware 
  linux-image-2.6.31-10-generic mesa-common-dev mesa-utils 
  module-init-tools nautilus nautilus-data network-manager odbcinst1debian1 
  openprinting-ppds parted perl perl-modules procps 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 
  pulseaudio-utils pxljr python-apport python-avahi python-central 
  python-desktopcouch python-desktopcouch-records python-gconf python-gmenu 
  python-gnome2 python-gnomecanvas python-gnomekeyring python-gst0.10 
  python-libxml2 python-problem-report python-qt4 python-qt4-dbus 
  python-ubuntuone-client python-ubuntuone-storageprotocol python-vte 
  python2.5 python2.5-minimal rhythmbox samba samba-common samba-common-bin 
  smbclient smbfs splix sreadahead synaptic tsclient ubuntu-standard 
  ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome udev ufw 
  unixodbc usb-creator usb-creator-common usb-creator-gtk usplash 
  uuid-runtime wpasupplicant x11-xserver-utils xserver-xorg-video-geode 
  xserver-xorg-video-nv xsplash 
The following packages are RECOMMENDED but will NOT be installed:
  empathy nvidia-common 
160 packages upgraded, 6 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 6398kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the couchdb package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the couchdb package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
```
```
root@ubuntu:/# dpkg --install /media/disk-1/tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb
dpkg: error processing /media/disk-1/tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /media/disk-1/tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb
root@ubuntu:/# dpkg --install /tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.debSelecting previously deselected package couchdb.
(Reading database ... 252503 files and directories currently installed.)
Preparing to replace couchdb 0.10.0~svn813472-0ubuntu1 (using .../couchdb_0.10.0~svn813472-0ubuntu2_i386.deb) ...
invoke-rc.d: initscript couchdb, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript couchdb, action "stop" failed.
dpkg: error processing /tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript couchdb, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /tmp/couchdb_0.10.0~svn813472-0ubuntu2_i386.deb

```

---

### Post by trulan on 2009-09-22
Here is a post that helped me yesterday when synaptic, apt-get, dpkg, etc. were all barfing over a specific package:
[http://ubuntuforums.org/showpost.php?p=2728028&postcount=4](http://ubuntuforums.org/showpost.php?p=2728028&postcount=4)
This may be a bad idea and the wrong solution for you.  But it is at least an idea.  Note that you would replace 'ardour' in his instructions with 'couchdb'.  This might also break all the packages that depend on couchdb so you'll want to check what depends on that before you do anything.

This is not necessarily a safe procedure but it worked for me.  In my case the problems were mostly self-inflicted and this fixed it right up.  I don't know if this will help you or not but it's another idea for you to investigate.

---

### Post by qwerty800 on 2009-09-23
I updated once again my cache, and this time used those two commands...
```
sudo mount --bind /proc /media/disk-1/proc
sudo mount --bind /sys /media/disk-1/sys
```
...before to Chroot.

It SEEMED to update flawlessly, but I wouldn't be really surprised to see THE black screen again.

---

### Post by qwerty800 on 2009-09-23
Ok, now, it boots!

It don't display anything graphical (GDM apparentry gone mad), but I'll do another topic for that, since the title is not very appropriate anymore.

---

