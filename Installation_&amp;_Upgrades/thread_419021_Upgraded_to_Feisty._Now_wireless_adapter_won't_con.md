---
title: "Upgraded to Feisty. Now wireless adapter won't connect!"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by al_scott on 2007-04-22
This morning I had an alert to tell me that Feisty was available to install. So, I decided to upgrade from Edgy.

It seems to have installed correctly, however I can't get my wireless to connect. I've had to connect to my router using an ethernet cable, so I can get on the web.

The card I have installed is an Edimax EW-7128g. I used the RT61 drivers to get it working on Edgy (I think). I can't remember how I installed it either - I just know it took me ages.

If I do iwconfig in the console, it shows ra0 as RT2500 Wireless, which makes me think that the drivers are OK. However, the adapter doesn't get a IP from the router as it should do.

Where should I start?!!

---

### Post by al_scott on 2007-04-23
I was thinking that perhaps the old ralink driver that I loaded in Edgy is still present.

Is this feasible? If so, how do I remove it?

---

### Post by Smokersroom on 2007-04-25
Exactly the same problem here... What a pain - all my internet browsing is now restricted to m*crosoft.

---

### Post by macabro22 on 2007-04-29
It seems to be happening to everyone. I cant connect wirelessly anylonger either. After ndiswrapping my windows drivers I can connect to the network, but I cant get a DNS servername or something like that. The wireless lan assistant cant change the /etc/resolv.conf file. 
I already tryied everthing, even changing access privileges and all that.

God damn this crap. The Feisty Upgrade sux.

---

### Post by ColJep on 2007-04-29
I have found out that you must use wep security with the new setup. It is no good just having a hidden ssid.   wpa does not work yet.

That got me back on line.

ColJep

---

### Post by Vil on 2007-05-01
I read in one thread that if you are using ndiswrapper from the repos, recompiling 1.42/43 from source fixed some of the problems. Might be worth a shot. =/

---

### Post by macabro22 on 2007-05-01
I am using WEP. But it doesn't matter. It won't connect even without encryption. 
Good grief...

Quoting Vil:
"I read in one thread that if you are using ndiswrapper from the repos, recompiling 1.42/43 from source fixed some of the problems. Might be worth a shot. =/"

Do you mind posting a link?

---

