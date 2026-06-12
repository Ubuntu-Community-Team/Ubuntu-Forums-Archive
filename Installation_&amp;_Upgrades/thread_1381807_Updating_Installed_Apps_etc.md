---
title: "Updating Installed Apps etc"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2010-01-15
Ok My Next Question ...

Using Synaptic and/or terminal is great and so easy, but i have noticed that applications are not always the latest versions that are in the repository ie cups for instance

So if i wanted to download the latest app from a website, what is the best way to install, based on having an earlier version already installed.  Is it better to just install over an older version or remove the older version, and then install the new version clean

If you remove and older version of an application first, what is the best method for doing this and removing any residual files etc that might be left on your system ?

Many thanks
:D

---

### Post by konqueror7 on 2010-01-15
> **whitetimer said:**
> Ok My Next Question ...

Using Synaptic and/or terminal is great and so easy, but i have noticed that applications are not always the latest versions that are in the repository ie cups for instance

So if i wanted to download the latest app from a website, what is the best way to install, based on having an earlier version already installed.  Is it better to just install over an older version or remove the older version, and then install the new version clean

If you remove and older version of an application first, what is the best method for doing this and removing any residual files etc that might be left on your system ?

Many thanks
:D

removing all config files and app,
```
sudo apt-get --purge remove <app>
```

instead by downloading from other sources, you may want to check out [Launchpad.net]("https://launchpad.net/")

you may as well read [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") in adding repos,,,

and regarding your question, there is no particular difference in the methods you said, bust uninstalling the old version if a new major version is available would be better (personally)...hope that answered it,,,:D

---

### Post by whitetimer on 2010-01-15
> **konqueror7 said:**
> removing all config files and app,
```
sudo apt-get --purge remove <app>
```

instead by downloading from other sources, you may want to check out [Launchpad.net]("https://launchpad.net/")

you may as well read [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") in adding repos,,,

and regarding your question, there is no particular difference in the methods you said, bust uninstalling the old version if a new major version is available would be better (personally)...hope that answered it,,,:D

Hi Konqueror

Thats great and thanks for your help !!!

---

