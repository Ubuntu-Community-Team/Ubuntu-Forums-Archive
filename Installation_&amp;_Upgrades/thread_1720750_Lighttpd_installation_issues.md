---
title: "Lighttpd installation issues"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2011-04-03
Hi to all.
I get an error message each time I try to install or "autoremove" software. Pls help.
Thanks.

First example: installing from terminal
```
sudo apt-get install krename 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  krename
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/293kB of archives.
After this operation, 1532kB of additional disk space will be used.
Selecting previously deselected package krename.
(Reading database ... 308153 files and directories currently installed.)
Unpacking krename (from .../krename_4.0.4-2ubuntu1_amd64.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up frontaccounting (2.2.8-1) ...
 * Reloading web server config apache2                                   [ OK ] 
Lighttpd not installed, skipping
invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.
ERROR 1045 (28000): Access denied for user 'mano'@'localhost' (using password: YES)
dpkg: error processing frontaccounting (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up krename (4.0.4-2ubuntu1) ...
Errors were encountered while processing:
 frontaccounting
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Second example: autoremove
```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up frontaccounting (2.2.8-1) ...
 * Reloading web server config apache2                                   [ OK ] 
Lighttpd not installed, skipping
invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.
ERROR 1045 (28000): Access denied for user 'mano'@'localhost' (using password: YES)
dpkg: error processing frontaccounting (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 frontaccounting
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Third example: installing from Ubuntu Sotware Centre

```
installArchives() failed: Selezionato il pacchetto libpodofo0.8.0.

(Lettura del database... 
(Lettura del database... 5%
(Lettura del database... 10%
(Lettura del database... 15%
(Lettura del database... 20%
(Lettura del database... 25%
(Lettura del database... 30%
(Lettura del database... 35%
(Lettura del database... 40%
(Lettura del database... 45%
(Lettura del database... 50%
(Lettura del database... 55%
(Lettura del database... 60%
(Lettura del database... 65%
(Lettura del database... 70%
(Lettura del database... 75%
(Lettura del database... 80%
(Lettura del database... 85%
(Lettura del database... 90%
(Lettura del database... 95%
(Lettura del database... 100%
(Lettura del database... 308148 file e directory attualmente installati.)

Estrazione di libpodofo0.8.0 (da .../libpodofo0.8.0_0.8.0+svn20100512-1_amd64.deb)...

Selezionato il pacchetto krename.

Estrazione di krename (da .../krename_4.0.4-2ubuntu1_amd64.deb)...

Elaborazione dei trigger per python-gmenu...

Rebuilding /usr/share/applications/desktop.it_IT.UTF8.cache...

Elaborazione dei trigger per desktop-file-utils...

Elaborazione dei trigger per hicolor-icon-theme...

Elaborazione dei trigger per python-support...

Configurazione di frontaccounting (2.2.8-1)...

 * Reloading web server config apache2

   ...done.

Lighttpd not installed, skipping

invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.

ERROR 1045 (28000): Access denied for user 'mano'@'localhost' (using password: YES)

dpkg: errore nell'elaborare frontaccounting (--configure):

 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1

Configurazione di libpodofo0.8.0 (0.8.0+svn20100512-1)...

Configurazione di krename (4.0.4-2ubuntu1)...

Elaborazione dei trigger per libc-bin...

ldconfig deferred processing now taking place

Si sono verificati degli errori nell'elaborazione:

 frontaccounting

Configurazione di frontaccounting (2.2.8-1)...

 * Reloading web server config apache2

   ...done.

Lighttpd not installed, skipping

invoke-rc.d: unknown initscript, /etc/init.d/lighttpd not found.

ERROR 1045 (28000): Access denied for user 'mano'@'localhost' (using password: YES)

dpkg: errore nell'elaborare frontaccounting (--configure):

 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1

dpkg: problemi con le dipendenze impediscono la configurazione di xsane2tess:

 xsane2tess dipende da tesseract; comunque:

  Il pacchetto tesseract non è installato.

dpkg: errore nell'elaborare xsane2tess (--configure):

 problemi con le dipendenze - lasciato non configurato

dpkg: problemi con le dipendenze impediscono la configurazione di cndrvcups-common:

 cndrvcups-common dipende da cupsys; comunque:

  Il pacchetto cupsys non è installato.

dpkg: errore nell'elaborare cndrvcups-common (--configure):

 problemi con le dipendenze - lasciato non configurato

Si sono verificati degli errori nell'elaborazione:

 frontaccounting

 xsane2tess

 cndrvcups-common


```

---

### Post by Dutch70 on 2011-04-03
Try running this...
```
sudo dpkg --configure -a
```

or this...
```
sudo apt-get -f install
```

Then see if you can install krename

---

### Post by manolomanolo on 2011-04-04
```
sudo dpkg --configure -a
[sudo] password for mano: 
Setting up frontaccounting (2.2.8-1) ...
 * Reloading web server config apache2                                   [ OK ] 
ln: creating symbolic link `/etc/lighttpd/conf-available/50-frontaccounting.conf': File exists
dpkg: error processing frontaccounting (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on cupsys; however:
  Package cupsys is not installed.
dpkg: error processing cndrvcups-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 frontaccounting
 xsane2tess
 cndrvcups-common

```

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up frontaccounting (2.2.8-1) ...
 * Reloading web server config apache2                                   [ OK ] 
ln: creating symbolic link `/etc/lighttpd/conf-available/50-frontaccounting.conf': File exists
dpkg: error processing frontaccounting (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 frontaccounting
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Dutch70 on 2011-04-04
Have you tried selecting a different mirror? 
Sorry, that's all I've got.

---

### Post by manolomanolo on 2011-04-04
After uninstalling frontaccounting i get this:

```
sudo dpkg --configure -a
[sudo] password for mano: 
dpkg: dependency problems prevent configuration of xsane2tess:
 xsane2tess depends on tesseract; however:
  Package tesseract is not installed.
dpkg: error processing xsane2tess (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on cupsys; however:
  Package cupsys is not installed.
dpkg: error processing cndrvcups-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xsane2tess
 cndrvcups-common
mano@mano-laptop:~$ whereis xane2tess
xane2tess:
mano@mano-laptop:~$ locate xane2tess
mano@mano-laptop:~$ sudo find / -iname xane2tess
mano@mano-laptop:~$ sudo apt-get remove xsane2tess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xsane2tess
mano@mano-laptop:~$ 
```

---

