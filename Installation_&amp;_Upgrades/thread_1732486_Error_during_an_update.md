---
title: "Error during an update"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Gotlieb on 2011-04-18
Hi

I get this error after I tried updating.


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC7B7B7D4439DBD6


Please help

Thanks anyway :confused:

---

### Post by zvacet on 2011-04-18
In terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EC7B7B7D4439DBD6 
```

```
sudo apt-get update
```

---

### Post by Gotlieb on 2011-04-19
> **zvacet said:**
> In terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EC7B7B7D4439DBD6 
```

```
sudo apt-get update
```
Hi,

Thanks for the reply, I just tried that right now.

(Q)


W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2)  Unable to connect to ppa.launchpad.net:http:


Please Help...

Thanks

---

### Post by Gotlieb on 2011-04-19
> **Gotlieb said:**
> Hi,

Thanks for the reply, I just tried that right now.

(Q)


W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_ZA.bz2)  Unable to connect to ppa.launchpad.net:http:


Please Help...

Thanks
I just got it, I replaced the key with the error key, thanks alot. 

Your a star

---

