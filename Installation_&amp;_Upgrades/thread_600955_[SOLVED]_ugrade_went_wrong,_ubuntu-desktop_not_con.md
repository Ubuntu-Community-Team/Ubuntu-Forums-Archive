---
title: "[SOLVED] ugrade went wrong, ubuntu-desktop not configured"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by matrooswolf on 2007-11-02
Hi,

My upgrade went wrong.  Update manager said that gnome-utils was not usable and ubuntu-desktop could not be configured because of dependencies (it depends on gnome-utils).

This is an error message (in mixed dutch, english and italian?):
```
dpkg: fout bij afhandelen van (--unpack):
subproces dpkg-deb --fsys-tarfile gaf een foutwaarde van 2 terug
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/openoffice.org-help-en-gb_1%3a2.3.0-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Instellen van gnome-utils (2.20.0.1-0ubuntu1) ...
/usr/share/gconf/schemas/gnome-search-tool.schemas:5408: parser error : PCDATA invalid Char value 14
a disabilita l&apos;uso del comando find dopo aver effettuato una ricerca veloce

dpkg: fout bij afhandelen gnome-utils (--configure):
 subproces post-installation script gaf een foutwaarde van 1 terug
dpkg: vereistenproblemen verhinderen de configuratie van ubuntu-desktop:
 ubuntu-desktop is afhankelijk van gnome-utils; maar:
  Pakket gnome-utils is nog niet geconfigureerd.
dpkg: fout bij afhandelen van ubuntu-desktop (--configure) :
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 gnome-utils
 ubuntu-desktop
```

Any ideas?  Is there a way to configure gnome-utils and ubuntu-desktop?

---

### Post by Pumalite on 2007-11-02
Save /home and data and do a clean install.

---

### Post by matrooswolf on 2007-11-02
Thanks,
I have home on a different partition.  So that's an option.

But I suppose there must be a way to fix this?

I can boot, login, and work (I'm actually typing this now in Gutsy),
still, when I try to update a package, I still get that error about gnome-utils and ubuntu-desktop :(

---

### Post by Pumalite on 2007-11-02
It's up to you what you want to live with. But, maybe somebody comes up with a better answer.

---

### Post by matrooswolf on 2007-11-03
I think the problem was due to a bad download. 
I removed the offending packages from /var/cache/apt/archives, and downloaded them again.  Everything ok now.

---

