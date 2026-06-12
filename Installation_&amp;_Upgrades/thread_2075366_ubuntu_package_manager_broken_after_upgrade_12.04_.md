---
title: "ubuntu package manager broken after upgrade 12.04 to 12.10"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by glaudiston on 2012-10-23
Today I accept the upgrade suggested by the update manager, then everything seems to be ok, a rebook was required and after rebook the package manager show up a error saying that a parcial instalation occurred and to run apt-get via command line.

then
```
root@ton-ubuntu:/home/glaudiston# apt-get install -f
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Corrigindo dependências... Pronto
Os seguintes pacotes foram automaticamente instalados e não são mais necessários:
  ca-certificates-java compiz-plugins-main-default fonts-droid
  gnome-exe-thumbnailer icedtea-netx-common libatk-wrapper-java
  libatk-wrapper-java-jni libattica0.3 libboost-serialization1.46.1
  libcapi20-3 libdconf-dbus-1-0 libdconf-qt0 libebackend-1.2-1 libecal-1.2-10
  libedata-cal-1.2-13 libgnomekbd7 libgweather-3-0 libllvm3.0
  libmusicbrainz3-6 libqtdee2 libqtgconf1 libyajl1 ttf-droid ttf-umefont
  tzdata-java wine-gecko1.4 winetricks
Use 'apt-get autoremove' para removê-los.
Os pacotes extra a seguir serão instalados:
  account-plugin-aim account-plugin-facebook account-plugin-google
  account-plugin-icons account-plugin-jabber account-plugin-salut
  account-plugin-windows-live account-plugin-yahoo empathy empathy-common eog
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins folks-common gcr
  gir1.2-gnomebluetooth-1.0 gir1.2-rb-3.0 gnome-contacts
  gnome-control-center-signon gnome-keyring gnome-online-accounts
  gnome-screensaver indicator-datetime libaccount-plugin-1.0-0
  libaccounts-glib0 libaccounts-qt1 libc-bin libc6 libcamel-1.2-40
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libebackend-1.2-5 libebook-1.2-14 libecal-1.2-15
  libedata-book-1.2-15 libedata-cal-1.2-18 libedataserver-1.2-17
  libedataserverui-3.0-4 libevolution libfolks-eds25 libfolks25 libgck-1-0
  libgcr-3-1 libgoa-1.0-0 libgoa-1.0-common libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgweather-3-1 libice6
  libimobiledevice3 libmission-control-plugins0 libmono-2.0-1 libmono-2.0-dev
  libmono-accessibility2.0-cil libmono-accessibility4.0-cil libmono-c5-1.1-cil
  libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-cecil-private-cil
  libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-corlib4.0-cil libmono-cscompmgd8.0-cil libmono-csharp4.0-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft2.0-cil libmono-debugger-soft4.0-cil
  libmono-http4.0-cil libmono-i18n-cjk4.0-cil libmono-i18n-mideast4.0-cil
  libmono-i18n-other4.0-cil libmono-i18n-rare4.0-cil libmono-i18n-west2.0-cil
  libmono-i18n-west4.0-cil libmono-i18n2.0-cil libmono-i18n4.0-all
  libmono-ldap2.0-cil libmono-ldap4.0-cil libmono-management2.0-cil
  libmono-management4.0-cil libmono-messaging-rabbitmq2.0-cil
  libmono-messaging-rabbitmq4.0-cil libmono-messaging4.0-cil
  libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build2.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-microsoft8.0-cil
  libmono-npgsql2.0-cil libmono-npgsql4.0-cil libmono-opensystem-c4.0-cil
  libmono-oracle2.0-cil libmono-oracle4.0-cil libmono-peapi2.0-cil
  libmono-peapi4.0-cil libmono-posix4.0-cil libmono-rabbitmq2.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng2.0-cil libmono-relaxng4.0-cil
  libmono-security4.0-cil libmono-sharpzip2.6-cil libmono-sharpzip4.84-cil
  libmono-simd2.0-cil libmono-simd4.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil libmono-system-ldap2.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net4.0-cil
  libmono-system-numerics4.0-cil libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime2.0-cil
  libmono-system-runtime4.0-cil libmono-system-security4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0-cil
  libmono-system-serviceprocess4.0-cil libmono-system-transactions4.0-cil
  libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-mvc1.0-cil
  libmono-system-web-mvc2.0-cil libmono-system-web-routing4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0-cil
  libmono-system-windows-forms4.0-cil libmono-system-xaml4.0-cil
  libmono-system-xml-linq4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmono-tasklets2.0-cil libmono-tasklets4.0-cil
  libmono-web4.0-cil libmono-webbrowser2.0-cil libmono-webbrowser4.0-cil
  libmono-webmatrix-data4.0-cil libmono-windowsbase3.0-cil
  libmono-windowsbase4.0-cil libmono-winforms2.0-cil libmono2.0-cil
  libmusicbrainz5-0 libqjson0 librhythmbox-core6 libsignon-extension1
  libsignon-glib1 libsignon-plugins-common1 libsignon-qt1 libsyncdaemon-1.0-1
  libunity-2d-private0 libusbmuxd2 libxmu6 libytnef0 mcp-account-manager-uoa
  mono-dmcs mono-xbuild monodevelop nautilus-data python-ubuntuone-client
  python-ubuntuone-storageprotocol seahorse signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signond
  telepathy-mission-control-5 thunderbird thunderbird-globalmenu
  thunderbird-gnome-support thunderbird-locale-pt ubuntuone-client
  ubuntuone-client-gnome unity-2d-panel unity-2d-shell unity-2d-spread
Pacotes sugeridos:
  mcp-account-manager-goa evolution-exchange evolution-dbg
  evolution-plugins-experimental evolution-data-server-dbg glibc-doc
  account-plugin-gadugadu account-plugin-groupwise account-plugin-icq
  account-plugin-irc account-plugin-mxit account-plugin-myspace
  account-plugin-sametime account-plugin-sip account-plugin-yahoojp
  account-plugin-zephyr exuberant-ctags mono-vbnc mono-xsp mono-xsp4
  monodevelop-database monodevelop-debugger-gdb monodevelop-nunit
  monodevelop-versioncontrol monodoc-browser latex-xft-fonts
  ubuntuone-client-proxy
Pacotes recomendados:
  libgluezilla gir1.2-syncmenu-0.1
Os pacotes a seguir serão REMOVIDOS:
  ia32-libs libebook-1.2-12 libedata-book-1.2-11 libedataserverui-3.0-1
  libgnome-desktop-3-2 libunity-core-5.0-5 nspluginwrapper q4wine wine wine1.3
  wine1.4 wine1.4-amd64 wine1.4-common
Os NOVOS pacotes a seguir serão instalados:
  account-plugin-aim account-plugin-facebook account-plugin-google
  account-plugin-icons account-plugin-jabber account-plugin-salut
  account-plugin-windows-live account-plugin-yahoo gcr gnome-contacts
  gnome-control-center-signon libaccount-plugin-1.0-0 libaccounts-glib0
  libaccounts-qt1 libcamel-1.2-40 libclutter-1.0-0 libclutter-1.0-common
  libclutter-gst-1.0-0 libclutter-gtk-1.0-0 libebackend-1.2-5 libebook-1.2-14
  libecal-1.2-15 libedata-book-1.2-15 libedata-cal-1.2-18
  libedataserver-1.2-17 libedataserverui-3.0-4 libgweather-3-1
  libimobiledevice3 libmusicbrainz5-0 libqjson0 librhythmbox-core6
  libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt1
  libusbmuxd2 libytnef0 mcp-account-manager-uoa signon-keyring-extension
  signon-plugin-oauth2 signon-plugin-password signon-ui signond
Os pacotes a seguir serão atualizados:
  empathy empathy-common eog evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins folks-common
  gir1.2-gnomebluetooth-1.0 gir1.2-rb-3.0 gnome-keyring gnome-online-accounts
  gnome-screensaver indicator-datetime libc-bin libc6 libevolution
  libfolks-eds25 libfolks25 libgck-1-0 libgcr-3-1 libgoa-1.0-0
  libgoa-1.0-common libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libice6 libmission-control-plugins0 libmono-2.0-1
  libmono-2.0-dev libmono-accessibility2.0-cil libmono-accessibility4.0-cil
  libmono-c5-1.1-cil libmono-cairo2.0-cil libmono-cairo4.0-cil
  libmono-cecil-private-cil libmono-codecontracts4.0-cil
  libmono-compilerservices-symbolwriter4.0-cil libmono-corlib4.0-cil
  libmono-cscompmgd8.0-cil libmono-csharp4.0-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft2.0-cil libmono-debugger-soft4.0-cil
  libmono-http4.0-cil libmono-i18n-cjk4.0-cil libmono-i18n-mideast4.0-cil
  libmono-i18n-other4.0-cil libmono-i18n-rare4.0-cil libmono-i18n-west2.0-cil
  libmono-i18n-west4.0-cil libmono-i18n2.0-cil libmono-i18n4.0-all
  libmono-ldap2.0-cil libmono-ldap4.0-cil libmono-management2.0-cil
  libmono-management4.0-cil libmono-messaging-rabbitmq2.0-cil
  libmono-messaging-rabbitmq4.0-cil libmono-messaging4.0-cil
  libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build2.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-microsoft8.0-cil
  libmono-npgsql2.0-cil libmono-npgsql4.0-cil libmono-opensystem-c4.0-cil
  libmono-oracle2.0-cil libmono-oracle4.0-cil libmono-peapi2.0-cil
  libmono-peapi4.0-cil libmono-posix4.0-cil libmono-rabbitmq2.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng2.0-cil libmono-relaxng4.0-cil
  libmono-security4.0-cil libmono-sharpzip2.6-cil libmono-sharpzip4.84-cil
  libmono-simd2.0-cil libmono-simd4.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil libmono-system-ldap2.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net4.0-cil
  libmono-system-numerics4.0-cil libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime2.0-cil
  libmono-system-runtime4.0-cil libmono-system-security4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0-cil
  libmono-system-serviceprocess4.0-cil libmono-system-transactions4.0-cil
  libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-mvc1.0-cil
  libmono-system-web-mvc2.0-cil libmono-system-web-routing4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0-cil
  libmono-system-windows-forms4.0-cil libmono-system-xaml4.0-cil
  libmono-system-xml-linq4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmono-tasklets2.0-cil libmono-tasklets4.0-cil
  libmono-web4.0-cil libmono-webbrowser2.0-cil libmono-webbrowser4.0-cil
  libmono-webmatrix-data4.0-cil libmono-windowsbase3.0-cil
  libmono-windowsbase4.0-cil libmono-winforms2.0-cil libmono2.0-cil
  libsyncdaemon-1.0-1 libunity-2d-private0 libxmu6 mono-dmcs mono-xbuild
  monodevelop nautilus-data python-ubuntuone-client
  python-ubuntuone-storageprotocol seahorse telepathy-mission-control-5
  thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-pt ubuntuone-client ubuntuone-client-gnome unity-2d-panel
  unity-2d-shell unity-2d-spread
173 pacotes atualizados, 43 pacotes novos instalados, 13 a serem removidos e 1434 não atualizados.
367 pacotes não totalmente instalados ou removidos.
É preciso baixar 0 B/70,5 MB de arquivos.
Depois desta operação, 99,8 MB de espaço em disco serão liberados.
Você quer continuar [S/n]? S
Extraíndo templates de pacotes : 100%
Pré-configurando pacotes ...
dpkg: erro: analisando arquivo '/var/lib/dpkg/status' próximo à linha 23742 pacote 'libfribidi0':
 mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@ton-ubuntu:/home/glaudiston#
```
```
# dpkg -i
dpkg: erro: analisando arquivo '/var/lib/dpkg/status' próximo à linha 23742 pacote 'libfribidi0':
 mixed non-coinstallable and coinstallable package instances present

```

I don't understand exactly what happen with libfribidi0... can be a solution download and install it manually ?

Anyone can help me fix it ?

Att
Ton

---

### Post by glaudiston on 2012-10-23
Ok, no one tried to help me, so I got the risk.

I edit the '/var/lib/dpkg/status' removing the paragraph above the line 23742, that refers to 'libfribidi0'.
```
vim /var/lib/dpkg/status +23742
```
and remove the block
```
Package: libfribidi0 
Status: deinstall ok config-files 
Priority: optional 
Section: libs 
Installed-Size: 192 
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com> 
Architecture: i386 
Source: fribidi 
Version: 0.19.2-1 
Config-Version: 0.19.2-1 
Depends: libc6 (>= 2.4) 
Description: Free Implementation of the Unicode BiDi algorithm 
 FriBiDi is a BiDi algorithm implementation for Hebrew and/or Arabic 
 languages. 
 This package contains the shared libraries. 
Original-Maintainer: Debian Hebrew Packaging Team <debian-hebrew-package@lists.alioth.debian.org> 
Homepage: http://www.fribidi.org/ 
```

So I tried;
```
#dpkg -P
dpkg: erro: analisando arquivo '/var/lib/dpkg/status' próximo à linha 25330 pacote 'libmms0':
 mixed non-coinstallable and coinstallable package instances present
```
The error change a litle is not more libfribidi0, now its '**libmms0**'

I do the same thing(to actual position reported):
```
vim /var/lib/dpkg/status +25330
```
and remove the block```
Package: libmms0
Status: deinstall ok config-files
Priority: optional
Section: libs
Installed-Size: 124
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libmms
Version: 0.6.2-2
Config-Version: 0.6.2-2
Depends: libc6 (>= 2.7), libglib2.0-0 (>= 2.12.0)
Description: MMS stream protocol library - shared library
 LibMMS is a common library for parsing mms:// and mmsh:// type network
 streams.  These are commonly used to stream Windows Media Video content
 over the web.  LibMMS itself is only for receiving MMS stream, it
 doesn't handle sending at all.

```

After that, The dpkg changes his behavior:
```
dpkg -P
dpkg: erro: --purge precisa de pelo menos um nome de pacote como argumento

Escreva dpkg --help para ajuda sobre instalar e desinstalar pacotes [*];
Utilize `dselect' ou `aptitude' para gestão de pacotes amigável;
Escreva dpkg -Dhelp para uma lista de valores de flags de debug do dpkg;
Escreva dpkg --force-help para uma lista de opções para forçar operações;
Escreva dpkg-deb --help para ajuda sobre manipular ficheiros *.deb;

Opções marcadas com [*] produzem muita saída de texto - utilize pipes com `less' ou `more' !

```

Hopeful, then I do a 'apt-get upgrade', and the process run some packages, but the last result was(last lines):
```
dpkg: error processing libc6:amd64 (--configure):
 package libc6:amd64 2.15-0ubuntu20 cannot be configured because libc6:i386 is at a different version (2.15-0ubuntu10.3)
Erros foram encontrados durante o processamento de:
 libc6:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Seems that the libc6 fail to install, this look bad.

I tried 'apt-get upgrade' again... various packages has been removed... to much... I'm fear what is happening... Its running now, maybe the system halt in some minutes, if do not halt... I will edit this post.

---

### Post by glaudiston on 2012-10-23
so, after one more 'apt-get update', 'apt-get upgrade -f', 'apt-get dist-upgrade' and a reboot, all seems to be fine.

problem solved! ;-)

---

### Post by robcar on 2012-12-29
> **glaudiston said:**
> so, after one more 'apt-get update', 'apt-get upgrade -f', 'apt-get dist-upgrade' and a reboot, all seems to be fine.

problem solved! ;-)

Thank you very much for sharing that above: I followed the same steps in order to get rid of a problem with 'icaclient' package and I eventually managed to have a functionally updatable system again.

Thank you again
--
rob

---

### Post by rocketero on 2013-02-14
@glaudiston, thanks man, you made my day, I just saw this thread and was able to fix a similar problem with dpkg. Much appreciated!

---

