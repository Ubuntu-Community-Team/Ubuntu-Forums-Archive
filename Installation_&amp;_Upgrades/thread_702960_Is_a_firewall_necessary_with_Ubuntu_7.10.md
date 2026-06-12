---
title: "Is a firewall necessary with Ubuntu 7.10"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by John Read on 2008-02-20
Hi,

I'm using Ubuntu 7.10 (Gutsy) with a wireless modem (Vodafone mobile broadband) and the broadband connection isn't made until sometime after the computer has booted.

Do you think it's worth me installing say Firestarter? I've heard that there are some issues if the broadband connection isn't detected at boot time?

I have not activated the root account - just use sudo.

Thanks in anticipation.

John R.

---

### Post by maniac_X on 2008-02-20
You already have IPTables installed by default. IPTables is essentially the active firewall, Firestarter is just a graphical front end for IPTables. Here is a recent link about using Firestarter for configuring a basic firewall. 

[http://www.techthrob.com/tech/firestarter.php](http://www.techthrob.com/tech/firestarter.php)

Hope it helps.

.

---

### Post by vishzilla on 2008-02-20
All ports are closed by default, if you want control over the IP tables you can install Firestarter firewall which is in the repo. But, its not mandatory

---

### Post by steveneddy on 2008-02-20
We have never felt the need to run a firewall since installing Ubuntu.

We have a web server at our house and don't run one with that eiher. I runs Ubuntu 6,06 LTS Server.

---

### Post by housam on 2008-02-21
You'll just loose some space for unnecessary program

---

### Post by adult swim on 2008-02-21
if i have a port open in my firewall for torrents and an exception for it in firestarter, will firestarter only allow only torrent leechers access?
edit: i guess what i am trying to say is that port wide open to anyone?

---

### Post by zvacet on 2008-02-21
@ adult swim

That port is used only by torrents.If you want to check do you have any port open go to the [Shields Up](http://www.grc.com/default.htm).

---

### Post by adult swim on 2008-02-21
thanks zvacet!
yet another reason why ubuntu is awesome!
my ports security were "very uncommon for a Windows networking-based PC."
haha windows!

---

### Post by John Read on 2008-02-22
Thanks everyone.
Your advice is much appreciated.
Regards,
John R.

---

