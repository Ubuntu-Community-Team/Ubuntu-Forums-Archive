---
title: "How to configure Internet through PPTP and ADSL on Ubuntu?"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by Tux on 2005-08-07
I just installed Ubuntu.  The system works more or less, except for Internet.
Obviously: I'll have to log in through my ISP.  I did not encounter a configuration step for this during installation.  I use an ADSL "modem" as gateway, which is accessible on the local network.
Where in Ubuntu do I configure Internet access?  Presumably I'll have to use PPTP (that's what I use with my iMac on the same ADSL gateway).
On my previous Debian install I used pppd, but that is a pain to configure.

---

### Post by eivind on 2005-08-08
Hm.

One way could be to follow the steps from ubuntuguide.org:

[http://www.ubuntuguide.org/#rp-pppoe](http://www.ubuntuguide.org/#rp-pppoe)

I haven't tried this myself, but it seems to be a half-hour job, which means: A bit of work, but not terribly much. It's also a bit of a catch-22, because you need an internet connection to manage it, but you probably won't have that connection until you have followed the steps described...

What can I say? Good luck :-)

Eivind

---

### Post by debian_n00b on 2005-08-09
[QUOTE=eivind]Hm.

One way could be to follow the steps from ubuntuguide.org:

[http://www.ubuntuguide.org/#rp-pppoe](http://www.ubuntuguide.org/#rp-pppoe)

I haven't tried this myself, but it seems to be a half-hour job, which means: A bit of work, but not terribly much. It's also a bit of a catch-22, because you need an internet connection to manage it, but you probably won't have that connection until you have followed the steps described...

What can I say? Good luck :-)

Eivind[/QUOTE]



Yes, this method does work.

After following the steps outlined to install the PPPOE package, change into the newly created directory   /opt/rp-pppoe-3.5/ .

Now, I'm not at the machine that I had to configure PPPOE on, but read the accompanying readme in that directory. Your have to simply type in something like start-adsl, or adsl-start and it will walk you through configuring the connection. Very basic and simple.

Then, just add the script to execute on startup and you're all done.

---

