---
title: "[SOLVED] apt-get install -f problem ._."
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by axel89 on 2007-09-03
hey well i was just wondering if any1 could help me with this:


i wanted to install some other alsa lib so i tried the pkg in apt-get thing
but after a while i got this problem 
[PHP]axel@Linuca:~$ sudo apt-get install -f libasound2
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
libasound2 ya está en su versión más reciente.
Tal vez quiera ejecutar `apt-get -f install' para corregirlo:
Los siguientes paquetes tienen dependencias incumplidas:
  libasound2: Depende: libc6 (>= 2.5-5) pero 2.5-0ubuntu14 va a ser instalado
E: Dependencias incumplidas. Intente 'apt-get -f install' sin paquetes (o especifique una solución).[/PHP]

when i do the "sudo apt-get install -f "
it sais it will remove or something like that all of my software so idk what to do :S


tnx in advance

---

### Post by aysiu on 2007-09-03
If you have dependency problems, it could stem from conflicting repository sources.

Try [getting a fresh set of repositories](http://www.psychocats.net/ubuntu/sources) and then doing ```
sudo aptitude update
sudo aptitude install libasound2
```

---

### Post by axel89 on 2007-09-04
wow tnx so much it worked (: 

got so much to learn u_u

---

