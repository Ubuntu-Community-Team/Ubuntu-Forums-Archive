---
title: "Problem with Karmic Server and slapd"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by carballinho on 2010-09-10
Good morning from Spain.

My english isn't native... so I hope that you can understand me.

I have an Ubuntu Karmic Server with Openldap installed and working propertly. I had no problems with it but, from several weeks ago, one error appeared.

When I start "apt-get upgrade" this appears (is in spanish):

root@ubuntuserver:~# apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando Ã¡rbol de dependencias
Leyendo la informaciÃ³n de estado... Hecho
0 actualizados, 0 se instalarÃ¡n, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarÃ¡n 0B de espacio de disco adicional despuÃ©s de esta operaciÃ³n.
Â¿Desea continuar [S/n]? s
Configurando slapd (2.4.18-0ubuntu1.1) ...
Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.4.18-0ubuntu1... done.
chown: invalid argument: `'
dpkg: error al procesar slapd (--configure):
el subproceso installed post-installation script devolviÃ³ el cÃ³digo de salida de error 1
Se encontraron errores al procesar:
slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

It seems that an update of slapd is wrong installed or something like this. The slapd server is working propertly, despite of this error.

I'm not an expert on linux...

Thank you in advance.

---

