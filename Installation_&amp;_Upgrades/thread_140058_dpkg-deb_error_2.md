---
title: "dpkg-deb error 2"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by Goldstein on 2006-03-05
Hi to everyone, and sorry for my bad english...

After a checkdisk, i can't upgrade or update. This is the error message when i use apt-get or aptitude:
> dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/amule_2.0.3-1ubuntu4_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/amule-utils_2.0.3-1ubuntu4_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
Se encontraron errores al procesar:
 /var/cache/apt/archives/amule_2.0.3-1ubuntu4_i386.deb
 /var/cache/apt/archives/amule-utils_2.0.3-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I guess this is because i don't "unmount mount-ro" in the  scandisk process, but now i don't know how to fix the problem.
Anticipated thanks for the help.

---

### Post by Xian on 2006-03-05
Try removing those two debs in the apt cache and repeat the process.
Appears to be having trouble just properly handling the files.

```

$ sudo rm -f /var/cache/apt/archives/amule_2.0.3-1ubuntu4_i386.deb
$ sudo rm -f /var/cache/apt/archives/amule-utils_2.0.3-1ubuntu4_i386.deb
```

---

### Post by Goldstein on 2006-03-05
Thanks, Xian, but no way. I think it is a more general problem. I can't install, update or upgrade nothing from the repos. Amule is only a example, but the error returned is the same in any use of dpkg, apt-get or aptitude. 
But i keep trying...

---

### Post by Xian on 2006-03-05
Give the output of this command:

$ sudo apt-get -f install

---

### Post by Goldstein on 2006-03-05
[QUOTE=Xian]Give the output of this command:

$ sudo apt-get -f install[/QUOTE]


nenon@Palantir:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 25 no actualizados.
nenon@Palantir:~$

---

### Post by Goldstein on 2006-03-05
And no install/update/upgrade, and the same error i posted before

---

### Post by Xian on 2006-03-05
Okay, what is the output of the dist-upgrade command??

$ sudo apt-get dist-upgrade

---

### Post by Goldstein on 2006-03-05
[QUOTE=Xian]Okay, what is the output of the dist-upgrade command??

$ sudo apt-get dist-upgrade[/QUOTE]

OK, but i have 23 updates pending...:???: 

[I]nenon@Palantir:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Calculando la actualización... Listo
Se instalarán los siguientes paquetes NUEVOS:
  libenchant1c2 python-wxgtk2.6
Se actualizarán los siguientes paquetes:
  bittornado bittornado-gui eog evms evms-ncurses gthumb irssi-text k3b
  k3blibs libevms-2.5 libpq4 libtotem-plparser0 lilypond lilypond-data
  mozilla-mplayer pmount rhythmbox screem serpentine totem totem-gstreamer
  ubuntu-docs xchat xchat-common xmms-coverviewer
25 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 24,9MB de archivos.
Se utilizarán 16,8MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main irssi-text 0.8.9+0.8.10rc5-0ubuntu4.1 [852kB]
Des:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main libevms-2.5 2.5.3-7ubuntu1~breezy1 [734kB]
Des:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libenchant1c2 1.1.6-1 [69,7kB]
Des:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main ubuntu-docs 5.10-6.3 [2366kB]
Des:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main evms 2.5.3-7ubuntu1~breezy1 [88,0kB]
Des:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main evms-ncurses 2.5.3-7ubuntu1~breezy1 [88,2kB]
Des:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main bittornado 0.3.13-1ubuntu1~breezy1 [155kB]
Des:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe python-wxgtk2.6 2.6.1.1.1ubuntu2 [2642kB]
Des:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe bittornado-gui 0.3.13-1ubuntu1~breezy1 [40,8kB]
Des:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main eog 2.13.2-0ubuntu1~breezy1 [495kB]
Des:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main gthumb 3:2.7.1-0ubuntu1~breezy1 [1146kB]
Des:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main k3blibs 0.12.7-1ubuntu1~breezy1 [892kB]
Des:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main k3b 0.12.7-1ubuntu1~breezy1 [3750kB]
Des:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main libpq4 8.1.2-1~breezy1 [187kB]
Des:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main libtotem-plparser0 1.2.1-0ubuntu1~breezy1 [24,9kB]
Des:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe lilypond 2.6.3-9~breezy1 [1129kB]
Des:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe lilypond-data 2.6.3-9~breezy1 [4736kB]
Des:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse mozilla-mplayer 3.17-1ubuntu1~breezy1 [431kB]
Des:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main pmount 0.9.6-1~breezy1 [36,5kB]
Des:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main rhythmbox 0.9.1-1ubuntu3~breezy1 [1614kB]
Des:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main screem 0.16.0-0ubuntu1~breezy1 [2100kB]
Des:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main serpentine 0.6.4-0ubuntu1~breezy1 [66,3kB]
Des:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main totem 1.2.1-0ubuntu1~breezy1 [10,1kB]
Des:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main totem-gstreamer 1.2.1-0ubuntu1~breezy1 [802kB]
Des:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main xchat 2.6.0-0ubuntu1~breezy1 [254kB]
Des:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main xchat-common 2.6.0-0ubuntu1~breezy1 [68,8kB]
Des:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe xmms-coverviewer 0.11-5~breezy1 [85,7kB]
Descargados 24,9MB en 5m25s (76,4kB/s)

Preconfigurando paquetes ...
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/libevms-2.5_2.5.3-7ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/evms_2.5.3-7ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/evms-ncurses_2.5.3-7ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/bittornado_0.3.13-1ubuntu1~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/python-wxgtk2.6_2.6.1.1.1ubuntu2_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/bittornado-gui_0.3.13-1ubuntu1~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/eog_2.13.2-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/gthumb_3%3a2.7.1-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/irssi-text_0.8.9+0.8.10rc5-0ubuntu4.1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/k3blibs_0.12.7-1ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/k3b_0.12.7-1ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/libenchant1c2_1.1.6-1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/libpq4_8.1.2-1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/libtotem-plparser0_1.2.1-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/mozilla-mplayer_3.17-1ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/pmount_0.9.6-1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/rhythmbox_0.9.1-1ubuntu3~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/screem_0.16.0-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/serpentine_0.6.4-0ubuntu1~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/totem_1.2.1-0ubuntu1~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/totem-gstreamer_1.2.1-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/ubuntu-docs_5.10-6.3_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/xchat_2.6.0-0ubuntu1~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/xchat-common_2.6.0-0ubuntu1~breezy1_all.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
dpkg-deb: el subproceso tar fue terminado por la señal (Violación de segmento)
dpkg: error al procesar /var/cache/apt/archives/xmms-coverviewer_0.11-5~breezy1_i386.deb (--unpack):
 el subproceso dpkg-deb --control devolvió el código de salida de error 2
Se encontraron errores al procesar:
 /var/cache/apt/archives/libevms-2.5_2.5.3-7ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/evms_2.5.3-7ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/evms-ncurses_2.5.3-7ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/bittornado_0.3.13-1ubuntu1~breezy1_all.deb
 /var/cache/apt/archives/python-wxgtk2.6_2.6.1.1.1ubuntu2_i386.deb
 /var/cache/apt/archives/bittornado-gui_0.3.13-1ubuntu1~breezy1_all.deb
 /var/cache/apt/archives/eog_2.13.2-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/gthumb_3%3a2.7.1-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/irssi-text_0.8.9+0.8.10rc5-0ubuntu4.1_i386.deb
 /var/cache/apt/archives/k3blibs_0.12.7-1ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/k3b_0.12.7-1ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/libenchant1c2_1.1.6-1_i386.deb
 /var/cache/apt/archives/libpq4_8.1.2-1~breezy1_i386.deb
 /var/cache/apt/archives/libtotem-plparser0_1.2.1-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
 /var/cache/apt/archives/mozilla-mplayer_3.17-1ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/pmount_0.9.6-1~breezy1_i386.deb
 /var/cache/apt/archives/rhythmbox_0.9.1-1ubuntu3~breezy1_i386.deb
 /var/cache/apt/archives/screem_0.16.0-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/serpentine_0.6.4-0ubuntu1~breezy1_all.deb
 /var/cache/apt/archives/totem_1.2.1-0ubuntu1~breezy1_all.deb
 /var/cache/apt/archives/totem-gstreamer_1.2.1-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/ubuntu-docs_5.10-6.3_all.deb
 /var/cache/apt/archives/xchat_2.6.0-0ubuntu1~breezy1_i386.deb
 /var/cache/apt/archives/xchat-common_2.6.0-0ubuntu1~breezy1_all.deb
 /var/cache/apt/archives/xmms-coverviewer_0.11-5~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

...as usual...

---

