---
title: "postfix uninstall"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by aurquiel on 2018-05-05
Hello i remove all the files of the postfix package, bot i having troubles with the apt every time i have been used

```
/var/lib/dpkg/info/postfix.postinst: línea 13: /usr/share/postfix/postinst.functions: No existe el archivo o el directorio
dpkg: error al procesar el paquete postfix (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Procesando disparadores para libc-bin (2.23-0ubuntu10) ...
Se encontraron errores al procesar:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ns3041266:~#

```

How i do if i want that the apt forget the postfix package were installed

---

### Post by TheFu on 2018-05-05
The package manager needs to be working perfectly.
Then
**sudo apt purge postfix**
If any of the files have been manually removed, then the easiest fix is to reinstall the package to put them back, then run the purge command.

Of course, the APT DB needs to be consistent for this to work.  The easiest way to get that is
```
sudo apt update
sudo apt upgrade  
```
and maybe reboot if libc or the kernel were updated.

After all of this, if any files are left in /etc/postfix, you can manually remove them AND any directories.

---

### Post by aurquiel on 2018-05-15
Neither purge or install worked this is the output

```
root@ns3041266:~# apt purge postfix
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete indicado a continuación se instaló de forma automática y ya no es necesario.
  procmail
Utilice «sudo apt autoremove» para eliminarlo.
Los siguientes paquetes se ELIMINARÁN:
  postfix*
0 actualizados, 0 nuevos se instalarán, 1 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se liberarán 3.697 kB después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 87522 ficheros o directorios instalados actualmente.)
Desinstalando postfix (3.1.0-3ubuntu0.3) ...
invoke-rc.d: unknown initscript, /etc/init.d/postfix not found.
dpkg: error al procesar el paquete postfix (--purge):
 el subproceso instalado el script pre-removal devolvió el código de salida de error 100
/var/lib/dpkg/info/postfix.postinst: línea 13: /usr/share/postfix/postinst.functions: No existe el archivo o el directorio
dpkg: error al reorganizar:
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
Procesando disparadores para libc-bin (2.23-0ubuntu10) ...
Se encontraron errores al procesar:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by TheFu on 2018-05-15
> If any of the files have been manually removed, then the easiest fix is to reinstall the package to put them back, then run the purge command.


Did you do that?  

It appears a number files that would be installed aren't there so the purge won't work. Do NOT manually remove files created/installed by the package manager.  Any files that are missing will cause a failure.

---

