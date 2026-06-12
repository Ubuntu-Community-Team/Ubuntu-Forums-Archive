---
title: "dpkg problem"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by jjsms on 2013-05-01
Hey guys.

i install some upgrades in ubuntu 12.10. Since the, I'm having this problem [http://ubuntuforums.org/showthread.php?t=1854573](http://ubuntuforums.org/showthread.php?t=1854573).

I try the sugestions in the thread, but when I use [COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a i get this error message:

(my ubuntu is in portuguse but i'll try to translate the best i can)

[/FONT][/COLOR]E: Falhou o download de alguns ficheiros de índice. Foram ignorados ou os antigos foram usados em seu lugar.
W: Não está a ser utilizado acesso exclusivo para apenas leitura ao ficheiro /var/lib/dpkg/lock
E: O dpkg foi interrompido, para corrigir o problema tem de correr manualmente 'sudo dpkg --configure -a' 

E: Failure to download some index files. The files was been ignored or the old files used in it place.
W: It is not been used the exclusive access to for read only file /var/lib/dpkg/lock
E: dpkg interrupted, to correct the problem you must run 'sudo dpkg --configure -a' manualy

when i run it, another error message appears in the console:

sudo: não foi possível abrir /var/lib/sudo/junior/1: Sistema de ficheiros apenas de leitura
dpkg: erro: não foi possível aceder à área de status do dpkg: Sistema de ficheiros apenas de leitura


Sudo: it was not been possible to open /var/lib/junior/1: Sistem files for read only.
dpkg: error: it is not possible to access dpkg status area: Sistem files for read only.

I'm totally lost... can someone help me?

---

### Post by ibjsb4 on 2013-05-01
Try this

```
sudo rm /var/lib/dpkg/lock
```

followed with

```
sudo dpkg --configure -a
```

Im not sure what the "read only" is all about.

---

### Post by jjsms on 2013-05-01
sudo: não foi possível abrir /var/lib/sudo/junior/1: Sistema de ficheiros apenas de leitura
rm: impossível remover «/var/lib/dpkg/lock»: Sistema de ficheiros apenas de leitura

Sudo: it was not been possible to open /var/lib/sudo/junior/1: read-only file system
rm: impossible to remove «/var/lib/dpkg/lock»: read-only file system

still the same thing...

---

### Post by jjsms on 2013-05-01
read-only file system :)

---

