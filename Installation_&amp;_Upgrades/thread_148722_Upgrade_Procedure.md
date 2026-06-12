---
title: "Upgrade Procedure"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by Geffers on 2006-03-22
I've got Breezy Badger's Kubuntu installed, I know Dapper Drake is due out soon.

When it arrives do I upgrade or do I need a fresh instal.

When a new version is launched do the Gnome and K versions come out together.

Geffers

---

### Post by John.Michael.Kane on 2006-03-22
Removed since it was not needed, or used.

---

### Post by smith.j.doe on 2006-03-22
To upgrade to Dapper here's what you'll need to do:

In the /etc/apt/sources.list change everything referring to breezy to dapper.
Then:
sudo apt-get update
sudo apt-get dist-upgrade

I read somewhere that once dapper is officially out this process would be automatic but not sure how that would be done.

Gnome and K do not have a sync'd release cycle and are not released at the same time.

Cheers!
JDS

---

### Post by Geffers on 2006-03-22
[QUOTE=smith.j.doe]To upgrade to Dapper here's what you'll need to do:

In the /etc/apt/sources.list change everything referring to breezy to dapper.
Then:
sudo apt-get update
sudo apt-get dist-upgrade

I read somewhere that once dapper is officially out this process would be automatic but not sure how that would be done.

Gnome and K do not have a sync'd release cycle and are not released at the same time.

Cheers!
JDS[/QUOTE]

Thanks for prompt reply, I'm having fun at the moment and getting the hang of Breezy.

Geffers

---

### Post by John.Michael.Kane on 2006-03-22
Geffers and your welcome since i said the samething..

---

