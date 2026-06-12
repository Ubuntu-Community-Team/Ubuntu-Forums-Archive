---
title: "Adobe Flash plugin installation"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by savramesh on 2010-12-13
i am new to ubuntu.

i am trying to install adobe flash player plugin through Ubuntu software center, but i am getting the following error


installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.102.65ubuntu0.10.10.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb

tried the same in synaptic package manager, but got the following error

E: /var/cache/apt/archives/flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb: conflicting packages - not installing flashplugin-installer

please help to install flash player..

---

### Post by oldos2er on 2010-12-13
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Quackers on 2010-12-13
It's also worth installing ubuntu-restricted-extras via synaptic package manager if you haven't already done so, for more usability :-)

---

### Post by savramesh on 2010-12-13
@Ann,

it worked thanks..

@Quackers

Thanks, i just did that as well..

---

### Post by Quackers on 2010-12-13
Good thinking :-) Enjoy!

---

### Post by oldos2er on 2010-12-13
> **Quackers said:**
> It's also worth installing ubuntu-restricted-extras via synaptic package manager if you haven't already done so, for more usability :-)

ubuntu-restricted-extras installs 32-bit flash with nspluginwrapper, which in my opinion does not work as well as 64-bit flash for us 64-bit Ubuntu users.

---

