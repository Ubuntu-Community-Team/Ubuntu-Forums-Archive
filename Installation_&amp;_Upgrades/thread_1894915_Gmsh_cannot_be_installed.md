---
title: "Gmsh cannot be installed"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by davidemontag on 2011-12-13
when I try to install Gmsh (mesh generator) I get some dependency errors :

I seguenti pacchetti presentano dipendenze non soddisfatte:
(Following packages have dependencies unsatisfied)

gmsh: Depends: libc6 (>= 2.7) ma 2.13-20ubuntu5 sta per essere installato
      Depends: libgcc1 (>= 1:4.1.1) ma 1:4.6.1-9ubuntu3 sta per essere installato
      Depends: libgomp1 (>= 4.2.1) ma 4.6.1-9ubuntu3 sta per essere installato
      Depends: libjpeg62 (>= 6b1) ma 6b1-1ubuntu2 sta per essere installato
      Depends: libstdc++6 (>= 4.6) ma 4.6.1-9ubuntu3 sta per essere installato
      Depends: libcgns2 (>= 2.5.3) ma 2.5.5-1 sta per essere installato

But all packages after ma are already installed.

How shall I proceed?? 

Tnx

---

### Post by BC59 on 2011-12-13
Why don't you use Ubuntu Software center? Which Ubuntu version you are using?

---

### Post by davidemontag on 2011-12-13
I am using 11.10 and tried to update by USC...and I got such a message from it.
I think to have some corrupted packages, how do I recover from it?? anyway, a fresh installation could solve the issue, I guess

---

### Post by BC59 on 2011-12-13
There are 2 solutions for the broken packages. Let's try the easy one. Open a terminal CTRL+ALT+T and execute:


```
sudo dpkg --configure -a
``` and then

```
sudo apt-get -f install
```

---

### Post by davidemontag on 2011-12-14
sudo dpkg --configure -a
[sudo] password for davide: 
davide@davideUbuntu-K53SV:~$ sudo apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 33 non aggiornati.
davide@davideUbuntu-K53SV:~$ sudo apt-get install gmsh
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 gmsh : Dipende: libmed1 (>= 2.3.6) ma non sta per essere installato
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati.


No luck: as I am working in italian, I hope that you can understand, <fatto means done
 but last line says : it is impossible to correct problems, some damaged packages are blocked.

Any idea???

---

### Post by BC59 on 2011-12-14
If you don't have installed the application Synaptic, you can install it from Ubuntu Software Center. 
Then open it and go to left down panel--Custom filters and then upper left panel Broken. 
From Broken choose to restore the broken packages. 
Then when you finish, try to install Gmsh from Ubuntu Software center.

---

### Post by davidemontag on 2011-12-15
I have no packages in broken!!!

Next step??

---

### Post by BC59 on 2011-12-15
In that case try to install the package libmed1 from Synaptic. If your architecture is 32bits install the package libmed1:i386 instead.

---

### Post by nardis_Miles1 on 2012-05-27
The dependencies for gmsh are pretty tangled. If you try to install gmsh, libmed1 is required. If you try to install libmed1, you will find that it depends on libhdf5-openmpi-1.8-4. If you try to install libhdf5-openmpi-1.8-4, you will find that it conflicts with libhdf5-1.8 and libhdf5-1.8.4. 

First, all of these dependencies are supposed to be handled invisibly by apt/synaptic, and they are not. Second, the dependencies for libhdf5 seem to be circular. This problem has been around for months. There is no such difficulty in natty. Who knows what the situation is in precise?

Art Edwards

---

