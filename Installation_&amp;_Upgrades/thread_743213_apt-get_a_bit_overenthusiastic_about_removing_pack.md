---
title: "apt-get a bit overenthusiastic about removing packages"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by lvm on 2008-04-02
Every time I run apt-get it informs me that a whole lot of packages is no longer required. Like kde-core, for instance (I am now running KDE on ubuntu). How can I tell it that I still need them and how can I trust autoremove after that?

The following packages were automatically installed and are no longer required:
  knetwalk kpat kpdf texlive-common libdb4.4++ kalzium-data ksokoban kolf
  kdemultimedia-kappfinder-data krdc krec krfb kscd kppp kshisen kmoon
  kdeartwork-style kmahjongg ksig ksim libkscan1 kcharselect kcoloredit
  artsbuilder kdessh kanagram kdeartwork-theme-window kmrml katomic ksvg
  kruler kdemultimedia-kfile-plugins ktux klettres gnome-bin kgoldrunner
  kbackgammon kpoker libkiten1 kgeography libgtk1.2 ksnapshot kpackage kooka
  kenolaba libgdk-pixbuf2 kblackbox libboost-python1.34.1 libgnomeui32 klatin
  kfloppy libgnome32 kstars ttf-dustin ksame kbruch kdeaddons-kfile-plugins
  kfilereplace kdeadmin-kfile-plugins kde-core kcalc texlive-base-bin
  kicker-applets libpoppler-qt2 keduca libarts1-xine texlive-fonts-recommended
  xfdesktop4-data kaudiocreator kdeedu-data kimagemapeditor kwalletmanager
  kweather kmplot libart2 kalzium ksirc knetworkconf librss1 klinkstatus
  klickety kpovmodeler gdk-imlib1 ksayit konq-plugins kmouth klaptopdaemon
  kworldclock kdewebdev kdeaccessibility kdict libthunar-vfs-1-2 ktouch
  khexedit kedit kbounce kvoctrain kbstate tidy arts ark kwordquiz kcron
  superkaramba kview noatun-plugins ktron kdegraphics-kfile-plugins libgmp3c2
  ttf-sjfonts kdenetwork-kfile-plugins cvs kdenetwork kttsd thunar dcoprss
  ksysv kwin4 kate-plugins kuser kreversi kdf kspaceduel kig libcvsservice0
  kpf juk noatun kdnssd klines libxml1 kfaxview kstars-data edict lskat libdb3
  kgamma kviewshell kommander kdegames-card-data libgnorbagtk0 gnome-libs-data
  kaddressbook-plugins kgeography-data kwifimanager kdeutils kjumpingcube
  kdegraphics kaboodle libgdk-pixbuf-gnome2 khangman kdeartwork-theme-icon
  thunar-data kdeartwork-misc kscreensaver xfdesktop4 kanjidic imlib-base
  texlive-base ksmiletris libgtk1.2-common liborbit0 kxsldbg gdk-imlib11
  quanta kbattleship kiconedit kdeadmin libglade-gnome0 kasteroids
  texlive-doc-base kfouleggs libkdeedu3 xfce4-utils knewsticker kopete ksnake
  kiten libtiff-tools eyesapplet libzvt2 kdat libgnomesupport0 indi
  kdewallpapers kdelirc kscreensaver-xsavers kpercentage libkdegames1 dbus-x11
  kjots klettres-data kfax kdeartwork-emoticons ksirtet libglade0 kmines kdvi
  kget kgpg konquest tex-common kolourpaint fifteenapplet kdemultimedia
  kmousetool kmag libtidy-0.99-0 kmilo kturtle ktimer quanta-data libgnorba27
  kmid kteatime kverbos kmix kdeartwork libarts1-audiofile kodo

---

### Post by piousp on 2008-04-02
did you installed "kubuntu-desktop" after kde-core ???? :confused:

---

### Post by lvm on 2008-04-03
I didn't but I don't see how it can help as

description
This package depends on all of the packages in the Kubuntu desktop system . _It is safe to remove this package if some of the desktop system packages are not desired._

and that's beside the point anyway, the question is: why apt-get considers some of the packages I've installed as no longer required, what went wrong and how can I fix package database?

---

### Post by vegetali on 2008-04-03
just a stupid question: does aptitude keep telling the same?

---

### Post by lvm on 2008-04-03
I think, yes. That is I never used aptitude before, but when I started it it marked these packages with d and highlighted with magenta. BTW I tried to install kubuntu-desktop - just in case, and all I've got is a lot of cr^H^H stuff I don't actually need.

---

### Post by zvacet on 2008-04-03
```
sudo apt-get install knetwalk kpat kpdf texlive-common libdb4.4++ kalzium-data ksokoban kolf
kdemultimedia-kappfinder-data krdc krec krfb kscd kppp kshisen kmoon
kdeartwork-style kmahjongg ksig ksim libkscan1 kcharselect kcoloredit
artsbuilder kdessh kanagram kdeartwork-theme-window kmrml katomic ksvg
kruler kdemultimedia-kfile-plugins ktux klettres gnome-bin kgoldrunner
kbackgammon kpoker libkiten1 kgeography libgtk1.2 ksnapshot kpackage kooka
kenolaba libgdk-pixbuf2 kblackbox libboost-python1.34.1 libgnomeui32 klatin
kfloppy libgnome32 kstars ttf-dustin ksame kbruch kdeaddons-kfile-plugins
kfilereplace kdeadmin-kfile-plugins kde-core kcalc texlive-base-bin
kicker-applets libpoppler-qt2 keduca libarts1-xine texlive-fonts-recommended
xfdesktop4-data kaudiocreator kdeedu-data kimagemapeditor kwalletmanager
kweather kmplot libart2 kalzium ksirc knetworkconf librss1 klinkstatus
klickety kpovmodeler gdk-imlib1 ksayit konq-plugins kmouth klaptopdaemon
kworldclock kdewebdev kdeaccessibility kdict libthunar-vfs-1-2 ktouch
khexedit kedit kbounce kvoctrain kbstate tidy arts ark kwordquiz kcron
superkaramba kview noatun-plugins ktron kdegraphics-kfile-plugins libgmp3c2
ttf-sjfonts kdenetwork-kfile-plugins cvs kdenetwork kttsd thunar dcoprss
ksysv kwin4 kate-plugins kuser kreversi kdf kspaceduel kig libcvsservice0
kpf juk noatun kdnssd klines libxml1 kfaxview kstars-data edict lskat libdb3
kgamma kviewshell kommander kdegames-card-data libgnorbagtk0 gnome-libs-data
kaddressbook-plugins kgeography-data kwifimanager kdeutils kjumpingcube
kdegraphics kaboodle libgdk-pixbuf-gnome2 khangman kdeartwork-theme-icon
thunar-data kdeartwork-misc kscreensaver xfdesktop4 kanjidic imlib-base
texlive-base ksmiletris libgtk1.2-common liborbit0 kxsldbg gdk-imlib11
quanta kbattleship kiconedit kdeadmin libglade-gnome0 kasteroids
texlive-doc-base kfouleggs libkdeedu3 xfce4-utils knewsticker kopete ksnake
kiten libtiff-tools eyesapplet libzvt2 kdat libgnomesupport0 indi
kdewallpapers kdelirc kscreensaver-xsavers kpercentage libkdegames1 dbus-x11
kjots klettres-data kfax kdeartwork-emoticons ksirtet libglade0 kmines kdvi
kget kgpg konquest tex-common kolourpaint fifteenapplet kdemultimedia
kmousetool kmag libtidy-0.99-0 kmilo kturtle ktimer quanta-data libgnorba27
kmid kteatime kverbos kmix kdeartwork libarts1-audiofile kodo
```

---

