---
title: "Testing system for Consolekit libpam dbus bugs"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TDFlanders on 2008-10-19
Hi,

There is a problem with authentication under 8.10, which a lot of users experience.

I have started a thread about this on launchpad. It is a bundle of my crashes so far, due to dbus and unsafe ownership of /home/$USER.

The bug squad team have great difficulties tracking down these bugs because they have a different system setup. Also the developers cannot reproduce most of these crashes because of the same reason.

The problem is that they use their system in a way that Newbies do not.

What lies at the cause of this problem is the following:

A) If you download packages through the gnome-terminal you will have to call root: '$ sudo apt-get ...'. The default download folder for this /home/$USER. This means that all packages you download their are owned by root.

If you open nautilus in the gui, you will in fact open '$ nautilus ...' and not '$ sudo nautilus ...'. This means that you cannot move any source packages to the waste bin. If you open '$ sudo nautilus' you can change read and write permissions through the gui (right click > properties > permissions) but you still cannot change ownership in group. That is: you have to snipe out every individual file, you cannot use ctrl+A and ctrl-left_click to unselect.

This makes it very tempting for newbies to just: '$ cd ; sudo chmod -cR 777 . ; sudo chown -cR 1000 .'. An experienced user would never do that. I read an idea in the idea pool to make a filesystem permissions and ownership back up tool, dating back to 2006. To may best knowledge nothing has become of it so far.

Anyway, the above command leads to unsafe ownership of a number of hidden files:

thomas@thomas-laptop:~$ ls -la  ~/.dbus/* ~/.dmrc ~/.gnupg/* ~/.gvfs ~/.Xauthority ~/.ICEauthority ~/.pulse/* ~/.compiz
-rwxrwxrwx 1 thomas thomas    28 2008-10-15 21:29 /home/thomas/.dmrc
-rwxrwxrwx 1 thomas thomas    28 2008-10-03 00:49 /home/thomas/.gnupg/gpg.conf
-rwxrwxrwx 1 thomas thomas     0 2008-10-03 00:49 /home/thomas/.gnupg/pubring.gpg
-rwxrwxrwx 1 thomas thomas     0 2008-10-03 00:49 /home/thomas/.gnupg/secring.gpg
-rwxrwxrwx 1 thomas thomas    40 2008-10-03 00:49 /home/thomas/.gnupg/trustdb.gpg
-rwxrwxrwx 1 thomas thomas 21293 2008-10-19 21:07 /home/thomas/.ICEauthority
-rwxrwxrwx 1 thomas thomas    55 2008-10-03 10:02 /home/thomas/.pulse/default-sink
-rwxrwxrwx 1 thomas thomas     1 2008-10-03 10:02 /home/thomas/.pulse/default-source
-rwxrwxrwx 1 thomas thomas   872 2008-10-19 19:00 /home/thomas/.pulse/volume-restore.table
-rwxrwxrwx 1 thomas thomas   173 2008-10-17 04:27 /home/thomas/.Xauthority

/home/thomas/.compiz:
total 20
drwxrwxrwx  3 thomas thomas  4096 2008-10-03 00:27 .
drwxrwxrwx 92 thomas thomas 12288 2008-10-20 00:31 ..
drwxrwxrwx  2 thomas thomas  4096 2008-10-09 16:00 session

/home/thomas/.dbus/session-bus:
total 12
drwxrwxrwx 2 thomas root 4096 2008-10-03 00:57 .
drwxrwxrwx 3 thomas root 4096 2008-10-03 00:57 ..
-rwxrwxrwx 1 thomas root  465 2008-10-19 22:58 00e2e23118afd712ae53375648e55de3-0

/home/thomas/.gvfs:
total 12
dr-x------  2 thomas thomas     0 2008-10-19 21:07 .
drwxrwxrwx 92 thomas thomas 12288 2008-10-20 00:31 ..
thomas@thomas-laptop:~$ 

B) Another problem may be that users activate too many authentication services:

thomas@thomas-laptop:~$ sudo dpkg-reconfigure -p low debconf ; sudo dpkg-reconfigure -p low libpam-ldap
[sudo] password for thomas: 
Configuring debconf
-------------------

Packages that use debconf for configuration share a common look and feel. You can select the type of user interface they use.

The dialog frontend is a full-screen, character based interface, while the readline frontend uses a more traditional plain text interface, and both the gnome and kde frontends 
are modern X interfaces, fitting the respective desktops (but may be used in any X environment). The editor frontend lets you configure things using your favorite text editor. 
The noninteractive frontend never asks you any questions.

  1. Dialog  2. Readline  3. Gnome  4. Kde  5. Editor  6. Noninteractive

Interface to use: 2


Debconf prioritizes the questions it asks you. Pick the lowest priority of question you want to see:
  - 'critical' only prompts you if the system might break.
    Pick it if you are a newbie, or in a hurry.
  - 'high' is for rather important questions
  - 'medium' is for normal questions
  - 'low' is for control freaks who want to see everything


Note that no matter what level you pick here, you will be able to see every question if you reconfigure a package with dpkg-reconfigure.

  1. critical  2. high  3. medium  4. low

Ignore questions with a priority less than: 4


Pluggable Authentication Modules (PAM) determine how authentication, authorization, and password changing are handled on the system, as well as allowing configuration of 
additional actions to take when starting user sessions.

Some PAM module packages provide profiles that can be used to automatically adjust the behavior of all PAM-using applications on the system.  Please indicate which of these 
behaviors you wish to enable.

  1. Cracklib password strength checking  2. Likewise Open  3. Unix authentication  4. LDAP Authentication  5. ConsoleKit Session Management  6. none of the above

(Enter the items you want to select, separated by spaces.)

PAM profiles to enable: 1 2 3 4 5


thomas@thomas-laptop:~$ 

C) If you use your system in this way it will become highly unstable and you will experience a number of crashes that the bug squad can not easily verify.

You can test whether a bug is due to this issue or not by running rsync and aptoncd and installing in a Virtual Machine. If you copy the virtual harddisk and mess up your system as described above, you will be able to check for differences. I would like to tell you though that the 'messed up' system will function remarkably well, other then experiencing a number of fatal system crashes, that are not easy to debug, since fatal off course, but also unpredictable.

A way to test this is to start all affected applications under valgrind and attach pidof in strace and gdb.

Commands that trigger the problem:

e.g. bogus pipes:

sudo compiz | compiz
sudo x-session-manager | pulseaudio

or

metacity --replace
compiz --replace

Involved applications are:

compiz
compiz.real 
bzr (certificate problem: unsafe ownership of .gnupg)
ca-certificates (idem)
canberra-gtk-play
hald-volume-monitor (or something like that)
gnome-session 
x-session-manager
console-kit-daemon
metacity
dbus-launch
dbus-session

and many more

All these applications have in common that they need to be authorized by consolekit (and or PAM etc.) to access /var/run/dbus/system_bus_socket

I noticed this in the /var/log files (TIP: run '$ sudo dpkg-reconfigure -ap low' and enable logging for absolutely everything)

It seems to me that consolekit may be involved in nearly all of my bugs.

If you try and run the following command:

'$ sudo apt-get remove consolekit'

you may begin to believe ...  

thomas@thomas-laptop:~$ sudo apt-get remove consolekit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bluez-alsa nvidia-71-modaliases libarts1c2a kdelibs4c2a libglitz-glx1 python-pexpect bluez-gstreamer libuser-perl nvidia-177-modaliases libgda3-common python-glade2-dbg
  gdesklets-data python-pycurl python-pyxattr kdelibs-data python-dbus-dbg liblualib50 gnumeric-common libmono-cairo2.0-cil python-utidylib deluge-torrent-common pptp-linux
  python-cairo-dbg python-pyorbit-dbg libgoffice-0-6-common libtidy-0.99-0 python-gconf-dbg python-soappy libavahi-qt3-1 libavahi-gobject0 python-4suite-doc icedax
  libnet-google-perl python-feedparser libemail-date-format-perl libglitz1 hddtemp python-numeric-dbg libwww-search-perl nvidia-173-modaliases libpkcs11-helper1
  libgnomesu-common rdiff-backup libmime-lite-perl python-setuptools python-pylibacl python-fpconst python-4suite-xml nvidia-common libgda3-bin libgda3-3 libjcode-pm-perl
  libgnome-keyring1.0-cil python-smartpm openvpn liblua50 python-gnomecanvas-dbg python-chardet gstreamer0.10-gnonlin librsync1 nvidia-96-modaliases libgdl-1-0
  openvpn-blacklist python-gobject-dbg python-rdflib python-gtk2-dbg libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  adept adept-dbgsym alacarte alleyoop aptoncd avahi-daemon avahi-utils bluetooth bluez bluez-gnome bluez-utils brasero bug-buddy compiz compiz-gnome compiz-gnome-dbgsym
  consolekit contact-lookup-applet contact-lookup-applet-dbgsym dbus dbus-x11 deluge-torrent deluge-torrent-dbgsym deskbar-applet deskbar-applet-dbg dhcdbd dvd95 ekiga eog
  evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet file-roller firefox-3.0-gnome-support
  firefox-gnome-support firestarter firestarter-dbgsym gconf-editor gdesklets gmail-notify gnome-about gnome-applets gnome-applets-dbgsym gnome-control-center gnome-games
  gnome-media gnome-mount gnome-netstatus-applet gnome-orca gnome-panel gnome-panel-dbg gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-settings-daemon gnome-spell gnome-terminal gnome-user-guide gnome-utils gnome-volume-manager gnomebaker gnumeric gstreamer0.10-gnomevfs hal hal-cups-utils
  isight-firmware-tools jockey-common jockey-gtk kde-window-manager kdebase-runtime kdebase-runtime-bin-kde4 kdelibs-bin kdelibs5 khelpcenter4 kwin kwin-style-alphacube
  kwin-style-alphacube-dbgsym landscape-client libbonoboui2-0 libdeskbar-tracker libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libeel2-2 libexchange-storage1.2-3 libgail-gnome-module libgnome-desktop-2 libgnome-desktop-2-7 libgnome-media0 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomesu0 libgnomesu0-dbgsym libgnomeui-0 libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-extra libgoffice-0-6
  libgsf-gnome-1-114 libgtkhtml-editor0 libgtkhtml3.14-19 libgtkhtml3.16-cil libkdecorations4 libkwineffects1 liblpint-bonobo0 libnss-mdns libnss-mdns-dbgsym libpam-blue
  libpam-blue-dbgsym libpanel-applet2-0 libswt-gnome-gtk-3.4-jni mousetweaks nautilus nautilus-cd-burner nautilus-dbg nautilus-share network-manager network-manager-gnome
  network-manager-openvpn network-manager-pptp openoffice.org-gnome pamusb-tools pitivi policykit policykit-gnome pulseaudio-module-hal pybackpack python-gnome2
  python-gnome2-dbg python-gnome2-desktop python-gnome2-desktop-dbg python-gnome2-extras python-gnome2-extras-dbg python-pyatspi rhythmbox screenlets seahorse-plugins
  serpentine sound-juicer soundconverter system-config-printer-gnome thoggen tomboy totem totem-dbg totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool
  tsclient ubuntu-desktop ubuntu-docs ubuntu-system-service update-notifier vinagre vino vuze xulrunner-1.9-gnome-support yelp
0 upgraded, 0 newly installed, 172 to remove and 0 not upgraded.
After this operation, 503MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
thomas@thomas-laptop:~$ 

Suggested solutions:

Make nautilus able to change ownership and permissions in bulk, also when called without sudo, or maybe only for /home or /home/$USER

Replace all sensitive hidden files in /home/$USER with symlinks that will not be affected.

Wright a warning in gnome-terminal that pops up when chmod, chown and such are called within /home/$USER. For instance ask: also hidden files? (-R)

Wright a warning when about to install a superfluous combination of authentication services.

Write some good howto's for newbies.

BTW: To track this problem down further: Try and make a list of the most common crashes in launchpad that are standing open for quite a long time, without a debug report. Compare it with the build-dep of consolekit and libpam and such. That should help you track down the malfunctioning applications.

Cheers,

Thomas

---

### Post by TDFlanders on 2008-10-19
You can also try to ask people who seemingly post non reproducible bugs on the forum to list the permission settings of the affected /home/$USER/files. Or you can ask them if they remember having received any of the following error messages:

1) On startup, after the login window:

User's $HOME/.dmrc file is being ignored.This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users.

2) gpg: WARNING: unsafe ownership on configuration file `/home/$USER/.gnupg/gpg.conf'

---

### Post by TDFlanders on 2008-10-19
Reported by  tdflanders on 2008-10-16
(undecided) Bug #284653:
This report is public
Consolekit crashes due to /var/dbus/system_bus_socket

(The title should have been [...] /var/run/dbus/system_bus_socket)

---

