---
title: "Upgrade and problems with Cinelerra, libmpeg3hv-dev e libmpeg3hv"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by openversus on 2007-04-07
I use ubuntu 6.10 with Cinelerra and after an upgrade I received an error message and now I can't use synaptic.
I'm sorry because the language is italian, but I hope that someone can help me...


[B]
I make *apt-get update * and then * apt-get upgrade* : then I read this on the terminal: [/B]

[I]È consigliabile eseguire `apt-get -f install' per correggere questi problemi.
I seguenti pacchetti hanno dipendenze non soddisfatte:
  cinelerra: Dipende: libmpeg3hv (>= 1:2.1.0) ma non è installato
             Dipende: libmpeg3hv (= 1:2.1.0-2svn20070221) ma non è installato
  libmpeg3hv-dev: Dipende: libmpeg3hv ma non è installato
  libquicktimehv: Dipende: libmpeg3hv (>= 1:2.1.0) ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.

**after this I write apt-get -f install**

root@joda:~# apt-get -f install
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Correzione delle dipendenze in corso... Fatto
I seguenti pacchetti sono stati installati automaticamente in precedenza e ora non sono più necessari:
  libattr1-dev kdelibs4-dev traceroute libaspell-dev libtasn1-3-dev
  libaudio-dev comerr-dev libpcre3-dev libopencdk8-dev libgcrypt11-dev
  liblualib50-dev libkrb5-dev qt3-dev-tools libsasl2-dev libavahi-client-dev
  libjasper-1.701-dev libkgantt0-dev libksieve0-dev libpcrecpp0 liblua50-dev
  lua50 libavahi-qt3-dev libacl1-dev ksync libgnutls-dev libqt3-mt-dev hspell
  libxslt1-dev libdbus-1-dev libssl-dev libkleopatra1-dev libart-2.0-dev
  libktnef1-dev liblzo-dev libkpimexchange1-dev libqt3-headers libkdepim1-dev
  liblcms1-dev libkadm55 libkcal2-dev gtkglarea5 libkgantt0 libartsc0-dev
  libmng-dev libmimelib1-dev libavahi-common-dev kdesdk-scripts libcupsys2-dev
  gettext-kde libidn11-dev kdepim-kresources libbz2-dev libarts1-dev
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti verranno inoltre installati:
  libmpeg3hv
I seguenti pacchetti NUOVI (NEW) saranno installati:
  libmpeg3hv
0 aggiornati, 1 installati, 0 da rimuovere e 5 non aggiornati.
4 non completamente installati o rimossi.
È necessario prendere 0B/326kB di archivi.
Dopo l'estrazione, verranno occupati 893kB di spazio su disco.
Continuare [S/n]? s
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  libmpeg3hv
Installare questi pacchetti senza la verifica [s/N]? s
(Lettura del database ... 166162 file e directory attualmente installati.)
Spacchetto libmpeg3hv (da .../libmpeg3hv_1%3a2.1.0-2svn20070221_i386.deb) ...
dpkg: errore processando /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn20070221_i386.deb (--unpack):
 tentata sovrascrittura di `/usr/bin/mpeg3cat', che si trova anche nel pacchetto mpeg3-utils
Sono occorsi degli errori processando:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn20070221_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

I also run apt-get autoremove but nothing appened

please help!

Ciao to everybody and... buena vida!

---

### Post by openversus on 2007-04-12
I resolved this problem :-)
I write on the terminal:

[I]dpkg --force-overwrite -i /var/cache/apt/archives/libmpeg3hv_1%3a2.0.0-1svn20060209+ubuntu_i386.deb
[/I]

I find here the solution: [https://init.linpro.no/pipermail/skolelinux.no/cinelerra/2006-March.txt]("https://init.linpro.no/pipermail/skolelinux.no/cinelerra/2006-March.txt")

So I'm really happy :-)

Buena vida!

---

