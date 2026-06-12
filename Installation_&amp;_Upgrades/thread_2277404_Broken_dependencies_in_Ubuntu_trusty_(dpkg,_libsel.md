---
title: "Broken dependencies in Ubuntu trusty (dpkg, libselinux1-dev)"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by incolumus on 2015-05-08
I cannot figure out how to solve some broken dependencies in my Ubuntu 14.04... this is what I get:

```

javi@emo:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... falló.
Los siguientes paquetes tienen dependencias incumplidas:
 dpkg : PreDepende: libselinux1 (>= 2.3) pero 2.2.2-1ubuntu0.1 está instalado
 libselinux1-dev : Depende: libsepol1-dev (>= 2.2) pero no está instalado
E: Error, pkgProblemResolver::Resolve generó cortes, esto puede haber sido causado por paquetes retenidos.
E: No se puede corregir las dependencias

```


It's in spanish, I can try to translate it into english (with "guessed" error messages), but I think that for someone familiarized with it, it should be clear enough.

Thanks for your help... It is preventing me from installing any package :/

___

This is my /etc/apt/sources.list:

```

deb http://archive.ubuntu.com/ubuntu trusty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ trusty-security main universe restricted multiverse
deb-src http://security.ubuntu.com/ubuntu/ trusty-security main universe restricted multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu trusty-updates main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main universe restricted multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu trusty-proposed main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-proposed main universe restricted multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu trusty-backports main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-backports main universe restricted multiverse #Added by software-properties

```

---

### Post by mc4man on 2015-05-08
Your dpkg depends suggest it's the utopic or vivid version, how did that happen?
post
```
apt-cache policy dpkg
```
```
apt-cache show dpkg
```
```
apt-cache madison dpkg
```

---

### Post by incolumus on 2015-05-09
I can't tell what happened, I remember trying a dist-upgrade and having to cancel it half the way because there was a problem... but I can't remember what the problem was. These are the outputs from the commands above:


```

javi@emo:~$ sudo apt-cache policy dpkg
dpkg:
  Instalados: 1.17.13ubuntu1.1
  Candidato:  1.17.13ubuntu1.1
  Tabla de versión:
 *** 1.17.13ubuntu1.1 0
        100 /var/lib/dpkg/status
     1.17.5ubuntu5.4 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.17.5ubuntu5 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

```
_______________________________________________________________________

```

javi@emo:~$ sudo apt-cache show dpkg
Package: dpkg                                                                                                         
Essential: yes                                                                                                        
Status: install ok installed                                                                                          
Priority: required                                                                                                    
Section: admin                                                                                                        
Installed-Size: 6517                                                                                                  
Origin: debian                                                                                                        
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>                                                 
Bugs: debbugs://bugs.debian.org                                                                                       
Architecture: amd64                                                                                                   
Multi-Arch: foreign                                                                                                   
Version: 1.17.13ubuntu1.1                                                                                             
Replaces: manpages-it (<< 2.80-4)
Pre-Depends: libbz2-1.0, libc6 (>= 2.14), liblzma5 (>= 5.1.1alpha+20120614), libselinux1 (>= 2.3), zlib1g (>= 1:1.1.4), tar (>= 1.23)
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.15.8), libdpkg-perl (<< 1.15.8)
Conflicts: ada-reference-manual (<< 20021112web-4), asn1-mode (<< 2.7-7), bogosort (<< 0.4.2-3), cl-yacc (<< 0.3-3), cpp-4.1-doc (<< 4.1.2.nf2-4), cpp-4.2-doc (<< 4.2.4.nf1-4), gcc-4.1-doc (<< 4.1.2.nf2-4), gcc-4.2-doc (<< 4.2.4.nf1-4), gcj-4.1-doc (<< 4.1.2.nf2-4), gcj-4.2-doc (<< 4.2.4.nf1-4), gfortran-4.1-doc (<< 4.1.2.nf2-4), gfortran-4.2-doc (<< 4.2.4.nf1-4), ggz-docs (<< 0.0.14.1-2), glame (<< 2.0.1-6), gnat-4.1-doc (<< 4.1.2.nf2-4), gnat-4.2-doc (<< 4.2.4.nf1-4), gtalk (<< 0.99.10-16), libalogg-dev (<< 1.3.7-2), libgtk1.2-doc (<< 1.2.10-19), libnettle-dev (<< 2), liborbit-dev (<< 0.5.17-12), libreadline5-dev (<< 5.2-8), librep-doc (<< 0.90), mmucl (<< 1.5.2-3), nxml-mode (<< 20041004-9), r6rs-doc (<< 1.0-2), serveez-doc (<< 0.1.5-3), slat (<< 2.0-6), texlive-base-bin-doc (<< 2007.dfsg.2-9), ttcn-el (<< 0.6.9-2), ulog-acctd (<< 0.4.3-3), xconq-doc (<< 7.4.1-5), zenirc (<< 2.112.dfsg-1)
Conffiles:
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
 /etc/cron.daily/dpkg b8065b6bfc248caba501c3f5bb508e66
Description-es: Sistema de gestión de paquetes de Debian
 Este paquete proporciona la infraestructura de bajo nivel para manejar la
 instalación y eliminación de paquetes de Debian.
 .
 Para instalar las herramientas de desarrollo de paquetes de Debian,
 instale el paquete dpkg-dev.
Description-md5: 2f156c6a30cc39895ad3487111e8c190
Homepage: [https://wiki.debian.org/Teams/Dpkg](https://wiki.debian.org/Teams/Dpkg)
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>

Package: dpkg
Essential: yes
Priority: required
Section: admin
Installed-Size: 6239
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>
Architecture: amd64
Version: 1.17.5ubuntu5.4
Replaces: manpages-it (<< 2.80-4)
Pre-Depends: libbz2-1.0, libc6 (>= 2.14), liblzma5 (>= 5.1.1alpha+20120614), libselinux1 (>= 2.1.0), zlib1g (>= 1:1.1.4), tar (>= 1.23)
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.15.8), libdpkg-perl (<< 1.15.8)
Filename: pool/main/d/dpkg/dpkg_1.17.5ubuntu5.4_amd64.deb
Size: 1953910
MD5sum: 82caeea040f70f8dffd2f1aa38446f6f
SHA1: cd08501e562401abba25cb6f61d0ac35128cf73a
SHA256: 985c87199393c00c872b1577a3656a466a33d15f6be793b08ce2375e98047aac
Description-es: Sistema de gestión de paquetes de Debian
 Este paquete proporciona la infraestructura de bajo nivel para manejar la
 instalación y eliminación de paquetes de Debian.
 .
 Para instalar las herramientas de desarrollo de paquetes de Debian,
 instale el paquete dpkg-dev.
Description-md5: 2f156c6a30cc39895ad3487111e8c190
Origin: Ubuntu
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Multi-Arch: foreign
Homepage: [https://wiki.debian.org/Teams/Dpkg](https://wiki.debian.org/Teams/Dpkg)
Supported: 5y
Task: minimal

Package: dpkg
Essential: yes
Priority: required
Section: admin
Installed-Size: 6239
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>
Architecture: amd64
Version: 1.17.5ubuntu5
Replaces: manpages-it (<< 2.80-4)
Pre-Depends: libbz2-1.0, libc6 (>= 2.14), liblzma5 (>= 5.1.1alpha+20120614), libselinux1 (>= 2.1.0), zlib1g (>= 1:1.1.4), tar (>= 1.23)
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.15.8), libdpkg-perl (<< 1.15.8)
Filename: pool/main/d/dpkg/dpkg_1.17.5ubuntu5_amd64.deb
Size: 1956240
MD5sum: ed27e7e9c0fa6f2440f81700af419251
SHA1: 2fd8c704c6aee2c28ba59e9f5e2651239a160172
SHA256: 5f2980165aae60567d1947ec330a9e75e2eaaf974095cea5a5b20af709b49586
Description-es: Sistema de gestión de paquetes de Debian
 Este paquete proporciona la infraestructura de bajo nivel para manejar la
 instalación y eliminación de paquetes de Debian.
 .
 Para instalar las herramientas de desarrollo de paquetes de Debian,
 instale el paquete dpkg-dev.
Description-md5: 2f156c6a30cc39895ad3487111e8c190
Origin: Ubuntu
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Multi-Arch: foreign
Homepage: [https://wiki.debian.org/Teams/Dpkg](https://wiki.debian.org/Teams/Dpkg)
Supported: 5y
Task: minimal

```
_______________________________________________________________________

```

javi@emo:~$ sudo apt-cache madison dpkg
      dpkg | 1.17.5ubuntu5.4 | [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
      dpkg | 1.17.5ubuntu5.4 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
      dpkg | 1.17.5ubuntu5 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
      dpkg | 1.17.5ubuntu5 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main Sources
      dpkg | 1.17.5ubuntu5.4 | [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main Sources
      dpkg | 1.17.5ubuntu5.4 | [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main Sources

```

Thanks for your help.

---

### Post by Bucky Ball on 2015-05-09
Please use [code] tags for terminal output. See the last link in my signature for how. I have added them to your last post. Thanks.

---

### Post by incolumus on 2015-05-09
Now it looks much better ;D

---

### Post by incolumus on 2015-05-09
Nobody has an idea or intuition on how to solve this situation? I don't want to reinstall, but if there is no other option I'll do.  :(

---

