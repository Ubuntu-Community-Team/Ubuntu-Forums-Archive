---
title: "I cannot update anything"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by georgeen on 2008-06-11
Hello folks:

Some weeks ago I was trying to update my portable ubuntu (Ubuntu Hardy 8.04 i386) but after downloading the new packages start to update sudo and the upgrade hangs (I wait for about 20 minutes) and my window manager too, so I must to reset my computer. After may days searching and trying I'm on the same position. I tried from synaptic, from terminal, cleaned  reboot (when I can), sometimes shows a segmentation fault error, etc.

Finally I decided to open this new thread and my most recent try, uninstall and reinstall sudo, because one of the solutions I found (but related of all kind of packages) was force uninstall and reinstall the problematic package, so I activate root and proceed.

This is the terminal output:

root@ubuntu:/home/ubuntu# apt-get install sudo
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libxalan110 libboost-thread1.34.1 libboost-date-time1.34.1 libxerces27
Utilice &#9516;½apt-get autoremove&#9516;&#9559; para eliminarlos.
Se actualizarán los siguientes paquetes:
  sudo
1 actualizados, 0 se instalarán, 0 para eliminar y 148 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 176kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Des:1 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) hardy-updates/main sudo 1.6.9p10-1ubuntu3.2 [176kB]
Descargados 176kB en 1s (131kB/s)
(Leyendo la base de datos ...  
102209 ficheros y directorios instalados actualmente.)
Preparando para reemplazar sudo 1.6.9p10-1ubuntu3 (usando .../sudo_1.6.9p10-1ubuntu3.2_i386.deb) ...
Desempaquetando el reemplazo de sudo ...
**E: Sub-process /usr/bin/dpkg received a segmentation fault.**
root@ubuntu:/home/ubuntu# apt-get remove sudo
**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. **
root@ubuntu:/home/ubuntu# dpkg --configure -a
root@ubuntu:/home/ubuntu# apt-get remove sudo
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libxalan110 libboost-thread1.34.1 libboost-date-time1.34.1 user-setup
  localechooser-data libxerces27
Utilice "apt-get autoremove" para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  apturl casper fast-user-switch-applet gdebi gdm gksu gnome-app-install
  gnome-netstatus-applet gparted hwtest-gtk lupin-casper network-manager-gnome
  software-properties-gtk sudo ubiquity ubiquity-casper ubiquity-frontend-gtk
  ubufox ubuntu-desktop ubuntu-minimal update-manager update-notifier
0 actualizados, 0 se instalarán, 22 para eliminar y 145 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 42,6MB después de desempaquetar.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  
102208 ficheros y directorios instalados actualmente.)
Desinstalando ubuntu-minimal ...
Desinstalando ubuntu-desktop ...
Desinstalando update-notifier ...
Desinstalando update-manager ...
Desinstalando software-properties-gtk ...
Desinstalando network-manager-gnome ...
Desinstalando hwtest-gtk ...
Desinstalando gparted ...
Desinstalando gnome-netstatus-applet ...
Desinstalando ubufox ...
Desinstalando apturl ...
Desinstalando gnome-app-install ...
Desinstalando fast-user-switch-applet ...
Desinstalando gdm ...
Desinstalando gdebi ...
Desinstalando gksu ...
Desinstalando lupin-casper ...
Desinstalando casper ...
Desinstalando ubiquity-frontend-gtk ...
Desinstalando ubiquity ...
Desinstalando ubiquity-casper ...
[B]dpkg: error al procesar sudo (--remove):
 El paquete está en un estado muy malo e inconsistente - debe reinstalarlo
 antes de intentar desinstalarlo.
Se encontraron errores al procesar:
 sudo
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
root@ubuntu:/home/ubuntu# apt-get clean
root@ubuntu:/home/ubuntu# apt-get check
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
root@ubuntu:/home/ubuntu# apt-get install sudo
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  libxalan110 libboost-thread1.34.1 libboost-date-time1.34.1 user-setup
  localechooser-data libxerces27
Utilice "apt-get autoremove" para eliminarlos.
Se actualizarán los siguientes paquetes:
  sudo
1 actualizados, 0 se instalarán, 0 para eliminar y 145 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 176kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Des:1 [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) hardy-updates/main sudo 1.6.9p10-1ubuntu3.2 [176kB]
Descargados 176kB en 1s (107kB/s)
Seleccionando el paquete sudo previamente no seleccionado.
(Leyendo la base de datos ...  
100847 ficheros y directorios instalados actualmente.)
Preparando para reemplazar sudo 1.6.9p10-1ubuntu3 (usando .../sudo_1.6.9p10-1ubuntu3.2_i386.deb) ...
**Desempaquetando el reemplazo de sudo ...**

*HERE THE APPLICATION HANGS*

English:
Again as in the very begining this was the original problem (even I've passed by E: Sub-process /usr/bin/dpkg received a segmentation fault as you saw) **the terminal hangs**. I have to reinstall my portable ubuntu?. After a painfully install I don't wanna do it again. Do you have some ideas or something?.

Spanish:
Estoy de nuevo como al comienzo, en el error original (incluso he pasado por E: Sub-process /usr/bin/dpkg received a segmentation fault como vieron) **se queda en el desempaquetamiento quieto**. Tengo que reinstalar mi ubuntu portatil?, la verdad no quisiera volver a pasar por el penoso proceso de reinstalarlo y luego no poder actualizarlo nuevamente. ¿Alguno de Uds. ya pasó por algo parecido y puede ayudarme?


Thanks in advance.


PD: 
English:
If someone need more information, please tell me how to obtain it I'm not an expert.

Spanish:
Si necesitan más información, por favor decirme como obtenerla ya que no soy muy experto.

---

### Post by Mark_in_Hollywood on 2008-06-11
I found something at another forum. I hope this helps.

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-642483/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-642483/)

---

### Post by georgeen on 2008-06-13
In fact the problem isn't the "returned error code (1)", the problem is that the process at final hangs, after all returned error is temporal, but I cannot overcome that hang that is the original problem.

---

### Post by avtolle on 2008-06-13
From what I see in your first post, it looks to me that the most efficient thing to do is to reinstall the operating system from scratch.

---

### Post by georgeen on 2008-06-15
Well, I don't know something about upgrades, because in pendrivelinux in [this link]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/") said that "Note: You wont be able to do system related upgrades. In order to do this, you'll need to do a Full Blown Ubuntu 8.04 USB install." so I suppose that when sudo is updated and it is part of the ubuntu system as other software, this is the problem, but I wanna know why it isn't possible if is a persistent installation.

So I have to format my casper-rw partition and update only software on top of the system like OOo or FF but no kernel updates or sudo.

Thanks for your time and cooperation.

---

