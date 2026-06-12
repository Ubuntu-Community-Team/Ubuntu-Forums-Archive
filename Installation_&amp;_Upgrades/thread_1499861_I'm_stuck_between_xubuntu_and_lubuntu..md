---
title: "I'm stuck between xubuntu and lubuntu."
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by mcyips on 2010-06-02
Hi,

-My first post, woooh...-
I'm quite a new Ubuntu user, and I wanted to migrate from Xubuntu 10.04 to Lubuntu. But now my desktop looks like nothing and not belonging to any session. In the terminal:
[FONT=Courier New]
gnome-session-save --kill

** (gnome-session-save:18478): WARNING **: Failed to call logout: The name org.gnome.SessionManager was not provided by any .service files[/FONT]

And :

[FONT=Courier New]sudo apt-get install lxsession-lite

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lxsession-lite: Depends: lxsession but it is not going to be installed
E: Broken packages[/FONT]


To install Lubuntu I launched the following command (first part comes from [Lubuntu doc]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Install%20Lubuntu%20from%20Ubuntu%20or%20any%20Ubuntu%20flavors") and second from [Psychocat]("http://www.psychocats.net/ubuntu/puregnome") to remove Xubuntu) :

[FONT=Courier New]sudo  add-apt-repository ppa:lubuntu-desktop/ppa [/FONT][FONT=Courier New] [/FONT]
[FONT=Courier New]sudo  apt-get update 

sudo apt-get remove a2ps abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview app-install-data-commercial aumix aumix-common catfish exaile exo-utils fortune-mod fortunes-min gigolo gimp gimp-data gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libbabl-0.0-0 libexo-0.3-0 libexo-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libjpeg-progs  liblink-grammar4 libmng1 libotr2 libots0 libpsiconv6 librecode0 libscim8c2a libsdl1.2debian-alsa libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad murrine-themes orage oss-compat pidgin pidgin-data pidgin-libnotify pidgin-otr psutils python-cddb python-mmkeys python-mutagen python-sexy ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-lyx usb-creator vim-runtime wdiff xchat xchat-common xfce-keyboard-shortcuts xfce4-appfinder xfce4-clipman  xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin  xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xscreensaver xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-icon-theme xubuntu-plymouth-theme xubuntu-wallpapers

sudo apt-get install ubuntu-desktop [/FONT]

If you could help me... Thanks !

Marie

---

### Post by lemming465 on 2010-06-04
Try **sudo apt-get install lubuntu-desktop**.

---

