---
title: "Problem with grub 2 and UEFI"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by cronopio23 on 2013-04-11
Dear> I speak spanish, and i try to write this thread in english. Sorry my mistakes. 
I bought an ultrabook with windows 8 and UEFI boot. I format the disk with gparted and i install ubuntu 12.10 from usb-live. Its finish with out mistakes, but ubuntu don't boot.
Four days ago, i am reading about UEFI boot, and i try to use this solutions with out success.
- Install the grub UEFI from boot-repair, the result is in this web [http://paste.ubuntu.com/5697401/](http://paste.ubuntu.com/5697401/) HERE IS ALL THE INFORMATION.
- change the options from the bios and install ubuntu testing all combinations. There is only two options> usb legacy -enable - disable -
- also, i install another linux distributions, with our success.

I hope you can help me, i want to continue using linux.
Thanks very much. 

Then, the same explanation in spanish.
En resumen, lo que hice fue comprar una ultrabook  marca cx que viene con windows 8 preinstalado y el sistema de booteo  UEFI. Utilizando el gparted formate todo -los dos discos que trae- y a  partir de un usb live de ubuntu 12.10 instale esta distribuci[on, la  cual termino perfecta sin errores, pero al tratar de iniciar el sistema  no bootea. 
Hace cuatro d[ias que vengo leyendo en torno al sistema de booteo UEFI, probe varias soluciones que cito a continuaci[on-
-  Instalar el grub uefi desde boot-repair, el proceso arrojo el siguiente  resultado [http://paste.ubuntu.com/5697401/](http://paste.ubuntu.com/5697401/) DONDE ESTA TODA LA  INFORMACION.
- cambiar las opciones de la bios e instalar desde todas  las combinaciones. Aclaro que solo son dos opciones -usb legacy- enable  y disable.
- tambi[en probe instalar otras distribuciones sin exito.
Espero  que un usuario solidario y caritativo me pueda ayudar, desde mis  conocimientos no encuentro soluci[on, y la verdad que no quiero dejar de  usar linux por este problema. 
Muchas gracias.

---

### Post by oldfred on 2013-04-11
It looks like you overwrote Windows, was that your intent. Some have recovery modes, but those partitions are also gone. If you did not intend to overwrite Windows and did not do a full backup before hand, you need to contact vendor. Some only charge a shipping fee.

You have an UltraBook which adds complications to a complicated UEFI install. You have a small 32GB SSD that is for Intel SRT to cache Windows. Several users kept Windows, turned off Intel SRT, and installed Ubuntu's / (root) to the SSD and added a /home onto the rotating drive.

You also have dual video which adds video issues. Many use Bumblebee. Just yesterday nVidia released the first beta of a driver that supports dual video.

You should have in your UEFI/BIOS settings to turn secure boot off. You have Ubuntu installed in UEFI mode and should from UEFI menu be able to choose the ubuntu folder and boot the grub file. You still have Windows boot files in your efi partition and UEFI also remembers settins which you may have to manually erase.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


        nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

---

### Post by cronopio23 on 2013-04-12
SOLUCIONADO. 
Parece ser que el problema se soluciona haciendo una  instalación automática de Ubuntu 12.10. Por lo menos así fue como  funcionó después de varios intentos. Todas las otras instalaciones las  había hecho desde una configuración manual de las particiones. Aunque  por todo lo que leí el tema es bastante complejo, depende de cada bios.  Espero que sigan mejorando el desarrollo para contrarestar este ataque  de Microsoft.

---

