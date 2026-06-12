---
title: "Install Ubuntu with up-to-date packages right away"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by Prendi on 2010-04-23
Hi, is there a way to install Ubuntu with up-to-date versions of all packages right away?

To clarify: With the normal LiveCDs, in order to install an up-to-date Ubuntu Lucid, I have to download a 700 MB LiveCD, install Ubuntu, and then use the Update Manager (or apt-get) to upgrade all outdates packages, which by now should be another about 300 MB. Old versions of SUSE Linux had the option of downloading an ~40MB installer ISO which did not contain any packages itself, but would download and install the most recent versions of all necessary packages.

Is there such a facility for Ubuntu as well? Or a way of using an outdated Ubuntu LiveCD (e.g. Lucid Beta 1) to still install an up-to-date system in a single pass?

I am *not* talking about netboot images such as netboot.me or boot.kernel.org, which AFAIK will download the full normal Ubuntu ISO during boot, so that I would still have to upgrade the system afterwards.

---

### Post by wilee-nilee on 2010-04-23
You can get daily builds of the development version up to when the new one is started.

---

### Post by Prendi on 2010-04-23
Ok, so that helps me to install an up-to-date Ubuntu up to the release date. But what if I want to install an up-to-date Lucid (LTS) in a year or so? Daily builds will only be available for the current development branch, won't they?

---

### Post by sunk8 on 2010-04-23
You could use *dpkg-repack* or *APTonCD* to backup your packages and install them on another computer, if that is what you want to do. *Sbackup* will keep your preferences up to date...

---

### Post by Prendi on 2010-04-23
Good to know, but that's not what I want.

Right now, to install an up-to-date Karmic, I need to download an 700MB CD Image, install it, and then download additional ~300MB of updates, which will in effect uninstall the version that were on the CD and then install the new ones. What I primarily would like to have is to only have to download that 700MB set of packages (+ the data necessary to boot the installer) that will actually end up on my system. If that doesn't work for whatever reason, I'd like to be able to somehow tell the Ubuntu installer from the LiveCD to install Ubuntu by using only those packages from the LiveCD that are still up-to-date, and to download the newest versions of the other packages and install these, instead of installing the old ones, and then replacing them by the new ones in a second step (which is what the update-manager/apt does).

---

### Post by snowpine on 2010-04-23
Yes, use the Ubuntu Minimal CD. It will download the current packages from the web:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Prendi on 2010-04-23
Cool, thanks. That's exactly what I wanted.

---

