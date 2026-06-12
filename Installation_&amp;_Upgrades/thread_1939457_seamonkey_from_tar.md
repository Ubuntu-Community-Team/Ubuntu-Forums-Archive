---
title: "seamonkey from tar"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-03-11
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

updating seamonkey from a tar archive is easy, and easy to keep up to date.

instead of fumbling around with repo's and ppa's for this i prefer to install precompiled binaries wrapped in a tar archive.  i then symlink my archive to /usr/lib/seamonkey

nab this url with your browser (save the file to $HOME/Downloads)

[http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.9.1/contrib/seamonkey-2.9.1.en-US.linux-x86_64.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.9.1/contrib/seamonkey-2.9.1.en-US.linux-x86_64.tar.bz2)

move the seamonkey package

```

sudo mv $HOME/Downloads/seamonkey* /usr/lib
cd /usr/lib

```

```

sudo su

```

```

tar -xf seamonkey*
sudo ln -s /usr/lib/seamonkey-* /usr/lib/seamonkey
sudo ln -s /usr/lib/seamonkey/seamonkey /usr/bin/seamonkey
sudo rm /usr/lib/seamonkey-*.tar.bz2
sudo ln -s /usr/lib/seamonkey/chrome/icons/default/default.png /usr/share/app-install/icons/seamonkey.png
sudo ln -s /usr/lib/seamonkey/chrome/icons/default/default.png /usr/share/icons/

```

```

sudo su

```

```

cat > /usr/share/applications/seamonkey.desktop << EOF
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Seamonkey
Comment=The Mozilla Suite
Icon=seamonkey
Exec=seamonkey
Categories=Network;GTK;Application;Email;Browser;WebBrowser;News;
StartupNotify=true
Terminal=false
EOF
ln -s /usr/share/applications/seamonkey.desktop /usr/share/app-install/desktop/

```


gotta do moar to get the desktop + link going gotta dig around...

for the apt version these 2 desktops work....
```

sudo su

```

```

cat > /usr/share/app-install/desktop/seamonkey:seamonkey.desktop << EOF
[Desktop Entry]
X-AppInstall-Package=seamonkey
X-AppInstall-Popcon=1866
X-AppInstall-Section=universe

Encoding=UTF-8
Name=SeaMonkey
Comment=Send and receive mail with SeaMonkey
GenericName=Mail Client
Exec=seamonkey %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=seamonkey
Categories=Application;Network;Email;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;x-scheme-handler/mailto;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
StartupWMClass=SeaMonkey
StartupNotify=true

X-Ubuntu-Gettext-Domain=app-install-data
EOF

```

&&

```

cat > /usr/share/applications/seamonkey.desktop << EOF
[Desktop Entry]
Encoding=UTF-8
Name=SeaMonkey
Name[ast]=Veceru de corréu SeaMonkey
Name[ca]=Client de correu SeaMonkey
Name[cs]=Po&#353;tovní klient SeaMonkey
Name[da]=SeaMonkey - e-post/nyhedsgruppe
Name[de]=SeaMonkey-E-Mail und -Nachrichten
Name[es]=Cliente de correo SeaMonkey
Name[fi]=SeaMonkey-sähköposti
Name[fr]=Messagerie SeaMonkey
Name[gl]=Cliente de correo SeaMonkey
Name[he]=SeaMonkey &#1491;&#1493;&#1488;&#1524;&#1500;/&#1495;&#1491;&#1513;&#1493;&#1514;
Name[hr]=SeaMonkey e-po&#353;ta/novosti
Name[hu]=SeaMonkey levelez&#337;kliens
Name[it]=Email SeaMonkey
Name[ko]=SeaMonkey
Name[nl]=SeaMonkey e-mail/nieuws
Name[pl]=Klient poczty SeaMonkey
Name[pt_BR]=Cliente de E-mail SeaMonkey
Name[ru]=&#1055;&#1086;&#1095;&#1090;&#1086;&#1074;&#1099;&#1081; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090; SeaMonkey
Name[sk]=SeaMonkey - po&#353;tový klient a novin
Name[sv]=E-postklienten SeaMonkey
Name[ug]=SeaMonkey &#1574;&#1744;&#1604;&#1582;&#1749;&#1578;/&#1582;&#1749;&#1739;&#1749;&#1585;
Name[zh_CN]=SeaMonkey &#37038;&#20214;/&#26032;&#38395;
Name[zh_TW]=SeaMonkey &#37109;&#20214;
Comment=Send and receive mail with SeaMonkey
Comment[ast]=Lleer y escribir corréu electrónicu
Comment[ca]=Llegiu i escriviu correu
Comment[cs]=&#268;tení a psaní po&#353;ty
Comment[da]=Skriv/læs e-post/nyhedsgruppe med SeaMonkey
Comment[de]=E-Mails und Nachrichten mit SeaMonkey lesen und schreiben
Comment[es]=Lea y escriba correos y noticias con SeaMonkey
Comment[fi]=Lue ja kirjoita sähköposteja
Comment[fr]=Lire et écrire des courriels
Comment[gl]=Lea e escriba correo electrónico
Comment[he]=&#1511;&#1512;&#1497;&#1488;&#1492;/&#1499;&#1514;&#1497;&#1489;&#1492; &#1513;&#1500; &#1491;&#1493;&#1488;&#1524;&#1500;/&#1495;&#1491;&#1513;&#1493;&#1514; &#1489;&#1488;&#1502;&#1510;&#1506;&#1493;&#1514; SeaMonkey
Comment[hr]=&#268;itajte/&#353;aljite e-po&#353;tu s SeaMonkey
Comment[hu]=Levelek írása és olvasása a SeaMonkeydel
Comment[it]=Per leggere e scrivere email
Comment[ja]=&#12513;&#12540;&#12523;&#12398;&#35501;&#12415;&#26360;&#12365;
Comment[ko]=SeaMonkey &#47700;&#51068;/&#45684;&#49828; &#51069;&#44592; &#48143; &#50416;&#44592; &#53364;&#46972;&#51060;&#50616;&#53944;
Comment[nl]=E-mail/nieuws lezen en schrijven met SeaMonkey
Comment[pl]=Czytanie i wysy&#322;anie e-maili
Comment[pt_BR]=Ler e escrever suas mensagens
Comment[ru]=&#1063;&#1080;&#1090;&#1072;&#1081;&#1090;&#1077; &#1080; &#1087;&#1080;&#1096;&#1080;&#1090;&#1077; &#1087;&#1080;&#1089;&#1100;&#1084;&#1072;
Comment[sk]=&#268;ítajte a pí&#353;te po&#353;tu, &#269;ítajte novinky pomocou programu SeaMonkey
Comment[sv]=Läs och skriv e-post
Comment[ug]=&#1574;&#1744;&#1604;&#1582;&#1749;&#1578; &#1739;&#1749; &#1582;&#1749;&#1739;&#1749;&#1585;&#1604;&#1749;&#1585;&#1606;&#1609; SeaMonkey &#1583;&#1575; &#1603;&#1734;&#1585;&#1736;&#1588; &#1739;&#1749; &#1610;&#1744;&#1586;&#1609;&#1588;
Comment[zh_CN]=&#38405;&#35835;&#37038;&#20214;&#25110;&#26032;&#38395;
Comment[zh_TW]=&#20197; SeaMonkey &#35712;&#23531;&#37109;&#20214;&#25110;&#26032;&#32862;
GenericName=Mail Client
Exec=seamonkey %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=seamonkey
Categories=Application;Network;Email;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;x-scheme-handler/mailto;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
StartupWMClass=SeaMonkey
StartupNotify=true
GenericName[ast]=Client de correu
GenericName[ca]=Client de correu
GenericName[da]=E-postklient
GenericName[de]=E-Mail-Anwendung
GenericName[es]=Cliente de correo
GenericName[fi]=Sähköpostiohjelma
GenericName[fr]=Client de messagerie
GenericName[gl]=Cliente de correo electrónico
GenericName[he]=&#1500;&#1511;&#1493;&#1495; &#1491;&#1493;&#1488;&#1524;&#1500;
GenericName[hr]=Klijent e-po&#353;te
GenericName[hu]=Levelez&#337;kliens
GenericName[it]=Client email
GenericName[ko]=&#47700;&#51068; &#53364;&#46972;&#51060;&#50616;&#53944;
GenericName[nl]=E-mailprogramma
GenericName[ru]=&#1055;&#1086;&#1095;&#1090;&#1086;&#1074;&#1099;&#1081; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090;
GenericName[sk]=Po&#353;tový klie
GenericName[ug]=&#1574;&#1744;&#1604;&#1582;&#1749;&#1578; &#1583;&#1744;&#1578;&#1575;&#1604;&#1609;
GenericName[zh_CN]=&#37038;&#20214;&#26032;&#38395;&#23458;&#25143;&#31471;
GenericName[zh_TW]=&#37109;&#20214;&#29992;&#25142;&#31471;
EOF

```

---

### Post by missmoondog on 2012-03-26
talk about fumbling?! my fingers are in knots already just reading all that. even copying & pasting it into a terminal looks like work. :(

---

### Post by boblizar on 2012-03-29
once you do this, you can easily upgrade....

just run 

```

sudo rm -rf /usr/lib/seamonkey*

```

to purge the old install

drop the new seamonkey tar into /usr/lib && run

```

sudo tar -xf seamonkey*
sudo ln -s /usr/lib/seamonkey-* /usr/lib/seamonkey
sudo rm /usr/lib/seamonkey-*.tar.bz2

```

done

download a new nightly every night and run 4 commands to install very latest, keep your flash, keep your java, keep your icons,

---

### Post by BBQdave on 2012-03-29
How 'bout...

download seamonkey
use archive manager to extract
*(in your favorite CLI)*
$ sudo mv /home/me/Downloads/seamonkey /opt/seamonkey


To use seamonkey:

*(in your favorite CLI)*
/opt/seamonkey/seamonkey
[I]hit enter
[/I]
You can configure seamonkey (from within the application preferences) to automatically update or you can manually update if you like.

Easy way to install current seamonkey and keep up to date ;)

---

### Post by ottosykora on 2012-03-30
@boblizar

it is really difficult to understand what it is all about here and why someone should do all that just to get something like:
sudo apt-get install seamonkey


or simply click in software center on seamonkey to install it.

---

### Post by boblizar on 2012-05-02
its using generic code for a generic install as if i had built my os from scratch.  why do i do it?  to easily keep up with versions.  i dont have to wait for the repository to update a seamonkey package when the browser starts giving messages of new versions.

to move a version up simply...

```

sudo rm -rf /usr/lib/seamonkey-*
sudo mv $HOME/Downloads/seamonkey* /usr/lib
sudo tar -xf /usr/lib/seamonkey-*

```

that being said, the repo versions are generally absurdly stale compared to mozillas websites tarballs....

2.4.1 is repo version, and today is 2.9.1 for latest.

---

### Post by zon14 on 2012-05-29
This is looking more relevant now.  I've been trying to reinstall Seamonkey ever since upgrading to 12.04 and even though an entry for it shows up in the software center, it says there's no package for it.  This is strange since obviously new versions are coming out for it, so it's far from abandonware and I've been unable to find an alternate repository.

---

### Post by zon14 on 2012-06-05
Oh, and one additional caveat, which I just ran into.  Check your dependencies.  I just installed it again using this method on a second laptop, but as it turns out the second one lacked some libraries the first one had already installed.  Seems Seamonkey wants a few 32bit libraries to run, and since this laptop's a 64bit machine, when I did a new install of 12.04, it didn't automatically include those libraries.

After I did that, it booted right up.  So yay.

---

