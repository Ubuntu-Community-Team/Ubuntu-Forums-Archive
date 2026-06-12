---
title: "upgrade and broken dependences (samba-common)"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Qwerty990 on 2010-05-13
Hi there guys!
A couple of days ago, I upgraded my Kubuntu to Lucid. In this phase, the system reported that it was impossible to upgrade samba-common, and the installation aborted on 90%. Nevertheless everything is working but KPakageKit, which reports:

«There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation.»

Neither "sudo aptitude safe-upgrade" nor "sudo apt-get -f install" solved the problem:

> omen@darkstar:~$ sudo aptitude safe-upgrade
[..]
I seguenti pacchetti saranno aggiornati:
  samba-common 
I seguenti pacchetti parzialmente instalalti saranno configurati:
  kubuntu-desktop samba samba-common-bin smbclient winbind 
1 pacchetti aggiornati, 0 installati, 112 da rimuovere e 0 non aggiornati.
È necessario prelevare 0B/396kB di archivi. Dopo l'estrazione, verranno liberati 1024MB.
Continuare? [Y/n/?] 
Scrittura delle informazioni sullo stato esteso... Fatto
Preconfigurazione dei pacchetti in corso
(Lettura del database... 467190 file e directory attualmente installati.)
Preparativi per sostituire samba-common v.2:3.4.0-3ubuntu5.6 (utilizzando .../samba-common_2%3a3.4.7~dfsg-1ubuntu3_all.deb)...
update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup danneggiato: stato non valido
dpkg: attenzione: vecchio script di pre-removal ha restituito lo stato di errore 2
dpkg - viene provato lo script dal nuovo pacchetto...
dpkg: errore nell'elaborare /var/cache/apt/archives/samba-common_2%3a3.4.7~dfsg-1ubuntu3_all.deb (--unpack):
 non c'è alcuno script nella nuova versione del pacchetto - saltato
Si sono verificati degli errori nell'elaborazione:
 /var/cache/apt/archives/samba-common_2%3a3.4.7~dfsg-1ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Errore durante l'installazione di un pacchetto. Tentativo di ripristino:
dpkg: problemi con le dipendenze impediscono la configurazione di samba:
 samba dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare samba (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di winbind:
 winbind dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare winbind (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di smbclient:
 smbclient dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare smbclient (--configure):
 problemi con le dipendenze - lasciato non configurato
Configurazione di samba-common-bin (2:3.4.7~dfsg-1ubuntu3)...
update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup danneggiato: stato non valido
dpkg: errore nell'elaborare samba-common-bin (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 2
dpkg: problemi con le dipendenze impediscono la configurazione di kubuntu-desktop:
 kubuntu-desktop dipende da smbclient; comunque:
  Il pacchetto smbclient non è ancora configurato.
dpkg: errore nell'elaborare kubuntu-desktop (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 samba
 winbind
 smbclient
 samba-common-bin
 kubuntu-desktop
Lettura elenco dei pacchetti... Fatto                   
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Lettura delle informazioni sullo stato esteso       
Inizializzazione dello stato dei pacchetti... Fatto

and

> omen@darkstar:~$ sudo dpkg --configure -a
[sudo] password for omen: 
dpkg: problemi con le dipendenze impediscono la configurazione di samba:
 samba dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare samba (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di winbind:
 winbind dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare winbind (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di smbclient:
 smbclient dipende da samba-common (= 2:3.4.7~dfsg-1ubuntu3); comunque:
  La versione di samba-common nel sistema è 2:3.4.0-3ubuntu5.6.
dpkg: errore nell'elaborare smbclient (--configure):
 problemi con le dipendenze - lasciato non configurato
Configurazione di samba-common-bin (2:3.4.7~dfsg-1ubuntu3)...
update-alternatives: error: /var/lib/dpkg/alternatives/nmblookup danneggiato: stato non valido
dpkg: errore nell'elaborare samba-common-bin (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 2
dpkg: problemi con le dipendenze impediscono la configurazione di kubuntu-desktop:
 kubuntu-desktop dipende da smbclient; comunque:
  Il pacchetto smbclient non è ancora configurato.
dpkg: errore nell'elaborare kubuntu-desktop (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 samba
 winbind
 smbclient
 samba-common-bin
 kubuntu-desktop

So the problem is really samba-common. Any ideas to solve this issue (which deny me to install-upgrade pakages)?

---

### Post by lemming465 on 2010-05-14
First try:```
sudo -i
apt-get update  # refresh package lists
apt-get upgrade -f
```
If that doesn't do it, second try:```
sudo aptitude reinstall samba
```
If that doesn't do it, third try removing all the installed packages with "samba" in their name by hand (e.g. from synaptic), and then reinstall them.

---

### Post by Qwerty990 on 2010-05-15
Well, the first two solutions din't work (always the same kind of error), and, sincerely, I'm a bit worried about the third, because of the fact that kubuntu-desktop needs samba-common (actually, this package is non configured due to samba's problems). But, afterall, I'll try ;)

thanks for your advises!

---

### Post by lemming465 on 2010-05-15
While kubuntu probably *wants* samba, so that the KIO SMB ioslaves work, it shouldn't make any difference to boot & login whether or not samba is temporarily absent.

---

