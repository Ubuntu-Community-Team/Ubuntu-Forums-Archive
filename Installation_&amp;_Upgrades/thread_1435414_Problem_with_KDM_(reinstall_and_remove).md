---
title: "Problem with KDM (reinstall and remove)"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by joel_xd on 2010-03-21
Hi everyone.

the last week I had a problem with my kubuntu. I was working normally with my virtualbox when the screen turn black without wallpaper, toolbar, menu, I just could change the programs with "alt+tab". I think it was fixed with a restart but no.Until now, after restart the pc show me just a console and kdm don't start, I have ubuntu desktop too and if I want a graphic enviroment I need to do a "sudo gdm start" and it's works. I don't know what happen with my kdm I try to reinstall without succes, when I try to remove I get this message:

[B]joel@Joel-PC:~$ sudo apt-get remove kdm
[sudo] password for joel:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Los siguientes paquetes se ELIMINARÁN:
  kdm
0 actualizados, 0 se instalarán, 1 para eliminar y 9 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 4162kB después de esta operación.
¿Desea continuar [S/n]? S
(Leyendo la base de datos ...  00%
297692 ficheros y directorios instalados actualmente.)
Desinstalando kdm ...
dpkg (subproceso): no se puede ejecutar script pre-removal instalado: Error de formato ejecutable
dpkg: error al procesar kdm (--remove):
 el subproceso script pre-removal instalado devolvió el código de salida de error 2
dpkg (subproceso): no se puede ejecutar script post-installation instalado: Error de formato ejecutable
dpkg: error al reorganizar:
 el subproceso script post-installation instalado devolvió el código de salida de error 2
Se encontraron errores al procesar:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

I has investigate surfing on internet and I didn't find a solution. I just found something about a bug 486436 in this link [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1883118.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1883118.html) I think this is my problem but I'm not sure.. and whatever I didn't found a solution. Maybe someone had this  problem too and if someone know how repair it. It will be great. I'm waiting for coments, thanks.

Pd. I tried to force the remove but nothing..

---

