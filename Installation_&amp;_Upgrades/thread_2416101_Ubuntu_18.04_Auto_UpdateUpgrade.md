---
title: "Ubuntu 18.04 Auto Update/Upgrade"
date: 2019-04-05
forum: Installation &amp; Upgrades
---

### Post by elliotbeken on 2019-04-05
Hi All, 

I currently have Ubuntu 18.04 running with automatic upgrades enabled. This is currently working fine without any issues.

I would however like for updates to be checked and installed 203 times a day. Currently i is only once a day.

My **/etc/apt/apt.conf.d/20auto-upgrades** config file:

[B]APT::Periodic::Update-Package-Lists "1"; 
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";[/B]

Is this possible or do i need to live with a minimum of 1 day?

---

### Post by Rubi1200 on 2019-04-05
> [COLOR=#000000]I would however like for updates to be checked and installed 203 times a day.[/COLOR]

Do you mean 2 or 3 times per day perhaps?

---

### Post by elliotbeken on 2019-04-05
> **Rubi1200 said:**
> Do you mean 2 or 3 times per day perhaps?

Yes correct.

---

### Post by Rubi1200 on 2019-04-06
I've not managed to come up with anything definitive but will keep searching.

---

