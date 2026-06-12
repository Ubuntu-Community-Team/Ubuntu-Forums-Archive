---
title: "Synaptic uninstall uninstalling libusb-0.1-4 blows away a lot more"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by abowyer1540 on 2010-02-07
Synaptic 0.62.5

When uninstalling libusb-0.1-4, it removes many other unassociated applications (like gnome-desktop, evolution, the kernel in the /boot directory... not nice. See below with a simulated apt-get remove libusb-0.1-4.

Linux hpmaindesktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

hpmain@hpmaindesktop:~$ sudo apt-get -s remove libusb-0.1-4
[sudo] password for hpmain: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.1-dev g++-4.1 libgtk2-ruby1.8 ruby1.8 ruby libreadline5
  libgconf2-ruby1.8 libgconf2-ruby libglib2-ruby1.8 libglade2-ruby1.8
  libcairo-ruby1.8 libatk1-ruby1.8 libpango1-ruby1.8 libglade2-ruby libruby1.8
  libgdk-pixbuf2-ruby1.8
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpi-support alsa-base apparmor apturl bluetooth bluez bluez-cups bluez-utils
  brltty brltty-x11 checkbox checkbox-gtk computer-janitor computer-janitor-gtk
  console-setup cups cups-driver-gutenprint devicekit-power evolution
  evolution-couchdb evolution-exchange evolution-indicator evolution-plugins
  f-spot foo2zjs foomatic-db foomatic-db-engine fuse-utils gdm
  gdm-guest-session ghostscript-cups gnome-bluetooth gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-session gnome-session-bin
  gnupg gvfs-backends gvfs-fuse hal hpijs hplip indicator-applet-session
  indicator-session initramfs-tools kbd libdevkit-power-gobject1
  libgnome-pilot2 libgpgme11 libgphoto2-2 libgphoto2-port0 libmtp8 libopenobex1
  libpisock9 libpisync1 libsane libusb-0.1-4 linux-image-2.6.31-19-generic
  media-player-info obex-data-server obexd-client openprinting-ppds pcmciautils
  pm-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pxljr
  python-gnupginterface python-software-properties rhythmbox sane-utils
  seahorse software-properties-gtk splix ubufox ubuntu-desktop udev
  update-manager update-manager-core update-notifier usbutils usplash
  usplash-theme-ubuntu wireless-crda xorg xsane xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom
0 upgraded, 0 newly installed, 99 to remove and 0 not upgraded.
Remv acpi-support [0.129]
Remv ubuntu-desktop [1.175]
Remv alsa-base [1.0.20+dfsg-1ubuntu5]
Remv apparmor [2.3.1+1403-0ubuntu27.3]
Remv ubufox [0.8-0ubuntu1]
Remv apturl [0.4.1ubuntu2]
Remv bluez-utils [4.51-0ubuntu2]
Remv bluetooth [4.51-0ubuntu2]
Remv gnome-bluetooth [2.28.1-0ubuntu2]
Remv bluez [4.51-0ubuntu2]
Remv bluez-cups [4.51-0ubuntu2]
Remv brltty-x11 [4.0-7ubuntu2]
Remv brltty [4.0-7ubuntu2]
Remv checkbox-gtk [0.8.6]
Remv checkbox [0.8.6]
Remv computer-janitor-gtk [1.13.3-0ubuntu2]
Remv computer-janitor [1.13.3-0ubuntu2]
Remv xserver-xorg-input-wacom [1:0.8.4.1-0ubuntu4] [xserver-xorg-input-all ]
Remv xserver-xorg-input-vmmouse [1:12.6.4-1ubuntu3] [xserver-xorg-input-all ]
Remv xserver-xorg-input-synaptics [1.1.2-1ubuntu7] [xserver-xorg-input-all ]
Remv xserver-xorg-input-mouse [1:1.4.0-2] [xserver-xorg-input-all ]
Remv xserver-xorg-input-evdev [1:2.2.5-1ubuntu6] [xserver-xorg-input-all xserver-xorg ]
Remv xserver-xorg-core [2:1.6.4-2ubuntu4.1] [xserver-xorg-input-all xserver-xorg ]
Remv xorg [1:7.4+3ubuntu10] [xserver-xorg-input-all xserver-xorg ]
Remv xserver-xorg [1:7.4+3ubuntu10] [xserver-xorg-input-all ]
Remv xserver-xorg-input-all [1:7.4+3ubuntu10]
Remv indicator-applet-session [0.2.0-0ubuntu2]
Remv indicator-session [0.1.7-0ubuntu3]
Remv gdm-guest-session [0.14]
Remv gdm [2.28.1-0ubuntu2.1]
Remv pm-utils [1.2.5-2ubuntu7]
Remv kbd [1.15-1ubuntu1]
Remv console-setup [1.34ubuntu4]
Remv splix [2.0.0-2ubuntu2]
Remv pxljr [1.1-0ubuntu7]
Remv openprinting-ppds [20090825-0ubuntu4]
Remv hpijs [3.9.8-1ubuntu2]
Remv hplip [3.9.8-1ubuntu2]
Remv cups-driver-gutenprint [5.2.4-0ubuntu2]
Remv ghostscript-cups [8.70.dfsg.1-0ubuntu3]
Remv foomatic-db-engine [4.0.3-0ubuntu2] [foomatic-db ]
Remv foomatic-db [20090825-0ubuntu4]
Remv foo2zjs [20090623-0ubuntu5]
Remv cups [1.4.1-5ubuntu2.1]
Remv gnome-power-manager [2.28.1-0ubuntu1.3]
Remv devicekit-power [011-1ubuntu2]
Remv evolution-plugins [2.28.1-0ubuntu2]
Remv evolution-indicator [0.2.4-0ubuntu3.1]
Remv evolution-exchange [2.28.1-0ubuntu1]
Remv evolution-couchdb [0.3.2-0ubuntu2]
Remv evolution [2.28.1-0ubuntu2]
Remv f-spot [0.6.1.5-0ubuntu1]
Remv gvfs-fuse [1.4.1-0ubuntu1]
Remv fuse-utils [2.7.4-1.1ubuntu4.3]
Remv gnome-pilot-conduits [2.0.15-1.2]
Remv gnome-pilot [2.0.17-0ubuntu2]
Remv gnome-session [2.28.0-0ubuntu5]
Remv gnome-session-bin [2.28.0-0ubuntu5]
Remv seahorse [2.28.1-0ubuntu1]
Remv update-notifier [0.90]
Remv update-manager [1:0.126.9]
Remv update-manager-core [1:0.126.9]
Remv software-properties-gtk [0.75.4]
Remv python-software-properties [0.75.4]
Remv python-gnupginterface [0.3.2-9ubuntu2]
Remv libgpgme11 [1.1.8-2ubuntu3]
Remv gnupg [1.4.9-4ubuntu7]
Remv gvfs-backends [1.4.1-0ubuntu1]
Remv hal [0.5.13-1ubuntu8]
Remv pulseaudio-module-x11 [1:0.9.19-0ubuntu4.1]
Remv pulseaudio-module-gconf [1:0.9.19-0ubuntu4.1]
Remv pulseaudio-module-bluetooth [1:0.9.19-0ubuntu4.1]
Remv pulseaudio-esound-compat [1:0.9.19-0ubuntu4.1]
Remv pulseaudio-module-udev [1:0.9.19-0ubuntu4.1] [pulseaudio ]
Remv pulseaudio [1:0.9.19-0ubuntu4.1]
Remv linux-image-2.6.31-19-generic [2.6.31-19.56]
Remv wireless-crda [1.10]
Remv pcmciautils [014-4ubuntu3]
Remv rhythmbox [0.12.5-0ubuntu5.2]
Remv media-player-info [3-0ubuntu1]
Remv xsane [0.996-2ubuntu1.1]
Remv sane-utils [1.0.20-4ubuntu3]
Remv libsane [1.0.20-4ubuntu3]
Remv usplash-theme-ubuntu [0.27]
Remv usplash [0.5.49]
Remv initramfs-tools [0.92bubuntu53] [udev ]
Remv udev [147~-6.1]
Remv libdevkit-power-gobject1 [011-1ubuntu2]
Remv libgnome-pilot2 [2.0.17-0ubuntu2]
Remv libgphoto2-2 [2.4.6-1ubuntu6]
Remv libgphoto2-port0 [2.4.6-1ubuntu6]
Remv libmtp8 [0.3.7-3ubuntu2]
Remv obexd-client [0.14-0ubuntu1]
Remv obex-data-server [0.4.4-2build1]
Remv libopenobex1 [1.5-2]
Remv libpisync1 [0.12.4-3ubuntu1]
Remv libpisock9 [0.12.4-3ubuntu1]
Remv usbutils [0.82-0ubuntu1]
Remv libusb-0.1-4 [2:0.1.12-13]
hpmain@hpmaindesktop:~$ 


I guess I should have checked this before removing for real as it blew away my desktop, boot kernel, etc.  Time now to re-install packages.  :icon_frown:


[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by mushwars on 2010-02-07
Whatever you do, dont restart your computer or anything untill you have them all reinstalled, or you will come up to a terminal only and no desktop.

Try to install packages that have a LOT of dependencies like ubuntu-desktop first, they will install everything else then you can pick off the stragglers.

good luck, sorry for your loss.

install xserver-xorg before you intsall ubuntu-desktop or you will have problems.

---

### Post by abowyer1540 on 2010-02-07
Yes, thanks, I kept my head and did as you said. Thankfully I've achieved a full reboot cycle :)



> **mushwars said:**
> Whatever you do, dont restart your computer or anything untill you have them all reinstalled, or you will come up to a terminal only and no desktop.

Try to install packages that have a LOT of dependencies like ubuntu-desktop first, they will install everything else then you can pick off the stragglers.

good luck, sorry for your loss.

install xserver-xorg before you intsall ubuntu-desktop or you will have problems.

---

