---
title: "Kubuntu 24.04.1 - install failed but now okay"
date: 2024-10-06
forum: Installation &amp; Upgrades
---

### Post by oygle on 2024-10-06
Recently did a fresh installation of Kubuntu 24.04.1. Initially a msg - "Package manager error", Dolphin locked up, couldn't unload USB, other error messages. The user created was 'Kubuntu' not my name, when I tried to login it still had the "Install" option. I tired the 'Install" and there was no system created. Logged in, tried to change the language and it locked again. Several more attempts to install and te same problems occurred.

**Then** I did an install and selected the option "Download updates during the installation" ( or whatever the exact wording was ), and the installation went flawlessly.

So, .. make sure that box is checked.

---

### Post by guiverc on 2024-10-06
If the installer didn't complete successfully, there is a chance that it'll not complete the installation, as installing stops when a significant error is encountered; thus later steps aren't even attempted.

My last QA test of Lubuntu *oracular* (24.10) encountered this, the results I detected were

- /var/log/installer wasn't created; that *final* step of the install was never run
- I was asked on my post-install boot if I wanted to TRY or INSTALL; ie. `lubuntu-installer-prompt` executed on the installed system, as it wasn't removed

The second point is what you were describing, only the package you had installed was `kubuntu-installer-prompt` asking if you wanted to TRY or INSTALL your installed Kubuntu system I bet.

My ['failed' install]("https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2083684") was caused (*I'm almost 100% certain*) by a temporary internet failure; thus package problem relating to a package it was trying to download...  Either way, the install actually worked except for two really minor issues; most users wouldn't probably notice the lack of *install metadata* being present on the system, and as for *try/install* issue, that could be easily removed anyway if the user wanted.  I didn't try the INSTALL option when `lubuntu-installer-prompt` run on my actual installed system, I only used the TRY & operation there was as I expected.

FYI:  If not obvious; *Lubuntu*, *Kubuntu* and *Ubuntu Unity* use the same `calamares` installer; which has been used by the Lubuntu team since 18.10; I'm referring to Lubuntu as its what I know best & where most of my QA goes; but Lubuntu/Kubuntu collaborate with install testing (24.04 & *later*).   I've had most luck when not using internet with installs; but I live *downunder* where we have slow & somewhat *crappy* internet.

---

### Post by oygle on 2024-10-06
> **guiverc said:**
> If the installer didn't complete successfully, there is a chance that it'll not complete the installation, as installing stops when a significant error is encountered; thus later steps aren't even attempted.

Yes, it was a significant error I think. As part of my "install routine" for fresh installs, I always format the SSD , so unfortunately, no crash reports or similar.

> **guiverc said:**
> FYI:  If not obvious; *Lubuntu*, *Kubuntu* and *Ubuntu Unity* use the same `calamares` installer; which has been used by the Lubuntu team since 18.10; I'm referring to Lubuntu as its what I know best & where most of my QA goes; but Lubuntu/Kubuntu collaborate with install testing (24.04 & *later*).   I've had most luck when not using internet with installs; but I live *downunder* where we have slow & somewhat *crappy* internet.

The name `calamares` rings a bell, as I did do some research after the failed install. Some posts mentioned the creation of the user "Kubuntu" , which is what I encountered. I live *downunder* also, internet speed is okay (fixed wireless).

---

