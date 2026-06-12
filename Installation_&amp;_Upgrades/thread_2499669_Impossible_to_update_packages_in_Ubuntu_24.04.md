---
title: "Impossible to update packages in Ubuntu 24.04"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by apgp on 2024-08-06
Hello. After installing Ubuntu 24.04 I cannot update packages. When I try with apt it returns:
dpkg: error processing package linux-image-5.15.0-117-generic (--remove):
 thread installed package linux-image-5.15.0-117-generic script post-remo
val returned error exit code 127
dpkg: too many errors, stopping
Errors found when processing:
 linux-image-5.15.0-117-generic
Process stopped due to too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
Help is appreciated

---

### Post by yancek on 2024-08-06
Is this a new install of Ubuntu 24.04 and the first attempt to update?  Post the exact command you ran.  I'm curious as to where this error comes in:  

>  error processing package linux-image-5.15.0-117-generic

as the default kernel on 24.04 should be 6.8?.

---

### Post by apgp on 2024-08-06
I updated from Ubuntu 22.04, with the command sudo apt update and then apt-upgrade

---

### Post by ActionParsnip on 2024-08-06
> **apgp said:**
> I updated from Ubuntu 22.04, with the command sudo apt update and then apt-upgrade

That won't change you to the next LTS. There is more to it than that. Did you by any chance, maually edit your sources to point to the newer release and _then _run those commands?

---

### Post by apgp on 2024-08-06
I do not think so. But I may have done it by trying to remove linux-image-5.15.0-117-generic

---

### Post by #&amp;thj^% on 2024-08-06
Will you please include this, it might give us a better clue:
```
sudo dpkg --configure -a
```
Paste that back here to see.

---

### Post by apgp on 2024-08-06
With that command it doesn't return anything

---

### Post by #&amp;thj^% on 2024-08-06
Alright then show this:
```
sudo apt update && sudo apt upgrade
```
Something just smells wrong here.

---

### Post by apgp on 2024-08-06
Obj:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease
Obj:2 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble InRelease                      
Obj:3 [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu) noble InRelease
Obj:4 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble-updates InRelease
Obj:5 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble-backports InRelease
Reading package list... Done
Creating dependency tree... Done
Reading status information... Done
3 packages can be upgraded. Run "apt list --upgradable" to see them.
W: [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease:](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease:) Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
E: Could not open lock file "/var/lib/dpkg/lock-frontend" - open (13: Permission denied)
E: Failed to obtain dpkg interface lock (/var/lib/dpkg/lock-frontend). Are you a superuser?

---

### Post by apgp on 2024-08-06
With apt list --upgradable 
libcurl3t64-gnutls/noble-updates,noble-security 8.5.0-2ubuntu10.2 amd64 [actualizable desde: 8.5.0-2ubuntu10.1]
libcurl4-gnutls-dev/noble-updates,noble-security 8.5.0-2ubuntu10.2 amd64 [actualizable desde: 8.5.0-2ubuntu10.1]
libcurl4t64/noble-updates,noble-security 8.5.0-2ubuntu10.2 amd64 [actualizable desde: 8.5.0-2ubuntu10.1]

---

### Post by #&amp;thj^% on 2024-08-06
:) just to be sure you copied and pasted those commands i gave right?
I ask because of this:
```
E: Could not open lock file "/var/lib/dpkg/lock-frontend" - open (13: Permission denied)
E: Failed to obtain dpkg interface lock (/var/lib/dpkg/lock-frontend). Are you a superuser? 
```
So was "sudo" used in those commands?

---

### Post by apgp on 2024-08-06
I have used sudo with those commands and this is the response.

---

### Post by #&amp;thj^% on 2024-08-06
Please try this:
```
sudo mv /var/lib/dpkg/lock-frontend /var/lib/dpkg/lock-frontend.bk
```
Now run this:
```
sudo apt update
```
Show me only the bottom command "sudo apt update"

---

### Post by apgp on 2024-08-06
Obj:1 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble InRelease
Obj:2 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble-updates InRelease              
Obj:3 [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) noble-backports InRelease            
Obj:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) noble-security InRelease               
Obj:5 [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu) noble InRelease
Leyendo lista de paquetes... Hecho                        
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Se pueden actualizar 3 paquetes. Ejecute «apt list --upgradable» para verlos.
W: [https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease:](https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease:) Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)

---

### Post by #&amp;thj^% on 2024-08-06
Ok now upgrade:
```
sudo apt upgrade
```
Post any errors back here please

---

### Post by apgp on 2024-08-07
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error al procesar el paquete linux-image-5.15.0-117-generic (--remove):
 el subproceso instalado paquete linux-image-5.15.0-117-generic script post-remo
val devolvió el código de salida de error 127
dpkg: demasiados errores, parando
Se encontraron errores al procesar:
 linux-image-5.15.0-117-generic
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2024-08-07
I thought so, **Grub Customizer**, That tool has caused so many problems for users.

Here is just one of the many posts here: [https://ubuntuforums.org/showthread.php?t=2198824](https://ubuntuforums.org/showthread.php?t=2198824)

Or another on AU :[https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken](https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken)

---

### Post by apgp on 2024-08-07
Already solved. The problem was in Grub Costumizer. Thank you so much.

---

### Post by #&amp;thj^% on 2024-08-07
Nice, and happy to help. :)

EDIT there is one thing we need to do is remove this "/var/lib/dpkg/lock-frontend.bk"
```
sudo rm -r /var/lib/dpkg/lock-frontend.bk
```

---

