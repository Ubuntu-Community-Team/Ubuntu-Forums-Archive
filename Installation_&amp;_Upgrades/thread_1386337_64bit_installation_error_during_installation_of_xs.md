---
title: "64bit installation error during installation of xserver-xorg-driver-all"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by paccaman on 2010-01-20
I'm trying to install Kubuntu 9.10 on my machine (I had the same problem with Kubuntu 9.04). The machine is:


 - Core 2 Quad 6600
- Nvidia 7600 GS
- Two disk seagate 500 in mirroring raid software


 When I try to install Kubuntu, after disk partition, my system dosn't see the CD. He tell me to insert disk into drive but I doesn't touch it. I resolved this mounting an external hard disk into /cdrom.
After this, the installation continues until the step "select and install software". At this step, the installation procedure tell me an error. During this error, in the other console, I've this:


```

 
Jan 19 21:58:09 in-target: Alcuni pacchetti non possono essere installati. Questo puÃ² voler dire
Jan 19 21:58:09 in-target: che Ã¨ stata richiesta una situazione impossibile oppure, se si sta
Jan 19 21:58:09 in-target: usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
Jan 19 21:58:09 in-target: non sono ancora stati creati o sono stati rimossi da Incoming.
Jan 19 21:58:09 in-target: Le seguenti informazioni possono aiutare a risolvere la situazione:
Jan 19 21:58:09 in-target:
Jan 19 21:58:09 in-target: I seguenti pacchetti hanno dipendenze non soddisfatte:
Jan 19 21:58:09 in-target:   xserver-xorg-video-all: Dipende: xserver-xorg-video-ati ma non Ã¨ installabile
Jan 19 21:58:09 in-target: E: Pacchetto danneggiato
Jan 19 21:58:09 in-target: tasksel: aptitude ha dato errore (100)
Jan 19 21:58:09 main-menu[488]: WARNING **: Configuring 'pkgsel' failed with error code 1
Jan 19 21:58:09 main-menu[488]: WARNING **: Menu item 'pkgsel' failed.
Jan 19 22:00:31 in-target: debconf: impossibile inizializzare il frontend: Passthrough
Jan 19 22:00:31 in-target: debconf: (Failed to open fd 3: Descrittore di file errato at (eval 25) line 3)
Jan 19 22:00:31 in-target: debconf: sarÃ  usato il frontend: Noninteractive



```
I've check the MD5 checksum of the CD and it match the teoric MD5. I'm also used the "check for error" function of CD and it doesn't find any problem.


 What can I do?

---

### Post by tachuela on 2010-01-20
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by paccaman on 2010-01-21
> **tachuela said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Hi Tachuela!
I've just read and tried this. :)

I don't know the utility of this information but in past I've just installed Ubuntu or Kubuntu on this machine. The version was Kubuntu 8.10 e ubuntu 8.04.

---

### Post by tachuela on 2010-01-21
Good Luck!

---

