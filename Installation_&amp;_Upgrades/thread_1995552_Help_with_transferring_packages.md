---
title: "Help with transferring packages"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-06-03
I'm moving my Kubuntu installation (12.04) from one computer to another, and I'm trying to move all the installed packages as well as the /home directory.  I tried the "dpkg --get-selections > packages.txt" trick, but it wouldn't install on my new computer when I finished it.  Because of that, I tried transferring the packages manually.  This is what "dpkg --get-selections" told me I have to transfer:
```
acroread-common apparmor-profiles aptdaemon aptdaemon-data at:i386 autoconf automake autotools-dev awesfx:i386 axel axel-kapt binfmt-support bison:i386 bleachbit bless blt:i386 c2esp
  ca-certificates-java cabextract ccache:i386 cdbs chkconfig chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra clamav-base cli-common comerr-dev:i386 compiz-core:i386
  compiz-plugins:i386 compiz-plugins-default:i386 compiz-plugins-extra:i386 compiz-plugins-main:i386 compiz-plugins-main-default:i386 cpp-4.5:i386 cron:i386 culmus cups-driver-gutenprint
  curl cvs:i386 dbus-java-bin dconf-gsettings-backend:i386 debhelper default-jre default-jre-headless defoma desmume:i386 dh-apparmor dh-make dh-modaliases dh-translations dhcp3-server
  dialog diffstat djvulibre-desktop:i386 dkms docbook dpkg-dev e2fslibs:i386 esound-common execstack:i386 fakeroot fdupes:i386 firefox firefox-globalmenu firefox-locale-af firefox-locale-ar
  firefox-locale-as firefox-locale-ast firefox-locale-be firefox-locale-bg firefox-locale-bn firefox-locale-br firefox-locale-bs firefox-locale-ca firefox-locale-cs firefox-locale-csb
  firefox-locale-da firefox-locale-de firefox-locale-el firefox-locale-en firefox-locale-eo firefox-locale-es firefox-locale-et firefox-locale-eu firefox-locale-fa firefox-locale-fi
  firefox-locale-fr firefox-locale-ga firefox-locale-gd firefox-locale-gl firefox-locale-gu firefox-locale-he firefox-locale-hi firefox-locale-hr firefox-locale-hu firefox-locale-hy
  firefox-locale-id firefox-locale-is firefox-locale-it firefox-locale-ja firefox-locale-ka firefox-locale-kk firefox-locale-km firefox-locale-kn firefox-locale-ko firefox-locale-ku
  firefox-locale-lg firefox-locale-lt firefox-locale-lv firefox-locale-mai firefox-locale-mk firefox-locale-ml firefox-locale-mn firefox-locale-mr firefox-locale-nb firefox-locale-nl
  firefox-locale-nn firefox-locale-nso firefox-locale-oc firefox-locale-or firefox-locale-pa firefox-locale-pl firefox-locale-pt firefox-locale-ro firefox-locale-ru firefox-locale-si
  firefox-locale-sk firefox-locale-sl firefox-locale-sq firefox-locale-sr firefox-locale-zh-hans firefox-locale-zh-hant flex:i386 fluid-soundfont-gm fluid-soundfont-gs fluidsynth:i386
  fonts-arabeyes fonts-arphic-ukai fonts-arphic-uming fonts-droid fonts-dzongkha fonts-farsiweb fonts-horai-umefont fonts-khmeros fonts-manchufont fonts-mgopen fonts-sil-abyssinica
  fonts-sil-ezra fonts-sil-gentium fonts-sil-gentium-basic fonts-sil-padauk fonts-sil-scheherazade fonts-takao-gothic fonts-takao-mincho fonts-tibetan-machine fonts-unfonts-core
  fonts-unfonts-extra foo2zjs freepats gamin:i386 gcc gcc-4.5-base gcc-4.5-base:i386 gcc-4.6 gcc-4.6-base:i386 gconf-service gconf-service-backend gconf2 gconf2-common gdebi-core
  gedit-common gettext gimp-data gimp-data-extras gimp-help-common gimp-help-de gimp-help-en gimp-help-es gimp-help-fr gimp-help-it gimp-help-ko gimp-help-nl gimp-help-nn gimp-help-pl         
  gimp-help-ru gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-vte-2.90 git git-core git-man                 
  glib-networking:i386 gnome-icon-theme graphviz:i386 gstreamer0.10-alsa:i386 gstreamer0.10-ffmpeg:i386 gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mp3:i386                                
  gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk-recordmydesktop gutenprint-locales gvfs gvfs:i386 gvfs-bin:i386 gvfs-common gvfs-daemons gvfs-libs   
  gvfs-libs:i386 hdapsd:i386 hddtemp:i386 hpijs hping3:i386 hplip-cups html2text humanity-icon-theme hunspell-ar hunspell-da hunspell-de-at hunspell-de-ch hunspell-de-de hunspell-en-ca        
  hunspell-eu-es hunspell-fr hunspell-gl-es hunspell-hu hunspell-kk hunspell-ko hunspell-ml hunspell-ne hunspell-ro hunspell-ru hunspell-se hunspell-sr hyphen-af hyphen-bn hyphen-ca           
  hyphen-de hyphen-en-us hyphen-fr hyphen-hr hyphen-hu hyphen-it hyphen-kn hyphen-pa hyphen-pl hyphen-ro hyphen-sl hyphen-sr icc-profiles-free icedtea-6-jre-cacao icedtea-6-jre-cacao:i386
  icedtea-6-jre-jamvm icedtea-6-jre-jamvm:i386 icedtea-6-plugin icedtea-6-plugin:i386 icedtea-7-jre-cacao icedtea-7-jre-cacao:i386 icedtea-7-jre-jamvm icedtea-7-jre-jamvm:i386 icedtea-netx
  icedtea-netx:i386 icedtea-netx-common icedtea-plugin imagemagick-common indicator-application:i386 intltool intltool-debian isc-dhcp-server iw jackd jackd2 jadetex java-common
  java-wrappers javascript-common jmol kaptain kde-l10n-ar kde-l10n-bg kde-l10n-bs kde-l10n-ca kde-l10n-ca-valencia kde-l10n-cs kde-l10n-csb kde-l10n-da kde-l10n-de kde-l10n-el kde-l10n-engb
  kde-l10n-eo kde-l10n-es kde-l10n-et kde-l10n-eu kde-l10n-fa kde-l10n-fi kde-l10n-fr kde-l10n-ga kde-l10n-gl kde-l10n-gu kde-l10n-he kde-l10n-hi kde-l10n-hr kde-l10n-hu kde-l10n-ia
  kde-l10n-id kde-l10n-is kde-l10n-it kde-l10n-ja kde-l10n-kk kde-l10n-km kde-l10n-kn kde-l10n-ko kde-l10n-lt kde-l10n-lv kde-l10n-mai kde-l10n-mk kde-l10n-ml kde-l10n-nb kde-l10n-nds
  kde-l10n-nl kde-l10n-nn kde-l10n-pa kde-l10n-pl kde-l10n-pt kde-l10n-ptbr kde-l10n-ro kde-l10n-ru kde-l10n-si kde-l10n-sk kde-l10n-sl kde-l10n-sr kde-l10n-zhcn kde-l10n-zhtw
  kdebase-runtime kdelibs5-dbg:i386 keyutils:i386 krb5-multidev:i386 kubuntu-restricted-addons:i386 kubuntu-restricted-extras:i386 kvirc kvirc-data kvirc-modules lacheck lame:i386
  language-pack-aa language-pack-aa-base language-pack-af language-pack-af-base language-pack-am language-pack-am-base language-pack-an language-pack-an-base language-pack-ar
  language-pack-ar-base language-pack-as language-pack-as-base language-pack-ast language-pack-ast-base language-pack-az language-pack-az-base language-pack-be language-pack-be-base
  language-pack-bem language-pack-bem-base language-pack-ber language-pack-ber-base language-pack-bg language-pack-bg-base language-pack-bn language-pack-bn-base language-pack-br
  language-pack-br-base language-pack-bs language-pack-bs-base language-pack-ca language-pack-ca-base language-pack-crh language-pack-crh-base language-pack-cs language-pack-cs-base
  language-pack-csb language-pack-csb-base language-pack-cv language-pack-cv-base language-pack-da language-pack-da-base language-pack-de language-pack-de-base language-pack-dv
  language-pack-dv-base language-pack-dz language-pack-dz-base language-pack-el language-pack-el-base language-pack-eo language-pack-eo-base language-pack-es language-pack-es-base
  language-pack-et language-pack-et-base language-pack-eu language-pack-eu-base language-pack-fa language-pack-fa-base language-pack-fi language-pack-fi-base language-pack-fil
  language-pack-fil-base language-pack-fo language-pack-fo-base language-pack-fr language-pack-fr-base language-pack-fur language-pack-fur-base language-pack-ga language-pack-ga-base
  language-pack-gd language-pack-gd-base language-pack-gl language-pack-gl-base language-pack-gnome-aa language-pack-gnome-aa-base language-pack-gnome-af language-pack-gnome-af-base
  language-pack-gnome-am language-pack-gnome-am-base language-pack-gnome-an language-pack-gnome-an-base language-pack-gnome-ar language-pack-gnome-ar-base language-pack-gnome-as
  language-pack-gnome-as-base language-pack-gnome-ast language-pack-gnome-ast-base language-pack-gnome-az language-pack-gnome-az-base language-pack-gnome-be language-pack-gnome-be-base
  language-pack-gnome-ber language-pack-gnome-ber-base language-pack-gnome-bg language-pack-gnome-bg-base language-pack-gnome-bn language-pack-gnome-bn-base language-pack-gnome-br
  language-pack-gnome-br-base language-pack-gnome-bs language-pack-gnome-bs-base language-pack-gnome-ca language-pack-gnome-ca-base language-pack-gnome-crh language-pack-gnome-crh-base
  language-pack-gnome-cs language-pack-gnome-cs-base language-pack-gnome-csb language-pack-gnome-csb-base language-pack-gnome-da language-pack-gnome-da-base language-pack-gnome-de
  language-pack-gnome-de-base language-pack-gnome-dv language-pack-gnome-dv-base language-pack-gnome-dz language-pack-gnome-dz-base language-pack-gnome-el language-pack-gnome-el-base
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-eo language-pack-gnome-eo-base language-pack-gnome-es language-pack-gnome-es-base language-pack-gnome-et
  language-pack-gnome-et-base language-pack-gnome-eu language-pack-gnome-eu-base language-pack-gnome-fa language-pack-gnome-fa-base language-pack-gnome-fi language-pack-gnome-fi-base
  language-pack-gnome-fil language-pack-gnome-fil-base language-pack-gnome-fo language-pack-gnome-fo-base language-pack-gnome-fr language-pack-gnome-fr-base language-pack-gnome-fur
  language-pack-gnome-fur-base language-pack-gnome-ga language-pack-gnome-ga-base language-pack-gnome-gd language-pack-gnome-gd-base language-pack-gnome-gl language-pack-gnome-gl-base
  language-pack-gnome-gu language-pack-gnome-gu-base language-pack-gnome-gv language-pack-gnome-gv-base language-pack-gnome-ha language-pack-gnome-ha-base language-pack-gnome-he
  language-pack-gnome-he-base language-pack-gnome-hi language-pack-gnome-hi-base language-pack-gnome-hr language-pack-gnome-hr-base language-pack-gnome-ht language-pack-gnome-ht-base
  language-pack-gnome-hu language-pack-gnome-hu-base language-pack-gnome-hy language-pack-gnome-hy-base language-pack-gnome-ia language-pack-gnome-ia-base language-pack-gnome-id
  language-pack-gnome-id-base language-pack-gnome-ig language-pack-gnome-ig-base language-pack-gnome-is language-pack-gnome-is-base language-pack-gnome-it language-pack-gnome-it-base
  language-pack-gnome-ja language-pack-gnome-ja-base language-pack-gnome-ka language-pack-gnome-ka-base language-pack-gnome-kk language-pack-gnome-kk-base language-pack-gnome-kl
  language-pack-gnome-kl-base language-pack-gnome-km language-pack-gnome-km-base language-pack-gnome-kn language-pack-gnome-kn-base language-pack-gnome-ko language-pack-gnome-ko-base
  language-pack-gnome-ks language-pack-gnome-ks-base language-pack-gnome-ku language-pack-gnome-ku-base language-pack-gnome-kw language-pack-gnome-kw-base language-pack-gnome-ky
  language-pack-gnome-ky-base language-pack-gnome-la language-pack-gnome-la-base language-pack-gnome-lb language-pack-gnome-lb-base language-pack-gnome-lg language-pack-gnome-lg-base
  language-pack-gnome-li language-pack-gnome-li-base language-pack-gnome-lo language-pack-gnome-lo-base language-pack-gnome-lt language-pack-gnome-lt-base language-pack-gnome-lv
  language-pack-gnome-lv-base language-pack-gnome-mai language-pack-gnome-mai-base language-pack-gnome-mg language-pack-gnome-mg-base language-pack-gnome-mhr language-pack-gnome-mhr-base
  language-pack-gnome-mi language-pack-gnome-mi-base language-pack-gnome-mk language-pack-gnome-mk-base language-pack-gnome-ml language-pack-gnome-ml-base language-pack-gnome-mn
  language-pack-gnome-mn-base language-pack-gnome-mr language-pack-gnome-mr-base language-pack-gnome-ms language-pack-gnome-ms-base language-pack-gnome-mt language-pack-gnome-mt-base
  language-pack-gnome-nan language-pack-gnome-nan-base language-pack-gnome-nb language-pack-gnome-nb-base language-pack-gnome-nds language-pack-gnome-nds-base language-pack-gnome-ne
  language-pack-gnome-ne-base language-pack-gnome-nl language-pack-gnome-nl-base language-pack-gnome-nn language-pack-gnome-nn-base language-pack-gnome-nso language-pack-gnome-nso-base
  language-pack-gnome-oc language-pack-gnome-oc-base language-pack-gnome-om language-pack-gnome-om-base language-pack-gnome-or language-pack-gnome-or-base language-pack-gnome-os
  language-pack-gnome-os-base language-pack-gnome-pa language-pack-gnome-pa-base language-pack-gnome-pap language-pack-gnome-pap-base language-pack-gnome-pl language-pack-gnome-pl-base
  language-pack-gnome-ps language-pack-gnome-ps-base language-pack-gnome-pt language-pack-gnome-pt-base language-pack-gnome-ro language-pack-gnome-ro-base language-pack-gnome-ru
  language-pack-gnome-ru-base language-pack-gnome-rw language-pack-gnome-rw-base language-pack-gnome-sa language-pack-gnome-sa-base language-pack-gnome-sc language-pack-gnome-sc-base
  language-pack-gnome-sd language-pack-gnome-sd-base language-pack-gnome-se language-pack-gnome-se-base language-pack-gnome-shs language-pack-gnome-shs-base language-pack-gnome-si
  language-pack-gnome-si-base language-pack-gnome-sk language-pack-gnome-sk-base language-pack-gnome-sl language-pack-gnome-sl-base language-pack-gnome-so language-pack-gnome-so-base
  language-pack-gnome-sq language-pack-gnome-sq-base language-pack-gnome-sr language-pack-gnome-sr-base language-pack-gnome-st language-pack-gnome-st-base language-pack-gnome-zh-hans
  language-pack-gnome-zh-hans-base language-pack-gnome-zh-hant language-pack-gnome-zh-hant-base language-pack-gu language-pack-gu-base language-pack-gv language-pack-gv-base language-pack-ha
  language-pack-ha-base language-pack-he language-pack-he-base language-pack-hi language-pack-hi-base language-pack-hne language-pack-hne-base language-pack-hr language-pack-hr-base
  language-pack-ht language-pack-ht-base language-pack-hu language-pack-hu-base language-pack-hy language-pack-hy-base language-pack-ia language-pack-ia-base language-pack-id
  language-pack-id-base language-pack-ig language-pack-ig-base language-pack-is language-pack-is-base language-pack-it language-pack-it-base language-pack-ja language-pack-ja-base
  language-pack-ka language-pack-ka-base language-pack-kde-aa language-pack-kde-aa-base language-pack-kde-af language-pack-kde-af-base language-pack-kde-am language-pack-kde-am-base
  language-pack-kde-ar language-pack-kde-ar-base language-pack-kde-as language-pack-kde-as-base language-pack-kde-ast language-pack-kde-ast-base language-pack-kde-az
  language-pack-kde-az-base language-pack-kde-be language-pack-kde-be-base language-pack-kde-bg language-pack-kde-bg-base language-pack-kde-bn language-pack-kde-bn-base language-pack-kde-br
  language-pack-kde-br-base language-pack-kde-bs language-pack-kde-bs-base language-pack-kde-ca language-pack-kde-ca-base language-pack-kde-crh language-pack-kde-crh-base
  language-pack-kde-cs language-pack-kde-cs-base language-pack-kde-csb language-pack-kde-csb-base language-pack-kde-da language-pack-kde-da-base language-pack-kde-de
  language-pack-kde-de-base language-pack-kde-dv language-pack-kde-dv-base language-pack-kde-el language-pack-kde-el-base language-pack-kde-eo language-pack-kde-eo-base language-pack-kde-es
  language-pack-kde-es-base language-pack-kde-et language-pack-kde-et-base language-pack-kde-eu language-pack-kde-eu-base language-pack-kde-fa language-pack-kde-fa-base language-pack-kde-fi
  language-pack-kde-fi-base language-pack-kde-fil language-pack-kde-fil-base language-pack-kde-fo language-pack-kde-fo-base language-pack-kde-fr language-pack-kde-fr-base
  language-pack-kde-fur language-pack-kde-fur-base language-pack-kde-ga language-pack-kde-ga-base language-pack-kde-gd language-pack-kde-gd-base language-pack-kde-gl
  language-pack-kde-gl-base language-pack-kde-gu language-pack-kde-gu-base language-pack-kde-gv language-pack-kde-gv-base language-pack-kde-ha language-pack-kde-ha-base language-pack-kde-he
  language-pack-kde-he-base language-pack-kde-hi language-pack-kde-hi-base language-pack-kde-hne language-pack-kde-hne-base language-pack-kde-hr language-pack-kde-hr-base
  language-pack-kde-hu language-pack-kde-hu-base language-pack-kde-hy language-pack-kde-hy-base language-pack-kde-ia language-pack-kde-ia-base language-pack-kde-id language-pack-kde-id-base
  language-pack-kde-is language-pack-kde-is-base language-pack-kde-it language-pack-kde-it-base language-pack-kde-ja language-pack-kde-ja-base language-pack-kde-ka language-pack-kde-ka-base
  language-pack-kde-kk language-pack-kde-kk-base language-pack-kde-kl language-pack-kde-kl-base language-pack-kde-km language-pack-kde-km-base language-pack-kde-kn language-pack-kde-kn-base
  language-pack-kde-ko language-pack-kde-ko-base language-pack-kde-ku language-pack-kde-ku-base language-pack-kde-kw language-pack-kde-kw-base language-pack-kde-la language-pack-kde-la-base
  language-pack-kde-lb language-pack-kde-lb-base language-pack-kde-lo language-pack-kde-lo-base language-pack-kde-lt language-pack-kde-lt-base language-pack-kde-lv language-pack-kde-lv-base
  language-pack-kde-mai language-pack-kde-mai-base language-pack-kde-mg language-pack-kde-mg-base language-pack-kde-mhr language-pack-kde-mhr-base language-pack-kde-mk
  language-pack-kde-mk-base language-pack-kde-ml language-pack-kde-ml-base language-pack-kde-mn language-pack-kde-mn-base language-pack-kde-mr language-pack-kde-mr-base language-pack-kde-ms
  language-pack-kde-ms-base language-pack-kde-mt language-pack-kde-mt-base language-pack-kde-nb language-pack-kde-nb-base language-pack-kde-nds language-pack-kde-nds-base
  language-pack-kde-ne language-pack-kde-ne-base language-pack-kde-nl language-pack-kde-nl-base language-pack-kde-nn language-pack-kde-nn-base language-pack-kde-oc language-pack-kde-oc-base
  language-pack-kde-om language-pack-kde-om-base language-pack-kde-or language-pack-kde-or-base language-pack-kde-pa language-pack-kde-pa-base language-pack-kde-pl language-pack-kde-pl-base
  language-pack-kde-ps language-pack-kde-ps-base language-pack-kde-pt language-pack-kde-pt-base language-pack-kde-ro language-pack-kde-ro-base language-pack-kde-ru language-pack-kde-ru-base
  language-pack-kde-rw language-pack-kde-rw-base language-pack-kde-sd language-pack-kde-sd-base language-pack-kde-se language-pack-kde-se-base language-pack-kde-si language-pack-kde-si-base
  language-pack-kde-sk language-pack-kde-sk-base language-pack-kde-sl language-pack-kde-sl-base language-pack-kde-sq language-pack-kde-sq-base language-pack-kde-sr language-pack-kde-sr-base
  language-pack-kde-st language-pack-kde-st-base language-pack-kde-zh-hans language-pack-kde-zh-hans-base language-pack-kde-zh-hant language-pack-kde-zh-hant-base language-pack-kk
  language-pack-kk-base language-pack-kl language-pack-kl-base language-pack-km language-pack-km-base language-pack-kn language-pack-kn-base language-pack-ko language-pack-ko-base
  language-pack-ks language-pack-ks-base language-pack-ku language-pack-ku-base language-pack-kw language-pack-kw-base language-pack-ky language-pack-ky-base language-pack-la
  language-pack-la-base language-pack-lb language-pack-lb-base language-pack-lg language-pack-lg-base language-pack-li language-pack-li-base language-pack-lo language-pack-lo-base
  language-pack-lt language-pack-lt-base language-pack-lv language-pack-lv-base language-pack-mai language-pack-mai-base language-pack-mg language-pack-mg-base language-pack-mhr
  language-pack-mhr-base language-pack-mi language-pack-mi-base language-pack-mk language-pack-mk-base language-pack-ml language-pack-ml-base language-pack-mn language-pack-mn-base
  language-pack-mr language-pack-mr-base language-pack-ms language-pack-ms-base language-pack-mt language-pack-mt-base language-pack-my language-pack-my-base language-pack-nan
  language-pack-nan-base language-pack-nb language-pack-nb-base language-pack-nds language-pack-nds-base language-pack-ne language-pack-ne-base language-pack-nl language-pack-nl-base
  language-pack-nn language-pack-nn-base language-pack-nso language-pack-nso-base language-pack-oc language-pack-oc-base language-pack-om language-pack-om-base language-pack-or
  language-pack-or-base language-pack-os language-pack-os-base language-pack-pa language-pack-pa-base language-pack-pap language-pack-pap-base language-pack-pl language-pack-pl-base
  language-pack-ps language-pack-ps-base language-pack-pt language-pack-pt-base language-pack-ro language-pack-ro-base language-pack-ru language-pack-ru-base language-pack-rw
  language-pack-rw-base language-pack-sa language-pack-sa-base language-pack-sc language-pack-sc-base language-pack-sd language-pack-sd-base language-pack-se language-pack-se-base
  language-pack-shs language-pack-shs-base language-pack-si language-pack-si-base language-pack-sk language-pack-sk-base language-pack-sl language-pack-sl-base language-pack-so
  language-pack-so-base language-pack-sq language-pack-sq-base language-pack-sr language-pack-sr-base language-pack-st language-pack-st-base language-pack-tlh language-pack-tlh-base
  language-pack-zh-hans language-pack-zh-hans-base language-pack-zh-hant language-pack-zh-hant-base latex-beamer latex-xcolor launchpad-integration lha:i386 lib32asound2 lib32asound2-dev
  lib32bz2-1.0 lib32ffi6 lib32gcc1 lib32gomp1 lib32ncurses5 lib32ncurses5-dev lib32ncursesw5 lib32nss-mdns lib32quadmath0 lib32stdc++6 lib32tinfo-dev lib32tinfo5 lib32z1 lib32z1-dev
  liba52-0.7.4:i386 libaa1:i386 libaacs0 libaacs0:i386 libaccess-bridge-java libaccess-bridge-java-jni libacl1:i386 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libappindicator1:i386 libappindicator3-1:i386 libapr1:i386 libaprutil1:i386 libapt-inst1.4:i386 libapt-pkg4.12:i386 libarchive12:i386 libart2.0-cil libasn1-8-heimdal:i386 libasound2:i386
  libasound2-dev libasound2-plugins:i386 libasyncns0:i386 libatasmart4:i386 libatk-wrapper-java libatk-wrapper-java-jni libatk-wrapper-java-jni:i386 libatk1.0-0:i386 libatkmm-1.6-1:i386
  libattr1:i386 libaudio-dev libaudio-dev:i386 libaudio2:i386 libaudiofile-dev libaudiofile-dev:i386 libaudiofile1 libaudiofile1:i386 libavahi-client-dev:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common-dev:i386 libavahi-common3:i386 libavahi-glib1 libavahi-glib1:i386 libavahi-ui-gtk3-0 libavahi-ui-gtk3-0:i386 libavahi-ui0 libavahi-ui0:i386
  libavc1394-0:i386 libavcodec-extra-53:i386 libavdevice53:i386 libavfilter2:i386 libavformat53:i386 libavutil-extra-51 libavutil-extra-51:i386 libbabl-0.0-0 libbison-dev libbison-dev:i386
  libbit-vector-perl libblas3gf:i386 libbluetooth3:i386 libbluray-bdj libbluray1 libbluray1:i386 libbonobo2-common libbonoboui2-common libboost-filesystem1.46.1:i386
  libboost-serialization1.46.1:i386 libboost-system1.46.1:i386 libboost-thread1.46.1:i386 libbsd0:i386 libbz2-1.0:i386 libc-dev-bin libc6:i386 libc6-dbg libc6-dbg:i386 libc6-dev
  libc6-dev:i386 libc6-dev-i386 libc6-i386 libc6-xen:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo-perl libcairo-script-interpreter2 libcairo-script-interpreter2:i386 libcairo2:i386
  libcairo2-dev:i386 libcairomm-1.0-1:i386 libcanberra-gtk3-0 libcanberra-gtk3-0:i386 libcanberra-gtk3-module libcanberra-gtk3-module:i386 libcanberra0:i386 libcap2:i386 libcap2-bin:i386
  libcapi20-3 libcapi20-3:i386 libcapi20-dev libcapi20-dev:i386 libcarp-clan-perl libcdaudio1:i386 libcddb2:i386 libcdio13 libcdparanoia0:i386 libcdt4:i386 libcelt0-0:i386 libcgraph5:i386
  libchm1:i386 libcolamd2.7.1:i386 libcomerr2:i386 libcommons-cli-java libcommons-lang-java libcompizconfig0:i386 libconfig++8:i386 libcroco3:i386 libcups2:i386 libcups2-dev:i386
  libcupscgi1:i386 libcupsimage2:i386 libcupsmime1:i386 libcupsppdc1:i386 libcurl3 libcurl3:i386 libcurl3-gnutls:i386 libcurl4-openssl-dev:i386 libdate-calc-perl libdate-calc-xs-perl
  libdatrie1:i386 libdb4.8 libdb4.8:i386 libdb4.8++ libdb4.8++:i386 libdb5.1:i386 libdbus-1-3:i386 libdbus-1-dev:i386 libdbus-glib-1-2:i386 libdbus-java libdbusmenu-glib4:i386
  libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386 libdbusmenu-qt2:i386 libdc1394-22 libdc1394-22:i386 libdca0:i386 libdconf0:i386 libdecoration0:i386 libdee-1.0-4 libdigest-hmac-perl
  libdirac-encoder0:i386 libdiscid0:i386 libdpkg-perl libdrm-dev:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libdvbpsi7:i386 libdvdnav4
  libdvdread4 libebml3 libebml3:i386 libecryptfs0:i386 libelf1:i386 libelfg0:i386 libenca0:i386 libept1.4.12:i386 liberror-perl libesd0 libesd0:i386 libesd0-dev libesd0-dev:i386
  libevent-2.0-5:i386 libexif12:i386 libexpat1:i386 libexpat1-dev:i386 libfaac0:i386 libfaad2 libffado2:i386 libffi6:i386 libfftw3-3:i386 libfile-find-rule-perl libfl-dev libfl-dev:i386
  libflac++6:i386 libflac8:i386 libflite1:i386 libfluidsynth1 libfluidsynth1:i386 libfontconfig1:i386 libfontconfig1-dev:i386 libfreetype6:i386 libfreetype6-dev:i386 libgail-3-0
  libgail-3-0:i386 libgail18 libgail18:i386 libgamin0:i386 libgcc1:i386 libgck-1-0:i386 libgconf-2-4 libgconf-2-4:i386 libgconf2-4 libgconf2-4:i386 libgconf2.0-cil libgcr-3-common
  libgcrypt11:i386 libgcrypt11-dev:i386 libgd2-xpm:i386 libgdbm3:i386 libgdiplus libgdk-pixbuf2.0-0:i386 libgdu-gtk0 libgdu-gtk0:i386 libgdu0 libgdu0:i386 libgee2 libgee2:i386 libgegl-0.0-0
  libgeoclue0:i386 libgettextpo0 libgettextpo0:i386 libgfortran3 libgfortran3:i386 libgif-dev:i386 libgif4:i386 libgimp2.0 libgl1-mesa-dev:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libgl2ps0:i386 libglade2-0 libglade2-0:i386 libglade2.0-cil libglade2.0-cil-dev libglademm-2.4-1c2a:i386 libglapi-mesa:i386 libglew1.6 libglew1.6:i386 libglib-perl libglib2.0-0:i386
  libglib2.0-bin libglib2.0-cil libglib2.0-cil-dev libglib2.0-data libglib2.0-dev:i386 libglibmm-2.4-1c2a:i386 libglibmm-2.4-dev:i386 libglu1-mesa:i386 libglu1-mesa-dev:i386 libgme0:i386
  libgmp10:i386 libgmp3c2:i386 libgnome-keyring0:i386 libgnome-vfs2.0-cil libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnutls-dev:i386 libgnutls-openssl27 libgnutls-openssl27:i386 libgnutls26:i386 libgnutlsxx27 libgnutlsxx27:i386 libgomp1 libgomp1:i386 libgpg-error-dev:i386 libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgps20:i386 libgraph4:i386 libgraphicsmagick3 libgsm1:i386 libgsm1-dev:i386 libgsoap1 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgssrpc4 libgssrpc4:i386 libgstreamer-plugins-bad0.10-0 libgstreamer-plugins-bad0.10-0:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgstreamermm-0.10-2:i386
  libgtk-3-0 libgtk-3-0:i386 libgtk-3-bin libgtk-3-common libgtk2-perl libgtk2.0-0:i386 libgtk2.0-cil libgtk2.0-cil-dev libgtkglext1:i386 libgtkmm-2.4-1c2a:i386 libgtkmm-3.0-1:i386
  libgtksourceview-3.0-0 libgtksourceview-3.0-0:i386 libgtksourceview-3.0-common libgtkspell0 libgtop2-common libgucharmap-2-90-7:i386 libgudev-1.0-0:i386 libgvc5:i386 libgvpr1:i386
  libhal-dev:i386 libhal-storage-dev:i386 libhal-storage1:i386 libhal1:i386 libhcrypto4-heimdal:i386 libhdf5-openmpi-1.8.4:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhsqldb-java libhunspell-1.3-0:i386 libhx509-5-heimdal:i386 libibverbs1:i386 libice-dev:i386 libice6:i386 libidl-common libidl0 libidl0:i386 libidn11:i386 libidn11-dev:i386
  libiec61883-0:i386 libieee1284-3:i386 libieee1284-3-dev:i386 libindicator3-7:i386 libindicator7:i386 libiso9660-8 libjack-jackd2-0:i386 libjasper1:i386 libjmol-java libjpeg-dev
  libjpeg-turbo8:i386 libjpeg-turbo8-dev libjpeg-turbo8-dev:i386 libjpeg62 libjpeg62:i386 libjpeg8:i386 libjpeg8-dev libjpeg8-dev:i386 libjs-mootools libjson0:i386 libk5crypto3:i386
  libkadm5clnt-mit8 libkadm5clnt-mit8:i386 libkadm5srv-mit8 libkadm5srv-mit8:i386 libkate1:i386 libkdb5-6 libkdb5-6:i386 libkeyutils1:i386 libkms1 libkms1:i386 libkpathsea5
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5-dev:i386 libkrb5support0:i386 libkvilib4 liblapack3gf:i386 liblaunchpad-integration-3.0-1 liblaunchpad-integration-common liblcms1:i386
  liblcms1-dev liblcms1-dev:i386 liblcms2-2:i386 libldap-2.4-2:i386 libldap2-dev libldap2-dev:i386 liblircclient0:i386 libllvm2.9 libllvm2.9:i386 libllvm3.0:i386 liblo-dev:i386 liblo7:i386
  liblockfile1:i386 liblog4j1.2-java liblqr-1-0:i386 libltdl-dev libltdl-dev:i386 libltdl7:i386 liblua5.1-0 liblua5.1-0:i386 liblzma5:i386 liblzo2-2 liblzo2-2:i386 liblzo2-dev:i386 libmad0
  libmad0:i386 libmad0-dev:i386 libmail-sendmail-perl libmatroska5:i386 libmatthew-debug-java libmetacity-private0 libmikmod2 libmikmod2:i386 libmimic0:i386 libminc2-1:i386
  libminiupnpc8:i386 libmms0:i386 libmng1:i386 libmodplug1 libmono-2.0-1:i386 libmono-accessibility2.0-cil libmono-accessibility4.0-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-c5-1.1-cil libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-cecil-private-cil libmono-cil-dev libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-corlib2.0-cil libmono-corlib4.0-cil libmono-cscompmgd8.0-cil libmono-csharp4.0-cil libmono-custommarshalers4.0-cil libmono-data-tds2.0-cil libmono-data-tds4.0-cil
  libmono-db2-1.0-cil libmono-debugger-soft2.0-cil libmono-debugger-soft4.0-cil libmono-http4.0-cil libmono-i18n-cjk4.0-cil libmono-i18n-mideast4.0-cil libmono-i18n-other4.0-cil
  libmono-i18n-rare4.0-cil libmono-i18n-west2.0-cil libmono-i18n-west4.0-cil libmono-i18n2.0-cil libmono-i18n4.0-all libmono-i18n4.0-cil libmono-ldap2.0-cil libmono-ldap4.0-cil
  libmono-management2.0-cil libmono-management4.0-cil libmono-messaging-rabbitmq2.0-cil libmono-messaging-rabbitmq4.0-cil libmono-messaging2.0-cil libmono-messaging4.0-cil
  libmono-microsoft-build-engine4.0-cil libmono-microsoft-build-framework4.0-cil libmono-microsoft-build-tasks-v4.0-4.0-cil libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build2.0-cil libmono-microsoft-csharp4.0-cil libmono-microsoft-visualc10.0-cil libmono-microsoft-web-infrastructure1.0-cil libmono-microsoft8.0-cil libmono-npgsql2.0-cil
  libmono-npgsql4.0-cil libmono-opensystem-c4.0-cil libmono-oracle2.0-cil libmono-oracle4.0-cil libmono-peapi2.0-cil libmono-peapi4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil
  libmono-rabbitmq2.0-cil libmono-rabbitmq4.0-cil libmono-relaxng2.0-cil libmono-relaxng4.0-cil libmono-security2.0-cil libmono-security4.0-cil libmono-sharpzip2.6-cil
  libmono-sharpzip2.84-cil libmono-sharpzip4.84-cil libmono-simd2.0-cil libmono-simd4.0-cil libmono-sqlite2.0-cil libmono-sqlite4.0-cil libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil libmono-system-configuration-install4.0-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil libmono-system-data-linq2.0-cil libmono-system-data-linq4.0-cil libmono-system-data-services-client4.0-cil libmono-system-data-services4.0-cil
  libmono-system-data2.0-cil libmono-system-data4.0-cil libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil libmono-system-identitymodel-selectors4.0-cil libmono-system-identitymodel4.0-cil libmono-system-ldap2.0-cil libmono-system-ldap4.0-cil
  libmono-system-management4.0-cil libmono-system-messaging2.0-cil libmono-system-messaging4.0-cil libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-runtime-caching4.0-cil libmono-system-runtime-durableinstancing4.0-cil libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime2.0-cil libmono-system-runtime4.0-cil libmono-system-security4.0-cil libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-routing4.0-cil libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0-cil libmono-system-serviceprocess4.0-cil libmono-system-transactions4.0-cil
  libmono-system-web-abstractions4.0-cil libmono-system-web-applicationservices4.0-cil libmono-system-web-dynamicdata4.0-cil libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-mvc1.0-cil libmono-system-web-mvc2.0-cil libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web2.0-cil libmono-system-web4.0-cil libmono-system-windows-forms-datavisualization4.0-cil libmono-system-windows-forms4.0-cil libmono-system-xaml4.0-cil
  libmono-system-xml-linq4.0-cil libmono-system-xml4.0-cil libmono-system2.0-cil libmono-system4.0-cil libmono-tasklets2.0-cil libmono-tasklets4.0-cil libmono-wcf3.0-cil libmono-web4.0-cil
  libmono-webbrowser2.0-cil libmono-webbrowser4.0-cil libmono-webmatrix-data4.0-cil libmono-windowsbase3.0-cil libmono-windowsbase4.0-cil libmono-winforms2.0-cil libmono2.0-cil libmp3lame0
  libmp3lame0:i386 libmpc2:i386 libmpeg2-4:i386 libmpfr4:i386 libmpg123-0 libmpg123-0:i386 libmpg123-dev libmpg123-dev:i386 libmysqlclient18:i386 libnautilus-extension1a:i386
  libncurses5:i386 libncurses5-dev libncursesw5:i386 libnet-dns-perl libnet-ip-perl libnet1:i386 libnet1-dev:i386 libnetcdf6:i386 libnetpbm10:i386 libnettle4:i386 libnl-dev:i386 libnl1
  libnl1:i386 libnotify-bin:i386 libnotify4 libnotify4:i386 libnspr4:i386 libnspr4-0d libnspr4-0d:i386 libnss3:i386 libnss3-1d libnss3-1d:i386 libntfs10:i386 libnuma1:i386
  libnumber-compare-perl libnunit-cil-dev libnunit2.5-cil libodbc1 libodbc1:i386 libode-dev:i386 libode1:i386 libofa0:i386 libogg-dev:i386 libogg0:i386 liboil0.3 liboil0.3:i386
  libopenal-data libopenal-dev:i386 libopenal1 libopenal1:i386 libopencore-amrnb0:i386 libopencore-amrwb0:i386 libopenjpeg2:i386 libopenmpi1.3:i386 libopenspc0:i386 liborbit2 liborbit2:i386
  liborc-0.4-0:i386 libosmesa6 libosmesa6:i386 libosp5:i386 libossp-uuid16:i386 libostyle1c2:i386 libp11-kit-dev:i386 libp11-kit0:i386 libpam-cap libpam-cap:i386 libpam-gnome-keyring:i386
  libpam-modules:i386 libpam-winbind libpam-winbind:i386 libpam0g:i386 libpango-perl libpango1.0-0:i386 libpangomm-1.4-1:i386 libpathplan4:i386 libpcap-dev libpcap0.8:i386 libpcap0.8-dev
  libpciaccess0:i386 libpcre3:i386 libpcre3-dev:i386 libpcrecpp0 libpcrecpp0:i386 libpcsclite1:i386 libpeas-1.0-0 libpeas-common libphonon4:i386 libpipeline1:i386 libpixman-1-0:i386
  libpixman-1-dev:i386 libpkcs11-helper1 libpkcs11-helper1:i386 libpng12-0:i386 libpng12-dev:i386 libpod-plainer-perl libpolkit-agent-1-0:i386 libpolkit-gobject-1-0:i386 libpoppler-glib8
  libpoppler-glib8:i386 libpoppler19:i386 libpopt-dev libpopt-dev:i386 libpopt0:i386 libpostproc52 libpostproc52:i386 libpq5:i386 libprotobuf7:i386 libproxy1:i386 libpthread-stubs0
  libpthread-stubs0:i386 libpthread-stubs0-dev libpthread-stubs0-dev:i386 libpulse-dev:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libqt3-mt:i386 libqt4-dbg:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-designer:i386 libqt4-dev:i386 libqt4-gui:i386 libqt4-help:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-opengl-dev:i386 libqt4-qt3support:i386
  libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libqtwebkit-dev:i386 libqtwebkit4:i386 libquadmath0 libquadmath0:i386 librarian0 libraw1394-11:i386 librcd0:i386 libreadline5 libreadline5:i386 libreadline6:i386 libreoffice-base
  libreoffice-filter-mobiledev libreoffice-help-ca libreoffice-help-cs libreoffice-help-da libreoffice-help-de libreoffice-help-dz libreoffice-help-el libreoffice-help-en-gb
  libreoffice-help-es libreoffice-help-et libreoffice-help-eu libreoffice-help-fi libreoffice-help-fr libreoffice-help-gl libreoffice-help-hi libreoffice-help-hu libreoffice-help-it
  libreoffice-help-ja libreoffice-help-km libreoffice-help-ko libreoffice-help-nl libreoffice-help-om libreoffice-help-pl libreoffice-help-pt libreoffice-help-pt-br libreoffice-help-ru
  libreoffice-help-sk libreoffice-help-sl libreoffice-help-zh-cn libreoffice-help-zh-tw libreoffice-java-common libreoffice-l10n-af libreoffice-l10n-ar libreoffice-l10n-as
  libreoffice-l10n-ast libreoffice-l10n-be libreoffice-l10n-bg libreoffice-l10n-bn libreoffice-l10n-br libreoffice-l10n-bs libreoffice-l10n-ca libreoffice-l10n-cs libreoffice-l10n-da
  libreoffice-l10n-de libreoffice-l10n-dz libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-l10n-eo libreoffice-l10n-es libreoffice-l10n-et libreoffice-l10n-eu
  libreoffice-l10n-fa libreoffice-l10n-fi libreoffice-l10n-fr libreoffice-l10n-ga libreoffice-l10n-gl libreoffice-l10n-gu libreoffice-l10n-he libreoffice-l10n-hi libreoffice-l10n-hr
  libreoffice-l10n-hu libreoffice-l10n-id libreoffice-l10n-is libreoffice-l10n-it libreoffice-l10n-ja libreoffice-l10n-ka libreoffice-l10n-km libreoffice-l10n-ko libreoffice-l10n-ku
  libreoffice-l10n-lt libreoffice-l10n-lv libreoffice-l10n-mk libreoffice-l10n-ml libreoffice-l10n-mn libreoffice-l10n-mr libreoffice-l10n-nb libreoffice-l10n-ne libreoffice-l10n-nl
  libreoffice-l10n-nn libreoffice-l10n-nso libreoffice-l10n-oc libreoffice-l10n-om libreoffice-l10n-or libreoffice-l10n-pa-in libreoffice-l10n-pl libreoffice-l10n-pt libreoffice-l10n-pt-br
  libreoffice-l10n-ro libreoffice-l10n-ru libreoffice-l10n-rw libreoffice-l10n-si libreoffice-l10n-sk libreoffice-l10n-sl libreoffice-l10n-sr libreoffice-l10n-st libreoffice-l10n-zh-cn
  libreoffice-l10n-zh-tw libresid-builder0c2a:i386 libroken18-heimdal:i386 librpm2:i386 librpmio2:i386 librpmsign0:i386 librsvg2-2:i386 librsvg2-common librsvg2-common:i386 librtmp-dev:i386
  librtmp0:i386 libruby1.8:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libschroedinger-1.0-0:i386 libsdl-image1.2 libsdl-image1.2:i386 libsdl1.2debian
  libsdl1.2debian:i386 libselinux1:i386 libsensors4:i386 libservlet2.5-java libsgmls-perl libshout3:i386 libsidplay1:i386 libsidplay2:i386 libsigc++-2.0-0c2a:i386 libsigc++-2.0-dev:i386
  libslang2:i386 libslang2-dev:i386 libsm-dev:i386 libsm6:i386 libsmbclient:i386 libsndfile1:i386 libsoundtouch0 libsoundtouch0:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsp1c2
  libspandsp2:i386 libspectrum8:i386 libspeex1:i386 libspeexdsp1:i386 libspice-client-glib-2.0-1:i386 libspice-client-gtk-2.0-1:i386 libspice-protocol-dev libspice-server-dev:i386
  libspice-server1:i386 libspiro0:i386 libsqlite3-0:i386 libssh-4:i386 libssl-dev:i386 libssl-doc libssl0.9.8 libssl0.9.8:i386 libssl1.0.0:i386 libstartup-notification0
  libstartup-notification0:i386 libstdc++6:i386 libstlport4.6ldbl:i386 libswscale2 libswscale2:i386 libswt-cairo-gtk-3-jni:i386 libswt-gtk-3-java:i386 libswt-gtk-3-jni:i386
  libsys-hostname-long-perl libtag1-vanilla:i386 libtag1c2a:i386 libtalloc2:i386 libtar0:i386 libtasn1-3:i386 libtasn1-3-dev:i386 libtdb1:i386 libtext-glob-perl libtextcat-data libthai0:i386
  libtheora0:i386 libtiff-tools:i386 libtiff4:i386 libtiff4-dev:i386 libtiffxx0c2 libtiffxx0c2:i386 libtinfo-dev libtinfo-dev:i386 libtinfo5:i386 libtommath0:i386 libtorque2:i386 libts-0.0-0
  libts-0.0-0:i386 libtwolame0:i386 libudev0:i386 libuninameslist0:i386 libunique-3.0-0:i386 libunistring0 libunistring0:i386 libunixsocket-java libupnp3:i386 libusb-0.1-4:i386
  libusb-1.0-0:i386 libusb-dev:i386 libutouch-evemu1 libutouch-evemu1:i386 libutouch-frame1:i386 libuuid1:i386 libv4l-0:i386 libv4l-dev:i386 libv4lconvert0:i386 libva-x11-1 libva-x11-1:i386
  libva1 libva1:i386 libvcdinfo0 libvdpau1 libvdpau1:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvncserver0 libvo-aacenc0 libvo-aacenc0:i386 libvo-amrwbenc0 libvo-amrwbenc0:i386
  libvoikko1:i386 libvorbis-dev:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libvpx1:i386 libvte-2.90-9 libvte-2.90-common libvte-common libvte9 libwavpack1:i386
  libwbclient0:i386 libwebkitgtk-1.0-common libwebkitgtk-3.0-common libwildmidi-config libwildmidi1 libwildmidi1:i386 libwind0-heimdal:i386 libwmf0.2-7 libwrap0:i386 libwxbase2.6-0:i386
  libwxbase2.8-0 libwxbase2.8-0:i386 libwxgtk2.6-0:i386 libwxgtk2.8-0 libwxgtk2.8-0:i386 libx11-6:i386 libx11-dev libx11-dev:i386 libx11-doc libx11-xcb1:i386 libx264-120 libx264-120:i386
  libxau-dev libxau-dev:i386 libxau6:i386 libxaw7:i386 libxcb-composite0 libxcb-composite0:i386 libxcb-glx0:i386 libxcb-keysyms1:i386 libxcb-randr0 libxcb-randr0:i386 libxcb-render0:i386
  libxcb-render0-dev libxcb-render0-dev:i386 libxcb-shape0:i386 libxcb-shm0:i386 libxcb-shm0-dev libxcb-shm0-dev:i386 libxcb-util0:i386 libxcb-xv0 libxcb-xv0:i386 libxcb1:i386 libxcb1-dev
  libxcb1-dev:i386 libxcomposite-dev:i386 libxcomposite1:i386 libxcursor-dev:i386 libxcursor1:i386 libxdamage-dev:i386 libxdamage1:i386 libxdmcp-dev libxdmcp-dev:i386 libxdmcp6:i386
  libxerces2-java libxext-dev:i386 libxext6:i386 libxfixes-dev:i386 libxfixes3:i386 libxft-dev:i386 libxft2:i386 libxi-dev:i386 libxi6:i386 libxine1-bin libxine1-misc-plugins
  libxinerama-dev:i386 libxinerama1:i386 libxml++2.6-2:i386 libxml++2.6-dev:i386 libxml-commons-external-java libxml-commons-resolver1.1-java libxml-parser-perl libxml2:i386 libxml2-dev
  libxml2-dev:i386 libxmu-dev:i386 libxmu-headers libxmu6:i386 libxmuu1:i386 libxpm4:i386 libxrandr-dev:i386 libxrandr2:i386 libxrender-dev:i386 libxrender1:i386 libxslt1-dev
  libxslt1-dev:i386 libxslt1.1:i386 libxss1:i386 libxt-dev:i386 libxt6:i386 libxtst6:i386 libxv-dev:i386 libxv1:i386 libxvidcore4 libxvidcore4:i386 libxxf86vm-dev:i386 libxxf86vm1:i386
  libzbar0:i386 libzeitgeist-1.0-1:i386 libzvbi-common linux-headers-3.2.0-24 linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic linux-headers-generic linux-libc-dev linux-libc-dev:i386
  lmodern lp-solve:i386 lsof:i386 lua5.1:i386 luatex lynx lynx-cur m4 macchanger:i386 make manpages-dev menu mesa-common-dev:i386 mesa-utils:i386 metacity-common min12xxw minissdpd:i386
  mono-4.0-gac mono-csharp-shell mono-dmcs mono-gac mono-runtime mono-xbuild monodoc-base myspell-af myspell-bg myspell-ca myspell-cs myspell-el-gr myspell-en-au myspell-en-gb myspell-en-za
  myspell-eo myspell-es myspell-et myspell-fa myspell-fo myspell-ga myspell-gd myspell-gv myspell-he myspell-hr myspell-hy myspell-it myspell-ku myspell-lt myspell-lv myspell-nb myspell-nl
  myspell-nn myspell-pl myspell-pt myspell-pt-br myspell-pt-pt myspell-sk myspell-sl mythes-ca mythes-cs mythes-de mythes-de-ch mythes-en-au mythes-en-us mythes-fr mythes-hu mythes-it
  mythes-ne mythes-pl mythes-ro mythes-ru mythes-sk ncurses-term netpbm:i386 notification-daemon:i386 ntrack-module-rtnetlink-0 odbcinst1debian2:i386 openjdk-6-jre openjdk-6-jre:i386
  openjdk-6-jre-headless openjdk-6-jre-headless:i386 openjdk-6-jre-lib openjdk-7-jre-headless openjdk-7-jre-headless:i386 openjdk-7-jre-lib opense-basic oss-compat p7zip:i386 p7zip-full:i386
  patch pavucontrol:i386 pax perl-doc pgf phonon:i386 phonon-backend-gstreamer:i386 pkg-config playmidi:i386 pmidi:i386 pnm2ppa po-debconf policykit-1-gnome polipo:i386 poppler-data
  prelink:i386 prosper ps2eps psensor-common ptouch-driver pulseaudio-esound-compat:i386 pxljr python-apsw python-apsw-doc python-aptdaemon python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-cairo python-central python-defer python-gtk2 python-mutagen python-notify python-scour python-socksipy python-support python-vte python-wxversion
  python-zeitgeist qjackctl qsynth:i386 qt-assistant-compat:i386 qt4-linguist-tools:i386 qt4-qmake:i386 quilt rar:i386 rarian-compat rastertosag-gdi recordmydesktop reiserfsprogs:i386
  rpm-common:i386 rpm2cpio:i386 scalpel:i386 secure-delete:i386 sgmlspl sharutils:i386 socat:i386 software-properties-common software-properties-gtk sp splix sysinfo tcl8.4:i386 tcl8.5:i386
  tdb-tools:i386 testdisk:i386 tex-common texlive-base texlive-binaries texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended
  texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base texlive-latex-base-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pstricks
  texlive-pstricks-doc tipa tk8.5:i386 tp-smapi-dkms tree:i386 tsconf ttf-alee ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-bengali-fonts ttf-dejavu ttf-dejavu-extra
  ttf-devanagari-fonts ttf-droid ttf-dzongkha ttf-gujarati-fonts ttf-kacst ttf-kacst-one ttf-kannada-fonts ttf-khmeros ttf-khmeros-core ttf-lao ttf-liberation ttf-lyx ttf-malayalam-fonts
  ttf-mgopen ttf-mscorefonts-installer ttf-opensymbol ttf-oriya-fonts ttf-sil-abyssinica ttf-sil-ezra ttf-sil-gentium-basic ttf-sil-padauk ttf-takao-gothic ttf-takao-mincho ttf-takao-pgothic
  ttf-thai-tlwg ttf-tmuni ttf-umefont ttf-unfonts-core ttf-unfonts-extra ttf-wqy-zenhei tzdata-java unixodbc unixodbc-dev:i386 unrar:i386 uuid:i386 videolan-doc virtualbox virtualbox-dkms
  virtualbox-qt vlc-data voikko-fi:i386 wbrazilian wbritish wbulgarian wcatalan wdanish wdutch wfaroese wfrench wgalician-minimos whois:i386 winbind:i386 wine:i386 wine-gecko1.4
  wine-gecko1.4:i386 wine-gecko1.5 wine-gecko1.5:i386 wine1.5:i386 wine1.5-amd64 wine1.5-i386:i386 wipe:i386 wireless-crda wirish witalian wmanx wngerman wnorwegian wogerman wpolish
  wportuguese wspanish wswiss wwwconfig-common x-ttcidfont-conf x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xfonts-100dpi xloadimage:i386
  xorg-sgml-doctools xscreensaver-data:i386 xscreensaver-gl:i386 xterm xtrans-dev xul-ext-ubufox yelp-xsl zenity-common zlib1g:i386 zlib1g-dev zlib1g-dev:i386
```

I tried copy-pasting chucks of that because the whole thing wouldn't install at once (that way I could see the ones with errors so it wouldn't have to interrupt the entire process), and it seemed to work relatively well, but I'm running into huge problems.  Now, when I tried "sudo apt-get install winbind:i386 wine:i386 wine-gecko1.4 wine-gecko1.4:i386 wine-gecko1.5 wine-gecko1.5:i386 wine1.5:i386 wine1.5-amd64 wine1.5-i386:i386 wipe:i386 wireless-crda wirish witalian wmanx" (and actually many other packages, not just those) the output is:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcanberra-gtk3-0:i386 libmono-cairo4.0-cil linux-headers-3.2.0-25 libmono-system-drawing4.0-cil notification-daemon:i386 libnotify4:i386 libbsd0:i386 libclamav6 libcanberra0:i386
  libquadmath0:i386 python-scour kvirc-data librarian0 rarian-compat linux-headers-generic libglade2-0 libvorbisfile3:i386 linux-headers-3.2.0-25-generic libtommath0 libgfortran3:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binfmt-support:i386 cabextract:i386 cron libcap2:i386 libcapi20-3 libcapi20-3:i386 libgettextpo0:i386 libmpg123-0 libmpg123-0:i386 libodbc1 libopenal-data libopenal1 libopenal1:i386
  libpam-modules:i386 libpipeline1:i386 libpopt0:i386 libtalloc2:i386 libunistring0:i386 libwbclient0:i386 libxslt1.1:i386 module-init-tools:i386 ntrack-module-rtnetlink-0 sudo:i386 unixodbc
  unrar:i386 unzip:i386 winetricks:i386
Suggested packages:
  checksecurity libmyodbc odbc-postgresql tdsodbc unixodbc-bin zip:i386 dosbox:any:i386
Recommended packages:
  wine1.4-amd64 wine1.4-i386:i386 cups-bsd:i386 gnome-exe-thumbnailer:i386 kde-runtime:i386 ttf-wqy-microhei:i386 xdg-utils:i386 gettext:i386
The following packages will be REMOVED:
  accountsservice acpi-support acpid acroread-common alsa-base alsa-utils amarok-common amarok-utils anacron apparmor apport apport-kde aptdaemon apturl-kde ark at:i386 avahi-autoipd
  avahi-daemon avahi-utils bind9-host binfmt-support bless bluedevil bluez bluez-alsa bluez-cups brltty build-essential cabextract cdbs chkconfig clamav clamav-base clamav-freshclam
  cli-common colord compiz-plugins-extra:i386 compiz-plugins-main:i386 compiz-plugins-main-default:i386 console-setup consolekit cron:i386 cryptsetup cryptsetup-bin cups cups-bsd cups-client
  cups-driver-gutenprint cvs:i386 dbus dbus-x11 debconf-i18n debhelper dh-apparmor dh-make dh-modaliases dh-translations dhcp3-server dkms dmsetup dnsutils dolphin dpkg-dev eject enchant
  flex:i386 fonts-arphic-uming foo2zjs foomatic-db-engine foomatic-filters freespacenotifier friendly-recovery ftp fuse gconf2 gdb gedit gettext gir1.2-peas-1.0 git git-core gpsd grub-common
  grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common gstreamer0.10-qapt gvfs gvfs:i386 gvfs-daemons gwenview hddtemp:i386 hostname hplip hplip-cups hunspell-ar hunspell-da hunspell-de-at
  hunspell-de-ch hunspell-de-de hunspell-en-ca hunspell-en-us hunspell-eu-es hunspell-fr hunspell-gl-es hunspell-hu hunspell-kk hunspell-ko hunspell-ml hunspell-ne hunspell-ro hunspell-ru
  hunspell-se hunspell-sr hyphen-af hyphen-bn hyphen-ca hyphen-de hyphen-en-us hyphen-fr hyphen-hr hyphen-hu hyphen-it hyphen-kn hyphen-pa hyphen-pl hyphen-ro hyphen-sl hyphen-sr icoutils
  intltool intltool-debian iputils-ping irqbalance isc-dhcp-server jadetex java-wrappers jockey-common jockey-kde k3b kaccessible kate katepart kbd kcalc kde-baseapps-bin kde-config-gtk
  kde-config-touchpad kde-runtime kde-style-oxygen kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf
  kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-kresources kdepim-runtime kdepim-strigi-plugins
  kdepimlibs-kio-plugins kdesudo kdm kdoctools kerneloops-daemon keyboard-configuration khelpcenter4 kinfocenter klipper kmag kmenuedit kmix kmousetool konsole kopete-message-indicator kppp
  ksnapshot ksysguard ksystemlog kubuntu-debug-installer kubuntu-firefox-installer kubuntu-notification-helper kvirc kvirc-modules kvkbd kwalletmanager language-selector-common
  language-selector-kde latex-beamer latex-xcolor libakonadi-calendar4 libakonadi-contact4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libbind9-80 libbit-vector-perl libcalendarsupport4 libcanberra-gtk3-module:i386 libcanberra-pulse libcarp-clan-perl
  libcrypt-passwdmd5-perl libcryptsetup4 libdebconf-kde0 libdevmapper-event1.02.1 libdevmapper1.02.1 libdns81 libdpkg-perl libencode-locale-perl liberror-perl libeventviews4
  libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl libfont-afm-perl libgdu0 libglade2.0-cil libglib2.0-cil libgsoap1
  libgtk2.0-cil libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libibverbs1:i386 libimobiledevice2 libincidenceeditorsng4 libio-socket-inet6-perl libio-socket-ssl-perl libisccfg82 libk3b6 libkabc4
  libkalarmcal2 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkde3support4 libkdegames5a libkdepim4 libkdepimdbusinterfaces4
  libkdewebkit5 libkemoticons4 libkexiv2-10 libkfile4 libkholidays4 libkhtml5 libkimap4 libkio5 libkipi8 libkldap4 libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4
  libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkonq-common libkonq5abi1 libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4
  libkprintutils4 libkresources4 libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libkunitconversion4 libkvilib4 libkworkspace4abi1
  libkxmlrpcclient4 liblapack3gf:i386 liblocale-gettext-perl liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl libmail-sendmail-perl libmailcommon4 libmailtools-perl
  libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmsn0.3 libmuonprivate1 libnet-http-perl libnet-ssleay-perl libnss-mdns
  libpam-ck-connector libpaper-utils libparted0debian1 libpeas-1.0-0 libplasma3 libplasmaclock4abi3 libplasmagenericshell4 libplist1 libprocesscore4abi1 libprocessui4a libpython2.7
  libqapt-runtime libqca2 libqca2-plugin-ossl libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-emailmerge libreoffice-help-en-us libreoffice-kde
  libreoffice-math libreoffice-style-oxygen libreoffice-writer libsane libsasl2-modules libsocket6-perl libsolid4 libsolidcontrol4abi2 libspectre1 libsyndication4 libsys-hostname-long-perl
  libtaskmanager4abi3 libtemplateparser4 libtext-charwidth-perl libtext-wrapi18n-perl libthreadweaver4 libtimedate-perl libupower-glib1 liburi-perl libusbmuxd1 libweather-ion6 libwww-perl
  libwww-robotrules-perl libxml-parser-perl linux-generic linux-image-3.2.0-23-generic linux-image-3.2.0-24-generic linux-image-3.2.0-25-generic linux-image-generic linux-sound-base lmodern
  metacity-common mlocate modemmanager module-init-tools muon muon-installer muon-notifier muon-updater myspell-af myspell-bg myspell-ca myspell-cs myspell-el-gr myspell-en-au myspell-en-gb
  myspell-en-za myspell-eo myspell-es myspell-et myspell-fa myspell-fo myspell-ga myspell-gd myspell-gv myspell-he myspell-hr myspell-hy myspell-it myspell-ku myspell-lt myspell-lv
  myspell-nb myspell-nl myspell-nn myspell-pl myspell-pt myspell-pt-br myspell-pt-pt myspell-sk myspell-sl mythes-ca mythes-cs mythes-de mythes-de-ch mythes-en-au mythes-en-us mythes-fr
  mythes-hu mythes-it mythes-ne mythes-pl mythes-ro mythes-ru mythes-sk netbase network-manager network-manager-pptp ntfs-3g ntpdate openoffice.org-hyphenation openssh-client openssh-server
  parted partitionmanager pgf plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python
  plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-menubar plasma-widget-message-indicator plasma-widget-networkmanagement plasma-widgets-addons
  plasma-widgets-workspace plymouth-label plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text plymouth-theme-ubuntu-text pm-utils po-debconf policykit-1 policykit-1-gnome polkit-kde-1
  powermgmt-base ppp pppconfig pppoeconf pptp-linux printer-applet printer-driver-foo2zjs printer-driver-gutenprint printer-driver-hpcups printer-driver-pxljr prosper ps2eps pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 python-aptdaemon python-kde4 python-qt4 python-uno qapt-batch qapt-deb-installer quassel rekonq resolvconf rfkill rsyslog rtkit
  samba-common-bin sane-utils software-properties-kde ssh-import-id ssl-cert sudo system-config-printer-kde systemsettings tcpdump telnet tex-common texlive-base texlive-binaries
  texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base
  texlive-latex-base-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pstricks texlive-pstricks-doc tipa ubuntu-minimal udisks ufw unzip update-inetd
  update-manager-kde update-notifier-common upower ureadahead usb-creator-common usb-creator-kde usb-modeswitch usb-modeswitch-data usbmuxd userconfig uuid-runtime wamerican wget wngerman
  wnorwegian wogerman wpasupplicant wpolish wportuguese wspanish wswiss x-ttcidfont-conf xinit xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xul-ext-ubufox
The following NEW packages will be installed:
  binfmt-support:i386 cabextract:i386 cron libcap2:i386 libcapi20-3 libcapi20-3:i386 libgettextpo0:i386 libmpg123-0 libmpg123-0:i386 libodbc1 libopenal-data libopenal1 libopenal1:i386
  libpam-modules:i386 libpipeline1:i386 libpopt0:i386 libtalloc2:i386 libunistring0:i386 libwbclient0:i386 libxslt1.1:i386 module-init-tools:i386 ntrack-module-rtnetlink-0 sudo:i386 unixodbc
  unrar:i386 unzip:i386 winbind:i386 wine:i386 wine-gecko1.4 wine-gecko1.4:i386 wine-gecko1.5 wine-gecko1.5:i386 wine1.5:i386 wine1.5-amd64 wine1.5-i386:i386 winetricks:i386 wipe:i386
  wireless-crda wirish witalian wmanx
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  hostname
0 upgraded, 41 newly installed, 577 to remove and 0 not upgraded.
Need to get 81.3 MB/113 MB of archives.
After this operation, 1,612 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]
```

Well that can't be right!  It wants me to remove random things like kdesudo?  And hostname!?  wtf?  So I think I'm doing something wrong.  I also noticed in the whole list that wine1.5 wasn't one of the packages even though it has a lot of Wine-related things.  And when I tried "sudo apt-get install wine1.5" the Wine installation went over perfectly.  So I'm thinking that all these things I'm trying to transfer over are just dependencies or whatever and doing "sudo apt-get install whateverprogram" would be more efficient than "sudo apt-get install all the pieces of the program".  So is there a way for me to get a list of installed PROGRAMS instead of just the programs' installed components?  I'm trying to move my installation from one computer to another, and I need to be able to access all the programs I had previously.

I'm really stuck.  I've tried everything I could find.  I even tried directly transferring /usr (it didn't go over well)!  I know (or at least hope) that transferring /home will give me all my settings, custom themes, custom menu structure, etc, but none of that will matter if I don't have the programs that go along with it.

So how do I transfer all my programs?  I'm really stuck here...

---

### Post by ajgreeny on 2012-06-03
It might be quicker and easier to clone your current partition(s) or whole disk with [clonezilla]("http://clonezilla.org/") and then restore the clone(s) to the new machine.  You may then need to install other drivers for graphics or wireless, depending on hardware differences, but it should be much quicker than starting over again, downloading and installing everything.

---

### Post by Lorin Ricker on 2012-06-03
Boy, Stonecold! You're a braver dude than I!... I'm not sure how to proceed along the lines of what you're doing, but I do note the following things:

[LIST=1]
[*] The list produced by dpkg --get-selections is in alphabetical order.  Pretty obviously, if you think about it, things won't install correctly if you try to use this list directly, as there's nothing alphabetical about installing application packages and their dependency packages.

[*] Clearly, "...and it seemed to work relatively well, but I'm running into huge problems" would imply that a lack of (many? any?) error messages does *_not_* imply that "things worked well."

[*] The distinction you next make, about installing "PROGRAMS" (a better term here is "applications") rather than just "packages" (a more generic term which includes both applications, support libraries, drivers and other core software components), is more on-track.  Unfortunately, I don't know of any dpkg sub-command (and I've looked in the man dpkg page) which regurgitates only ***applications***, which is what you seem to be looking for... Sorry.
[/LIST]

With apologies for this advice after your horse has left the barn -- What I've done for years is rather old-school, but is the only effective thing that I know to do for this problem:  **I keep a _system_ _logbook_**.  Yes, one of those old-fashioned things that you write in with a pen or pencil.  In it, I record not only significant system events (like each backup, upgrades, etc.), but also tables of which applications, by package name, that I've installed (and when, and which version).

Then, when I get to upgrade or move a system, I've got a ready list of applications to re-install... I just work down through the list in Synaptic (or now, in Ubuntu Software Center) and install the ones that I still want (yes, I often abandon an app after using it for a while... it's just no longer needed).

*Advice*: With a little thought, you could probably draw up a list from memory of the applications that you're actively using, and (re)build your system by just installing those.  Your private configuration files (hidden files in /home/<yourusername>...) provide some clues & memory aides as you build your manual list.  Then, if and when you discover an old app that you forgot, but suddenly need again, you can just re-install it at that time.  The ones that you've forgotten and never need again are better off left behind, uninstalled.

This is a place and case where "being thorough", even anal-retentive, about your former system's installed app list could be counter-productive.

Hope this helps -- I mean it constructively, not critically! ;) -- Lorin

---

### Post by Stonecold1995 on 2012-06-03
> **ajgreeny said:**
> It might be quicker and easier to clone your current partition(s) or whole disk with [clonezilla]("http://clonezilla.org/") and then restore the clone(s) to the new machine.  You may then need to install other drivers for graphics or wireless, depending on hardware differences, but it should be much quicker than starting over again, downloading and installing everything.

Using Clonezilla might be hard because my old computer only has one partition for the whole install, but the new one has a partition for /boot and /, and a partition for /home on a whole different drive.  Is there a way for me to work with that?  My new computer has full disk encryption for /home and encryption for / (/boot is unencrypted), so I probably won't be able to transfer it using a live CD because I don't know how to mount that kind of encrypted partition.  Is there a way for me to split up my old partition and place the right pieces in an encrypted disk like that?  I've tried using PartedMagic, but it won't run on my new computer (the screen just stays black and flickers blue every few seconds) and also it can't transfer special files (it thinks /dev/zero really is infinitely large and won't copy it).

Also, how do I re-install the correct drivers?  Is there a command or program that I can run that will detect new hardware automatically correct any hardware issues?  The two computers *are* quite different.  My old one is an HP Pavilion dv6, my new one is a MainGear ex-L 15 SuperStock, and the hardware couldn't be more different (AMD Radeon 6770M vs nVidia GeForce 675M, Bigfoot Killer Wireless vs some kind of Intel Wireless, etc).

---

### Post by Lorin Ricker on 2012-06-03
> **Stonecold1995 said:**
> 
...The two computers *are* quite different. ...

Given all the differences between the two systems you've described, you are facing *multiple equations with multiple unknowns*.  This is going to drive you crazy.

*My best advice*:  Stop trying to "finesse" this installation on your new system.  You're just gonna get in deep and become maddeningly frustrated.  Cloning and copying "the whole system" are gonna be futile.

Instead:  1) Do a clean install from a your favorite distro CDROM onto the new system.  It should be able to handle your new system's partitions, including the encrypted one... and you know, you don't have to keep it encrypted if you don't want/need that complexity? -- Change it at this point of virgin installation.

2) Get basic networking up and functional on your new system -- likely needed and done by the install anyway.  Be sure that you can reboot it and regain net connectivity before proceeding.

3) Be sure that the user account that you set up on your new system carries the same (**uid**,**gid**) pair (user-id and group-id) as your old account on your old system... Not essential, but if there's no pressing reason to change this, it'll be easier to do the next steps if they coincide (are equal).

4) Use your network, esp. **ssh** and **rsync**, to copy your own **/home/<yourusername>...** directory tree from your old system to your new, retaining file ownerships (uid,gid) as you transfer the dir-tree.  Repeat as needed for any other user accounts and dir-trees (spouse, kids, etc.), and again retaining (uid,gid) pairs for each account and dir-tree.

5) Now, as the last step, install the applications you *need* (again)... see my previous post.  Doing this after your move your own dir-tree(s) means that you'll be retaining your own personal configurations and settings per-application (in general), including any "automatic conversions & upgrades" that a particular app might want to impose, rather than trying to cope with these things during the dir-tree transfers.  This usually avoids unwanted surprises.

6) Probably the thing that you'll ***not*** be able to directly transfer from old to new system is/are the desktop settings and customization.  Again, the path of least resistance and effort is to just bite the bullet and customize your new system's desktop from scratch and as-you-go/need.  Here again, IMHO, anal-retentiveness is counter-productive... *especially* here. Doing desktop customization a second (third? ...?) time will allow you to rethink your configurations and possibly learn new and more effective dt-tricks.  And if you're actually moving from Gnome to Unity, almost nothing "transfers" anyway.

7) Keep your old system alive and online for a week or two as a point-of-reference (checkpoint) as you continue to configure your new one... You'll know when you're comfortable in decommissioning the old one, re-purposing it for something neat, right? ;)

Summary: Taking the path of least resistance here is going to save you hours, even *days*, of frustrating work.  _IMHO_, doing the above is *much less work and hassle* than trying to "shortcut" this thing.  Again, this is offered constructively, not critically! -- Lorin

---

### Post by Stonecold1995 on 2012-06-03
> **Lorin Ricker said:**
> 
6) Probably the thing that you'll ***not*** be able to directly transfer from old to new system is/are the desktop settings and customization.  Again, the path of least resistance and effort is to just bite the bullet and customize your new system's desktop from scratch and as-you-go/need.  Here again, IMHO, anal-retentiveness is counter-productive... *especially* here. Doing desktop customization a second (third? ...?) time will allow you to rethink your configurations and possibly learn new and more effective dt-tricks.  And if you're actually moving from Gnome to Unity, almost nothing "transfers" anyway.

That's one of the thing I MOST need transferred!  I thought things like menu customizations, etc were stored in /home though?  I actually almost managed to successfully transfer everything once (all settings etc were successfully moved, and if I remember correctly all the programs were also transferred (I think I used "sudo cp -ru" to transfer new applications from the old /usr to the new one).  The directories I transferred were /home, /etc, /lib*, and /opt.  I think all the programs/applications worked and the menu structure and all the customizations transferred right, but it was a very rough transfer.  Basically I did "sudo cp -ru" to transfer the majority of it.  The reason I didn't keep it like that and decided to try again was because of a huge number of hardware issues.  NetworkManager was completely dead, there were numerous graphical bugs, sound wasn't working, the GPU wasn't detected (based on Folding@home saying there were zero detected GPUs), and the permissions for /home were really messed up (I fixed that though just by changing the permissions though).  So I know it *can* work, because that transfer was just proof-of-concept.  All I need to do now is know what subdirectories *shouldn't* have been transferred.  My guess is that most of the problems were caused by moving /etc because it contains a lot of hardware-specific configuration files.  So what subdirectories *do* I need to move?  Obviously things like /etc/apt but what else?

So I know it CAN be done, and I've seen people do it, but I don't know which directories need to be moved and which don't.  I know the obvious ones not to move (/dev, /sys, /proc, /run, etc.) but I don't know which *sub*directories shouldn't be moved (like /etc/apt).  I'm also pretty sure /var should be moved but it seems to have a special file that won't transfer.

---

### Post by Stonecold1995 on 2012-06-12
I finally got everything transferred! :p

I copied my /home directory, which allowed me to keep all my custom settings, etc.  Then I installed most of the packages I had by reviewing all the packages I'd installed previously.  I found them all in /var/cache/apt/archives and just installed the .deb packages I needed!  I must have run "sudo apt-get clean" sometime a few months ago because some of the earliest packages I'd installed weren't in there, but those were the ones I always install on new systems (kubuntu-restricted-extras, etc).

---

