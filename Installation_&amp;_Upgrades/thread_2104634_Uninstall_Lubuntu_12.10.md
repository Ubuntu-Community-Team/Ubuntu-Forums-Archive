---
title: "Uninstall Lubuntu 12.10"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by IronLyon on 2013-01-13
I installed Lubuntu 12.10 on my laptop, but have decided to use Ubuntu instead. The problem is, I want to remove Lubuntu and am unable to. I have tried using the method provided by other users which is :

"sudo apt-get purge --auto-remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview  ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg  elementary-icon-theme esound-common galculator gdebi gdebi-core  gecko-mediaplayer giblib1 gnome-icon-theme-full gnome-mplayer gnome-system-tools  gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview  gtk2-engines-pixbuf guvcview hardinfo indicator-status-provider-pidgin leafpad  libaacs0 libabiword-2.9 libaudclient2 libaudcore1 libaudiofile1 libbinio1ldbl  libbluray1 libbs2b0 libcddb2 libcompfaceg1 libcue1 libencode-locale-perl  libept1.4.12 libesd0 libexo-1-0 libexo-common libexo-helpers  libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1  libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgmlib0  libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2  libgsf-1-114 libgsf-1-common libgtkmathview0c2a libguess1 libhtml-form-perl  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl  libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl  libio-socket-ssl-perl libjpeg-progs libjpeg-turbo-progs liblink-grammar4  libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl  libmailtools-perl libmcrypt4 libmenu-cache1 libmowgli2 libmpg123-0  libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libobrender27 libobt0  libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libresid-builder0c2a  libsidplay2 libsocket6-perl libtar0 libtidy-0.99-0 libtie-ixhash-perl  libtimedate-perl libuniconf4.6 liburi-perl libvdpau1 libwebcam0 libwv-1.2-4  libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl  libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1  lightdm-gtk-greeter link-grammar-dictionaries-en lm-sensors lubuntu-artwork  lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop  lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf  lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin  lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint  ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data  pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo  plymouth-theme-lubuntu-text python-pysqlite2 python-xklavier scrot sylpheed  sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends  transmission ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn  xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf  xfonts-100dpi xpad xscreensaver xscreensaver-data"

This I noticed was for Lubuntu 12.04, so i was wondering if it is different for 12.10 or what else the problem is. I installed Using an iso. Thanks for any help you can provide!

---

### Post by offgridguy on 2013-01-13
If lubuntu 12.10 is the only OS on your laptop, you don't have to remove it.
You can install ubuntu to the same partition and it will format and install, removing
whatever was on there previously.

---

### Post by IronLyon on 2013-01-13
Right now I have both Ubuntu as well as windows 7 along side Lubuntu. Ubuntu is dual loaded with windows 7 but the problem is I have Lubuntu's choices at the beginning of my boot and then if I want to choose Windows or Ubuntu, I have to select again. It is rather bothersome and a waste of time is the main issue.

Also I have tried to run the set up for Ubuntu to try and figure it out that way, but Lubuntu wouldn't run it and I'm not entirely sure why. Just gave me an error message when I selected the wubi starter icon in my usb. I even tried to drag it to the desktop and it still wouldnt work. Do you think burning the ubuntu iso would do anything different to fix the problem?

---

### Post by offgridguy on 2013-01-14
> **IronLyon said:**
> Right now I have both Ubuntu as well as windows 7 along side Lubuntu. Ubuntu is dual loaded with windows 7 but the problem is I have Lubuntu's choices at the beginning of my boot and then if I want to choose Windows or Ubuntu, I have to select again. It is rather bothersome and a waste of time is the main issue.

Also I have tried to run the set up for Ubuntu to try and figure it out that way, but Lubuntu wouldn't run it and I'm not entirely sure why. Just gave me an error message when I selected the wubi starter icon in my usb. I even tried to drag it to the desktop and it still wouldnt work. Do you think burning the ubuntu iso would do anything different to fix the problem?
It sounds like you have a wubi install, this is something i
have no experience with, sorry.

---

### Post by IronLyon on 2013-01-17
The wubi install is on another boot page. I'll try and explain the way my system is booting up. I have a sager laptop, so the initial sager screen will come up giving me the regular press black to get to bios. Then my computer will go to a screen giving me four options: boot into Ubuntu, (which in this case is actually lubuntu) two different recovery options, or to boot into windows 7. Once I choose windows 7 it sends me to ANOTHER choose OS to work in, giving me the option of Windows 7 or Ubuntu. As I'm sure you understand this is very annoying, especially seeing as I don't even want Lubuntu any longer. I would like to remove the Lubuntu and to have the first OS choice screen be done away with if possible.

Thanks for trying to help so far!

---

### Post by oldfred on 2013-01-17
It sounds like you have a full partitioned install of Lubuntu and a wubi install of Ubuntu inside Windows.

wubi has to use Windows boot loader and is just a file inside the Windows NTFS partition. 

If you really just want Windows & wubi, you can just install the Windows boot loader to the MBR. But I suggest a full install of Ubuntu to the Lubuntu partition you already have and uninstall wubi.

To reuse existing partition(s) you have to use Something else or manual install and choose the existing Lubuntu partition as you new / (root) and choose format as ext4. If you already have swap it will reuse it and reinstall grub to the MBR.

Auto install will try to shrink an existing partition and add a new partition for Ubuntu.
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

