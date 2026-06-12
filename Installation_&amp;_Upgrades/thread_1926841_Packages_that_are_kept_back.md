---
title: "Packages that are kept back"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by podollb on 2012-02-17
This is a fairly basic question, but one that I've always wondered about...

When I issue an upgrade via "**sudo apt-get upgrade**" I often times get "kept back" packages:

[I][COLOR="DarkGreen"]The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/COLOR]
[/I]
Usually I just manually run "**sudo apt-get dist-upgrade**" to download/install those packages.

But my question is: Will those packages ever become NOT "kept back"? 

Or is this by design, and running dist-upgrade is the only (and intended way) to pull down such packages since they are more core upgrades (i.e. new kernel)?

---

