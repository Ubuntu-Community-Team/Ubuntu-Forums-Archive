---
title: "Trying to remove kubuntu desktop after testing"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Toeclipper on 2010-01-02
Hi all, new user here!

I have settled on Ubuntu 9.10 as my preferred distro and was keen to try out which desktop I preferred so I installed kubuntu-desktop and all its dependencies via synoptic package manager following a guide on psychocats.net.
Decided I preferred Gnome and wanted to get rid of all duplicated applications etc so followed same guide to remove.
[http://http://www.psychocats.net/ubuntu/puregnome]("http://http//www.psychocats.net/ubuntu/puregnome")

In terminal I entered:
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig && sudo apt-get install ubuntu-desktop

However once I get password prompt I can no longer type into the terminal!

Anyone know why not?

---

### Post by tommcd on 2010-01-02
> **Toeclipper said:**
> 
However once I get password prompt I can no longer type into the terminal!
Anyone know why not?
When you type your password in the terminal the cursor does not move. This is normal. It is a security feature so no one can look over your shoulder while you are typing and try to guess how many characters your password is.
So enter the command as posted on the psychocats site:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Then type your password when prompted and hit enter. The command will be executed. If you get errors, post them here.

And welcome to the Ubuntu forums! 
I like Gnome much better than KDE also :)

---

### Post by Toeclipper on 2010-01-02
Doh!

Thanks for your help, I didn't realise that :rolleyes:

---

