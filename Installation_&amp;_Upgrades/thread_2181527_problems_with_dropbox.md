---
title: "problems with dropbox"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by 4dr14n on 2013-10-18
Good morning!,

I was trying to install dropbox some minutes ago 
```
 sudo apt-get install dropbox
```

but this is what appeared (I put it in Spanish, but I translate it aswell).

```
Leyendo lista de paquetes... HechoCreando árbol de dependencias       
Leyendo la información de estado... Hecho
*El paquete dropbox no está disponible, pero algún otro paquete hace referencia*
*a él. Esto puede significar que el paquete falta, está obsoleto o sólo se*
*encuentra disponible desde alguna otra fuente*


E: El paquete «dropbox» no tiene un candidato para la instalación



```
The packet, dropbox is not avalaible, but some other packet refers to it. This can mean that the packet it missing, it is obsolete o it is just avalaible from other source


could some one tell me something about?

Thanks a lot!

---

### Post by Toz on 2013-10-18
Which version of Ubuntu are you using?

Dropbox is not in the repositories. You need to download the correct .deb file from [https://www.dropbox.com/install?os=lnx]("https://www.dropbox.com/install?os=lnx") (Ubuntu 32 or 64 bit) and install it via:
```
sudo dpkg -i dropbox_1.6.0_amd64.deb
```
...or for 32-bit:
```
sudo dpkg -i dropbox_1.6.0_i386.deb
```

If you're using nautilus as your file manager, you can also install "nautilus-dropbox" for dropbox integration into the file manager.

---

### Post by 4dr14n on 2013-10-18
Thanks Toz, actually from the webpage it worked perfectly.

---

