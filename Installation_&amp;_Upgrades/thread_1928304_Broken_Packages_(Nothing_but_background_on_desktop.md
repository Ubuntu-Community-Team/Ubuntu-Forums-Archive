---
title: "Broken Packages (Nothing but background on desktop)"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by c00lr0d on 2012-02-19
i restarted the computer and logged in nothing but the background comes up it happed while i was removing packages off my computer i might have removed something i shouldn't have (Not meaning to) i think it was python-central i did try to reinstall it but it did not work. i am using Ubuntu hardy LTS

---

### Post by cortman on 2012-02-19
Oh boy. Don't mess with Python packages at all, they're pretty integral.

Have you tried opening a terminal (Ctrl+Alt+t) and running

```
sudo apt-get install -f
```

to fix the broken packages?

---

### Post by c00lr0d on 2012-02-20
shortcut key doesn't work it just displays my background with a arrow nothing else but i can get in the text based Ubuntu with CTRL+ALT+F1 and i tried that nothing special

---

### Post by c00lr0d on 2012-02-20
> **c00lr0d said:**
> shortcut key doesn't work it just displays my background with a arrow nothing else but i can get in the text based Ubuntu with CTRL+ALT+F1 and i tried that nothing special i can get into the internet ok because i got a key on my keyboard that brings up the internet but i cant bring any other apps because my desktop shortcuts and top bar wont come up

---

### Post by cortman on 2012-02-20
If you can get to a command line with Ctrl+Alt+F1, run the command given above in it, and post the results.

---

### Post by c00lr0d on 2012-02-20
Here it is
```
monna@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sg3-utils lirc menu-xdg python-gtk2-doc menu libarts1c2a libmtp7 libarchive1
  gnome-games-extra-data hal-cups-utils libgcj8-1 xfonts-scalable
  libgail-gnome-module debhelper libsensors3 tracker libgcj-bc intltool-debian
  kdenlive-data libsnmp15 untex guidance-backends
  openoffice.org-filter-binfilter libgda3-common python-gnomecanvas libbtctl4
  openoffice.org-java-common gnome-bluetooth tracker-utils
  parallels-modules-2.6.24-25-generic python-mysqldb cupsddk app-install-data
  gnome-cards-data ggzcore-bin ttf-dustin bsh-gcj kdelibs-data
  python-gtksourceview2 libjaxp1.3-java-gcj dvd+rw-tools python-gtkglext1 m4
  update-notifier-common po-debconf openoffice.org-writer2latex libggzmod4
  ncurses-term liblualib50 libxml-twig-perl libgdl-gnome-1-0 libgcj8-jar
  libsgutils1 python-pyorbit python-gconf wv nautilus-data libgpod3
  libxerces2-java-gcj system-tools-backends libgweather1 python-configobj
  libeel2-data xfonts-75dpi guile-1.6-libs gedit-common gnome-utils
  python-openssl setserial gettext libxevie1 python-celementtree
  libnet-dbus-perl bsh gnome-about libcdio-cdda0 gcj-4.2-base python-soappy
  capplets-data libavahi-qt3-1 libgcj-common libwv-1.2-3 expect python-brlapi
  python-xdg deborphan libjaxp1.3-java libggz2 icedax libgweather-common
  at-spi python-pyopenssl libgcj8-1-awt libjline-java mousetweaks
  gnome-system-monitor system-config-printer-common libxerces2-java pax
  libqthreads-12 gnome-games-data libdbus-qt-1-1c2 recordmydesktop
  libwps-0.1-1 dpkg-dev libxalan2-java libgpod-common xfonts-100dpi cdrdao
  libgnomevfs2-bin libgnome-speech7 tcl8.4 cupsddk-drivers libtie-ixhash-perl
  libxml-xpath-perl libcdio-paranoia0 synaptic libeel2-2 python-cups
  tracker-search-tool python-fpconst gnome-netstatus-applet parallels-modules
  gnome-terminal-data liboobs-1-4 libgda3-3 libsnmp-base html2text libggzcore9
  imagemagick gnome-system-tools libgnomebt0 gvfs gvfs-backends liblua50
  libmlt-data gnome-applets-data alien libtracker-gtk0 libguile-ltdl-1
  libgtkglext1 vnc4-common libscrollkeeper0 python-twisted-bin libgdl-1-0
  libxalan2-java-gcj gnome-panel-data o3read hplip-data libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by cortman on 2012-02-20
Ok, run

```
sudo apt-get install gnome-shell
```

and see if you get your DE back.

---

### Post by c00lr0d on 2012-02-20
this is what came up ```
monna@ubuntu:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-shell

```

---

### Post by snowpine on 2012-02-20
It was called **ubuntu-desktop** back in 8.04, however you may not be able to install it easily since 8.04 Desktop is "end of life."

---

### Post by c00lr0d on 2012-02-20
I have tried to install ubuntu-desktop it says ```
monna@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gimp-python but it is not going to be installed
E: Broken packages
monna@ubuntu:~$ 

```

---

### Post by snowpine on 2012-02-20
Making progress, now:

```
sudo apt-get install -f
```

Although you might run into the problem that 8.04 is end of support.

---

### Post by cortman on 2012-02-20
At this point (having realized the OP is running Hardy) I would say the best bet would be to reinstall, and install 10.04 or later. You can copy your data off using a live CD, and reinstall.

---

### Post by c00lr0d on 2012-02-25
ok i will i got a usb stick so i can install from usb so thanks for your help

---

