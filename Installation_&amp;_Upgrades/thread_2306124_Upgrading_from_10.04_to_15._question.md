---
title: "Upgrading from 10.04 to 15.?? question"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by SuperGeorge on 2015-12-12
I really want to upgrade to the latest version (mostly cause i need openssl to support sa256) but i am worried about loss.  I have a web server, squid proxy, and email server running.   Will i lose all the settings for these servers.

Just kinda need to know what to expect if i upgrade.   I've been using windows all of my life so this is kinda new to me :)

Thanx

---

### Post by Bucky Ball on 2015-12-12
*Thread moved to **Installation & Upgrades**.*

I can't help a lot with your issues but I would add this: for your setup I'd stick with the long-term support releases (LTS) rather than the interims. They have five years support. The current LTS release is 14.04 LTS. The interims have nine months support. You don't want to be doing this every six - nine months. LTS releases are also upgradeable via the net to the next LTS (every two years available) skipping the interim releases in between. 

There is no 'upgrade' as such from 10.04 to 15.10, only a clean install, but if you were upgrading via the net or from install media from a supported release to a supported release then no, your settings shouldn't be changed. With a clean install, it will wipe everything, obviously enough, so you will need to do good backups and add stuff back post-install. 

Good luck. :)

---

### Post by SuperGeorge on 2015-12-12
Thank you. that was very good info :)

---

### Post by Bucky Ball on 2015-12-12
No probs. Hope it helps. One other thing: 14.04 Ubuntu will look totally different to 10.04. Ubuntu now uses Unity as a desktop environment. I'd advise you to 'Try Ubuntu' from the disk before installing. As you have servers setup, not sure if you are going to be using a DE, but if you are, try Unity before installing. If you don't like, try Xubuntu or Lubuntu. They look a lot more like 10.04. 

You can try them all from install media.

---

### Post by SuperGeorge on 2015-12-12
Awesome. gonna try out the 14.04 LTS after i spend all day doing back-ups; lol.  Thanx again, you da man :)

---

### Post by Bucky Ball on 2015-12-13
All good. With the servers you could install the [server ISO]("http://www.ubuntu.com/download/server"), as you don't need a full-blown DE, or perhaps even one at all,  then just:

```
sudo apt-get install xfce4
```

... will get you a lightweight desktop environment (the one Xubuntu uses). Add whatever else you need via 'apt-get install'. 

```
sudo apt-get install xfce4 lxterminal pcmanfm 
```

... etc. Have fun backing up and good luck with the process. :)

---

