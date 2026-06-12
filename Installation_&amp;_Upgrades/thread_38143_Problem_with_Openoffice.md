---
title: "Problem with Openoffice"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Dexterri on 2005-05-30
Hi I'm new in Ubuntu (I've used Debian before), I've installed it, all seems to work good, but Ubuntu software updates says me that there are 3 updates available:

- openoffice.org-gtk-gnome
- openoffice.org-l10n-en
- openoffice.org-thesaurus-en-us

when I try to install them some errors occur, and when I try to reconfigure them with command "dpkg --configure -a", this is the result:

[I]Configuro openoffice.org-bin (1.1.3-8ubuntu2.3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postinst.d/prelink exited with return code 1
dpkg: errore processando openoffice.org-bin (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di openoffice.org-debian-files:
 openoffice.org-debian-files dipende da openoffice.org-bin (>> 1.1.2+1.1.3); comunque:
  Il pacchetto openoffice.org-bin non è ancora configurato.
dpkg: errore processando openoffice.org-debian-files (--configure):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 openoffice.org-bin
 openoffice.org-debian-files[/I]

Moreover if I try to install any other package from synaptic the system crashs and I have to reboot...

Can anyone help me to solve this problem?

Thanks in advance... Dexterri

---

