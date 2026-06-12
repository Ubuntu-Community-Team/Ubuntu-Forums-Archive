---
title: "Reverting PHP to 5.2 in Lucid 10.04"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mathews.kyle on 2010-04-05
I recently upgraded my main development laptop to Lucid. Lucid upgraded PHP to 5.3 and as I'm mainly a PHP developer, this has caused quite a few problems. What's the easiest way to revert back to the the 5.2 series? Googling hasn't found any good solutions.

---

### Post by Mustang Matt on 2010-04-05
I don't have the answer to your question, but I'm curious what problems you ran into.

---

### Post by djoxyk on 2010-04-05
I'm curious too. I have upgraded php 5.3 on lucid. It works ok.

---

### Post by Bachstelze on 2010-04-05
> **mathews.kyle said:**
> I recently upgraded my main development laptop to Lucid. Lucid upgraded PHP to 5.3 and as I'm mainly a PHP developer, this has caused quite a few problems. What's the easiest way to revert back to the the 5.2 series? Googling hasn't found any good solutions.

You could add the Karmic repositories to your sources.list and do some apt-policy magic to lock PHP to Karmic, or compile PHP 5.2 from source.

---

### Post by obrienmd on 2010-04-05
Would be _very_ intersted in this, especially if there was a PPA / named package to do this... Drupal / Open Atrium don't play nice with PHP 5.3 yet, and many of our Drupal webapps would need non-trivial updates to do so. The latest Drupal core is rumored to work well, but none of the sites we have deployed are working well on 5.3, for whatever reason (contrib modules, etc).

Cheers!

---

### Post by djoxyk on 2010-04-05
if you need just downgrade version, try to remove current version and you can use synaptic to install older one, use force version under the package menu.
i do not touch Drupal, but wordpress works ok with php 5.3

another way is to download sources of 5.2 and compile it (if there's no version in reps).

---

### Post by Bachstelze on 2010-04-05
OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

* First remove all your existing PHP packages. You can list them with e.g.:

```
dpkg -l | grep php
```

* Then duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:

```
sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list
```

* Create a file in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php);

```
Package: php5
Pin: release a=karmic
Pin-Priority: 991
```

The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic.

---

### Post by obrienmd on 2010-04-06
> **Bachstelze said:**
> OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

* First remove all your existing PHP packages. You can list them with e.g.:

```
dpkg -l | grep php
```

* Then duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:

```
sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list
```

* Create a file in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php);

```
Package: php5
Pin: release a=karmic
Pin-Priority: 991
```

The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic.

Awesome! Love the idea... Hate the idea of having to remember to set this when adding any php package :)

---

### Post by obrienmd on 2010-04-06
> **Bachstelze said:**
> OK, here's how to do the Apt magic to get PHP packages from the karmic repositories:

* First remove all your existing PHP packages. You can list them with e.g.:

```
dpkg -l | grep php
```

* Then duplicate your existing sources.list replacing lucid with karmic and save it in sources.list.d:

```
sed s/lucid/karmic/g /etc/apt/sources.list | sudo tee /etc/apt/sources.list.d/karmic.list
```

* Create a file in /etc/apt/preferences.d like this (call it for example /etc/apt/preferences.d/php);

```
Package: php5
Pin: release a=karmic
Pin-Priority: 991
```

The big problem is that wildcards don't work, so you will need one such stanza for each PHP package you want to pull from karmic.

Actually, this seems to make apt-get / aptitude install ALL NEW packages from the karmic repositories...

---

### Post by Reiger on 2010-04-06
No it won't. It will now have *both* the Lucid and the Karmic repositories enabled side by side; and because the Lucid versions of all software is from a repository with a higher major version number than their Karmic counterparts this will make APT use Lucid repositories (it prefers latest software by default), unless specified otherwise.

That is where the preferences file comes in; it basically tells APT to prefer the karmic PHP packages to the Lucid ones.

Where this gets problematic is if PHP or associated packages depend on things like binutils that have broken their ABI or API over an upgrade. If that happens you will have Karmic PHP & related packages built for the old calling conventions confronted with the new ones and failing in interesting ways... Similarly if packages have been dropped or renamed or something like that you will have trouble to get APT to do conflict resolution and installation properly.

---

### Post by obrienmd on 2010-04-06
> **Reiger said:**
> No it won't. It will now have *both* the Lucid and the Karmic repositories enabled side by side; and because the Lucid versions of all software is from a repository with a higher major version number than their Karmic counterparts this will make APT use Lucid repositories (it prefers latest software by default), unless specified otherwise.

That is where the preferences file comes in; it basically tells APT to prefer the karmic PHP packages to the Lucid ones.

Where this gets problematic is if PHP or associated packages depend on things like binutils that have broken their ABI or API over an upgrade. If that happens you will have Karmic PHP & related packages built for the old calling conventions confronted with the new ones and failing in interesting ways... Similarly if packages have been dropped or renamed or something like that you will have trouble to get APT to do conflict resolution and installation properly.

Got it, seems to be working. Maybe the demand for this will grow into a well-managed PPA :)

---

### Post by FFuser on 2010-04-17
Hi, I've a similar problem

I want to upgrade to Lucid, but I need PHP5.2

This is because I'm developping my own site, and the deployment server is a PHP 5.2 server so it is not a solution for me to use PHP 5.3 locally to test.

Also using Karmic packages is not a real solution because these are on a older version and my site is does not work on it (I need PHP 5.2.13). So for now I compiled PHP myself, but I rather want to use a PPA/third party repository.

I know "http://www.dotdeb.org/", but their packages wont work on newer versions of Ubuntu (because older versions used the package name libkrb53, but newer once use libkrb5-3 so synaptic does not let install me it because of a missing dependency)

Maybe someone knows a solution to easily create a libkrb53 "alias"/"meta" package to use this repository, or knows a good working third party repository that has new PHP 5.2 packages that works on Ubuntu (Lucid)

Greetings

---

