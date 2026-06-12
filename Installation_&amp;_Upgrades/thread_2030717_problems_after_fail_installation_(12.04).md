---
title: "problems after fail installation (12.04)"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2012-07-21
Dear users,
I was trying to install flightgear, but something was wrong and now "ubuntu software center" does not work. It says that the software catalogue is broken and it must be repaired. If I click on "repair it now" it does not work. And the problem remains. I also tried from terminal "sudo apt-get install -f" but without success. Shall I install ubuntu again?
What would you suggest?
Thank you
Ubuntu 12.04

---

### Post by telegiovi on 2012-07-21
perhaps the problem is here:

I seguenti pacchetti hanno dipendenze non soddisfatte: 
 fgfs-models-base : Rompe: fgfs-base (< 2.6.0) ma la versione 2.4.0-1 sta per essere installata 
 flightgear : Dipende: fgfs-base (>= 2.6.0) ma la versione 2.4.0-1 sta per essere installata 
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione). 

it seems to me that some programs are half installed but I cannot remove them

---

