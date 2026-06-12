---
title: "Can't upgrade to Lucid form Karmic"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by mi_di on 2010-06-15
I can't upgrade from Karmic to Lucid, I think it's some problem with the repositories but I don't know how to solve it.

If I try to use the update manager I get a message that says "Can't download release notes. Check your Internet connection". I've tried changing the repository and I get the same message, but I can log in to the Internet, and download and install any program from the repository. I also get regular updates for Karmic so the repository is fine.

I tried the command line

```

~$ sudo apt-get dist-upgrade 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```

It basically says that there are no packages for installing. So I tried the recommended process for the server edition, and I installed the update-manager-core.

For some reason I don't understand I get different results with and without sudo

```

~$ sudo do-release-upgrade 
Checking for a new ubuntu release
No new release found

```

```

~$ do-release-upgrade 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Eliminando la `/' inicial de los nombres

Leyendo caché

Comprobando el gestor de paquetes
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Actualizando la información del repositorio
WARNING: Failed to read mirror file
Done downloading            

Comprobando el gestor de paquetes
Reading package lists: Donem lucid/partner Packages: 94   Packages: 94  
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculando los cambios

Calculando los cambios

Algunas aplicaciones han dejado de tener soporte 

Canonical Ltd. ya no proporciona soporte para los siguientes 
paquetes. Puede conseguir soporte de la comunidad. 

Para quitar: 
atomix, bluetooth, compiz-fusion-plugins-extra, gnome-pilot, 
gnome-pilot-conduits, libdb4.6, libesd-alsa0, libgmime-2.0-2a, 
libgtkhtml2-0, libgtksourceview-common, libgtksourceview1.0-0, 
libnautilus-burn4, libpolkit-dbus2, libpolkit-grant2, libpolkit2, 
libscim8c2a, libsensors3, libtracker-gtk0, libtrackerclient0, 
libusplash0, libwv-1.2-3, mesa-utils, netcat-traditional, policykit, 
python-beagle, python-sexy, scim, scim-bridge-agent, 
scim-bridge-client-gtk, scim-gtk2-immodule, scim-modules-socket, 
sensord, sreadahead, tracker, tracker-search-tool, tracker-utils, 
tuxmath, untex, wv, xsane, xsane-common, xsplash 



¿Desea comenzar la actualización? 


Se van a desinstalar 34 paquetes. Se van a instalar 275 paquetes 
nuevos. Se van a actualizar 1623 paquetes. 

Debe descargar un total de 70.5M. Esta descarga tardará 8 minutos 
aproximadamente con una conexión DSL de 1Mbit y 2 horas 44 minutos 
aproximadamente con un módem de 56k. 

Descargar e instalar la actualización puede llevar varias horas. Una 
vez finalizada la descarga, el proceso no podrá cancelarse. 

 Continuar [sN]  Detalles [d]s

Descargando
Done downloading            
Done downloading            
Done downloading            

No se han podido descargar las actualizaciones 

Se ha cancelado la actualización. Compruebe su conexión a Internet 
o el soporte de la instalación y vuelva a intentarlo. Se 
conservarán todos los archivos descargados hasta ahora. 

Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/x264/libx264-85_0.85.1448+git1a6d32-4_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.2.2+debian-0ubuntu2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.14-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.18-1ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/d/dirac/libdirac-encoder0_1.0.2-2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/libseed0_2.28.1-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/seed_2.28.1-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/c/clutter-gtk-0.10/gir1.0-clutter-gtk-0.10_0.10.4-0ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/ttf-sazanami/ttf-sazanami-gothic_20040629-7ubuntu2_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/ttf-sazanami/ttf-sazanami-mincho_20040629-7ubuntu2_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xview/xviewg_3.2p1.4-25_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/v/vim/vim-gtk_7.2.330-1ubuntu3_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/speech-tools/libestools1.2_1.2.96~beta-6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.10-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-base0.10/gstreamer0.10-gnomevfs_0.10.28-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/system-config-printer/hal-cups-utils_1.2.0+20100408-0ubuntu5.2_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/scim/scim_1.4.9-2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/scim/scim-gtk2-immodule_1.4.9-2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/scim/scim-modules-socket_1.4.9-2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/scim/libscim8c2a_1.4.9-2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.10-1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/libtrackerclient0_0.6.95-1ubuntu6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/libtracker-gtk0_0.6.95-1ubuntu6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/u/usplash/libusplash0_0.5.51_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/w/wv/libwv-1.2-3_1.2.4-2ubuntu3_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/sexy-python/python-sexy_0.1.9-1ubuntu3_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/u/ureadahead/sreadahead_0.100.0-4.1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/stellarium/stellarium_0.10.4-0ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/s/stellarium/stellarium-data_0.10.4-0ubuntu1_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/totem/totem-gstreamer_2.30.2-0ubuntu1_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/tracker-search-tool_0.6.95-1ubuntu6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/tracker-utils_0.6.95-1ubuntu6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/tracker_0.6.95-1ubuntu6_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-gothic_20030809-6_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/ttf-kochi/ttf-kochi-mincho_20030809-6_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/ttf-sil-andika/ttf-sil-andika_1.0.basic-4_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tuxmath/tuxmath_1.7.2-1ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/ubuntu-xsplash-artwork_0.8.5-0ubuntu2_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/u/untex/untex_9210-11_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/u/usb-creator/usb-creator_0.2.22_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/w/wv/wv_1.2.4-2ubuntu3_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xfig/xfig_3.2.5.b-1ubuntu1_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xfig/xfig-libs_3.2.5.b-1ubuntu1_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane_0.996-2ubuntu3_i386.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane-common_0.996-2ubuntu3_all.deb 
404 Not Found 
Failed to fetch 
http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/xsplash_0.8.5-0ubuntu2_i386.deb 
404 Not Found 



Restaurando el estado original del sistema

Cancelando
Reading package lists: Donem karmic/partner Packages: 94   Packages: 94  
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

It seems to go farther without sudo but It has problems in getting the files. I'm not sure if this is a repository issue or if it's because I called the function without sudo permissions.

Finally my /etc/apt/sources.list file

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://astromirror.uchicago.edu/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://astromirror.uchicago.edu/ubuntu/ karmic universe
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://astromirror.uchicago.edu/ubuntu/ karmic multiverse
deb http://astromirror.uchicago.edu/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://astromirror.uchicago.edu/ubuntu/ karmic-security main restricted
deb http://astromirror.uchicago.edu/ubuntu/ karmic-security universe
deb http://astromirror.uchicago.edu/ubuntu/ karmic-security multiverse
# deb http://mirrors.ibiblio.org/pub/mirrors/CRAN/bin/linux/ubuntu jaunty/ # (desactivado en la actualización a karmic)

```

I hope someone can help, I'm sorry part of the messages are in spanish but they are pretty standard and I can translate if you have problems.

Thanks in advance!

---

### Post by dino99 on 2010-06-15
change "karmic" by "lucid" into the sources.list, then update and upgrade

---

### Post by mi_di on 2010-06-15
So when I change karmic for lucid in the sources list I get a lot of available upgrades but I receive a warning about some packages that can't be upgraded, and I'm asked if I want a partial upgrade.

Is this equivalent to a release upgrade?

---

### Post by mi_di on 2010-06-15
Well, I'm not sure what happened, but I received an update for a S.M.A.R.T package in Karmic and then I was able to upgrade from the update manager.

I would love to understand whatever was the problem but I'm happy just for being able to upgrade.

Thanks for your advise dino99!

---

