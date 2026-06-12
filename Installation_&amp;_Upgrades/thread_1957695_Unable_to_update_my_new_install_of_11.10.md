---
title: "Unable to update my new install of 11.10"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by unknown user on 2012-04-13
I have not long installed the downloaded version of 11.10 and have just recently tried to update it, via the update manager. I did start this once before, but the connection got lost so the updates were not fully downloaded. 

However, now when I try to do this whilst pointing at a server in the UK, it checks and tells me that there are updates and lists 390 of them. I click on install updates, enter my password and then receive the following error message after a short time. &#8220;Requires installation of untrusted packages&#8221; The action would require the installation of packages from untrusted sources&#8221;. The only option I have is to close the error message box.

I have changed the server to the Main Server and this does not work.

Does anyone have an idea how I can update my system now and get shot of this error message?

This is the error message box that I get when I try to download via the update manager:

[IMG]http://i369.photobucket.com/albums/oo138/ukphiltr7/Screenshotat2012-04-14163410.png[/IMG]

Note: the text in the message is that as posted below in my previous post in the blue text.

I think the problem may now be due to the fact that I tried to enter the works proxy settings in the network settings, which did not work and then I took them out again.

---

### Post by raja.genupula on 2012-04-13
Hi actually the issue is with you're trying to install third party software . so Ubuntu update manager asking like that .

so while doing installations/upgrades/updates like this you must make sure that those sources are 100% well known to you .

well along with that are you  getting any GPG errors or anything similar ? 

its better to post the terminal text here to understand betterly .

---

### Post by unknown user on 2012-04-13
Is this still the case for all of the updates that are being pushed down via the update manager? It seems strange that the updates would be recommended by Ubuntu and then when you come to install them it says you can't as they are untrusted sources.

I was going to, but it was quite big, will add it shortly.

This is the message that I get when I click on the Details option in the error box:

"[COLOR="Blue"]accountsservice acpid aisleriot alsa-utils app-install-data-partner appmenu-qt apport apport-gtk apt apt-transport-https apt-utils aptdaemon aptdaemon-data apturl apturl-common at-spi2-core bamfdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab bind9-host binutils bluez bluez-alsa bluez-cups bluez-gstreamer brasero brasero-cdrkit brasero-common brltty bzip2 checkbox checkbox-gtk colord command-not-found command-not-found-data compiz compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default cups cups-bsd cups-client cups-common cups-ppdc deja-dup desktop-file-utils dnsutils empathy empathy-common eog evince evince-common evolution-data-server evolution-data-server-common file-roller firefox firefox-globalmenu firefox-gnome-support firefox-locale-en gbrainy gcalctool gconf2 gconf2-common gedit gedit-common ghostscript ghostscript-cups ghostscript-x gir1.2-atspi-2.0 gir1.2-gconf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-totem-1.0 gir1.2-unity-4.0 gir1.2-webkit-3.0 gnome-accessibility-themes gnome-bluetooth gnome-control-center gnome-control-center-data gnome-desktop3-data gnome-font-viewer gnome-games-common gnome-icon-theme gnome-keyring gnome-mahjongg gnome-online-accounts gnome-orca gnome-power-manager gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor gnome-utils-common gnomine gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter gzip hpijs hplip hplip-cups hplip-data ifupdown indicator-datetime indicator-session indicator-sound initramfs-tools initramfs-tools-bin initscripts isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-selector-common language-selector-gnome libaccountsservice0 libapt-inst1.3 libapt-pkg4.11 libarchive1 libasound2-plugins libatk-adaptor libatspi2.0-0 libbamf0 libbamf3-0 libbind9-60 libbluetooth3 libbrasero-media3-1 libbrlapi0.5 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libcamel-1.2-29 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcolord1 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3-gnutls libdecoration0 libdns69 libebackend-1.2-1 libebook1.2-12 libecal1.2-10 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver1.2-15 libedataserverui-3.0-1 libevince3-3 libfreetype6 libgail-3-0 libgail-3-common libgck-1-0 libgconf2-4 libgcr-3-1 libgnome-bluetooth8 libgnome-control-center1 libgnome-desktop-3-2 libgoa-1.0-0 libgrip0 libgs9 libgs9-common libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtksourceview-3.0-0 libgtksourceview-3.0-common libgudev-1.0-0 libgweather-3-0 libgweather-common libgwibber-gtk2 libgwibber2 libhpmud0 libicu44 libimobiledevice2 libisc62 libisccc60 libisccfg62 libjasper1 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblightdm-gobject-1-0 liblwres60 libmetacity-private0 libmono-zeroconf1.0-cil libmysqlclient16 libnautilus-extension1 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnotify0.4-cil libnux-1.0-0 libnux-1.0-common libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime libpam0g libpng12-0 libpulse-mainloop-glib0 libpulse0 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-writer libsane-hpaio libsmbclient libssl1.0.0 libsyncdaemon-1.0-1 libt1-5 libtotem0 libubuntuone-1.0-1 libubuntuone1.0-cil libudev0 libunity-2d-private0 libunity-core-4.0-4 libunity6 libusbmuxd1 libv4l-0 libvorbis0a libvorbisenc2 libvorbisfile3 libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxml2 lightdm linux-generic linux-headers-3.0.0-17 linux-headers-3.0.0-17-generic linux-headers-generic linux-image-3.0.0-17-generic linux-image-generic linux-libc-dev lzma metacity metacity-common mobile-broadband-provider-info mousetweaks multiarch-support mysql-common nautilus nautilus-data nautilus-sendto-empathy network-manager nux-tools onboard openssl pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-brlapi python-cups python-cupshelpers python-gobject python-gobject-cairo python-httplib2 python-launchpadlib python-libxml2 python-pam python-papyon python-pkg-resources python-problem-report python-pyatspi2 python-software-properties python-ubuntuone-client python-uno qdbus samba-common samba-common-bin seahorse shotwell simple-scan smbclient sni-qt software-center software-properties-common software-properties-gtk system-config-printer-common system-config-printer-gnome system-config-printer-udev sysv-rc sysvinit-utils telepathy-indicator thunderbird thunderbird-globalmenu thunderbird-gnome-support tomboy totem totem-common totem-mozilla totem-plugins ttf-opensymbol tzdata ubuntu-docs ubuntuone-client ubuntuone-client-gnome ubuntuone-couch udev unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-common unity-lens-applications unity-services uno-libs3 update-manager update-manager-core update-notifier update-notifier-common upstart ure usbmuxd vinagre vino x11-common xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-video-openchrome xul-ext-ubufox[/COLOR]"

---

### Post by raja.genupula on 2012-04-13
go to update manager -> settings -> in the tabs make sure that main PPA check boxes are selected .

EDIT: if you try in terminal

> sudo apt-get upgrade

it gonna ask you as yes or no . if you give yes / y . all going to be installed .

---

### Post by unknown user on 2012-04-14
Hi there, I am not too sure what the main PPA are and where I need to look in the update manager > settings
.
I tried it through the command below and it did not work. It did show the old proxy address that I entered into the network manager when trying to connect to their wired network. I went to System Settings >  Network > Network Proxy > Method = Manual, and then added the works proxy address and port into all the 4 lines and then clicked on Apply System Wide. This did not work and I then removed all the works proxy address and port and then clicked Apply System Wide.

|This does not seem to of removed all the entries of the previously entered work proxy address as in the terminal window, I could see the work proxy that I had entered and deleted. Is there anywhere else that I can look to take this proxy out?

---

### Post by unknown user on 2012-04-14
Well, I am not too sure of what I did but it is working now. I have been able to download and successfully install the updates, so my update manager now says my system is up to date.

I looked aain at the proxy settings and messed around with them a few times, trying to get shot of the works proxy details. I then run the command again in the terminal and this time it seemed to collect some of the packages, but then failed. So I reooted and then tried to run the update manager again and would you 'adam & eve' it, but it worked. I am not sure if it was just one thing that I did or the running the update again in the terminal or a bit of both, but it seems to be working now.

Thanks for your help and words on my post.

---

