---
title: "Converting Lubuntu to Ubuntu"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by am_i_registered on 2016-12-01
Hello there,

Does anybody know how can I convert my Lubuntu installation to Ubuntu?
Obviously I want to avoid a clean install as that would require a lot work reinstalling all the software that I already installed in Lubuntu.

I am basically looking for the packages that are installed in Lubuntu along with the lubuntu-desktop so that I can remove them and then install ubuntu-desktop with its default apps.
Such a command is available here: [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)
But it was last updated in 2013 and obviously it is not valid today.

Any ideas?

---

### Post by am_i_registered on 2016-12-01
OK. I did a little experiment and it seems that it worked.
Basically, I run the command from the link I posted above and I removed all the packages that they returned an error from it. 
Here is the new command:
> sudo apt-get remove abiword abiword-common abiword-plugin-grammar ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman catfish elementary-icon-theme fonts-lyx galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-application-gtk2 leafpad libaacs0 libaudclient2 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libenca0 libexo-1-0 libexo-common libexo-helpers libfaad2 libfluidsynth1 libfm-data libfm-gtk-bin libfm-gtk-data libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libid3tag0 libimlib2 libindicate-gtk3 libjpeg-progs libjpeg-turbo-progs libloudmouth1-0 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libmusicbrainz3-6 libnet-dbus-perl libonig2 liboobs-1-5 libopts25 libots0 libpisock9 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsdl1.2debian libsidplay2 libtidy-0.99-0 libtie-ixhash-perl libuniconf4.6 libva1 libvdpau1 libvte-common libvte9 libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-10 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-data lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox pcmanfm pidgin pidgin-data pidgin-libnotify plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-notifyd xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
I purposely didn't remove Chromium because I like it.
After this command and a reboot, the system booted in Ubuntu and it seems that everything went well.
I did that on Lubuntu 16.10 fully updated.

---

### Post by oldos2er on 2016-12-02
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It'll help others having the same question. Thanks!

---

