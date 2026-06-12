---
title: "Updating Problem"
date: 2023-02-06
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2023-02-06
Does anyone have any idea how to fix a problem I am having after trying to install Libreoffice-common.  I've tried uninstalling it in terminal and on Ubuntu Software.  Here is what terminal tells me -  ```
Reading state information... DoneYou might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
none@none-OptiPlex-3020:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
none@none-OptiPlex-3020:~$ sudo apt --fix-broken install libreoffice-common
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi libappstream-glib8
  libcdr-0.1-1 libcolamd2 libflashrom1 libfreehand-0.1-1 libftdi1-2 libfuse2
  libmspub-0.1-1 libpagemaker-0.0-0 libsuitesparseconfig5 libva-wayland2
  libvisio-0.1-1 lp-solve
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 84 not upgraded.
8 not fully installed or removed.
Need to get 0 B/23.4 MB of archives.
After this operation, 59.1 MB of additional disk space will be used.
Setting up libapt-pkg6.0:amd64 (2.4.9) ...
(Reading database ... 195077 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a7.3.7-0ubuntu0.22.04.1_all.deb ..
.
Unpacking libreoffice-common (1:7.3.7-0ubuntu0.22.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a7.
3.7-0ubuntu0.22.04.1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice4.1.
13-freedesktop-menus 4.1.13-9811
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or di
rectory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directo
ry
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a7.3.7-0ubuntu0.22.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Impavidus on 2023-02-07
You have openoffice4.1 installed. As LibreOffice is a fork of OpenOffice, they have some common filenames, so they can't be installed on the same system. First remove openoffice4.1.

---

### Post by ActionParsnip on 2023-02-07
What is the output of:
```

dpkg -l | grep -i office | grep ^ii

```

---

### Post by shane_faulkinbury2 on 2023-02-13
I've tried everything guys and still having the problem.  Here is what I get after trying everything and running command ```
[COLOR=#000000][FONT=&quot]dpkg -l | grep -i office | grep ^ii[/FONT][/COLOR]
```



```
dpkg -l | grep -i office | grep ^iiii  mythes-en-us                               1:7.2.0-2                               all          English (USA) Thesaurus for LibreOffice
ii  openoffice4.1.13-freedesktop-menus         4.1.13-9811                             all          OpenOffice desktop integration



```

---

### Post by shane_faulkinbury2 on 2023-02-13
I did a ```
apt list --installed
``` and still see ```
openoffice4.1.13-freedesktop-menus
``` installed locally.

---

### Post by ActionParsnip on 2023-02-13
Remove it with:
```

sudo apt --purge remove openoffice4.1.13-freedesktop-menus libreoffice*
sudo apt clean

```
You can then install the office suite you like. Should be much cleaner

---

### Post by shane_faulkinbury2 on 2023-02-14
```
sudo apt --purge remove openoffice4.1.13-freedesktop-menus libreoffice*&lt;div&gt;[sudo] password for none:&amp;nbsp;&lt;/div&gt;&lt;div&gt;Reading package lists... Done&lt;/div&gt;&lt;div&gt;Building dependency tree... Done&lt;/div&gt;&lt;div&gt;Reading state information... Done&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-l10n-en-gb' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-l10n-en-us' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-l10n-en-za' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-style-andromeda' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-ast' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-dmaths' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-calc' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-sdbc-postgresql' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-impress-nogui' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-gug' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-lightproof-en' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-lightproof-hu' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-calc-nogui' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-l10n-4.3' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-l10n-4.4' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-gnome' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-base-core' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-pdfimport' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-kmr' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-filter-mobiledev' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-nso' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-zemberek' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-core' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-pt-br' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-szl' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice.org' for glob  'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-cy' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-da' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-de' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-dz' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-el' for glob 'libreoffice*'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-grammarcheck-eo' for glob   removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-si' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-sk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-sl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-sr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-sr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-ss' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ss' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-st' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-st' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-sv' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-szl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-szl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-ta' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ta' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-te' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-te' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-tg' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-tg' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-th' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-th' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-tn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-tn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-tr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-ts' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ts' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-ug' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ug' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-uk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-uk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-uz' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-uz' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-ve' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ve' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-vi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-xh' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-xh' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-zh-cn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-zh-tw' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-grammarcheck-zu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-zu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice.org' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice.org-calc' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice.org-writer' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-core-nogui' instead of 'libreoffice-bundled'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-us'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-hyphenation-tr'&lt;/div&gt;&lt;div&gt;Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-spellcheck-tr'&lt;/div&gt;&lt;div&gt;Package 'libreoffice-voikko' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-canzeley-client' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-dmaths' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-lightproof-en' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-lightproof-hu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-lightproof-pt-br' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-lightproof-ru-ru' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-numbertext' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-parlatype' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-templates' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-texmaths' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-writer2latex' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-writer2xhtml' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-zemberek' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-dev' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-dev-common' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-dev-doc' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ca' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-cs' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-da' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-de' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-dz' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-el' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-en-gb' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-es' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-et' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-eu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-fi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-fr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-gl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-hi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-hu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-id' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-it' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ja' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-km' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ko' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-nl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-om' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-pl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-pt' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-pt-br' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-ru' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-sk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-sl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-sv' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-tr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-vi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-zh-cn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-help-zh-tw' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-java-common' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-af' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-am' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ar' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-as' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ast' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-be' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-bg' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-bn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-br' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-bs' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ca' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-cs' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-cy' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-da' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-de' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-dz' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-el' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-en-gb' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-en-za' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-eo' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-es' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-et' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-eu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-fa' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-fi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-fr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ga' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-gd' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-gl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-gu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-gug' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-he' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-hi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-hr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-hu' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-id' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-in' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-is' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-it' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ja' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ka' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-kk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-km' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-kmr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-kn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ko' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-lt' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-lv' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-mk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ml' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-mn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-mr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-nb' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ne' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-nl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-nn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-nr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-nso' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-oc' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-om' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-or' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-pa-in' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-pl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-pt' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-pt-br' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ro' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ru' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-rw' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-si' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-sk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-sl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-sr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ss' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-st' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-sv' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-szl' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ta' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-te' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-tg' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-th' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-tn' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-tr' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ts' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ug' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-uk' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-uz' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-ve' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-vi' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-xh' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 'libreoffice-l10n-za' is not installed, so not removed&lt;/div&gt;&lt;div&gt;Package 
``` this look right?

---

### Post by shane_faulkinbury2 on 2023-02-14
I had to cut some code out to shorten it, but I think you get the gist?

---

### Post by ActionParsnip on 2023-02-14
OK is libreoffice or OpenOffice installed. If not then try to do what you were initially doing

---

### Post by shane_faulkinbury2 on 2023-02-14
Same thing![IMG]https://ubuntuforums.org/attachment.php?attachmentid=291769&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291770&stc=1[/IMG]

---

### Post by ActionParsnip on 2023-02-14
OK, what is the output of:
```

sudo apt -f install

```

---

### Post by shane_faulkinbury2 on 2023-02-14
> sudo apt -f install[sudo] password for none: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi libappstream-glib8
  libcdr-0.1-1 libcolamd2 libflashrom1 libfreehand-0.1-1 libftdi1-2 libfuse2
  libmspub-0.1-1 libpagemaker-0.0-0 libsuitesparseconfig5 libva-wayland2
  libvisio-0.1-1 lp-solve
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  apt-utils libreoffice-common
The following NEW packages will be installed:
  libreoffice-common
The following packages will be upgraded:
  apt-utils
1 upgraded, 1 newly installed, 0 to remove and 110 not upgraded.
16 not fully installed or removed.
Need to get 23.6 MB of archives.
After this operation, 59.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 apt-utils amd64 2.4.9 [211 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed/main amd64 libreoffice-common all 1:7.3.7-0ubuntu0.22.04.2 [23.4 MB]
Fetched 23.6 MB in 10s (2,282 kB/s)                                            
Setting up apt (2.4.9) ...
(Reading database ... 195154 files and directories currently installed.)
Preparing to unpack .../apt-utils_2.4.9_amd64.deb ...
Unpacking apt-utils (2.4.9) over (2.4.8) ...
Preparing to unpack .../libreoffice-common_1%3a7.3.7-0ubuntu0.22.04.2_all.deb ..
.
Unpacking libreoffice-common (1:7.3.7-0ubuntu0.22.04.2) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a7.
3.7-0ubuntu0.22.04.2_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice4.1.
13-freedesktop-menus 4.1.13-9811
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or di
rectory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directo
ry
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a7.3.7-0ubuntu0.22.04.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
The Software Updater still isn't working, but that may be another problem?

---

### Post by ActionParsnip on 2023-02-14
OK, run
```

sudo apt --purge autoremove
sudo apt --purge remove `dpkg -l | grep ^ii | grep -i OpenOffice | awk {'print $2'}`
sudo apt clean

```
You can't have libreoffice and OpenOffice installed. This will then square the packages off.

---

### Post by shane_faulkinbury2 on 2023-02-15
Okay, I ran the commands and same thing.

---

### Post by shane_faulkinbury2 on 2023-02-15
Openoffice is gone from my Show Applications.  Should I start another thread for my update problem?

---

### Post by Impavidus on 2023-02-16
The Show Applications isn't relevant. The important bit is: is OpenOffice gone as far as your package manager is concerned?

Error messages from Update Manager or similar GUI tools aren't very helpful. We like the error messages from the apt command line tools. Don't start a new thread until you're sure your update problem is unrelated. Because it looks related to me.

---

### Post by shane_faulkinbury2 on 2023-02-17
Here is my CLI update.

> sudo apt updateIgn:1 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy InRelease
Err:2 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                         
Hit:5 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease                       
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                 
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease               
Err:5 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease                       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EDE055B645F044F
Hit:8 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease          
Hit:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease                
Hit:10 [https://ppa.launchpadcontent.net/flatpak/stable/ubuntu](https://ppa.launchpadcontent.net/flatpak/stable/ubuntu) jammy InRelease  
Hit:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-proposed InRelease               
Hit:4 [https://packages-old.element.io/debian](https://packages-old.element.io/debian) default InRelease                 
Ign:12 [https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu](https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu) jammy InRelease
Err:13 [https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu](https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EDE055B645F044F
E: The repository 'https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.




---

### Post by ActionParsnip on 2023-02-17
[https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu/dists/](https://ppa.launchpadcontent.net/me-davidsansome/clementine/ubuntu/dists/)
This doesn't support Jammy and should be removed.

You should also disable to install CD as a source.

You can import the ProtonVPN GPG key with:
```

curl -fsSL 'https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x[COLOR=#000000]*4EDE055B645F044F*[/COLOR]' | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/protonvpn-stable.gpg

```
Source: [https://askubuntu.com/questions/1350266/problem-in-sudo-apt-update-with-proton-vpn](https://askubuntu.com/questions/1350266/problem-in-sudo-apt-update-with-proton-vpn)

---

### Post by shane_faulkinbury2 on 2023-02-17
I just tried to update in Gnome Software and get this.  What is ```
/var/lib/PackageKit/preparedupdate
```?

---

### Post by shane_faulkinbury2 on 2023-02-17
Okay, I [COLOR=#000000]disabled the install CD as a source and [/COLOR][COLOR=#000000]imported the ProtonVPN GPG key.  When I unchecked the install CD and Reloaded I got this -

 I actually unchecked the install CD before importing the ProtonVPN so that was why I got the error probably?[/COLOR]

---

### Post by shane_faulkinbury2 on 2023-02-17
I thought Libreoffice was removed since I do not see it in my apps and Openoffice is installed and running fine.  I however ran a 

```
sudo apt list --installed
```

and still see it.

I want to keep Openoffice and get rid of Libeoffice.

---

