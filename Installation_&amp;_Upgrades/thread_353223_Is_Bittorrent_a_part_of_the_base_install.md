---
title: "Is Bittorrent a part of the base install"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by rphelps on 2007-02-04
I have noticed a lot of disk accessing going on which seems to happen when I am logged on. I have also noticed bittorrent service of some kind is being shutdown when I shutdown my computer. 

Is bittorrent a part of the base install? Is it necessary for Ubuntu updates etc? I didn't specifically ask for this to be installed. 

I am now thinking of reinstalling the OS as it may be possible my machine is compromised.

---

### Post by kingmonkey on 2007-02-04
Your machine isn't compromised.

How much RAM do you have, maybe its accessing you swap partition. 

Do not worry about the bittorrent thing - it is normal.

Bittorrent isn't illegal as many people believe.

---

### Post by rphelps on 2007-02-04
Thanks for the information. I would still like to know if bittorrent is a part of the base install and if it is necessary to update or download software from the Ubuntu repository. 

Does anyone know if bittorrent is a part of the base install or necessary for Ubuntu?

---

### Post by Rabbit_Alex on 2007-02-04
Here is how to install Azureus, Bittornado and uTorrent.

[How to install P2P BitTorrent Client Azureus]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29")

---

### Post by az on 2007-02-04
> **rphelps said:**
> I would still like to know if bittorrent is a part of the base install and if it is necessary to update or download software from the Ubuntu repository. 

Does anyone know if bittorrent is a part of the base install or necessary for Ubuntu?

There is a bittorrent client included in the base install.  It does not run unless you open a torrent.  Currently, the package manager does not use bittorrent for downloading or updating your software - it should not be running unless you opened it.

Click on the gnome networking tools and see exactly what is listening to the network.

---

