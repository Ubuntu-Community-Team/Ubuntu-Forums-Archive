---
title: "sudo aptitude upgrade"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by aguilarpia33 on 2020-05-30
Good morning every time I run the command
```
sudo aptitude upgrade
```
I get the following error.
I am using the latest version of ubuntu LTS.
Thank you

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Configurando gconf2-common (3.2.6-6ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error al procesar el paquete gconf2-common (--configure):
 el subproceso instalado paquete gconf2-common script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de gconf-service-backend:
 gconf-service-backend depende de gconf2-common (= 3.2.6-6ubuntu1); sin embargo:
 El paquete `gconf2-common' no está configurado todavía.


dpkg: error al procesar el paquete gconf-service-backend (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gconf-service:
 gconf-service depende de gconf-service-backend (= 3.2.6-6ubuntu1); sin embargo:
 El paquete `gconf-service-backend' no está configurado todavía.


dpkg: error al procesar el paquete gconf-service (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libgconf-2-4:amd64:
 libgconf-2-4:amd64 depende de gconf2-common (= 3.2.6-6ubuntu1); sin embargo:
 El paquete `gconf2-common' no está configurado todavía.


dpkg: error al procesar el paquete libgconf-2-4:amd64 (--configure):
 problemas de dependencias - No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                                        No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                   No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                            No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                     se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gconf2:
 gconf2 depende de gconf-service; sin embargo:
 El paquete `gconf-service' no está configurado todavía.
 gconf2 depende de libgconf-2-4 (>= 3.2.6-6ubuntu1); sin embargo:
 El paquete `libgconf-2-4:amd64' no está configurado todavía.
 gconf2 depende de gconf-service-backend (= 3.2.6-6ubuntu1); sin embargo:
 El paquete `gconf-service-backend' no está configurado todavía.


dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 gconf2-common
 gconf-service-backend
 gconf-service
 libgconf-2-4:amd64
 gconf2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2020-05-30
you can only have one opened upgrading tool at once; you get that error due to some other opened upgrading tool like synaptic

Other packages dependencies errors could be due to non genuine sources used, so getting races/conflicts. So only use the LTS repos.

---

### Post by aguilarpia33 on 2020-05-30
Thank you very much because with your help I solved the problem.

---

### Post by aguilarpia33 on 2020-05-31
Please can you copy what repositories you use.
Thank you

---

