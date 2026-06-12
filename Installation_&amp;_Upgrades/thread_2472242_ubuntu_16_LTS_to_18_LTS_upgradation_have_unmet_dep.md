---
title: "ubuntu 16 LTS to 18 LTS upgradation have unmet dependencies"
date: 2022-02-22
forum: Installation &amp; Upgrades
---

### Post by saif7861 on 2022-02-22
During the upgradation from ubuntu 16LTS to 18LTS on VMWARE PLATFORM using CLI I have got the following dependencies even though I have had workarounds as such apt-get install -f apt-get clean dpkg --configure -a but still not getting success to upgrade it.

The following packages have unmet dependencies:
 checkbox-converged : Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin but it is not installable
 indicator-keyboard : Depends: libgnome-desktop-3-17 (>= 3.17.92) but it is not going to be installed
 libc-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1.4 is to be installed
 libc-dev-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1.4 is to be installed
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu11.3) but 2.27-3ubuntu1.4 is to be installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu11.3) but 2.27-3ubuntu1.4 is to be installed
 liboxideqtquick0 : Depends: liboxideqtcore0 (= 1.21.5-0ubuntu0.16.04.1) but it is not installable
 libunity-webapps0 : Depends: unity-webapps-service but it is not installable
 locales : Depends: libc-bin (> 2.27)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.6.7-1~18.04 is to be installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.6.7-1~18.04 is to be installed
 unity-webapps-qml : Depends: liboxideqt-qmlplugin (>= 1.3.0) but it is not installable or
                              qml-module-qtwebkit but it is not going to be installed
                     Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin but it is not installable or
                              qtdeclarative5-ubuntu-ui-toolkit-plugin-gles but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
==============================================================================

apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 checkbox-converged : Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin but it is not installable
 indicator-keyboard : Depends: libgnome-desktop-3-17 (>= 3.17.92) but it is not installed
 libc-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1.4 is installed
 libc-dev-bin : Depends: libc6 (< 2.24) but 2.27-3ubuntu1.4 is installed
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu11.3) but 2.27-3ubuntu1.4 is installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu11.3) but 2.27-3ubuntu1.4 is installed
 liboxideqtquick0 : Depends: liboxideqtcore0 (= 1.21.5-0ubuntu0.16.04.1) but it is not installable
 libunity-webapps0 : Depends: unity-webapps-service but it is not installable
 locales : Depends: libc-bin (> 2.27)
 python3 : PreDepends: python3-minimal (= 3.5.1-3) but 3.6.7-1~18.04 is installed
           Depends: libpython3-stdlib (= 3.5.1-3) but 3.6.7-1~18.04 is installed
 unity-webapps-qml : Depends: liboxideqt-qmlplugin (>= 1.3.0) but it is not installable or
                              qml-module-qtwebkit but it is not installed
                     Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin but it is not installable or
                              qtdeclarative5-ubuntu-ui-toolkit-plugin-gles but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by Impavidus on 2022-02-22
I see you have some packages from 18.04 already installed on your 16.04 system, which is why you have package conflicts. You would have to downgrade those packages to those for 16.04 first, before you can start your upgrade. That is not so easy, even more so as 16.04 is already out of support (unless you signed up for additional security maintenance). So, considering that your system is a mess, has been unsupported for a year and Ubuntu 18.04 is getting a bit old too, are you sure you want to upgrade to 18.04? A fresh install will be easier and you could jump just as easily straight to 20.04, unless you depend on software unavailable on 20.04.

---

