---
title: "Latest version of Firefox and Thunderbird"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by nomko on 2011-09-27
Hi,

Where can i find the PPA for the latest stable versions of Thunderbird and Firefox? I'm running Ubuntu10.04.3 32-bit.
Is it correct that the latest version is version 7 for both programs?

Many thanks!

---

### Post by gabikilalala on 2011-09-27
hi,
well try this
for thunderbird:

```

sudo add-apt-repository ppa:ricotz/ppa && sudo apt-get update
sudo apt-get install thunderbird
```
and for firefox:
```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox ubufox
```

in terminal
i hope i helped you

---

### Post by nomko on 2011-09-27
> **gabikilalala said:**
> hi,
well try this
for thinderbird:
sudo add-apt-repository ppa:ricotz/ppa && sudo apt-get update
sudo apt-get install thunderbird


I've asked my very dear friend Google and he replied with this: [https://launchpad.net/~mozillateam/+archive/thunderbird-stable]("https://launchpad.net/%7Emozillateam/+archive/thunderbird-stable") for the official PPA for Thunderbird. So what wrong with this PPA??

---

### Post by Frogs Hair on 2011-09-27
The creator of the PPA had used the stop publishing option for some reason , but the option was removed and the PPA was updated 9 minutes ago .

---

### Post by nomko on 2011-09-28
> **Frogs Hair said:**
> The creator of the PPA had used the stop publishing option for some reason , but the option was removed and the PPA was updated 9 minutes ago .
 
But i can use the PPA of Launchpad also for both programs? There's no difference between the "official" PPA and the PPA of ricotz?

---

### Post by lovinglinux on 2011-09-28
> **gabikilalala said:**
> hi,
well try this
for thunderbird:

```

sudo add-apt-repository ppa:ricotz/ppa && sudo apt-get update
sudo apt-get install thunderbird
```
and for firefox:
```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox ubufox
```

in terminal
i hope i helped you

For Firefox see the [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?p=1058851).

The Mozilla team also have a PPA for Thunderbird.

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```

---

