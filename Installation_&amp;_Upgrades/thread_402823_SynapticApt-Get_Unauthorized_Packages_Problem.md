---
title: "Synaptic/Apt-Get Unauthorized Packages Problem"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by thinkdreams on 2007-04-06
I am currently testing a Feisty Fawn BETA upgrade from Edgy (in which I used the update manager recommended method). Everything is working properly, although I have noticed in the last two or so days that my synaptic (and apt-get) seem to report that my packages are unauthorized when I attempt to add new packages. My hardware is a Dell Inspiron E1505 laptop.

Basically, the error I get is "not authorized" in synaptic when I select even base packages. My ubuntu GPG keys haven't changed, and I was able to perform the upgrade OK. I checked (and even regrabbed the GPG keys for the standard Ubuntu repos) but still nothing.

Any ideas for what might be causing this? I am on the internet (no firewall in between) and able to browse websites, etc. just fine.

Other than that, Beryl, Network Manager (with VPNC support), and everything else I upgraded from works great. I can't wait until 7.04 is officially out.

Thanks,
Thinkdreams

---

### Post by thinkdreams on 2007-04-06
As an update, as I'm trying different things to get it to work, I am able to receive and update my system using the update-manager application.

---

### Post by thinkdreams on 2007-04-06
Well, it seems my problem fixed itself. I applied 61 updates through update manager (they automatically showed up this morning) and it required a reboot. After doing so, synaptic seems to be authorized with packages now.

I'll keep an eye on it and post here if I have more trouble, but it may just be a Beta software thing. Not sure.

---

