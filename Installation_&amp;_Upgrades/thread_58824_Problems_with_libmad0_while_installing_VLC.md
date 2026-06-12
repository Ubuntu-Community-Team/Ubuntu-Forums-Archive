---
title: "Problems with libmad0 while installing VLC"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by Rurouni Diei on 2005-08-21
Hi!! I'm afraid to say that I am totally new to Linux (I have been using it for just 4 days), so I still find some problems quite out of my reach to solve. I have been trying to install VLC using synaptic, but I found the following problem:

W: Falló al obtener [http://es.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb)
  El tamaño difiere

(Which means, if you can't read Spanish, that the system couldn't get the file right because the size is different than expected)

Several other programs also need libmad0 to be installed, so I finally downloaded it manually from the Debian web page, but I couldn't install it because my libc6 was not up to date. Again, I downloaded the last version of libc6 from the Debian web page, but I couldn't install it either. The error message I got was this one:

 dpkg -i libc6_2.3.5-4_i386.deb
dpkg: acerca de libc6_2.3.5-4_i386.deb que contiene libc6:
 libc6 hace conflicto con initrd-tools (<< 0.1.79)
  initrd-tools (versión 0.1.77ubuntu3) es instalado.
dpkg: error al procesar libc6_2.3.5-4_i386.deb (--install):
 paquetes en conflicto - no se instalará libc6
Se encontraron errores al procesar:
 libc6_2.3.5-4_i386.deb

Which means that libc6 cannot be installed because it will cause conflict with initrd-tools.

I feel I am too much a newby to solve this problem, so I finally decided to post this message. Can anybode tell me what is wrong (or what I am doing wrong) and help me solve this problem (so that I can finally install VLC and watch my DVDs!!)? Thanks a lot  :)

---

