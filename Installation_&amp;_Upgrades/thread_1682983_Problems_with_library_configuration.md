---
title: "Problems with library configuration"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by E. A. on 2011-02-06
I'm having trouble with my Ubuntu 10.4 LTS system. Every time I try to install a new package or run apt-get upgrade I get a number of errors. There must be something wrong with some package but I'm not experienced enough to identify what the problem is. 
This is the output from the last time I ran apt-get upgrade (in spanish; I could attempt a translation if needed):
```

emilio@poderosa:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
21 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? 
Configurando libutempter0 (1.1.5-2) ...
Creating utempter group...
groupadd: no se puede bloquear /etc/gshadow; inténtelo más tarde.
addgroup: `/usr/sbin/groupadd -g 127 utempter' devolvió el código de error 10. Saliendo.
chown: grupo inválido: «root:utempter»
dpkg: error al procesar libutempter0 (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de libkpty4:
 libkpty4 depende de libutempter0; sin embargo:
 El paquete `libutempter0' no está configurado todavía.
dpkg: error al procesar libkpty4 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libkdesu5:
 libkdesu5 depende de libkpty4 (= 4:4.5.3-0ubuntu1~lucid1~ppa1); sin embargo:
 El paquete `libkpty4' no está configurado todavía.
dpkg: error al procesar libkdesu5 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdebase-runtime:
 kdebase-runtime depende de libkdesu5 (>= 4:4.5); sin embargo:
 El paquete `libkdesu5' no está configurado todavía.
 kdebase-runtime depende de libkpty4 (>= 4:4.5); sin embargo:
 El paquete `libkpty4' no está configurado todavía.
dpkg: error al procesar kdebase-runtime (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                                                                                                                   No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                                                                                                     No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                              No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
       No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                           No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                    No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                                                        No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                 No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
          No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                              No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                       No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                                                           problemas de dependencias impiden la configuración de amarok:
 amarok depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
dpkg: error al procesar amarok (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de libkde3support4:
 libkde3support4 depende de libkpty4 (= 4:4.5.3-0ubuntu1~lucid1~ppa1); sin embargo:
 El paquete `libkpty4' no está configurado todavía.
dpkg: error al procesar libkde3support4 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdelibs5:
 kdelibs5 depende de libkde3support4 (= 4:4.5.3-0ubuntu1~lucid1~ppa1); sin embargo:
 El paquete `libkde3support4' no está configurado todavía.
 kdelibs5 depende de libkdesu5 (= 4:4.5.3-0ubuntu1~lucid1~ppa1); sin embargo:
 El paquete `libkdesu5' no está configurado todavía.
 kdelibs5 depende de libkpty4 (= 4:4.5.3-0ubuntu1~lucid1~ppa1); siNo se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
           No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                               No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                        No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                                                            No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                     n embargo:
 El paquete `libkpty4' no está configurado todavía.
dpkg: error al procesar kdelibs5 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdepim-runtime:
 kdepim-runtime depende de kdebase-runtime (>= 4:4.4.5); sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 kdepim-runtime depende de kdelibs5 (>= 4:4.4.5); sin embargo:
 El paquete `kdelibs5' no está configurado todavía.
dpkg: error al procesar kdepim-runtime (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python-kde4:
 python-kde4 depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 python-kde4 depende de kdepim-runtime; sin embargo:
 El paquete `kdepim-runtime' no está configurado todavía.
 python-kde4 depende de libkpty4 (>= 4:4.5); sin embargo:
 El paquete `libkpty4' no está configurado todavía.
dpkg: error al procesar python-kde4 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdesudo:
 kdesudo depende de kdebase-runtime (>= 4:4.3.95); sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 kdesudo depende de kdelibs5 (>= 4:4.3.95); sin embargo:
 El paquete `kdelibs5' no está configurado todavía.
dpkg: error al procesar kdesudo (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gdebi-kde:
 gdebi-kde depende de python-kde4 (>= 3.16.0-0ubuntu11); sin embargo:
 El paquete `python-kde4' no está configurado todavía.
 gdebi-kde depende de kdesudo; sin embargo:
 El paquete `kdesudo' no está configurado todavía.
dpkg: error al procesar gdebi-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de install-package:
 install-package depende de gdebi-kde; sin embargo:
 El paquete `gdebi-kde' no está configurado todavía.
dpkg: error al procesar install-package (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdebase-bin:
 kdebase-bin depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
dpkg: error al procesar kdebase-bin (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
dpkg: error al procesar kdemultimedia-kio-plugins (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kmines:
 kmines depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
dpkg: error al procesar kmines (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de polkit-kde-1:
 polkit-kde-1 depende de kdebase-runtime (>= 4:4.4.2); sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 polkit-kde-1 depende de kdelibs5 (>= 4:4.4.2); sin embargo:
 El paquete `kdelibs5' no está configurado todavía.
dpkg: error al procesar polkit-kde-1 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-properties-kde:
 software-properties-kde depende de python-kde4; sin embargo:
 El paquete `python-kde4' no está configurado todavía.
 software-properties-kde depende de install-package; sin embargo:
 El paquete `install-package' no está configurado todavía.
dpkg: error al procesar software-properties-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager-kde:
 update-manager-kde depende de python-kde4; sin embargo:
 El paquete `python-kde4' no está configurado todavía.
 update-manager-kde depende de kdesudo; sin embargo:
 El paquete `kdesudo' no está configurado todavía.
dpkg: error al procesar update-manager-kde (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kpackagekit:
 kpackagekit depende de kdebase-runtime; sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 kpackagekit depende de polkit-kde-1; sin embargo:
 El paquete `polkit-kde-1' no está configurado todavía.
 kpackagekit depende de software-properties-kde; sin embargo:
 El paquete `software-properties-kde' no está configurado todavía.
 kpackagekit depende de update-manager-kde; sin embargo:
 El paquete `update-manager-kde' no está configurado todavía.
dpkg: error al procesar kpackagekit (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                    dpkg: problemas de dependencias impiden la configuración de kubuntu-debug-installer:
 kubuntu-debug-installer depende de kdebase-runtime (>= 4:4.4.2); sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 kubuntu-debug-installer depende de kdelibs5 (>= 4:4.4.2); sin embargo:
 El paquete `kdelibs5' no está configurado todavía.
 kubuntu-debug-installer depende de kpackagekit; sin embargo:
 El paquete `kpackagekit' no está configurado todavía.
dpkg: error al procesar kubuntu-debug-installer (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de kwave:
 kwave depende de kdebase-runtime (>= 4:4.3.95); sin embargo:
 El paquete `kdebase-runtime' no está configurado todavía.
 kwave depende de kdelibs5 (>= 4:4.4.0); sin embargo:
 El paquete `kdelibs5' no está configurado todavía.
dpkg: error al procesar kwave (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                                                                                    No se ha escrito ningún informe de Apport porque ya se alcanzado el nivel MaxReports
                             Se encontraron errores al procesar:
 libutempter0
 libkpty4
 libkdesu5
 kdebase-runtime
 amarok
 libkde3support4
 kdelibs5
 kdepim-runtime
 python-kde4
 kdesudo
 gdebi-kde
 install-package
 kdebase-bin
 kdemultimedia-kio-plugins
 kmines
 polkit-kde-1
 software-properties-kde
 update-manager-kde
 kpackagekit
 kubuntu-debug-installer
 kwave
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

