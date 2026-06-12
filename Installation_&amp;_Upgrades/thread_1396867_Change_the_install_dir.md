---
title: "Change the install dir"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Bietje on 2010-02-02
I've installed ubuntu (and windows xp & 7) on the smallest HD i have (160gb). And I only use is for those systems. All my programs and datais on a 500gb disk. I never had problems in windows installing programs there. But now, in ubuntu I don't get it.

I googled around a bit and found the dpkg program. I tried that with the --instdir= option. 
I cd-ed to the dir of the .deb i wanted to install and there i executed the following command: sudo dpkg -i --instdir=/media/DATA0 kmess_2.0.2-1_i386.deb

Then, the system returned an error:
```
(Database inlezen ... 138747 bestanden en mappen geïnstalleerd.)
Voorbereiden om kmess 2.0.2-1 te vervangen (door kmess_2.0.2-1_i386.deb) ...
Uitpakken van vervangende kmess ...
dpkg (subproces): kan verouderd post-removal script niet uitvoeren: No such file or directory
dpkg: waarschuwing: verouderd post-removal script geeft een fout terug met status 2
dpkg - script uit het nieuwe pakket wordt geprobeerd ...
dpkg (subproces): kan nieuw post-removal script niet uitvoeren: No such file or directory
dpkg: fout bij afhandelen van kmess_2.0.2-1_i386.deb (--install):
 subproces nieuw post-removal script gaf een foutwaarde 2 terug
dpkg (subproces): kan nieuw post-removal script niet uitvoeren: Bestand of map bestaat niet
dpkg: fout tijdens opruimen:
 subproces nieuw post-removal script gaf een foutwaarde 2 terug
Processing triggers for man-db ...
dpkg (subproces): kan installed post-installation script niet uitvoeren: Bestand of map bestaat niet
dpkg: subproces installed post-installation script gaf een foutwaarde 2 terug
```Yes its dutch, sorry for that I can't help that I'm born in the Netherlands. It says the following:

[LIST]
[*]cannot run old post-removal script: no such file/dir
[*]cannot run new post-removal script: no such file/dir
[*]cannot run post-istallation script: no such firle/dir
[*]it returned error value 2
[/LIST]
How can I fix this error?

Thanks in advance, Bietje

---

