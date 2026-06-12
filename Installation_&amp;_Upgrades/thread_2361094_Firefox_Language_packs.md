---
title: "Firefox Language packs"
date: 2017-05-12
forum: Installation &amp; Upgrades
---

### Post by Liamdale on 2017-05-12
A while back Firefox started to act up, crashing continuously.  Everything I tried was to no avail.  I started using Chromium and have recently installed Vivaldi as backup browser.  I have completely removed Firefox ( or so I thought) but yesterday Ubuntu requested an update for the Firefox language packs.  My version of Firefox used  English and French language packs.  Since the automatic update is still active, I am assuming that the Firefox Language packs are still installed.  How can I uninstall them.  My research on the web has been fruitless to date.

---

### Post by vasa1 on 2017-05-12
What does```
apt list --installed | grep -i firefox
```show?

---

### Post by #&amp;thj^% on 2017-05-12
```
apt search firefox-locale
Sorting... Done
Full Text Search... Done
firefox-locale-af/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Afrikaans language pack for Firefox

firefox-locale-an/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Aragonese language pack for Firefox

firefox-locale-ar/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Arabic language pack for Firefox

firefox-locale-as/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Assamese language pack for Firefox

firefox-locale-ast/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Asturian language pack for Firefox

firefox-locale-az/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Azerbaijani language pack for Firefox

firefox-locale-be/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-bg/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Bulgarian language pack for Firefox

firefox-locale-bn/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Bengali language pack for Firefox

firefox-locale-br/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Breton language pack for Firefox

firefox-locale-bs/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Bosnian language pack for Firefox

firefox-locale-ca/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Catalan; Valencian language pack for Firefox

firefox-locale-cak/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Kaqchikel language pack for Firefox

firefox-locale-cs/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Czech language pack for Firefox

firefox-locale-csb/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-cy/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Welsh language pack for Firefox

firefox-locale-da/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Danish language pack for Firefox

firefox-locale-de/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  German language pack for Firefox

firefox-locale-el/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Greek language pack for Firefox

firefox-locale-en/xenial-updates,xenial-security,now 53.0.2+build1-0ubuntu0.16.04.2 amd64 [installed]
  English language pack for Firefox

firefox-locale-eo/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Esperanto language pack for Firefox

firefox-locale-es/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Spanish; Castilian language pack for Firefox

firefox-locale-et/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Estonian language pack for Firefox

firefox-locale-eu/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Basque language pack for Firefox

firefox-locale-fa/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Persian language pack for Firefox

firefox-locale-fi/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Finnish language pack for Firefox

firefox-locale-fr/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  French language pack for Firefox

firefox-locale-fy/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Western Frisian language pack for Firefox

firefox-locale-ga/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Irish language pack for Firefox

firefox-locale-gd/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Gaelic; Scottish Gaelic language pack for Firefox

firefox-locale-gl/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Galician language pack for Firefox

firefox-locale-gn/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Guarani language pack for Firefox

firefox-locale-gu/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Gujarati language pack for Firefox

firefox-locale-he/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Hebrew language pack for Firefox

firefox-locale-hi/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Hindi language pack for Firefox

firefox-locale-hr/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Croatian language pack for Firefox

firefox-locale-hsb/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Sorbian, Upper language pack for Firefox

firefox-locale-hu/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Hungarian language pack for Firefox

firefox-locale-hy/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Armenian language pack for Firefox

firefox-locale-id/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Indonesian language pack for Firefox

firefox-locale-is/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Icelandic language pack for Firefox

firefox-locale-it/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Italian language pack for Firefox

firefox-locale-ja/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Japanese language pack for Firefox

firefox-locale-ka/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Georgian language pack for Firefox

firefox-locale-kab/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Kabyle language pack for Firefox

firefox-locale-kk/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Kazakh language pack for Firefox

firefox-locale-km/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Central Khmer language pack for Firefox

firefox-locale-kn/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Kannada language pack for Firefox

firefox-locale-ko/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Korean language pack for Firefox

firefox-locale-ku/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-lg/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-lt/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Lithuanian language pack for Firefox

firefox-locale-lv/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Latvian language pack for Firefox

firefox-locale-mai/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Maithili language pack for Firefox

firefox-locale-mk/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Macedonian language pack for Firefox

firefox-locale-ml/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Malayalam language pack for Firefox

firefox-locale-mn/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-mr/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Marathi language pack for Firefox

firefox-locale-ms/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Malay language pack for Firefox

firefox-locale-nb/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Bokmål, Norwegian; Norwegian Bokmål language pack for Firefox

firefox-locale-nl/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Dutch; Flemish language pack for Firefox

firefox-locale-nn/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Norwegian Nynorsk; Nynorsk, Norwegian language pack for Firefox

firefox-locale-nso/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-oc/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-or/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Oriya language pack for Firefox

firefox-locale-pa/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Panjabi; Punjabi language pack for Firefox

firefox-locale-pl/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Polish language pack for Firefox

firefox-locale-pt/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Portuguese language pack for Firefox

firefox-locale-ro/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Romanian language pack for Firefox

firefox-locale-ru/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Russian language pack for Firefox

firefox-locale-si/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Sinhala; Sinhalese language pack for Firefox

firefox-locale-sk/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Slovak language pack for Firefox

firefox-locale-sl/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Slovenian language pack for Firefox

firefox-locale-sq/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Albanian language pack for Firefox

firefox-locale-sr/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Serbian language pack for Firefox

firefox-locale-sv/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Swedish language pack for Firefox

firefox-locale-sw/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language

firefox-locale-ta/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Tamil language pack for Firefox

firefox-locale-te/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Telugu language pack for Firefox

firefox-locale-th/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Thai language pack for Firefox

firefox-locale-tr/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Turkish language pack for Firefox

firefox-locale-uk/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Ukrainian language pack for Firefox

firefox-locale-ur/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Urdu language pack for Firefox

firefox-locale-uz/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Uzbek language pack for Firefox

firefox-locale-vi/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Vietnamese language pack for Firefox

firefox-locale-xh/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Xhosa language pack for Firefox

firefox-locale-zh-hans/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Simplified Chinese language pack for Firefox

firefox-locale-zh-hant/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Traditional Chinese language pack for Firefox

firefox-locale-zu/xenial-updates,xenial-security 53.0.2+build1-0ubuntu0.16.04.2 amd64
  Transitional package for unavailable language


``` 
This can be done via:
```
sudo apt-get remove firefox-locale-*
```
Which removes the whole shebang.
Or by selection IE: 
```
This can be done via:
sudo apt-get remove firefox-locale-firefox-locale-zh-hant
```
Will just remove the Simplified Chinese language pack for Firefox.
Mine will show as follows removing the whole lot of of them:
```
sudo apt-get remove firefox-locale-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'firefox-locale-hsb' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-kab' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-zh-hans' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-zh-hant' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-mai' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-nso' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-af' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-an' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ar' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-as' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-az' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-be' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-bg' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-bn' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-br' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-bs' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ca' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-cs' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-cy' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-da' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-de' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-el' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-en' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-eo' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-es' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-et' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-eu' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-fa' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-fi' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-fr' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-fy' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ga' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-gd' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-gl' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-gn' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-gu' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-he' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-hi' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-hr' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-hu' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-hy' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-id' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-is' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-it' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ja' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ka' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-kk' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-km' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-kn' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ko' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ku' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-lg' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-lt' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-lv' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-mk' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ml' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-mn' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-mr' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ms' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-nb' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-nl' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-nn' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-oc' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-or' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-pa' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-pl' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-pt' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ro' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ru' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-si' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sk' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sl' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sq' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sr' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sv' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-sw' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ta' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-te' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-th' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-tr' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-uk' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ur' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-uz' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-vi' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-xh' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-zu' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-ast' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-cak' for glob 'firefox-locale-*'
Note, selecting 'firefox-locale-csb' for glob 'firefox-locale-*'
Package 'firefox-locale-af' is not installed, so not removed
Package 'firefox-locale-an' is not installed, so not removed
Package 'firefox-locale-ar' is not installed, so not removed
Package 'firefox-locale-as' is not installed, so not removed
Package 'firefox-locale-ast' is not installed, so not removed
Package 'firefox-locale-az' is not installed, so not removed
Package 'firefox-locale-be' is not installed, so not removed
Package 'firefox-locale-bg' is not installed, so not removed
Package 'firefox-locale-bn' is not installed, so not removed
Package 'firefox-locale-br' is not installed, so not removed
Package 'firefox-locale-bs' is not installed, so not removed
Package 'firefox-locale-ca' is not installed, so not removed
Package 'firefox-locale-cak' is not installed, so not removed
Package 'firefox-locale-cs' is not installed, so not removed
Package 'firefox-locale-csb' is not installed, so not removed
Package 'firefox-locale-cy' is not installed, so not removed
Package 'firefox-locale-da' is not installed, so not removed
Package 'firefox-locale-de' is not installed, so not removed
Package 'firefox-locale-el' is not installed, so not removed
Package 'firefox-locale-eo' is not installed, so not removed
Package 'firefox-locale-es' is not installed, so not removed
Package 'firefox-locale-et' is not installed, so not removed
Package 'firefox-locale-eu' is not installed, so not removed
Package 'firefox-locale-fa' is not installed, so not removed
Package 'firefox-locale-fi' is not installed, so not removed
Package 'firefox-locale-fr' is not installed, so not removed
Package 'firefox-locale-fy' is not installed, so not removed
Package 'firefox-locale-ga' is not installed, so not removed
Package 'firefox-locale-gd' is not installed, so not removed
Package 'firefox-locale-gl' is not installed, so not removed
Package 'firefox-locale-gn' is not installed, so not removed
Package 'firefox-locale-gu' is not installed, so not removed
Package 'firefox-locale-he' is not installed, so not removed
Package 'firefox-locale-hi' is not installed, so not removed
Package 'firefox-locale-hr' is not installed, so not removed
Package 'firefox-locale-hsb' is not installed, so not removed
Package 'firefox-locale-hu' is not installed, so not removed
Package 'firefox-locale-hy' is not installed, so not removed
Package 'firefox-locale-id' is not installed, so not removed
Package 'firefox-locale-is' is not installed, so not removed
Package 'firefox-locale-it' is not installed, so not removed
Package 'firefox-locale-ja' is not installed, so not removed
Package 'firefox-locale-ka' is not installed, so not removed
Package 'firefox-locale-kab' is not installed, so not removed
Package 'firefox-locale-kk' is not installed, so not removed
Package 'firefox-locale-km' is not installed, so not removed
Package 'firefox-locale-kn' is not installed, so not removed
Package 'firefox-locale-ko' is not installed, so not removed
Package 'firefox-locale-ku' is not installed, so not removed
Package 'firefox-locale-lg' is not installed, so not removed
Package 'firefox-locale-lt' is not installed, so not removed
Package 'firefox-locale-lv' is not installed, so not removed
Package 'firefox-locale-mai' is not installed, so not removed
Package 'firefox-locale-mk' is not installed, so not removed
Package 'firefox-locale-ml' is not installed, so not removed
Package 'firefox-locale-mn' is not installed, so not removed
Package 'firefox-locale-mr' is not installed, so not removed
Package 'firefox-locale-ms' is not installed, so not removed
Package 'firefox-locale-nb' is not installed, so not removed
Package 'firefox-locale-nl' is not installed, so not removed
Package 'firefox-locale-nn' is not installed, so not removed
Package 'firefox-locale-nso' is not installed, so not removed
Package 'firefox-locale-oc' is not installed, so not removed
Package 'firefox-locale-or' is not installed, so not removed
Package 'firefox-locale-pa' is not installed, so not removed
Package 'firefox-locale-pl' is not installed, so not removed
Package 'firefox-locale-pt' is not installed, so not removed
Package 'firefox-locale-ro' is not installed, so not removed
Package 'firefox-locale-ru' is not installed, so not removed
Package 'firefox-locale-si' is not installed, so not removed
Package 'firefox-locale-sk' is not installed, so not removed
Package 'firefox-locale-sl' is not installed, so not removed
Package 'firefox-locale-sq' is not installed, so not removed
Package 'firefox-locale-sr' is not installed, so not removed
Package 'firefox-locale-sv' is not installed, so not removed
Package 'firefox-locale-sw' is not installed, so not removed
Package 'firefox-locale-ta' is not installed, so not removed
Package 'firefox-locale-te' is not installed, so not removed
Package 'firefox-locale-th' is not installed, so not removed
Package 'firefox-locale-tr' is not installed, so not removed
Package 'firefox-locale-uk' is not installed, so not removed
Package 'firefox-locale-ur' is not installed, so not removed
Package 'firefox-locale-uz' is not installed, so not removed
Package 'firefox-locale-vi' is not installed, so not removed
Package 'firefox-locale-xh' is not installed, so not removed
Package 'firefox-locale-zh-hans' is not installed, so not removed
Package 'firefox-locale-zh-hant' is not installed, so not removed
Package 'firefox-locale-zu' is not installed, so not removed
The following packages will be REMOVED:
  firefox-locale-en
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 1,032 kB disk space will be freed.

```
**Be carefull and look at what's being uninstalled first before saying yes.**

---

### Post by Liamdale on 2017-05-12
The Screen Capture of apt list --installed | grep -i firefox: 

```

firefox-locale-en/now 53.0+build6-0ubuntu0.14.04.1 i386 [installed,upgradable to: 53.0.2+build1-0ubuntu0.14.04.2]
firefox-locale-fr/now 53.0+build6-0ubuntu0.14.04.1 i386 [installed,upgradable to: 53.0.2+build1-0ubuntu0.14.04.2]
unity-scope-firefoxbookmarks/trusty,now 0.1+13.10.20130809.1-0ubuntu1 all [installed,automatic]

```

It seems that the language packs are still present.

1fallen has also answered my thread with the solution: Verification - apt search firefox-locale  (which lists all the languages with an update notation for english and french)
                                                                  Removal -   sudo apt-get remove firefox-locale-* (To remove all) or individually :sudo apt-get remove firefox-locale-firefox-locale-en

```

firefox-locale-el/trusty-updates,trusty-security 53.0.2+build1-0ubuntu0.14.04.2 i386
  Greek language pack for Firefox


firefox-locale-en/trusty-updates,trusty-security 53.0.2+build1-0ubuntu0.14.04.2 i386 [upgradable from: 53.0+build6-0ubuntu0.14.04.1]
  English language pack for Firefox


...


...


firefox-locale-fi/trusty-updates,trusty-security 53.0.2+build1-0ubuntu0.14.04.2 i386
  Finnish language pack for Firefox


firefox-locale-fr/trusty-updates,trusty-security 53.0.2+build1-0ubuntu0.14.04.2 i386 [upgradable from: 53.0+build6-0ubuntu0.14.04.1]
  French language pack for Firefox

```

Thanks to you both for this quick reply.

---

### Post by ajgreeny on 2017-05-12
If you prefer a GUI this is one of the queries quickly answered if you install and use **synaptic**.

It is always the first extra package I add to any of the *ubuntu family that do not use it as default.  
It used to be included as the default package manager in all Ubuntu versions and, as far as I'm aware, is still the default in Debian, on which Ubuntu is based.

---

### Post by Liamdale on 2017-05-12
_Synaptic_ !  yes I have it and I still don't use it efficiently.  I experimented and found the Language packs.  There is an icon with an exclamation mark which probably means that the files are orphans.  I didn't have a chance to remove the language packs yet, i'll try Synaptic.

Thanks for the suggestion.

---

### Post by vasa1 on 2017-05-12
There may also be something like "xul-ext-ubufox" left over.

---

### Post by Liamdale on 2017-05-12
I have used Synaptic with the complete removal option and my problem seems seems solved.  After the Synaptic removal I reran the > [COLOR=#000000][FONT=&quot]apt list --installed | grep -i firefox[/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000] and
the > [/COLOR][/FONT][COLOR=#000000][FONT=&quot]apt search firefox-locale[/FONT][/COLOR][COLOR=#000000][FONT=&quot] and the language packs are nowhere to be found.  Thanks to the three of you for this knowledge.  I will place it I my reference file.[/FONT][/COLOR]

> [COLOR=#000000]There may also be something like "xul-ext-ubufox" left over.[/COLOR]

Yes, I saw that in Synaptic.  What does it mean?

[FONT=arial]I have found information on xul-ext-ubufox (one by 1fallen) which explains the use as:
> Ubuntu-specific configuration defaults and apt support for Firefox.

Adds Ubuntu-specific modifications to Firefox.

Integrates the browser with Ubuntu to:

Enable searching for missing plugins from Ubuntu software catalog
Add the following options to the Help menu:
Get help on-line
Help translating Firefox
Ubuntu Release Notes
Set homepage to Ubuntu Start Page
Display a restart notification after upgrading Firefox
Add ask.com to the search engines.

I assume I can remove this file without consequence[/FONT]

---

### Post by vasa1 on 2017-05-13
> **Liamdale said:**
> ...
I assume I can remove this file without consequence[/FONT]
Yes. If you ever re-install Firefox from the software center, you'll get it back.

---

### Post by ajgreeny on 2017-05-13
I usually remove the xul-ext-ubufox from my systems as it is unnecessary for firefox to run and offers nothing that I need; it is just a Ubuntu extension for firefox.

I can not even remember exactly what it adds to the browser.

---

### Post by howefield on 2017-05-13
> **ajgreeny said:**
> I can not even remember exactly what it adds to the browser.

Just for info, extract from package description.. :)

```
apt-cache show xul-ext-ubufox
 Adds Ubuntu-specific modifications to Firefox.
 .
 Integrates the browser with Ubuntu to:
  * Add a "Report a bug" entry to the Help menu
  * Set homepage to Ubuntu Start Page
  * Display a restart notification after upgrading Firefox
```

---

### Post by vasa1 on 2017-05-13
> **howefield said:**
> Just for info, extract from package description.. :)

```
apt-cache show xul-ext-ubufox
 Adds Ubuntu-specific modifications to Firefox.
 .
 Integrates the browser with Ubuntu to:
  * Add a "Report a bug" entry to the Help menu
  * Set homepage to Ubuntu Start Page
  * Display a restart notification after upgrading Firefox
```Where did you get that?

I don't see so much detail with apt-cache show or apt show on my 16.04 :???:

Edit: I found the same details on [https://launchpad.net/ubuntu/+source/ubufox/3.2-0ubuntu1](https://launchpad.net/ubuntu/+source/ubufox/3.2-0ubuntu1)

---

### Post by howefield on 2017-05-13
> **vasa1 said:**
> Where did you get that?

As per the output.. apt-cache show.

I ran it in 17.04 but also just checked a 16.04 machine with the same results.

---

### Post by vasa1 on 2017-05-13
> **howefield said:**
> As per the output.. apt-cache show.

I ran it in 17.04 but also just checked a 16.04 machine with the same results.
I this is what I get with the same command on 16.04 :```
03:25 PM ~ $ apt-cache show xul-ext-ubufox
Package: xul-ext-ubufox
Priority: optional
Section: web
Installed-Size: 59
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: all
Source: ubufox
Version: 3.2-0ubuntu1
Replaces: ubufox (<< 0.9~rc2-0ubuntu3)
Depends: libglib2.0-0 (>= 2.26)
Breaks: ubufox (<< 0.9~rc2-0ubuntu3)
Filename: pool/main/u/ubufox/xul-ext-ubufox_3.2-0ubuntu1_all.deb
Size: 35170
MD5sum: ab6b7f2bfaffb8c26c8603e4f9eab27a
SHA1: a08dbf7bec0d4836906474ff35b28440bda0b729
SHA256: 1910a2c92bde6ead84901fbc490ab4f7127708e230cde40417471831dbf26043
Description: Ubuntu modifications for Firefox
Description-md5: 088fdbb1da04b8e46a9f4364a53586c7
Homepage: https://launchpad.net/ubufox
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop, ubuntukylin-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-mate-cloudtop

03:32 PM ~ $ 

```I looked at *man apt-cache* for hints but couldn't find any to get a more verbose *Description* output.

One possibility is that you see more detail because you have the package installed? I don't. But merely installing the package doesn't give me more output. Maybe it needs a full install of Firefox from the repos? My Firefox is direct from Mozilla.

---

### Post by Liamdale on 2017-05-13
I removed [COLOR=#000000]xul-ext-ubufox, but further searches with synaptic has revealed three more extensions for Firefox: [/COLOR]xul-ext-websites-integration,  libufe-xidgetter0 and xul-ext-unity.  I assume that these can also be removed?

---

### Post by ajgreeny on 2017-05-13
I get exactly the same output to the apt-cache-show command as vasa1, hence my original query and uncertainty about what it was supposed to add.

@ Liamdale
That is strange as I do not seem to be able to even find those three extensions in the repos for 16.04.
Are you still using 14.04 as your info suggests?

---

### Post by Liamdale on 2017-05-13
Yes, I'm still with Ubuntu 14.04.  After my post I decided to remove the three extensions.  I don't expect any unfortunate consequences.  We will see.

---

