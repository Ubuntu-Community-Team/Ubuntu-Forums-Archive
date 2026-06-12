---
title: "Configuring Network Hangs during installation"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by prokofiev_2000 on 2005-04-07
During installation I get to the screen "Configuring Network with DHCP". The installation progress bar gets to 33% then stops. Can someone please help? I am trying to set up a HP Netserver LH II with three SCSI drives. I don't have a network cable plugged into the network card. Could this be the problem? Thanks in advance!

---

### Post by nad on 2005-04-08
Just to be clear here; Does it hang or freeze?

It will hang for the better part of a minute or so (I  do not know the default timeout) if you do not have access to a DHCP server. If you would be connected to an internal network server with the cable plugged in, then, yes this is your problem.

If it freezes, I need more information to help.

---

### Post by fedork on 2005-05-31
I have exact same problem. On this machine I have a NIC (soem very old one and I am not sure whether it even works) which is not connected. I also have a wireless card which I need ndiswrapper for, so it probably does not make any difference at this point. 

For me it FREEZES, that is, I waited for quite a while (a lot more than a minute) and it would not move and it does not react to Ctrl-Alt-Del or anything else, so I have to reset the machine.

Do you think it could be the card and pulling it out may help?

---

### Post by fedork on 2005-06-01
removing the NIC did help!

---

