---
title: "dpkg error after fsck"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by PauGNU on 2010-01-27
Hi all,

This morning I got up and when opened my computer the first message I got was about an error while mounting partitions. The only way to go on was to execute fsck on my ubuntu partition. There were a lot of errors fixed (at least a 0.91% of the filesystem).

Once I rebooted it seemed that all was back to normal again. But "docky" was missing on my desktop. When I tried to run it from the terminal, the system told me that there was not a "docky" package. Weird. So when I tried to install it again, I got this dpkg error:


> pau@xps-karmic64:~$ sudo apt-get install docky
[sudo] password for pau: 
S'està llegint la llista de paquets... Error!
E: No es pot analitzar el fitxer del paquet /var/lib/dpkg/status (1)
E: No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.


I looked up on the forums and found a perl script that would make a new status file. I tried moving the status-old to status, but it wouldn't work.

The script made a new status file and once I moved it to /var/lib/dpkg/status, apt-get update didn't return error messages anymore. But when I tried to install docky again, I got this error:
> pau@xps-karmic64:~$ sudo apt-get install docky
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet 
docky ja es troba en la versió més recent.
Potser voldreu executar `apt-get -f install' per a corregir-ho:
Els següents paquets tenen dependències sense satisfer:
  firefox-branding: Depèn: firefox (= 3.6+nobinonly-0ubuntu1~mfs~karmic1)
                    Entra en conflicte: firefox-3.5-branding (< 3.6~hg20100117r33523)
  linux-backports-modules-wireless-karmic-generic: Depèn: linux-backports-modules-2.6.31-14-generic però no serà instal·lat
E: Dependències insatisfetes. Intenteu 'apt-get -f install' sense paquets (o especifiqueu una solució).


So then I run apt-get -f install and...
> pkg: warning: files list file for package `chromium-browser' missing, assuming package has no files currently installed.
(S'està llegint la base de dades ... 70%dpkg: unrecoverable fatal error, aborting:
 el fitxer de la llista de fitxers del paquet «docky» conté un nom de fitxer buit
E: Sub-process /usr/bin/dpkg returned an error code (2)


As you can see, at the 70% it fails and return and "unrecoverable fatal error". And I don't know what to do now...

What can I do?.

Thanks!

---

### Post by PauGNU on 2010-01-27
Hi again,

To fix the problem I had to edit manually the status file and remove all packages that were in conflict. After that, everything worked fine!.

Thanks!

---

### Post by arubislander on 2010-01-27
Great job figuring it out. And I especially enjoyed reading the messages the system threw at you in Catalan :)

Maybe you could mark this thread as solved? Use the thread tools in the upper right.

---

