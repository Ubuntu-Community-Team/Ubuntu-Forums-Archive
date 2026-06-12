---
title: "uninstall xubuntu"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by jorgos on 2007-08-29
Hi,
I installed** kubuntu-desktop**, and **xubuntu-desktop** on top of my Ubuntu Feisty installation, through Synaptic. Now I'd like to *completely* remove **xubuntu-desktop** only. Any suggestions..?

---

### Post by mojoman on 2007-08-29
Have a look at this, it might help.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

EDIT: Have you tried (in the terminal):

sudo apt-get remove --purge xubuntu-desktop

It might be an option but It's a meta-package so it might not be possible to remove it with this commando.

---

### Post by jorgos on 2007-08-29
I would use the link, just that it's for a *pure* Gnome and I would like to keep my **kubuntu-desktop**. I could of course do that and reinstall **kubuntu-desktop**, I was wondering though if there was a quicker way, **kubuntu-desktop** is large...:(
As for
"sudo apt-get remove --purge xubuntu-desktop"
I think also it would only remove the metapackage, I saw it in another thread.
By the way, where is this "Somewhere Cold" place???

---

### Post by mojoman on 2007-08-29
I did a search on the forum and came up with this.

[http://ubuntuforums.org/showthread.php?t=205002&highlight=remove+xubuntu](http://ubuntuforums.org/showthread.php?t=205002&highlight=remove+xubuntu)

Somewhere too cold is Stockholm, Sweden

---

### Post by Seisen on 2007-08-29
Actually you can still follow those directions to uninstall Xubuntu, it shouldn't touch Kubuntu at all. When you copy everything it just leave out the very last part of the command where it stays

```
&& sudo apt-get install ubuntu-desktop
```

---

### Post by jorgos on 2007-08-29
[I][I]jorgo@ubuntu:~$ sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce gxine hal-cups-utils libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 mousepad mozilla-thunderbird orage python-cups python-exo scim-anthy scim-chewing scim-hangul scim-pinyin system-config-printer thunar thunar-archive-plugin thunar-doc thunar-media-tags-plugin thunar-volman-plugin vim-runtime xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
Password:
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#960;&#959;&#965; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#959;&#957;&#964;&#945;&#953; &#960;&#953;&#945;:
  libopenexr2c2a libarts1c2a libmtp5 libavahi-compat-libdnssd1 libpythonize0
  vorbis-tools ncompress liblockdev1 mplayer-skins libflac++5c2 libexiv2-0.12
  language-pack-kde-el libwxgtk2.6-0 liboggflac3 fftw3 kdelibs-data
  libpoppler1-qt libtdb1 libarts1-akode libmimelib1c2a liblualib50 kdeedu-data
  koffice-data python2.5-dev kde-icons-mono libcurl3-gnutls
  language-pack-kde-el-base libdvbpsi4 libavformat0d pykdeextensions libxosd2
  procmail libvlc0 arts libjasper-runtime libakode2 libgmp3c2 libggi2
  perl-suid libavahi-qt3-1 libgii1 libwxbase2.6-0 icedax poster ocrad
  libtunepimp5 libifp4 debtags libdbus-qt-1-1c2 libgii1-target-x libdvdnav4
  libiso9660-4 rdiff-backup ksysguardd psutils zoo qobex libmeanwhile1
  libgpgme11 pmount libtar liblua50 ladcca2 libimlib2 libvcdinfo0 librsync1
  libnjb5 libofa0 libopenobex1
&#935;&#961;&#951;&#963;&#956;&#959;&#960;&#959;&#953;&#942;&#963;&#964;&#949; &#964;&#959; 'apt-get autoremove' &#947;&#953;&#945; &#957;&#945; &#964;&#945; &#945;&#960;&#959;&#956;&#945;&#954;&#961;&#973;&#957;&#949;&#964;&#949;
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#913;&#934;&#913;&#921;&#929;&#917;&#920;&#927;&#933;&#925;:
  abiword abiword-common abiword-plugins adept adept-batch adept-common
  adept-installer adept-manager adept-notifier adept-updater akregator amarok
  amarok-xine anthy ark digikam gnumeric-common gnumeric-gtk gqview
  gtk2-engines-xfce gwenview gxine hal-cups-utils k3b kaddressbook kaffeine
  kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance
  kde-guidance-powermanager kde-i18n-el kde-style-polyester kde-systemsettings
  kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins kdebluetooth
  kdegraphics-kfile-plugins kdelibs4c2a kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint
  kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt
  kio-locate kipi-plugins kitchensync klipper kmag kmail kmailcvt kmenuedit
  kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf
  knetworkmanager knode knotes koffice-libs konq-plugins konqueror
  konqueror-nsplugins konsole kontact konversation kooka kopete korganizer
  kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb kscreensaver
  kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg
  ksysguard ksystemlog ktorrent kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kvoctrain kwalletmanager kwin
  kwin-style-crystal language-selector-qt libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3
  libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a
  libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgtkmathview0c2a
  libjpeg-progs libk3b2 libk3b2-mp3 libkcal2b libkcddb1 libkdepim1a
  libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 libmodplug0c2 libots0
  libpcre3 libpulse0 libskim0 libt1-5 libtagc0 libthunar-vfs-1-2
  libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4
  libxfcegui4-4 libxine1 libxine1-ffmpeg libxvmc1 mousepad mozilla-thunderbird
  networkstatus openoffice.org-kde orage python-cups python-exo python-kde3
  scim-anthy scim-chewing scim-hangul scim-pinyin skim system-config-printer
  thunar thunar-archive-plugin thunar-doc thunar-media-tags-plugin
  thunar-volman-plugin vim-runtime vlc vlc-nox xarchiver xfburn
  xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin
  xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin
  xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin
  xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin
  xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils
  xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4
  xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash
  xubuntu-default-settings xubuntu-desktop xubuntu-docs
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 222 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 3 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
&#935;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#957;&#945; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#969;&#952;&#959;&#973;&#957; 0B &#945;&#960;&#972; &#945;&#961;&#967;&#949;&#943;&#945;.
&#924;&#949;&#964;&#940; &#964;&#951;&#957; &#945;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#952;&#945; &#949;&#955;&#949;&#965;&#952;&#949;&#961;&#969;&#952;&#959;&#973;&#957; 692MB &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
&#920;&#941;&#955;&#949;&#964;&#949; &#957;&#945; &#963;&#965;&#957;&#949;&#967;&#943;&#963;&#949;&#964;&#949; [&#925;/&#959;]; 
[/I][/I]

after removing [I]&& sudo apt-get install ubuntu-desktop
[/I]
there are still kde packages in the list of packages to be uninstalled
sorry for the greek above

Stockholm... must be great! I've been in Copenhagen and Reykjavik

---

### Post by Seisen on 2007-08-29
That makes no sense why its pulling kubuntu-desktop also. hmmm........

---

### Post by jorgos on 2007-08-29
before posting in this thread
I installed kde with aptitude
then installed kde-desktop with synaptic
then installed xubuntu-desktop with synaptic
and then uninstalled kde with purge
(kubuntu is working normal)

maybe that's the reason?

P.S. At first I just intented to install kubuntu-desktop, by mistake I installed the whole kde, that's why I removed it

---

### Post by mojoman on 2007-08-29
> **jorgos said:**
> before posting in this thread
I installed kde with aptitude
then installed kde-desktop with synaptic
then installed xubuntu-desktop with synaptic
and then uninstalled kde with purge
(kubuntu is working normal)

maybe that's the reason?

P.S. At first I just intented to install kubuntu-desktop, by mistake I installed the whole kde, that's why I removed it

Hmm, I can't see why and have to say that I agree with Seisen that it doesn't make sense that the KDE packages should be removed. 

Have you tried removing it with synaptic? You could try a search for xubuntu (in synaptics) and uninstall all packages that come up. 

Stockholm is ok. But too cold...

---

### Post by jorgos on 2007-08-29
I'll listen to u and do this through Synaptic.

Thanks for your time!!!:)

You haven't been in Greece, we're ablaze, it's so hot...

---

### Post by mojoman on 2007-08-29
> **jorgos said:**
> I'll listen to u and do this through Synaptic.

Thanks for your time!!!:)

You haven't been in Greece, we're ablaze, it's so hot...

You're welcome. Do you know an app called deborphan? It's used to find and unistall 'orphaned' packages (i.e. packages that are no longer required but still is installed). If you uninstall with synaptic you could use it to make sure you don't have any un-used stuff remaining on your system. It's a very handy tool, especially in a situation like this.

---

### Post by maybeway36 on 2007-08-29
Also do:
```
sudo apt-get autoremove
```

---

