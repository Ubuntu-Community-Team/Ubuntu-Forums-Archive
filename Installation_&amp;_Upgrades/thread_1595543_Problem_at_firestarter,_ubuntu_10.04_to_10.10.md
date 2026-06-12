---
title: "Problem at firestarter, ubuntu 10.04 to 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by payperme on 2010-10-13
Hi, i did the upgrade to ubuntu 10.10, all works fine except this i have some problem with Firestarter and somo conecction with a library, this is the log in console:

root@buddha:/home/payperme# apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Configurando firestarter (1.0.3-8ubuntu1) ...
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted
dpkg: error al procesar firestarter (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 134
Se encontraron errores al procesar:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)

i just read some of this bugs, but anyone has resolution to this fail, some has the same problem? Let me know maybe we can fix this! Thanks

---

### Post by payperme on 2010-10-13
I solved this, i did some schema like Debian with root user only for administration but its not the same, i fix it with:

sudo apt-get update
sudo apt-get upgrade

Thanks to his thread [http://forum.ubuntu.ru/index.php?topic=117901.0](http://forum.ubuntu.ru/index.php?topic=117901.0)

:), thanks!

---

