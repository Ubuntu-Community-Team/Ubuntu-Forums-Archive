---
title: "Glibc relocation error after upgrade"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by nusch on 2010-06-25
I have problem I've run several updates:
```

Start-Date: 2010-06-19  18:04:17
Upgrade: poppler-utils (0.12.4-0ubuntu4, 0.12.4-0ubuntu5), libpoppler-qt4-3 (0.12.4-0ubuntu4, 0.12.4-0ubuntu5), libpoppler5 (0.12.4-0ubuntu4, 0.12.4-0ubuntu5), libpoppler-glib4 (0.12.4-0ubuntu4, 0.12.4-0ubuntu5), libgnomekbd4 (2.30.0-0ubuntu2, 2.30.1-0ubuntu1), libgnomekbd-common (2.30.0-0ubuntu2, 2.30.1-0ubuntu1)
End-Date: 2010-06-19  18:04:26

Start-Date: 2010-06-20  16:48:24
Install: phonon-dbg (4.6.2-0ubuntu5), amarok-dbg (2.3.0-0ubuntu4), phonon-backends-dbg (4.4.0-0ubuntu2)
End-Date: 2010-06-20  16:48:37

Start-Date: 2010-06-22  15:08:52
Upgrade: chromium-browser (5.0.375.38~r46659-0ubuntu0.10.04.1, 5.0.375.70~r48679-0ubuntu0.10.04.1)
End-Date: 2010-06-22  15:09:19

Start-Date: 2010-06-22  16:52:24
Upgrade: libcupsppdc1 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libcupsimage2 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libcupscgi1 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libcupsdriver1 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), cupsddk (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libtiff4-dev (3.9.2-2, 3.9.2-2ubuntu0.3), cups-client (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libtiffxx0c2 (3.9.2-2, 3.9.2-2ubuntu0.3), cups-ppdc (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), linux-image-2.6.32-22-generic-tuxonice (2.6.32-22.36~ppa2, 2.6.32-22.36~ppa5), tuxonice-userui (1.0.git20100407~ppa6~lucid1, 1.0.git20100407~ppa7~lucid1), cups-common (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libcups2 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), cups (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libcups2-dev (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), cups-bsd (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), libtiff4 (3.9.2-2, 3.9.2-2ubuntu0.3), chromium-browser-inspector (5.0.375.38~r46659-0ubuntu0.10.04.1, 5.0.375.70~r48679-0ubuntu0.10.04.1), libcupsmime1 (1.4.3-1ubuntu1, 1.4.3-1ubuntu1.2), linux-headers-2.6.32-22-generic-tuxonice (2.6.32-22.36~ppa2, 2.6.32-22.36~ppa5)
End-Date: 2010-06-22  16:55:45

```
I remember after one of updates (I bet glibc) kde asked for restart, but ignored it for a while, now while installing new software at stage of dpkg --configure it results with such error:
```

root@novopad:~# dpkg --configure -a
Konfigurowanie mtop (0.6.6-1.3) ...
mysql: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
mysql: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
dpkg: b&#322;&#261;d przetwarzania mtop (--configure):
 podproces zainstalowany skrypt post-installation zwróci&#322; kod b&#322;&#281;du 127
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 mtop

```
How to solve this

---

### Post by kalistona on 2010-06-25
i do not understand polak - pdwzarnia???, but about errors you must re-start and then reload then 'clean'.
i do not know if errors will be still here but it is simple and clear. 
mysql ? a nice database.
why twice ?

---

### Post by nusch on 2010-06-25
I've done restart already, main error 'relocation error' is in english, where is the problem?
```

root@novopad:~# LANG="en_GB.UTF-8" dpkg --configure -a
Setting up mtop (0.6.6-1.3) ...
mysql: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
mysql: relocation error: /lib/libnss_files.so.2: symbol __rawmemchr, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference
dpkg: error processing mtop (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 mtop

```

---

