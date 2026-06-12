---
title: "can't update or install new package because of broken pipe"
date: 2024-04-25
forum: Installation &amp; Upgrades
---

### Post by antorca59 on 2024-04-25
hello, good morning
I tried to update my system but I get this message:
```
$sudo apt-get upgrade[sudo] contraseña para antonio: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt --fix-broken install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 linux-tools-6.5.0-27 : Depende: linux-tools-common pero no está instalado
E: Dependencias incumplidas. Intente «apt --fix-broken install» sin paquetes (o especifique una solución).

```
[COLOR=#000000]I read that maybe a package did not install properly. The only package I tried to install was "tlp" because my laptop is overheating. I decided to uninstall it but I get:
```
[/COLOR]$sudo apt-get remove tlpLeyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt --fix-broken install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 linux-tools-6.5.0-27 : Depende: linux-tools-common pero no va a instalarse
 tlp-rdw : Depende: tlp (= 1.6.1-2~mantic1) pero no va a instalarse
E: Dependencias incumplidas. Intente «apt --fix-broken install» sin paquetes (o especifique una solución).
[COLOR=#000000]
```
[/COLOR]I followed the suggestion but received:
 ```
$sudo apt --fix-broken installLeyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes adicionales:
  linux-tools-common
Se instalarán los siguientes paquetes NUEVOS:
  linux-tools-common
0 actualizados, 1 nuevos se instalarán, 0 para eliminar y 27 no actualizados.
2 no instalados del todo o eliminados.
Se necesita descargar 0 B/545 kB de archivos.
Se utilizarán 643 kB de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
(Leyendo la base de datos ... 355781 ficheros o directorios instalados actualmen
te.)
Preparando para desempaquetar .../linux-tools-common_6.5.0-28.29_all.deb ...
Desempaquetando linux-tools-common (6.5.0-28.29) ...
dpkg: error al procesar el archivo /var/cache/apt/archives/linux-tools-common_6.
5.0-28.29_all.deb (--unpack):
 intentando sobreescribir `/usr/bin/cpupower', que está también en el paquete li
nux-laptop-tools-common 6.5.0-1006.9
dpkg-deb: error: el subproceso copiado fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar:
 /var/cache/apt/archives/linux-tools-common_6.5.0-28.29_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Can you, please, help me?
Thanks

---

### Post by antorca59 on 2024-04-29
hi 
I was receiving the message:
```
dpkg-deb: error: el subproceso copiado fue terminado por la señal (Tubería rota)
Se encontraron errores al procesar: /var/cache/apt/archives/linux-tools-common_6.5.0-28.29_all.deb
```
I applied
```
sudo dpkg -i --force-all /var/cache/apt/archives/linux-tools-common_6.5.0-28.29_all.deb
sudo apt-get -f install

```
That made the trick!
I followed the solution:
[https://lists.debian.org/debian-user-spanish/2004/09/msg00724.html](https://lists.debian.org/debian-user-spanish/2004/09/msg00724.html)

---

