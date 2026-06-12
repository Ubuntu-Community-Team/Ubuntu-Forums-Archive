---
title: "software database damaged after today's upgrade"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ViperScull on 2010-03-11
I did the daily aptitude safe-upgrade, and it got stuck when it was trying to unpack the package **foomatic-db**. After a while (like 4 minutes), i pressed Ctrl+c so that i could recover dpkg, and it finished configuring the packages updated so far.

well, i tried the safe-upgrade again for the rest of the packages, but same happened again.
Then i tried apitude hold, but it did not work. Said there was no foomatic-db package at all.

I thought there could be a problem with the dependencies, and i removed foomatic-db-engine ir order to reinstall it. 

Now, i can't install, reinstall, remove anything.

I've deleted */var/lib/dpkg/info/foomatic-db.list* and */var/cache/apt/archives/foomatic-db_20100216-0ubuntu2_all.deb *
just in case something was wrong.

The error i got in console:
> E: No se pudo localizar un archivo para el paquete foomatic-db. Esto puede significar que necesita arreglar manualmente este paquete.
Escribiendo información de estado extendido... Hecho
E: No se pudo localizar un archivo para el paquete foomatic-db. Esto puede significar que necesita arreglar manualmente este paquete.
E: Error interno: no se pudo generar la lista de paquetes a descargar

My translation would be something like this:
> E: can't locate foomatic-db package. This could mean you need to fix it manually
E: Internal error: package list to download could not be generated.

I tried to change the idiom to english, but when i try, a window pops up saying that the software database is damaged, and tell me to try apt-get install -f.

Doing that, i get stuck unpacking foomatic-db.

Edit: Well, now after 3 minutes, foomatic-db was unpacked, and the dependencies solved. Everything is back to normal. But all the unpackings are being very slow.

---

