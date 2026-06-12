---
title: "[SOLVED] Segmentation fault with aMSN"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by LoloftheRings on 2008-11-21
A few days ago, I installed aMSN. When I press the 'login' button, I get a segmentation fault (terminal output) and aMSN disappears. I tried reinstalling it a few times but it didn't work. I didn't compile it myself, but just apt-get installed it.

Any idea's?

Thanks in advance.

---

### Post by lemming465 on 2008-11-22
File a bug report in launchpad, and switch to "kmess" as an alternative in the interim?

---

### Post by LoloftheRings on 2008-11-23
I found another thread about this. I can't remember where and I also can't find it anymore. I had to edit some .conf file and remove a 'wins'.
I believe it's in launchpad already. It works now.
Thanks anyway

---

### Post by mastapat11 on 2009-06-10
the fix is to remove 'wins' from the hosts: line in /etc/nsswitch.conf

---

### Post by nickkontos on 2009-11-27
worked for me, thanks :)

---

### Post by Robynsveil on 2010-04-24
But is this a fix, really? I need to access my Windows shares, and that the "wins" entry in the /etc/nsswitch.conf file is essential to make this work. Apparently it is WINS that crashes (according to the aMSN forums) but if WINS crashes, why can I still access my folders?

Seems all very 'too-hard basket' to me...:(

---

### Post by Robynsveil on 2010-04-26
Okay, aMSN appears to not much care whether their software works when WINS is enabled, so I'm going to have to look for another client to access MSN from within the gnome environment. 

I noticed there is KMess, but that seems set up for Kubuntu, which I'm not using. Or can I still use KMess in just plain vanilla gnome?

---

### Post by franciel on 2010-05-25
Some people think after remove the 'wins' from line hosts of nsswitch.conf file solve all problems, but this increase others problems, like name resolution in internal network.  

Hey, do not remove de wins, but simply move after the dns, I do this with my line and names in internal network and aMSN work correctly:

hosts:          dns wins files mdns4_minimal [NOTFOUND=return] mdns4

Att,
Franciel
MSN: [email]jose_franciel@hotmail.com[/email]

:popcorn:

---

