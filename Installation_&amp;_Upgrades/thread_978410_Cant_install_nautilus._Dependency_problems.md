---
title: "Cant install nautilus. Dependency problems"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Mighty_Pooh on 2008-11-11
Ive been doing some dist upgrades on my laptop.
And the last one realy f..... up. 
Now everytime i try to install a program i get this error.

/var/lib/dpkg/info/nautilus-data.postinst: 11: gconf-schemas: Permission denied
dpkg: fejl under behandling af nautilus-data (--configure):
 underproces post-installation script returnerede afslutningsstatus 127
dpkg: afhængighedsproblemer forhindrer konfiguration af nautilus:
 nautilus afhænger af nautilus-data (>= 1:2.22), men:
  Pakken nautilus-data er ikke sat op endnu.
 nautilus afhænger af nautilus-data (<< 1:2.23), men:
  Pakken nautilus-data er ikke sat op endnu.
dpkg: fejl under behandling af nautilus (--configure):
 afhængighedsproblemer - efterlader den ukonfigureret
dpkg: afhængighedsproblemer forhindrer konfiguration af nautilus-sendto:
 nautilus-sendto afhænger af nautilus-extensions-2.0, men:
  Pakken 'nautilus-extensions-2.0' er ikke installeret.
  Pakken nautilus, som giver nautilus-extensions-2.0, er ikke sat op endnu.
dpkg: fejl under behandling af nautilus-sendto (--configure):
 afhængighedsproblemer - efterlader den ukonfigureret
Der opstod fejl under behandlingen:
 evince
 nautilus-data
 nautilus
 nautilus-sendto
E: Sub-process /usr/bin/dpkg returned an error code (1)

I know its danish sorry about that. But basicly what it says is dependency problems. And permission denied.

i do sudo apt-get install -f

---

