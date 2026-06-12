---
title: "Apt-get install build-essential"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by Obstacle1 on 2005-11-14
I've tried to install the build-essential package but i've got this :
```

Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Alcuni pacchetti non possono essere installati. Questo pu&#242; voler
dire che &#232; stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.

Poich&#232; &#232; stata richiesta solo una singola operazione &#232; molto facile che
il pacchetto semplicemente non sia installabile, si consiglia
di inviare un "bug report" per tale pacchetto.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  build-essential: Dipende: libc6-dev ma non sta per essere installato oppure
                            libc-dev
                   Dipende: g++ (>= 3:3.3) ma non sta per essere installato
E: Pacchetto non integro

```

What can i' do?

---

### Post by adwait on 2005-11-14
How about a translation? Try using different respositories because I am not getting an error on my end.

---

### Post by Obstacle1 on 2005-11-15
Sorry for the post!I found the solution,i've got wrong                                                                                                                
/etc/apt/sources.list
the mirror were for Ubuntu Hoary!
Very Sorry:oops:

---

