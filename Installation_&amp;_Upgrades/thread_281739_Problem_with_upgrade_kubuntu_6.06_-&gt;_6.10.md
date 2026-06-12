---
title: "Problem with upgrade kubuntu 6.06 -&gt; 6.10"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by grzes on 2006-10-21
Hi :)

My english isn't good so please look at that:

```
grzes@grzes:~$ sudo apt-get dist-upgrade
Password:
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Nale&#380;y uruchomi&#263; `apt-get -f install', aby je naprawi&#263;.
Nast&#281;puj&#261;ce pakiety maj&#261; niespe&#322;nione zale&#380;no&#347;ci:
libc6-dev: Wymaga: libc6 (= 2.4-1ubuntu12) ale 2.3.6-0ubuntu20 jest zainstalowany
xutils: Wymaga: xutils-dev ale nie jest zainstalowany
E: Niespe&#322;nione zale&#380;no&#347;ci. Spróbuj u&#380;y&#263; -f.
```

```
grzes@grzes:~$ sudo apt-get -f install
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Naprawianie zale&#380;no&#347;ci... Gotowe
Zostan&#261; zainstalowane nast&#281;puj&#261;ce dodatkowe pakiety:
gcc-4.1-base libc6 libc6-i686 libcupsys2 libcupsys2-dev libfreetype6 libfreetype6-dev libgcc1 libgcrypt11 libgcrypt11-dev libgnutls-dev
libgnutls13 libgpg-error-dev libgpg-error0 liblzo-dev libopencdk8 libopencdk8-dev libpopt-dev libpopt0 libqt3-headers libqt3-mt
libqt3-mt-dev libstdc++6 libtasn1-3 libtasn1-3-dev libxft-dev libxft2 qt3-dev-tools x11-common xfonts-encodings xkb-data xutils-dev
Sugerowane pakiety:
glibc-doc cupsys-common rng-tools libgcrypt11-doc gnutls-doc gnutls-bin libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libqt3-i18n qt3-doc
Polecane pakiety:
libgl1-mesa-glx libgl1 libqt3-compat-headers libtasn1-3-bin
Nast&#281;puj&#261;ce pakiety zostan&#261; USUNI&#280;TE:
x-window-system-core xserver-xorg
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
gcc-4.1-base libcupsys2-dev libgcrypt11-dev libgnutls-dev libgnutls13 libgpg-error-dev liblzo-dev libopencdk8-dev libpopt-dev libtasn1-3
libtasn1-3-dev xfonts-encodings xkb-data xutils-dev
Nast&#281;puj&#261;ce pakiety zostan&#261; zaktualizowane:
libc6 libc6-i686 libcupsys2 libfreetype6 libfreetype6-dev libgcc1 libgcrypt11 libgpg-error0 libopencdk8 libpopt0 libqt3-headers libqt3-mt
libqt3-mt-dev libstdc++6 libxft-dev libxft2 qt3-dev-tools x11-common
18 aktualizowanych, 14 nowo instalowanych, 2 usuwanych i 1000 nieaktualizowanych.
4 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0B/15,1MB archiwów.
Po rozpakowaniu zostanie dodatkowo u&#380;yte 10,4MB miejsca na dysku.
Czy chcesz kontynuowa&#263; [T/n]? T
Rozpakowywanie szablonów dla pakietów: 100%
Prekonfiguracja pakietów ...
(Odczytywanie bazy danych ... 116412 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia libc6 2.3.6-0ubuntu20 (wykorzystuj&#261;c .../libc6_2.4-1ubuntu12_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego libc6 ...
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: ostrze&#380;enie - poprzedni skrypt post-removal zwróci&#322; kod b&#322;&#281;du 127
dpkg - próba wywo&#322;ania skryptu z nowego pakietu ...
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/libc6_2.4-1ubuntu12_i386.deb (--unpack):
podproces new post-removal script zwróci&#322; kod b&#322;&#281;du 127
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dpkg: b&#322;&#261;d podczas czyszczenia &#347;rodowiska:
podproces pre-installation script zwróci&#322; kod b&#322;&#281;du 127
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
/var/cache/apt/archives/libc6_2.4-1ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can eanyone help? Please :) 

*- Grzes*

---

### Post by gustolove on 2006-10-21
There are different language forums. Most likely there will be one with the language that you are best with.


[http://www.ubuntu.com/community/forums](http://www.ubuntu.com/community/forums)

---

