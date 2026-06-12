---
title: "freecontrib.org down?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by buddachile on 2006-10-27
I havent' been able to connect to freecontrib.org since yesterday. anyone else experiencing this? any news on what's going on?

---

### Post by hsu_linux on 2006-10-27
I have not been able to resolve packages.freecontrib.org since yesterday.  DNS will not resolve the name.  Is anyone else experiencing this?

---

### Post by BackInTimeMan on 2006-10-27
Yep, same here. It's been like this for a few days now for me. The website comes up OK:

[http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

and there is thread about the problem here:

[https://launchpad.net/products/plf/+bug/68262](https://launchpad.net/products/plf/+bug/68262)

---

### Post by kerry_s on 2006-10-27
I switched mine to->

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) etch main

---

### Post by jetpeach on 2006-10-27
hmm, still down.  is the one you listed kerry_s the same as the plf? since it's for etch, it makes me a bit nervous (compatibility problems?)

---

### Post by moeFinley on 2006-10-27
I could get to it at work today (about 11:00am BST).  But I couldn't yesterday or this evening?  I figured it was too many ppl upgrading to Edgy and then downloading easyubuntu.

---

### Post by wiredrat on 2006-10-27
Repository has been changed with [this file]("ftp://ftp.easynet.fr/plf/ubuntu/README"):
```

This project is now in dormant state, as the plf/ubuntu team resigned due
to lack of time. If you want more detail or want to help, please contact 
misc, either on irc ( #plf@irc.freenode.net ), or send a email on 
misc at zarb.org .

```

---

### Post by gotgenes on 2006-10-27
The IRC channel greeting says
> plf server is down, potentialy raided by the FBI
:(

---

### Post by vibestriton on 2006-10-27
Jeesh... gossip central around here... hehe   :)

Whois:  freecontrib.org
... 
Name Server:NS0.XNAME.ORG 
Name Server:NS1.XNAME.ORG 
...

From [http://xname.org/:](http://xname.org/:)

[FONT=Arial][SIZE=3]"[/SIZE][/FONT][FONT=Arial][SIZE=3]XName is temporarily closed since 08:00PM CEST yesterday evening. We were experiencing the largest DDoS we ever had on both ns0 and ns1 IP addresses, forcing our upstream providers to cut off XName servers in order to preserve their  other customers."

[/SIZE][/FONT] 
 [FONT=Arial][SIZE=3]"We're working hard in order to have at least one DNS server answering ASAP, and we already negociated with a premium transit provider to host one of our DNS servers shortly."[/SIZE][/FONT]

---

### Post by kerry_s on 2006-10-28
> **jetpeach said:**
> hmm, still down.  is the one you listed kerry_s the same as the plf? since it's for etch, it makes me a bit nervous (compatibility problems?)

Just grab w32codecs and libdvdcss2 it's only codecs so it shouldn't mess with anything else, after you grab them you can just delete the repo or disable.

---

### Post by frieko on 2006-10-28
Fallback repository works for me:

deb [http://mrpouit.free.fr/plf-fallback](http://mrpouit.free.fr/plf-fallback) edgy-plf free non-free
deb-src [http://mrpouit.free.fr/plf-fallback](http://mrpouit.free.fr/plf-fallback) edgy-plf free non-free

---

### Post by gvgerman on 2006-10-28
I also had problems w/ freecontrib.org

Using the "alternate install" method found here: [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades") I was able to circumvent the freecontrib.org problem and had a successful upgrade.

When the Alt Install CD asks if you want to check the web for the latest packages, select "no".  If you select "yes", it will ck the web and fail at freecontrib.org

---

### Post by Thund3rstruck on 2006-10-28
kerry_s,

whats the gpg key for that site?

---

### Post by hsu_linux on 2006-10-29
wget [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg) -O- | sudo apt-key add -

---

### Post by markba on 2006-10-30
> **hsu_linux said:**
> wget [http://mrpouit.tuxfamily.org/12B83718.gpg](http://mrpouit.tuxfamily.org/12B83718.gpg) -O- | sudo apt-key add -

Could also be done (seems more logical) with this one:
wget [http://mrpouit.free.fr/plf-fallback/12B83718.gpg](http://mrpouit.free.fr/plf-fallback/12B83718.gpg) -O- | sudo apt-key add -

---

### Post by markba on 2006-10-30
I've tried the fallback repo's ([http://mrpouit.free.fr/plf-fallback)](http://mrpouit.free.fr/plf-fallback)), but it seems like Opera or Java is not part of it. Does anyone know if these packages are availaible in the original repo (which is down now of course). For Java I'm sure, for Opera not because I had a separate repo for that (deb.opera.com) but according to Ubuntu Guide, the freecontrib repo should cover this too.

---

### Post by mr_pouit on 2006-10-30
Java was removed, because it is available in multiverse repository since dapper.
And opera was removed because it is availble in the Canonical commercial repository. ;)

---

### Post by hsu_linux on 2006-10-30
If anyone cares, these repos are back up:

deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free

---

### Post by BackInTimeMan on 2006-10-30
Thanks, hsu_linux!

---

### Post by morr on 2006-10-31
:KS The servers are up and working!

---

### Post by msak007 on 2006-11-04
Anybody know the GPG key for the site? It's finally back up and I can connect to it, but get an error when trying to update because there's no GPG key:

```
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
```

This is on a fresh Edgy install, and there doesn't seem to be any info anywhere about needing a GPG key to connect. I didn't have to in Dapper anyway.

Edit: Nevermind, I didn't look hard enough. Went to the site linked to earlier in the thread ([http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)) and the GPG key is right there.

---

### Post by tronica on 2006-11-04
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -

---

