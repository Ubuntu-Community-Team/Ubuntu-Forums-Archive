---
title: "Why does the installer ask to install updates?"
date: 2020-10-11
forum: Installation &amp; Upgrades
---

### Post by Tadaen_Sylvermane on 2020-10-11
Did a Xubuntu 20.04 this morning for my wife. During installation it asks if I want to download updates while installing. Says "This makes things faster after the installation." I've seen this over the years on every version I've used. However what I don't get is after the initial boot it still shows me updates available. When I install them it does a full download. So what exactly does that option do? It's clearly not downloading the updates?

---

### Post by deadflowr on 2020-10-11
It *should* be downloading the updates. (emphasis on should)
I've done this many times and then run an apt update/full-upgrade post install and it always lists either 0 of xxxMb needed to download, or a small amount like 12Kb of xxxMb needed to download.
Meaning most, if not all, updates were already downloaded.
If no downloads show it probably means networking was not working as expected.
Or, in a worst case scenario, the installer is somehow broke for that function.

---

### Post by ActionParsnip on 2020-10-11
Could be that new updates were pushed during the install and reboot phase..

---

