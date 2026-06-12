---
title: "Update manager problem upgrading to Gutsy"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by flamer on 2007-10-16
When I want to pre-update to gutsy  using this command:

[update-manager -d]

The updater hangs at fetching file 117 an then 113

[img]http://shrani.si/f/4/cV/4Q3HBcPe/screenshot.png[/img]

[img]http://shrani.si/f/m/Aj/449OCtJm/screerrrnshot.png[/img]

Ather a couple of minutes it goes on

and then it says:

[img]http://shrani.si/f/20/qy/2R9vLp46/screenshot1.png[/img]

and then it asks me to download and install. Is it safe to upgrade?

---

### Post by xmouse on 2007-10-16
Hi,

I hardly know update manager but i think it's safe to upgrade but you should do it on the other way. So replace everything from feisty to gutsy in /etc/apt/sources.list what originally was in that and after make an apt-get update&&apt-get dist-upgrade
But if you want to do it with update manager i think it's really safe.
I think it'll do it well. I hope this can help.

xmouse

---

### Post by flamer on 2007-10-16
Ok thanx. I'll try it

---

