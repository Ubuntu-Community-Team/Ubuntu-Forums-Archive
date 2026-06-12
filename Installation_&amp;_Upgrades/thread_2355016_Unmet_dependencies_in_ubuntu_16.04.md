---
title: "Unmet dependencies in ubuntu 16.04"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by wimathome on 2017-03-08
I am unable to update or upgrade ubuntu 16.04 LTS and get error messages about unmet dependencies.

sudo apt-get -f install gives this response:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-human
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 0 to remove and 282 not upgraded.
20 not fully installed or removed.
Need to get 0 B/22,5 MB of archives.
After this operation, 58,4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 340897 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb ...
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial1) over (1:5.1.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone help me to resolve this?

---

### Post by QIII on 2017-03-08
Hello!

Please use code tags to enclose terminal commands and results.  The preserves terminal formatting and makes your post easier to read.

To use code tags:

1. Click the # button in the toolbar above the text entry box, place your cursor between the code tags that appear and paste or type your text.

2. Paste or type your text, highlight it and then click the # button.

3. Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text. The square brackets are required.

---

### Post by Perfect Storm on 2017-03-08
Try upgrade the system first:

```
sudo apt-get upgrade
```

---

### Post by wimathome on 2017-03-08
Upgrade gives me this as response:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.6~rc2) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-java-common : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by QIII on 2017-03-08
Have you installed a version of LibreOffice from a repository or .deb other than the 16.04 repository?

---

### Post by wimathome on 2017-03-08
No I didn't install libreoffice recently. Actually it was pre-installed when I bought it a couple of months ago and it always worked fine.

---

### Post by QIII on 2017-03-08
Pre-installed by whom?

---

### Post by wimathome on 2017-03-08
By the retailer who sold me the computer. They sell notebooks with pre-installed ubuntu.

---

### Post by QIII on 2017-03-08
OK.

Looks like libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial1) is a security update.

Have you tried

```
sudo apt update
```
```
sudo apt dist-upgrade
```?

apt also has full-upgrade, but dist-upgrade is not deprecated.  They do slightly different things.  dist-upgrade will attempt to handle dependencies "intelligently".

Neither dist-upgrade nor full-upgrade will attempt to upgrade you to the next release of Ubuntu.

---

### Post by wimathome on 2017-03-08
OK, thanks. So this is what I got.

After sudo apt update:

```
Hit:1 http://be.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://be.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://be.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Get:5 http://be.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [184 kB]
Get:6 http://be.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [139 kB]
Get:7 http://be.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [169 kB]
Get:8 http://be.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2.520 B]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54,2 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [40,7 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32,1 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37,0 kB]
Fetched 1.152 kB in 1s (1.029 kB/s)                                
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
283 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

After sudo apt-get dist-upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.6~rc2) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-java-common : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by steeldriver on 2017-03-08
The root of the problem seems to be that a debian **openoffice **package has been installed at some point, and that's causing a conflict with **libreoffice**

```

dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782

```

---

### Post by wimathome on 2017-03-08
Yes, that could be. So how could I solve that?

---

### Post by ian-weisser on 2017-03-08
Uninstall the debian libreoffice packages.
If in doubt, uninstall ALL libreoffice packages, then reinstall from the Ubuntu repositories.

---

### Post by wimathome on 2017-03-09
I tried to remove both libreoffice and openoffice with 
sudo apt-get purge openoffice and sudo apt-get purge libreoffice 

but that doesn't work.

---

### Post by steeldriver on 2017-03-09
Perhaps it was installed via dpkg not apt? what does

```

dpkg -l | grep -i openoffice

```

say?

---

### Post by wimathome on 2017-03-09
That says a lot:
```
ii  hyphen-en-us                                  2.8.8-2ubuntu1                                all          US English hyphenation patterns for LibreOffice/OpenOffice.org
ii  mythes-de                                     20120516-2                                    all          German Thesaurus for OpenOffice.org/LibreOffice
ii  mythes-de-ch                                  20120516-2                                    all          German Thesaurus for OpenOffice.org/LibreOffice (Swiss Version)
ii  mythes-en-au                                  2.1-5.4                                       all          Australian English Thesaurus for OpenOffice.org
ii  openoffice                                    4.1.2-3                                       amd64        Brand module for OpenOffice 4.1.2
ii  openoffice-base                               4.1.2-3                                       amd64        Base module for Apache OpenOffice 4.1.2
ii  openoffice-brand-base                         4.1.2-3                                       amd64        Base brand module for OpenOffice 4.1.2
ii  openoffice-brand-calc                         4.1.2-3                                       amd64        Calc brand module for OpenOffice 4.1.2
ii  openoffice-brand-de                           4.1.2-3                                       amd64        Brand language module for OpenOffice 4.1.2
ii  openoffice-brand-draw                         4.1.2-3                                       amd64        Draw brand module for OpenOffice 4.1.2
ii  openoffice-brand-en-gb                        4.1.2-3                                       amd64        Brand language module for OpenOffice 4.1.2
ii  openoffice-brand-fr                           4.1.2-3                                       amd64        Brand language module for OpenOffice 4.1.2
ii  openoffice-brand-impress                      4.1.2-3                                       amd64        Impress brand module for OpenOffice 4.1.2
ii  openoffice-brand-math                         4.1.2-3                                       amd64        Math brand module for OpenOffice 4.1.2
ii  openoffice-brand-nl                           4.1.2-3                                       amd64        Brand language module for OpenOffice 4.1.2
ii  openoffice-brand-writer                       4.1.2-3                                       amd64        Writer brand module for OpenOffice 4.1.2
ii  openoffice-calc                               4.1.2-3                                       amd64        Calc module for Apache OpenOffice 4.1.2
ii  openoffice-core01                             4.1.2-3                                       amd64        Core module for Apache OpenOffice 4.1.2
ii  openoffice-core02                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-core03                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-core04                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-core05                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-core06                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-core07                             4.1.2-3                                       amd64        Office core module for Apache OpenOffice 4.1.2
ii  openoffice-de                                 4.1.2-3                                       amd64        Language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-base                            4.1.2-3                                       amd64        Base language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-calc                            4.1.2-3                                       amd64        Calc language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-draw                            4.1.2-3                                       amd64        Draw language module for Apache OpenOffice , language de
ii  openoffice-de-help                            4.1.2-3                                       amd64        Language help module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-impress                         4.1.2-3                                       amd64        Impress language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-math                            4.1.2-3                                       amd64        Math language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-res                             4.1.2-3                                       amd64        Language resource module for Apache OpenOffice 4.1.2, language de
ii  openoffice-de-writer                          4.1.2-3                                       amd64        Writer language module for Apache OpenOffice 4.1.2, language de
ii  openoffice-debian-menus                       4.1.2-9782                                    all          OpenOffice desktop integration
ii  openoffice-draw                               4.1.2-3                                       amd64        Draw module for Apache OpenOffice 4.1.2
ii  openoffice-en-gb                              4.1.2-3                                       amd64        Language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-base                         4.1.2-3                                       amd64        Base language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-calc                         4.1.2-3                                       amd64        Calc language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-draw                         4.1.2-3                                       amd64        Draw language module for Apache OpenOffice , language en_GB
ii  openoffice-en-gb-help                         4.1.2-3                                       amd64        Language help module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-impress                      4.1.2-3                                       amd64        Impress language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-math                         4.1.2-3                                       amd64        Math language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-res                          4.1.2-3                                       amd64        Language resource module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-en-gb-writer                       4.1.2-3                                       amd64        Writer language module for Apache OpenOffice 4.1.2, language en_GB
ii  openoffice-fr                                 4.1.2-3                                       amd64        Language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-base                            4.1.2-3                                       amd64        Base language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-calc                            4.1.2-3                                       amd64        Calc language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-draw                            4.1.2-3                                       amd64        Draw language module for Apache OpenOffice , language fr
ii  openoffice-fr-help                            4.1.2-3                                       amd64        Language help module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-impress                         4.1.2-3                                       amd64        Impress language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-math                            4.1.2-3                                       amd64        Math language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-res                             4.1.2-3                                       amd64        Language resource module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-fr-writer                          4.1.2-3                                       amd64        Writer language module for Apache OpenOffice 4.1.2, language fr
ii  openoffice-gnome-integration                  4.1.2-3                                       amd64        Gnome integration module for Apache OpenOffice 4.1.2
ii  openoffice-graphicfilter                      4.1.2-3                                       amd64        Graphic filter module for Apache OpenOffice 4.1.2
ii  openoffice-images                             4.1.2-3                                       amd64        Images module for Apache OpenOffice 4.1.2
ii  openoffice-impress                            4.1.2-3                                       amd64        Impress module for Apache OpenOffice 4.1.2
ii  openoffice-javafilter                         4.1.2-3                                       amd64        Java filter module for Apache OpenOffice 4.1.2
ii  openoffice-math                               4.1.2-3                                       amd64        Math module for Apache OpenOffice 4.1.2
ii  openoffice-nl                                 4.1.2-3                                       amd64        Language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-base                            4.1.2-3                                       amd64        Base language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-calc                            4.1.2-3                                       amd64        Calc language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-draw                            4.1.2-3                                       amd64        Draw language module for Apache OpenOffice , language nl
ii  openoffice-nl-help                            4.1.2-3                                       amd64        Language help module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-impress                         4.1.2-3                                       amd64        Impress language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-math                            4.1.2-3                                       amd64        Math language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-res                             4.1.2-3                                       amd64        Language resource module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-nl-writer                          4.1.2-3                                       amd64        Writer language module for Apache OpenOffice 4.1.2, language nl
ii  openoffice-ogltrans                           4.1.2-3                                       amd64        OpenGL slide transitions module for Apache OpenOffice 4.1.2
ii  openoffice-onlineupdate                       4.1.2-3                                       amd64        Online update modul for Apache OpenOffice 4.1.2
ii  openoffice-ooofonts                           4.1.2-3                                       amd64        Mailcap module for Apache OpenOffice 4.1.2
ii  openoffice-ooolinguistic                      4.1.2-3                                       amd64        Linguistic module for Apache OpenOffice 4.1.2
ii  openoffice-pyuno                              4.1.2-3                                       amd64        Pyuno module for Apache OpenOffice 4.1.2
ii  openoffice-ure                                4.1.2-3                                       amd64        UNO Runtime Environment for OpenOffice 4.1.2
ii  openoffice-writer                             4.1.2-3                                       amd64        Writer module for Apache OpenOffice 4.1.2
ii  openoffice-xsltfilter                         4.1.2-3                                       amd64        XSLT filter samples module for Apache OpenOffice 4.1.2
ii  openoffice.org-hyphenation                    0.9                                           all          Hyphenation patterns for OpenOffice.org


```

---

### Post by ian-weisser on 2017-03-11
> **wimathome said:**
> but that doesn't work.

Unfortunately, that's not enough information to help you.
Please show us everything you tried, and the complete output of each try.
More details help a lot.

---

### Post by oldrocker99 on 2017-03-11
Have you done this?```
sudo apt-get -f install
```

If that command is recommended, it is a good idea to enter it. This will most likely remove your LibreOffice files, and then you can enter```
sudo apt-get install libreoffice
```

Good luck.

---

### Post by wimathome on 2017-03-11
> **ian-weisser said:**
> Unfortunately, that's not enough information to help you.
Please show us everything you tried, and the complete output of each try.
More details help a lot.
OK. So sudo apt-get -f install gave
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libhsqldb1.8.0-java libreoffice-base-drivers libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-human
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 0 to remove and 286 not upgraded.
19 not fully installed or removed.
Need to get 0 B/22,5 MB of archives.
After this operation, 58,4 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 340845 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb ...
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial1) over (1:5.1.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
sudo apt-get remove openoffice*.* gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openoffice.org-debian-menus' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en-ca' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en-us' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-updatedicts' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-de' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-fr' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-nl' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-kde' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-common' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-an' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ca' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eo' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-es' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-eu' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-fo' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-gl' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nb' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nn' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-nr' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ns' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ss' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-st' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tl' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-tn' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-uz' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-ve' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-xh' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-zu' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-impress' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hunspell' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-en' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-fi' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ga' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-hr' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-id' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-calc' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-writer' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-lt' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-pl' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation-ru' for glob 'openoffice*.*'
Note, selecting 'openoffice.org2-thesaurus' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-ure' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-en-gb' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-writer' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-de' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-it' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-pl' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-bundled' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-calc' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-en' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-es' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-dict-fr' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-base' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-en-us' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-core' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-draw' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-dev-doc' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-math' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-dmaths' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-at' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-spellcheck-de-de' for glob 'openoffice*.*'
Note, selecting 'openoffice.org' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-unbundled' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-hyphenation' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3' for glob 'openoffice*.*'
Note, selecting 'openoffice.org3-base' for glob 'openoffice*.*'
Note, selecting 'openoffice.org-thesaurus-en-au' for glob 'openoffice*.*'
Package 'openoffice.org-thesaurus-it' is not installed, so not removed
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Package 'openoffice.org-hunspell' is not installed, so not removed
Package 'openoffice.org-core' is not installed, so not removed
Note, selecting 'hunspell-an' instead of 'openoffice.org-spellcheck-an'
Package 'openoffice.org' is not installed, so not removed
Note, selecting 'hunspell-ca' instead of 'openoffice.org-spellcheck-ca'
Package 'openoffice.org-spellcheck-en-us' is not installed, so not removed
Note, selecting 'hunspell-eu' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Package 'openoffice.org-writer' is not installed, so not removed
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en-us'
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en'
Package 'openoffice.org-hyphenation-hr' is not installed, so not removed
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-ru' instead of 'openoffice.org-hyphenation-ru'
Package 'openoffice.org-base' is not installed, so not removed
Package 'openoffice.org-common' is not installed, so not removed
Package 'openoffice.org-dev-doc' is not installed, so not removed
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-de' instead of 'openoffice.org-thesaurus-de'
Note, selecting 'mythes-de-ch' instead of 'openoffice.org-thesaurus-de-ch'
Note, selecting 'mythes-en-au' instead of 'openoffice.org-thesaurus-en-au'
Note, selecting 'mythes-en-au' instead of 'openoffice.org2-thesaurus'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-en-ca'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Package 'openoffice.org-calc' is not installed, so not removed
Package 'openoffice.org-kde' is not installed, so not removed
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Package 'openoffice.org-dmaths' is not installed, so not removed
Package 'openoffice.org-bundled' is not installed, so not removed
Package 'openoffice.org3-writer' is not installed, so not removed
Package 'openoffice.org3' is not installed, so not removed
Package 'openoffice.org3-dict-es' is not installed, so not removed
Package 'openoffice.org3-dict-en' is not installed, so not removed
Package 'openoffice.org3-dict-fr' is not installed, so not removed
Package 'openoffice.org3-base' is not installed, so not removed
Package 'openoffice.org3-en-gb' is not installed, so not removed
Package 'openoffice.org3-impress' is not installed, so not removed
Package 'openoffice.org3-fr' is not installed, so not removed
Package 'openoffice.org3-math' is not installed, so not removed
Package 'openoffice.org3-calc' is not installed, so not removed
Package 'openoffice.org3-nl' is not installed, so not removed
Package 'openoffice.org3-de' is not installed, so not removed
Package 'openoffice.org3-draw' is not installed, so not removed
Package 'openoffice.org-ure' is not installed, so not removed
Package 'openoffice.org-debian-menus' is not installed, so not removed
Package 'openoffice.org-hyphenation-lt' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.6~rc2) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-java-common : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
sudo apt-get remove libreoffice*.* gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice.org-writer' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-help-5.1' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-3.5' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-3.6' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-4.0' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-4.1' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-4.2' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-4.3' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-4.4' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-5.0' for glob 'libreoffice*.*'
Note, selecting 'libreoffice-l10n-5.1' for glob 'libreoffice*.*'
Note, selecting 'libreoffice.org-calc' for glob 'libreoffice*.*'
Package 'libreoffice-l10n-3.5' is not installed, so not removed
Package 'libreoffice-l10n-3.6' is not installed, so not removed
Package 'libreoffice-l10n-4.0' is not installed, so not removed
Package 'libreoffice-l10n-4.1' is not installed, so not removed
Package 'libreoffice-l10n-4.2' is not installed, so not removed
Package 'libreoffice-l10n-4.3' is not installed, so not removed
Package 'libreoffice-l10n-4.4' is not installed, so not removed
Package 'libreoffice-l10n-5.0' is not installed, so not removed
Package 'libreoffice-dtd-officedocument1.0' is not installed, so not removed
Package 'libreoffice.org-calc' is not installed, so not removed
Package 'libreoffice.org-writer' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.6~rc2) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-java-common : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
sudo apt-get purge openoffice gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.6~rc2) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-java-common : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-breeze : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.6~rc2-0ubuntu1~xenial1) but 1:5.1.4-0ubuntu1 is to be installed
 openoffice-brand-base : Depends: openoffice but it is not going to be installed
 openoffice-brand-calc : Depends: openoffice but it is not going to be installed
 openoffice-brand-de : Depends: openoffice but it is not going to be installed
 openoffice-brand-draw : Depends: openoffice but it is not going to be installed
 openoffice-brand-en-gb : Depends: openoffice but it is not going to be installed
 openoffice-brand-fr : Depends: openoffice but it is not going to be installed
 openoffice-brand-impress : Depends: openoffice but it is not going to be installed
 openoffice-brand-math : Depends: openoffice but it is not going to be installed
 openoffice-brand-nl : Depends: openoffice but it is not going to be installed
 openoffice-brand-writer : Depends: openoffice but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
I hope this gives you enough information. Thanks.

---

### Post by wimathome on 2017-03-12
I tried to remove openoffice packages with ```
sudo dpkg --remove --force-depends --force-remove-reinstreq openoffice
```
Reply as ```
dpkg: openoffice: dependency problems, but removing anyway as you requested:
 openoffice-brand-draw depends on openoffice.
 openoffice-brand-de depends on openoffice.
 openoffice-brand-nl depends on openoffice.
 openoffice-brand-calc depends on openoffice.
 openoffice-brand-math depends on openoffice.
 openoffice-brand-fr depends on openoffice.
 openoffice-brand-impress depends on openoffice.
 openoffice-brand-en-gb depends on openoffice.
 openoffice-brand-base depends on openoffice.
 openoffice-brand-writer depends on openoffice.

(Reading database ... 340844 files and directories currently installed.)
Removing openoffice (4.1.2-3) ...
```
After this sudo apt-get -f install responds as follows: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libhsqldb1.8.0-java libreoffice-base-drivers libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-human
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following packages will be REMOVED:
  openoffice-brand-base openoffice-brand-calc openoffice-brand-de
  openoffice-brand-draw openoffice-brand-en-gb openoffice-brand-fr
  openoffice-brand-impress openoffice-brand-math openoffice-brand-nl
  openoffice-brand-writer
The following packages will be upgraded:
  libreoffice-common
1 upgraded, 0 newly installed, 10 to remove and 286 not upgraded.
19 not fully installed or removed.
Need to get 0 B/22,5 MB of archives.
After this operation, 867 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 340812 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb ...
Unpacking libreoffice-common (1:5.1.6~rc2-0ubuntu1~xenial1) over (1:5.1.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wimathome on 2017-03-12
Seems like I found a solution here: [https://ubuntuforums.org/showthread.php?t=1642173](https://ubuntuforums.org/showthread.php?t=1642173)
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libreoffice-common_1%3a5.1.6~rc2-0ubuntu1~xenial1_all.deb
```
This seemed to remove the .deb package that was causing the problems.

---

