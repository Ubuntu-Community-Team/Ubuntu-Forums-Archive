---
title: "PCMCIA failure after dist upgrade"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by blastradius on 2006-06-04
Hi

I don't actually know what PCMCIA is but I've noticed that Ubuntu now lists it as having 'failed' during boot up.  This must be as a result of the Dapper upgrade.  Nothing seems to be amiss though.

Can someone tell me what PCMCIA is and how I can fix this problem.

Thanks in advance

Eric

---

### Post by skelooth on 2006-06-04
same thing here. I think it has to do with laptops but I'm not sure.... 

Most. frustrating. upgrade. ever.

---

### Post by CyberX on 2006-06-04
Hello
PCMCIA cards are those small devices that you plug into laptops (like my Firewire/USB2.0 PCMCIA card). I think it is possible to have PCMCIA cards with desktops, but surely it is not your case.
You can disable the PCMCIA service with BUM, but if you still get this message, you can try this:

cd /etc/rcS.d/
sudo mv S40pcmcia _S40pcmcia

this will stop pcmcia initializing at boot (probably you will have some other numbers between "S" and "pcmcia").

---

### Post by Nordoelum on 2006-06-04
This message will occur when I use it on a desktop PC?

---

### Post by edopizza on 2006-06-30
[QUOTE=Nordoelum]This message will occur when I use it on a desktop PC?[/QUOTE]

The /etc/init.d/rcS script will start all the process in the folder /etc/rcS.d where the names starts with S?? (?? are two numbers). If in the folder /etc/rcS.d/ is present a file named S??pcmcia*, your desktop PC will try to start the pcmcia card, even if none is installed. 
Just rename the S40pcmcia and S13pcmciautils files like it has been explained above (check if the numbers 40 and 13 are correct!!!). 

```

sudo mv /etc/rcS.d/S40pcmcia backup_S40pcmcia 
sudo mv /etc/rcS.d/S13pcmciautils backup_S13pcmciautils

```

---

