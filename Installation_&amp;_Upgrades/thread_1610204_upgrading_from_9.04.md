---
title: "upgrading from 9.04"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by faintscrawl on 2010-10-31
Hi,

I'm trying to upgrade from 9.1. Originally I was using update manager, but the upgrade failed. Now I have a big icon red with white line on the top toolbar. When I hover over it, it tells me to run Package Manager in order to fix Broken Packages. However, that doesn't work. If I try to run the upgrade again I end up being told to use the terminal and run sudo apt-get install -f. When I do that I get the following ...

tom@Franz:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bluez-alsa melt evolution-data-server-dbg libgsf-gnome-1-114
  firefox-3.5-branding libglitz-glx1 libatk1.0-dbg bluez-gstreamer swh-plugins
  libgsf-1-114-dbg kdenlive-data wine-gecko libmpeg3cv
  xulrunner-1.9.1-gnome-support libseed0 libmlt++2 libcvaux1 evince-dbg upower
  libpango1.0-0-dbg libgnomedb3-common libgnomedb3-4 libgnomevfs2-0-dbg
  epiphany-browser-data gobject-introspection-glib-2.0 evolution-dbg
  libatspi-dbg liblog4j1.2-java libupower-glib1 libflac++6 mesa-common-dev
  gobject-introspection-repository frei0r-plugins libxft2-dbg python-utidylib
  gobject-introspection libfontconfig1-dbg libgoffice-dbg libflickrnet2.2-cil
  libgsf-gnome-1-114-dbg libtidy-0.99-0 libgda3-sqlite
  gstreamer0.10-plugins-ugly-dbg libfltk1.1 libgavl1 libgnomedb3-bin
  libloudmouth1-0-dbg python-feedparser libgirepository1.0-0
  gobject-introspection-freedesktop libglitz1 firefox-3.5-gnome-support
  gnome-panel-dbg libdbus-qt-1-1c2 x11proto-fixes-dev libcv1 libgnomedb3-4-dbg
  gnome-js-common libgoffice-0-8 libsox-fmt-base nautilus-dbg
  libgtkhtml3.14-dbg libhighgui1 libquicktimecv libgcj9-0-awt libsox-fmt-alsa
  rhino gnome-applets-dbg liboobs-1-4-dbg python-4suite-xml libgda3-3-dbg
  optlibx11-noxcb-data libguicastcv libgnomeui-0-dbg libxft-dev
  libgnome-keyring1.0-cil libxfixes-dev libsox1a libmlt-data totem-dbg
  optlibx11-noxcb-6 libgail-gnome-dbg libmx4j-java libmlt1 libmpeg3-1
  libgoffice-0-8-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  consolekit fontconfig-config gdm ifupdown indicator-applet
  indicator-applet-session initramfs-tools initramfs-tools-bin libatk1.0-0
  libc-dev-bin libc6-dev libc6-i686 libdevkit-power-gobject1 libdrm-nouveau1
  libdrm-radeon1 libfontconfig1 libfontconfig1-dbg libfontconfig1-dev
  libindicator0 libnih-dbus1 libnih1 libplymouth2 libpopt0 libudev0
  libupower-glib1 libxklavier16 manpages-dev mountall plymouth
  plymouth-theme-ubuntu-text udev upower upstart ureadahead
Suggested packages:
  uswsusp gnome-orca gok glibc-doc watershed
Recommended packages:
  indicator-sound indicator-application indicator-me libatk1.0-data
The following packages will be REMOVED:
  devicekit-power gnome-power-manager indicator-session usplash
  usplash-theme-ubuntu
The following NEW packages will be installed:
  initramfs-tools-bin libdrm-nouveau1 libindicator0 libnih-dbus1 libnih1
  libplymouth2 libupower-glib1 libxklavier16 manpages-dev plymouth
  plymouth-theme-ubuntu-text upower
The following packages will be upgraded:
  consolekit fontconfig-config gdm ifupdown indicator-applet
  indicator-applet-session initramfs-tools libatk1.0-0 libc-dev-bin libc6-dev
  libc6-i686 libdevkit-power-gobject1 libdrm-radeon1 libfontconfig1
  libfontconfig1-dbg libfontconfig1-dev libpopt0 libudev0 mountall udev
  upstart ureadahead
22 upgraded, 12 newly installed, 5 to remove and 1610 not upgraded.
1 not fully installed or removed.
Need to get 0B/12.7MB of archives.
After this operation, 4,755kB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on mountall
tom@Franz:~$ 

Any tips on what I should do from here?

Thanks!

---

### Post by Enigmapond on 2010-10-31
In all honesty, I would just back-up your home directory and do a fresh install off of a Live CD. You can fix broken packages with synaptic but you may encounter problems in the upgrade...just my opinion. Hope this helps.

Cheers!

---

### Post by faintscrawl on 2010-10-31
Thanks. You're probably be right. And it's been a long time since I did a fresh install.

What's the easiest way to back-up and then re-load 'home'? Just drag it to usb key and then drag it back after I've installed the new os?

Thanks.

---

### Post by Enigmapond on 2010-10-31
That's what I would do..just keep the things you definitely don't want to lose. I tried to upgrade from Jaunty to Lucid and it didn't go that well and since I did a fresh install I'm virtually bug free as I was in Jaunty..Good Luck!:)

---

### Post by ziffolo on 2010-10-31
oh damn I should have read this post earlier -.-'

---

### Post by faintscrawl on 2010-10-31
So I created a USB startup disc, turn off computer, restarted and it completely bypassed the usb and booted up as usual. I made a bootable dvd and the same thing happened?

Any ideas.

Thanks.

---

### Post by Enigmapond on 2010-10-31
Yes you need to change the bios on your computer to boot from USB or CD. Usually right at the start-up if you press F8 or F12 (some computers are different), it will bring up a screen that you can change this.

---

### Post by faintscrawl on 2010-10-31
I thought I'd done that, but I tried again and it worked. I have a new problem, though.

When I get to the Who are You? part of the installation, I fill in my username, password, etc, but it doesn't give me the option of going forward. Eventually it says it's waiting for me, but the "forward" button won't light up and become activated.

Also, I can't connect to the internet. Do you need to have access to the internet to complete the installation?

Thanks so much.

---

### Post by faintscrawl on 2010-10-31
Ha. Figured it out. Common problem. Can't use uppercase in username. Someone should fix this because I got a green checkmark beside a username with a capital.

I like Ubuntu but would never be able to use it if it weren't for my reliable, easy-to-use Mac that let me connect to the internet and ask silly questions that get Ubuntu, shuddering and clunky, to take off. (It does fly nicely, though, once it's in the air.)

Now to figure out my internet issue. I had to go through it last time I upgraded too.  Oh, joy.

---

