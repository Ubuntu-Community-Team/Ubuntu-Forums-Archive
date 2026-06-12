---
title: "Update con errores, no se puede correr"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by chalejto on 2013-11-26
Hola a todos, le cuento que tengo ubunut 12.04 64  en mi notebook, y desde que lo instalé,  al hacer update me salen algunos errores y lo peor de todo es que ahora quise instalar una aplicación y me rechazo e indicó que debía reparar primero estos problemas.
Traté de eliminarlos desde el sources.list, pero  no aparece ninguno de estos paquetes que me indican que están con problemas. Mi pregunta es si alguien sabe como arreglar los paquetes.
El error que me muestra el terminal son los siguientes:
```

Ign [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/main Sources    
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/universe Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/main amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/restricted amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/universe amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/multiverse amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/main Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/multiverse Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/restricted Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/universe Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/main amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/restricted amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/universe amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/main Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/restricted Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/universe Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/main amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/restricted amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/main Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/restricted Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe Translation-en_US
  Unable to connect to cl.archive.ubuntu.com:http:
Err [http://cl.archive.ubuntu.com](http://cl.archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to cl.archive.ubuntu.com:http:
W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://cl.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to cl.archive.ubuntu.com:80 (190.113.0.250). - connect (110: Connection timed out)


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US)  Unable to connect to cl.archive.ubuntu.com:http:


W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://cl.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to cl.archive.ubuntu.com:http:


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Saludos y gracias

---

### Post by heir4c on 2013-11-26
This is a English forum so try to write in English, ThanX.
Beside that: Use a other server to update and upgrade. This one is at the moment out of reach. I click on your links (the one in red) and it won't load.

---

### Post by chalejto on 2013-11-26
> **heir4c said:**
> This is a English forum so try to write in English, ThanX.
Beside that: Use a other server to update and upgrade. This one is at the moment out of reach. I click on your links (the one in red) and it won't load.

Thanks by your language advise. Related to my update problem, how can I change the server or better Can I delete my wrong packages?

Best regards

---

### Post by heir4c on 2013-11-27
Sorry for the late reply.

Go via the Dash (UbuntuLogo in the top left) and search for Software&Updates
Click on the icon to open it.
In the first Tab you see a button next to: "Download from"
There you can choose a other server. Click on the last option. ("other" or something like that, I have a Dutch version).
There you click on the button on the top right. He search than to find the best server. (connection and speed).
Then try to do again a update.
I hope it will help. 
If not, post it here.

---

### Post by heir4c on 2013-11-27
FYI: Use tags to include a long output from the terminal to post it here. (To long to scroll :) )
Use the # option above the text-field and put the text between the code tags:

[code]text here[/ code]

There is normal not a space between the / en code but than I can't show it to you.

---

### Post by chalejto on 2013-12-08
> **heir4c said:**
> FYI: Use tags to include a long output from the terminal to post it here. (To long to scroll :) )
Use the # option above the text-field and put the text between the code tags:

[code]text here[/ code]

There is normal not a space between the / en code but than I can't show it to you.


Thanks, yor information worked perfectly.

---

