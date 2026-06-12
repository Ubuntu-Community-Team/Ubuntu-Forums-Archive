---
title: "Lost repositories"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by maxsteffens on 2015-12-04
how to install?
Lost repositories.

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"
```

```
$ sudo apt-get install vlc
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os pacotes extra a seguir serão instalados:
  libbasicusageenvironment0 libcddb2 libchromaprint0 libcrystalhd3
  libdc1394-22 libdvbpsi9 libebml4 libgles1-mesa libgles2-mesa libgroupsock1
  libiso9660-8 libkate1 liblivemedia23 libmatroska6 libmodplug1 libmpcdec6
  libproxy-tools libresid-builder0c2a libshine3 libsidplay2 libssh2-1 libupnp6
  libusageenvironment1 libva-drm1 libva-x11-1 libvcdinfo0 libvlc5 libvlccore8
  libxcb-composite0 libxcb-xv0 libzvbi-common libzvbi0 vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-samba
Pacotes sugeridos:
  libchromaprint-tools python-acoustid firmware-crystalhd videolan-doc
  libdvdcss2
Os NOVOS pacotes a seguir serão instalados:
  libbasicusageenvironment0 libcddb2 libchromaprint0 libcrystalhd3
  libdc1394-22 libdvbpsi9 libebml4 libgles1-mesa libgles2-mesa libgroupsock1
  libiso9660-8 libkate1 liblivemedia23 libmatroska6 libmodplug1 libmpcdec6
  libproxy-tools libresid-builder0c2a libshine3 libsidplay2 libssh2-1 libupnp6
  libusageenvironment1 libva-drm1 libva-x11-1 libvcdinfo0 libvlc5 libvlccore8
  libxcb-composite0 libxcb-xv0 libzvbi-common libzvbi0 vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-samba
0 pacotes atualizados, 37 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso baixar 11,5 MB de arquivos.
Depois desta operação, 58,5 MB adicionais de espaço em disco serão usados.
Você quer continuar? [S/n] s
AVISO: Os pacotes a seguir não podem ser autenticados!
  libbasicusageenvironment0 libcrystalhd3 libdvbpsi9 libebml4 libgles1-mesa
  libgles2-mesa libgroupsock1 liblivemedia23 libmatroska6 libmpcdec6 libshine3
  libssh2-1 libusageenvironment1 libva-drm1 libva-x11-1 libxcb-composite0
  libxcb-xv0 libzvbi-common libzvbi0 libchromaprint0 libdc1394-22 libupnp6
  libcddb2 libiso9660-8 libkate1 libmodplug1 libproxy-tools
  libresid-builder0c2a libsidplay2 libvcdinfo0 vlc-data libvlccore8 libvlc5
  vlc-nox vlc vlc-plugin-notify vlc-plugin-samba
Instalar estes pacotes sem verificação? [s/N] s
Obter:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libbasicusageenvironment0 amd64 2014.01.13-1 [16,4 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libcrystalhd3 amd64 1:0.0~git20110715.fdd2f19-11
  404  Not Found
Obter:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libdvbpsi9 amd64 1.2.0-1 [45,4 kB]
Obter:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libebml4 amd64 1.3.0-2 [51,7 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-updates/main libgles1-mesa amd64 10.3.2-0ubuntu0.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-updates/main libgles2-mesa amd64 10.3.2-0ubuntu0.1
  404  Not Found
Obter:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libgroupsock1 amd64 2014.01.13-1 [22,0 kB]
Obter:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe liblivemedia23 amd64 2014.01.13-1 [267 kB]
Obter:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libmatroska6 amd64 1.4.1-2 [155 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libmpcdec6 amd64 2:0.1~r459-4.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libshine3 amd64 3.1.0-2  
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libssh2-1 amd64 1.4.3-3  
  404  Not Found
Obter:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libusageenvironment1 amd64 2014.01.13-1 [7.510 B]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libva-drm1 amd64 1.3.1-3 
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libva-x11-1 amd64 1.3.1-3
  404  Not Found
Obter:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/main libxcb-composite0 amd64 1.10-2ubuntu1 [5.036 B]
Obter:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/main libxcb-xv0 amd64 1.10-2ubuntu1 [8.772 B]
Obter:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libzvbi-common all 0.2.35-2 [38,7 kB]
Obter:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libzvbi0 amd64 0.2.35-2 [293 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libchromaprint0 amd64 1.1-1build2
  404  Not Found
Obter:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libdc1394-22 amd64 2.2.1-2ubuntu2 [75,0 kB]
Obter:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libupnp6 amd64 1:1.6.17-1.2 [142 kB]
Obter:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libcddb2 amd64 1.3.2-5fakesync1 [33,9 kB]
Obter:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libiso9660-8 amd64 0.83-4.1ubuntu1 [18,8 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libkate1 amd64 0.4.1-1.1 
  404  Not Found
Obter:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libmodplug1 amd64 1:0.8.8.4-4.1 [147 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libproxy-tools amd64 0.4.11-4ubuntu1
  404  Not Found
Obter:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libresid-builder0c2a amd64 2.1.1-14 [39,4 kB]
Obter:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libsidplay2 amd64 2.1.1-14 [102 kB]
Obter:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic/universe libvcdinfo0 amd64 0.7.24+dfsg-0.2 [90,7 kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe vlc-data all 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe libvlccore8 amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe libvlc5 amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe vlc-nox amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe vlc amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe vlc-plugin-notify amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) utopic-security/universe vlc-plugin-samba amd64 2.2.0-0ubuntu0.14.10.1
  404  Not Found
Baixados 1.561 kB em 33s (46,4 kB/s)                                           
E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/c/crystalhd/libcrystalhd3_0.0~git20110715.fdd2f19-11_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/crystalhd/libcrystalhd3_0.0~git20110715.fdd2f19-11_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgles1-mesa_10.3.2-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgles1-mesa_10.3.2-0ubuntu0.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgles2-mesa_10.3.2-0ubuntu0.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgles2-mesa_10.3.2-0ubuntu0.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmpc/libmpcdec6_0.1~r459-4.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmpc/libmpcdec6_0.1~r459-4.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/s/shine/libshine3_3.1.0-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/shine/libshine3_3.1.0-2_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libs/libssh2/libssh2-1_1.4.3-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libs/libssh2/libssh2-1_1.4.3-3_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-drm1_1.3.1-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-drm1_1.3.1-3_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-x11-1_1.3.1-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-x11-1_1.3.1-3_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/c/chromaprint/libchromaprint0_1.1-1build2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/chromaprint/libchromaprint0_1.1-1build2_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libk/libkate/libkate1_0.4.1-1.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libk/libkate/libkate1_0.4.1-1.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/libp/libproxy/libproxy-tools_0.4.11-4ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libp/libproxy/libproxy-tools_0.4.11-4ubuntu1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_2.2.0-0ubuntu0.14.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-data_2.2.0-0ubuntu0.14.10.1_all.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore8_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlccore8_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc5_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc5_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-notify_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-notify_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Falhou ao buscar [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-samba_2.2.0-0ubuntu0.14.10.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-plugin-samba_2.2.0-0ubuntu0.14.10.1_amd64.deb)  404  Not Found

E: Impossível buscar alguns arquivos, talvez executar apt-get update ou tentar com --fix-missing?
```

---

### Post by LukeMorrison on 2015-12-04
If I am reading this correctly, it appears you are running an unsupported version of *ubuntu (14.10).  You could update directly from 14.10 --> 15.04 --> 15.10, but it would be quicker to backup your data and do a fresh install of 15.10.  If you are unfamiliar with how to do this, please ask.

---

### Post by howefield on 2015-12-04
Ubuntu 14.10 is end of life, the repositories are no longer currently supported so either change your sources.list to old.releases as per [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) or much more recommended is to upgrade to a supported release, currently 15.04 which expires January coming, 15.10 which expires next July or 14.04.x

---

