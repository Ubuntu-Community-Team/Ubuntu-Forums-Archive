---
title: "Ubuntu 18.04 E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by hectoresqui on 2018-11-10
sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
11 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando libnma0:amd64 (1.8.10-2ubuntu1) ...
dpkg: error al procesar el paquete libnma0:amd64 (--configure):
 fgets dió una cadena vacía de `/var/lib/dpkg/info/libnma0:amd64.triggers'
Configurando language-selector-gnome (0.188.1) ...
Sorry: ValueError: source code string cannot contain null bytes
  File "/usr/lib/python3/dist-packages/LanguageSelector/gtk/__init__.py", line 1
    &#65533;PN
      ^
SyntaxError: invalid character in identifier


dpkg: error al procesar el paquete language-selector-gnome (--configure):
 instalado language-selector-gnome paquete post-installation guión el subproceso devolvió un error con estado de salida 1
dpkg: problemas de dependencias impiden la configuración de network-manager-pptp-gnome:
 network-manager-pptp-gnome depende de libnma0 (>= 1.1.90); sin embargo:
 El paquete `libnma0:amd64' no está configurado todavía.


dpkg: error al procesar el paquete network-manager-pptp-gnome (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de network-manager-gnome:
 network-manager-gnome depende de libnma0 (= 1.8.10-2ubuntu1); sin embargo:
 El paquete `libnma0:amd64' no está configurado todavía.


dpkg: error al procesar el paquete network-manager-gnome (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-control-center:
 gnome-control-center depende de libnma0 (>= 1.1.90); sin embargo:
 El paquete `libnma0:amd64' no está configurado todavía.
 gnome-control-center depende de language-selector-gnome (>= 0.179~); sin embargo:
 El paquete `languageNo se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                                                No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                                                                         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
  No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
           -selector-gnome' no está configurado todavía.
 gnome-control-center depende de network-manager-gnome (>= 0.9.8); sin embargo:
 El paquete `network-manager-gnome' no está configurado todavía.


dpkg: error al procesar el paquete gnome-control-center (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                  dpkg: problemas de dependencias impiden la configuración de gir1.2-nma-1.0:amd64:
 gir1.2-nma-1.0:amd64 depende de libnma0 (>= 1.8.0); sin embargo:
 El paquete `libnma0:amd64' no está configurado todavía.


dpkg: error al procesar el paquete gir1.2-nma-1.0:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-desktop:
 ubuntu-desktop depende de gnome-control-center; sin embargo:
 El paquete `gnome-control-center' no está configurado todavía.
 ubuntu-desktop depende de language-selector-gnome; sin embargo:
 El paquete `language-selector-gnome' no está configurado todavía.


dpkg: error al procesar el paquete ubuntu-desktop (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-initial-setup:
 gnome-initial-setup depende de libnma0 (>= 1.1.90); sin embargo:
 El paquete `libnma0:amd64' no está configurado todavía.


dpkg: errNo se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
                  or al procesar el paquete gnome-initial-setup (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-shell:
 gnome-shell depende de gir1.2-nma-1.0; sin embargo:
 El paquete `gir1.2-nma-1.0:amd64' no está configurado todavía.


dpkg: error al procesar el paquete gnome-shell (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-session:
 ubuntu-session depende de gnome-shell (>= 3.24.3-0ubuntu2); sin embargo:
 El paquete `gnome-shell' no está configurado todavía.


dpkg: error al procesar el paquete ubuntu-session (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         dpkg: problemas de dependencias impiden la configuración de gdm3:
 gdm3 depende de gnome-shell (>= 3.19.92); sin embargo:
 El paquete `gnome-shell' no está configurado todavía.


dpkg: error al procesar el paquete gdm3 (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
         Se encontraron errores al procesar:
 libnma0:amd64
 language-selector-gnome
 network-manager-pptp-gnome
 network-manager-gnome
 gnome-control-center
 gir1.2-nma-1.0:amd64
 ubuntu-desktop
 gnome-initial-setup
 gnome-shell
 ubuntu-session
 gdm3
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

