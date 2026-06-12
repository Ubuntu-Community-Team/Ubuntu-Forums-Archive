---
title: "apt-get errors :( i dont know how to"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by x2l2 on 2006-08-07
when i try to make apt-get upgrade or dist-upgrade get this error :(
i dont know what is the package that try to install or errase 
how can i know? what can i do ?

```

$ sudo apt-get -V upgrade

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

1 no instalados del todo o eliminados.
(1 not installed or removed)

Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]?

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


```

---

### Post by BitTorrentBuddha on 2006-08-07
Could you post a vague translation with this?

---

### Post by x2l2 on 2006-08-07
er... ok...

$ sudo apt-get -V upgrade

Reading pakage list... ok
Making dependecy tree... ok
0 updated, 0 will be installed, 0 for delete y 0 not updated.
1 not completed installed or removed

Need download 0B of files 
will use 0B of disk space ....
¿continue [Y/n]?y 
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by tseliot on 2006-08-07
try with:
```
sudo apt-get install -f
```

---

### Post by x2l2 on 2006-08-07
> **tseliot said:**
> try with:
```
sudo apt-get install -f
```

i tryed but get same error 

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

