---
title: "Apt-mirror"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by Instrumenstrual on 2014-09-04
[SIZE=5][I][B]Hi all!
[/B][/I][/SIZE]
[SIZE=3]First of all, _excuse my poor english and post-style_ (first thread here!!!). Let's the explication begins:[/SIZE]

Im trying to set up a local repository (where i'd upload my custom packages if needed) in **Ubuntu Server 14.04.1** virtual machine with **VirtualBox 4.3.12** (4.3.14 causes bugs in Windows hosts).
In my host's network there's a proxy configuration (proxy.es.ad.bull.net:3128) and the VM is in bridge mode. I add this extrainfo:

[ATTACH=CONFIG]256129[/ATTACH]




I've followed some tutorials and im stucked when trying to run apt-mirror command. I'll explain you what steps i've done:



[LIST=1]
[*]**apt-get install apt-mirror apache2**
[*]**nano /etc/apt/mirror.list**
[ATTACH=CONFIG]256136[/ATTACH]
[*]**apt-mirror -c apt-mirror**
[ATTACH=CONFIG]256133[/ATTACH]

When i go to that line in /usr/bin/apt-mirror:
[ATTACH=CONFIG]256135[/ATTACH]

I gave it a chance running just apt-mirror and this is what i get:
[ATTACH=CONFIG]256134[/ATTACH]
[/LIST]


PS: I quit one extra '/' from one variable in /usr/bin/apt-mirror but it seems that it doesn't take some real effect.


Idk where the problem or error is!! Please, I summon your goodness!!!

---

