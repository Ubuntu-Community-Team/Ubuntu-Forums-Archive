---
title: "Which bugs for CD installer crash attempting to install 3rd-party software?"
date: 2021-01-20
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2021-01-20
I ran into a problem installing Focal, as the installer app crashed attempting to install third-party software.  *I* worked around it by delaying the third-party software until I had a clean install with open-source updates (the system needs the nVIDIA 390 drivers on account of the documentation-not-available nF780a), but a newbie might not know to work around this issue.  Which bugs are relevant to the installer crash(es)?  Links to the Pages at Launchpad woud be appreciated.

**Update:**  18.04.5-LTS Bionic installs without a hitch any which way.  Suspect regression somewhere in the 20.04.1-LTS CD image.

---

### Post by bcschmerker on 2021-01-25
**Update:**  The crash is across distros for 20.04.1-LTS, and I got a Bug number for ubuntu-cdimage:  [#1871268 "Installation fails due to useless immediate configuration error when "Install Third-Party Drivers" is selected"](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1871268) -- confirmed ISO-installer regression first appearing April 2020.  Will marked SOLVED upon (actual!) Fix Released.

---

### Post by bcschmerker on 2021-03-19
**New CD Image ubuntu-20.04.2-desktop-amd64.iso terminates properly.**  Had post-installation snags with the *msi*® N610GT-1GD3-LP dismounted, chalked 'em up to an obsolete driver for the planar C77.  Treating nvidia-340 as a WontFix; nvidia-*-390 work as advertised.

---

