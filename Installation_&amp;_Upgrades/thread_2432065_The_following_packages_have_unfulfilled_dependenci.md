---
title: "The following packages have unfulfilled dependencies: libreoffice"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by andreycastro27 on 2019-11-26
I try to update my ubuntu by running


sudo apt upgrade


Reading package list ... Done
Creating dependency tree
Reading status information ... Done
You may want to run "apt --fix-broken install" to correct it.
The following packages have unfulfilled dependencies:
 libreoffice-pdfimport: Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is installed
 libreoffice-style-breeze: Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is installed
 libreoffice-style-galaxy: Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is installed
 libreoffice-style-tango: Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is installed
E: Unfulfilled dependencies. Try "apt --fix-broken install" without packages (or specify a solution).


I execute


sudo apt-get remove --purge libreoffice-style-galaxy


Reading package list ... Done
Creating dependency tree
Reading status information ... Done
You may want to run "apt --fix-broken install" to correct it.
The following packages have unfulfilled dependencies:
 libreoffice-pdfimport: Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 will be installed
 libreoffice-style-breeze: Depends: libreoffice-style-galaxy but will not be installed
                            Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is going to be installed
 libreoffice-style-tango: Depends: libreoffice-style-galaxy but will not be installed
                           Depends: libreoffice-common (= 1: 6.0.7-0ubuntu0.18.04.10) but 1: 6.0.7-0ubuntu0.18.04.9 is going to be installed
E: Unfulfilled dependencies. Try "apt --fix-broken install" without packages (or specify a solution)


help please I could not update ubuntu

---

### Post by uRock on 2019-11-26
Have you run the command it is offering, yet?
```
sudo apt --fix-broken install
```

---

### Post by andreycastro27 on 2019-11-26
Hi have the next error

sudo apt --fix-broken install
Reading package list... Done
Creating Dependencies Tree       
Reading status information... Fact
Correcting dependencies... Ready
The following additional packages will be installed:
  freeoffice-common
The following packages will be updated:
  freeoffice-common
1 updated, 0 new will be installed, 0 to remove and 122 not updated.
4 not completely installed or deleted.
You need to download 0 B/24.7 MB of files.
0 B of additional disk space will be used after this operation.
Do you want to continue? S/n] S


(Reading the database ... 190409 files or directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking freeoffice-common (1:6.0.7-0ubuntu0.18.04.10) on (1:6.0.7-0ubuntu0.18.04.9) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb (--unpack):
 cannot open `/usr/lib/libreoffice/share/gallery/education/PaperClip-Blue.png.dpkg-new': Operation not allowed
rmdir: failed to delete '/var/lib/libreoffice/share/prereg/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/share/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/program/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
Errors were found when processing:
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb

---

### Post by andreycastro27 on 2019-11-26
```
list all libreoffice 

libreoffice/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-avmedia-backend-gstreamer/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-base/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-base-core/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-base-drivers/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-calc/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-canzeley-client/bionic,bionic 0.5.1-1 all
libreoffice-common/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-core/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-dev/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-dev-common/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-dev-doc/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-dmaths/bionic,bionic 4.4.0.0+dfsg1-1 all
libreoffice-draw/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-evolution/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-gnome/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-gtk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-gtk2/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-gtk3/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-help-ca/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-cs/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-da/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-de/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-dz/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-el/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-en-gb/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-en-us/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-help-es/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-help-et/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-eu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-fi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-fr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-gl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-hi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-hu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-it/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-ja/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-km/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-ko/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-nl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-om/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-pl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-pt/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-pt-br/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-ru/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-sk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-sl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-sv/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-tr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-vi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-zh-cn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-help-zh-tw/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-impress/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-java-common/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-kde/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-kde4/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-l10n-af/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-am/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ar/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-as/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ast/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-be/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-bg/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-bn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-br/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-bs/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ca/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-cs/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-cy/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-da/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-de/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-dz/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-el/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-en-gb/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-en-za/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-eo/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-es/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-l10n-et/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-eu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-fa/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-fi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-fr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ga/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-gd/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-gl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-gu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-gug/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-he/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-hi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-hr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-hu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-id/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-in/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-is/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-it/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ja/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ka/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-kk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-km/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-kn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ko/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-lt/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-lv/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-mk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ml/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-mn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-mr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-nb/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ne/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-nl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-nn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-nr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-nso/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-oc/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-om/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-or/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-pa-in/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-pl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-pt/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-pt-br/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ro/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ru/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-rw/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-si/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-sk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-sl/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-sr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ss/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-st/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-sv/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ta/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-te/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-tg/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-th/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-tn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-tr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ts/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ug/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-uk/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-uz/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-ve/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-vi/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-xh/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-za/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-zh-cn/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-zh-tw/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-l10n-zu/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-librelogo/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-lightproof-en/bionic,bionic 0.4.3+1.6-1 all
libreoffice-lightproof-hu/bionic,bionic 1.6.2+1.6-1 all
libreoffice-lightproof-pt-br/bionic,bionic 1:6.0.3-3 all
libreoffice-lightproof-ru-ru/bionic,bionic 0.3.4+1.6-1 all
libreoffice-math/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-mysql-connector/bionic-updates,bionic-security 1.0.2+LibO6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-nlpsolver/bionic-updates,bionic-updates,bionic-security,bionic-security 0.9+LibO6.0.7-0ubuntu0.18.04.10 all
libreoffice-officebean/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-ogltrans/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-pdfimport/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-report-builder/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-report-builder-bin/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-script-provider-bsh/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-script-provider-js/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-script-provider-python/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-sdbc-firebird/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-sdbc-hsqldb/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-sdbc-postgresql/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-style-breeze/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-style-elementary/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-style-galaxy/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-style-hicontrast/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-style-human/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-style-oxygen/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-style-sifr/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-style-tango/bionic-updates,bionic-updates,bionic-security,bionic-security,now 1:6.0.7-0ubuntu0.18.04.10 all [instalado]
libreoffice-subsequentcheckbase/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreoffice-systray/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64
libreoffice-templates/bionic,bionic 0.1.20120814-0ubuntu3 all
libreoffice-texmaths/bionic,bionic 0.43-2 all
libreoffice-voikko/bionic 5.0-3 amd64
libreoffice-wiki-publisher/bionic-updates,bionic-updates,bionic-security,bionic-security 1.2.0+LibO6.0.7-0ubuntu0.18.04.10 all
libreoffice-writer/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64 [actualizable desde: 1:6.0.7-0ubuntu0.18.04.9]
libreoffice-writer2latex/bionic-updates,bionic-updates,bionic-security,bionic-security 1.4-8~18.04 all
libreoffice-writer2xhtml/bionic-updates,bionic-updates,bionic-security,bionic-security 1.4-8~18.04 all
libreoffice-zemberek/bionic,bionic 1.0~rc2-10.4 all
libreofficekit-data/bionic-updates,bionic-updates,bionic-security,bionic-security 1:6.0.7-0ubuntu0.18.04.10 all
libreofficekit-dev/bionic-updates,bionic-security 1:6.0.7-0ubuntu0.18.04.10 amd64

by uninstalling one by one 

error

dpkg: attention: the request to uninstall libreoffice-dev-common will not be taken into account because it is not installed
```

I don't know what else to do. help

---

### Post by wildmanne39 on 2019-11-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bashing-om on 2019-11-26
ndreycastro27; Hello

As we have:
> 
1 updated, 0 new will be installed, 0 to remove and 122 not updated.


122 packages NOT updated !

In small steps,we see what to do

run:
```

sudo apt update

```

Now IF that completes with no errors -
run:
```

sudo apt full-upgrade

```

where I do expect error notices- post that complete output for our inspection. See then what we need next to do.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by andreycastro27 on 2019-11-26
Hi execute sudo apt update

**gn:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease**
**Obj:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                              **
**Obj:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                              **
**Obj:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease               **
**Obj:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease              **
**Obj:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease**
**Leyendo lista de paquetes... Hecho                     **
**Creando árbol de dependencias       **
**Leyendo la información de estado... Hecho**

sudo apt full-upgrade

**Leyendo lista de paquetes... Hecho**
**Creando árbol de dependencias       **
**Leyendo la información de estado... Hecho**
**Tal vez quiera ejecutar «apt --fix-broken install» para corregirlo.**
**Los siguientes paquetes tienen dependencias incumplidas:**
** libreoffice-pdfimport : Depende: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) pero 1:6.0.7-0ubuntu0.18.04.9 está instalado**
** libreoffice-style-breeze : Depende: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) pero 1:6.0.7-0ubuntu0.18.04.9 está instalado**
** libreoffice-style-galaxy : Depende: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) pero 1:6.0.7-0ubuntu0.18.04.9 está instalado**
** libreoffice-style-tango : Depende: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) pero 1:6.0.7-0ubuntu0.18.04.9 está instalado**
**E: Dependencias incumplidas. Intente «apt --fix-broken install» sin paquetes (o especifique una solución).**

---

### Post by Bashing-om on 2019-11-26
andreycastro27; Ouch -

I get the gist of it - but I am not mult-language endowed :(

Let's try this in English, so I can completely understand what the package manager relates:
```

LANG=C;sudo apt update
LANG=C;sudo apt full-upgrade

```

[INDENT]safety is no accident
[/INDENT]

---

### Post by andreycastro27 on 2019-11-26
i execute 

**sudo apt update**


gn:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Obj:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Obj:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Obj:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Obj:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Obj:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package list... Done
Creating Dependencies Tree
Reading status information... Fact


**sudo apt full-upgrade**


Reading package list... Done
Creating Dependencies Tree
Reading status information... Fact
You may want to run "apt --fix-broken install" to fix it.
The following packages have unfulfilled dependencies:
libreoffice-pdfimport : Depends: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) but 1:6.0.7-0ubuntu0.18.04.9 is installed.
libreoffice-style-breeze : Depends: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) but 1:6.0.7-0ubuntu0.18.04.9 is installed.
libreoffice-style-galaxy : Depends: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) but 1:6.0.7-0ubuntu0.18.04.9 is installed.
libreoffice-style-tango : Depends: libreoffice-common (= 1:6.0.7-0ubuntu0.18.04.10) but 1:6.0.7-0ubuntu0.18.04.9 is installed.
E: Unfulfilled dependencies. Try "apt --fix-broken install" without packages (or specify a solution).

---

### Post by Bashing-om on 2019-11-26
andreycastro27; Ho-Kay :)

Try:
```

sudo apt clean
sudo apt purge libreoffice-common
sudo apt update
sudo apt install libreoffice-common

```


[INDENT]see what happens
[/INDENT]

---

### Post by andreycastro27 on 2019-11-26
last command output 

**sudo apt install libreoffice-common**

(Reading the database ... 186047 files or directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking freeoffice-common (1:6.0.7-0ubuntu0.18.04.10) on (1:6.0.7-0ubuntu0.18.04.9) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb (--unpack):
 cannot open `/usr/lib/libreoffice/share/gallery/diagrams/Component-Circle05-Transparent-Red.svg.dpkg-new': Operation not allowed
rmdir: failed to delete '/var/lib/libreoffice/share/prereg/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/share/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/program/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
Errors were found when processing:
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by andreycastro27 on 2019-11-26
Hi, last command output
[B]
 [COLOR=#000000][FONT=&quot]sudo apt install libreoffice-common[/FONT][/COLOR][/B]

dpkg: attention: the file list file of the `libreoffice-style-breeze' package is missing, it will be assumed that the package does not have any file currently installed.
dpkg: Attention: the file list file of the `libreoffice-gnome' package is missing, it will be assumed that the package does not have any file currently installed.
dpkg: Attention: the file list file of the `libreoffice-pdfimport' package is missing, it will be assumed that the package does not have any file currently installed.
(Reading the database ... 186047 files or directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking freeoffice-common (1:6.0.7-0ubuntu0.18.04.10) on (1:6.0.7-0ubuntu0.18.04.9) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb (--unpack):
 cannot open `/usr/lib/libreoffice/share/gallery/diagrams/Component-Circle05-Transparent-Red.svg.dpkg-new': Operation not allowed
rmdir: failed to delete '/var/lib/libreoffice/share/prereg/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/share/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/program/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
Errors were found when processing:
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can't find a solution to this.

---

### Post by wildmanne39 on 2019-11-26
Do you need more instructions on how to use code tags? I am happy to explain better if needed.

---

### Post by Bashing-om on 2019-11-26
andreycastro27; Well
> 
I can't find a solution to this.


While it might be of interest to see the permissions on the file " /usr/lib/libreoffice/share/gallery/diagrams/Component-Circle05-Transparent-Red.svg.dpkg-new"
Perhaps in the interest of expediency just take a sledgehammer to the situation - purge libreoffice entirely and re-install.

Any libreoffice files you need to backup prior ?
Or you want to keep plugging away at getting libreoffice-common to install ?

I am hampered by the fact that I do not have libreoffice installed on this system, as such I can not verify files. I do not mind plugging away at the situation, however.

[INDENT][INDENT]what does it take to keep libreoffice satisfied ?
[/INDENT][/INDENT]

---

### Post by Impavidus on 2019-11-27
> **andreycastro27 said:**
> last command output 

**sudo apt install libreoffice-common**

```
(Reading the database ... 186047 files or directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb ...
Unpacking **[COLOR=red]freeoffice-common[/COLOR]** (1:6.0.7-0ubuntu0.18.04.10) on (1:6.0.7-0ubuntu0.18.04.9) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb (--unpack):
 cannot open `/usr/lib/libreoffice/share/gallery/diagrams/Component-Circle05-Transparent-Red.svg.dpkg-new': Operation not allowed
rmdir: failed to delete '/var/lib/libreoffice/share/prereg/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/share/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice/program/': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
rmdir: failed to delete '/var/lib/libreoffice': File or directory does not exist
Errors were found when processing:
 /var/cache/apt/archives/libreoffice-common_1%3a6.0.7-0ubuntu0.18.04.10_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I'm not really familiar with freeoffice (it seems to be yet another office suite), but it's probably what's causing the problem. I can't find a freeoffice-common package in the official Ubutu repositories.

---

### Post by rsteinmetz70112 on 2019-11-27
I think you may be right - [www.freeoffice.com](www.freeoffice.com) they have a repository [https://shop.softmaker.com/repo/apt](https://shop.softmaker.com/repo/apt) but their installation instructions seem to require you to download a .deb and install it manually using dpkg.

Maybe the OP can tell us if he installed freeoffice.

I'd suggest removing it, fixing the dependencies and reinstall it if you want. I don't know why you would want it over LibreOffice but there may be reasons.

---

