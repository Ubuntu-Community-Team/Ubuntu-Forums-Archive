---
title: "Ubuntu 12.04 installation ...."
date: 2021-08-14
forum: Installation &amp; Upgrades
---

### Post by raed1107 on 2021-08-14
[COLOR=#222222][FONT=Verdana]Good day


First of all an apology for my English, that my writing is not very good (and I dare to put it in English first and then in Spanish in case my doubt is better understood).


It's my first time posting something around here, I hope and get it right!


I have a problem (or I think I have it), a client asks me to install Ubuntu in its version 12.04, for reasons of compatibility in its programs, but the equipment that I am given on a very new (recent) equipment:


Part Number: 1R2J6LA
HP 280 G5 SFF Computer, Intel Core i5-10500 3.10GHz, 8GB, 1TB, Windows 10 Pro 64-bit
BIOS Manufacturer: AMI
BIOS revision: F.22


Going into BIOS settings, it doesn't show me the option from UEFI to Legacy.


Reading in various forums I see installation options with more recent Ubuntu versions (not necessarily the current one) but my client keeps telling me that it can only work currently with version 12.04, there will be some way to install with this version of Ubuntu (12.04 ), you don't need to keep Windows 10 as you don't need it.


I appreciate the support or guidance you can give me.
[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]

-------

Buen día


Primero que nada una disculpa por mi ingles, que no es muy bueno mi escritura (y me atrevo a colocarlo en Ingles primero y después en Español por si se entiende mejor mi duda).


Es mi primera vez que publico algo por aquí, espero y hacerlo bien!


Tengo un problema (o creo tenerlo), un cliente me pide que instale Ubuntu en su versión 12.04, por motivos de compatibilidades en sus programas, pero el equipo que me entrego en un equipo muy nuevo (reciente):


Numero de parte: 1R2J6LA
Computadora HP 280 G5 SFF, Intel Core i5-10500 3.10GHz, 8GB, 1TB, Windows 10 Pro 64-bit
Fabricante del BIOS: AMI
Revisión del BIOS: F.22


Entrando a configuración del BIOS, no me muestra la opción de UEFI a Legacy.


Leyendo en varios foros veo opciones de instalación con versiones de Ubuntu mas recientes (no necesariamente la actual) pero mi cliente me sigue comentando que solo puede trabajar actualmente con la versión 12.04, habrá alguna forma de hacer la instalación con esta versión de Ubuntu (12.04), no es necesario mantener Windows 10 ya que no lo necesita.


Agradezco el apoyo u orientación que me puedan brindar.

[/FONT][/COLOR]

---

### Post by mikewhatever on 2021-08-14
I very much doubt it possible or a good idea. 
12.04 has no support for recent hardware. It is alse EoL, and we do not support EoL releases here.
Explain to your client, that there are limits of what is workable and what is reasonable.

---

### Post by Impavidus on 2021-08-14
If the applications only work with Ubuntu 12.04, then the right solution is to change the applications &#8211; either replace or, if the client has the source code, port to a recent release of Ubuntu. But I'm sure you know that.

12.04 was the latest LTS release when Microsoft demanded a change to UEFI as they released Windows 8. I think 12.04, or at least the last point release, had some support for this stuff, but maybe not for everything. I remember people who wanted to dual boot had to resort to 12.10 for a while. I'm not sure on the situation for the later point releases of 12.04. Of course, it's all a long time ago.

Ubuntu 12.04 being unsupported also means it's unsupported by this forum.

Another option is to install 12.04 in a virtual machine.

---

### Post by raed1107 on 2021-08-14
[QUOTE = Impavidus; 14053523] Si las aplicaciones solo funcionan con Ubuntu 12.04, entonces la solución correcta es cambiar las aplicaciones, ya sea reemplazarlas o, si el cliente tiene el código fuente, migrar a una versión reciente de Ubuntu. Pero estoy seguro de que lo sabe. 

12.04 fue la última versión de LTS cuando Microsoft exigió un cambio a UEFI cuando lanzaron Windows 8. Creo que 12.04, o al menos la última versión, tenía algo de soporte para estas cosas, pero tal vez no para todo. Recuerdo que las personas que querían un arranque dual tuvieron que recurrir a 12.10 por un tiempo. No estoy seguro de la situación para las versiones posteriores de la versión 12.04. Por supuesto, todo fue hace mucho tiempo. 

Ubuntu 12.04 no es compatible también significa que este foro no lo admite. 

Otra opción es instalar 12.04 en una máquina virtual. [/ QUOTE]


El cliente lo sabe, el problema es que entra un tercero y es donde todo se detiene todo, por querer "acaparar mercado" sigue sin actualizar su sistema (intencionalmente).

En Resumen: 

1-Yo soy el proveedor de Equipos de Computo.
2-Mi cliente me compra los equipos, pero los manda a un tercero (para instalación de software especial)(segun el cliente)
3-El tercero en cuestión realiza la instalación de Ubuntu para instalar software "especial" para el uso que le da mi cliente...

En generación pasadas de Equipo de Computo no había problemas con la instalación pero con los equipos recientes ya no le quieren aceptar los equipos (a mi cliente), pero aquí entra otra cuestión, que el "tercero" tiene un alto stock de equipos de generaciones pasadas... Y estoy seguro que no va actualizar hasta que se agote su stock y tenga que hacerlo forzosamente.

Sobre que Ubuntu 12.4 no es admitido en este foro, les ofrezco una disculpa, es la primer vez que ingreso y aun no conozco bien donde va cada hilo....


Gracias por el apoyo!!!

---

### Post by GhX6GZMB on 2021-08-14
Why don't you get a second machine (there are always unused PCs around), install 20.04 and test your customer's application on that?
Then you have arguments and data to make a decision.

---

