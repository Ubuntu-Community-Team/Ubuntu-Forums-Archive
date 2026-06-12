---
title: "apt-get behind a proxy"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by Haydel on 2006-04-19
Hi,

I'm trying to install kubuntu-desktop using apt-get.

I have configured the proxy variable in apt.conf.

When I run (sudo apt-get update), this is what I get:

[INDENT]Des:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Descargados 1B en 5s (0B/s)
Leyendo lista de paquetes... Hecho[/INDENT]

It looks fine, it says Done in spanish.

But when I run the command (sudo apt-get install kubuntu-desktop) this is what I get:

[INDENT]Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete kubuntu-desktop
[/INDENT]
It says Done to reading Packages and creating dependencies tree.
But then it says that the kubuntu-desktop pakage couldnt be found.

Any idea on how can I solve this problem?

Thanks in advance.

---

### Post by fdoving on 2006-04-19
Check your /etc/apt/sources.list
Make sure the main archive is enabled.

- Frode

---

### Post by Haydel on 2006-04-21
Thanks fdoving, that was it.

Now I have Kubuntu runing.

Thanks again.

---

