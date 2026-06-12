---
title: "Cannot install some updates"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by dpm on 2006-06-02
I've got a minor, but annoying problem.

The update-notifier is showing 5 updates (**app-install-data**,** gnome-app-install**,** pcmcia-cs**,** tetex-base **and** tetex-extra**) since a couple of days (since the day before release IIRC), which I cannot install. 

Basically, when I click on "Install Updates", an "Examining your System" progress bar dialog pops up and exits straight away, without actually installing anything. The funny thing is, when I launch synaptic and reload all sources, it doesn't show any upgradable packages. For example, with **app-install-data**, update-manager tells me that there is a 0.1.33 version available, whereas Synaptic tells me that the latest version is 0.1.32 (which is the one I've got installed at the moment).

I upgraded to Dapper about two months before the release and I never had such a problem. My **sources.list** has always been the same, which includes the official source and binary repositories + official upgrades + universe + multiverse + backports, and it seems ok to me.

I do not quite why this is happening now. My last update was two days before release, I think. IIRC, one day before release there were no more updates, and on the release day this started to happen. First I saw the updates for **pcmcia-cs**,** tetex-base **and** tetex-extra **on the update-manager, which I couldn't install, and today I see in addition **app-install-data** and** gnome-app-install**, which I cannot install, either.

Any comment will be appreciated. Thanks.

---

### Post by dpm on 2006-06-02
Well, that was a quick one, it took me less time to find the solution than to actually type the problem. Oh well...

Setting:

Synaptic: Settings>Preferences>Distribution> "Always Prefer the Highest Version".

solved the problem.

Some time ago I had set this to "Prefer Versions from: **dapper**", but of course, the updates come from **dapper-updates** now...


Cheers.

---

