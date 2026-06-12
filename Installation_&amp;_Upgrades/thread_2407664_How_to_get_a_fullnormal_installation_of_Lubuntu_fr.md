---
title: "How to get a full/normal installation of Lubuntu from a DVD only install?"
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by mikeymikec on 2018-12-07
I installed Lubuntu 18.10 (it had to be that - rather than the 18.04 LTS I'm used to - in order to get features working properly such as battery level indication) on a cheap tablet/netbook hybrid which wouldn't give me the option to connect to wifi during the installation (yet did directly after rebooting), so the installation was limited to what was on the DVD.

I noticed quite a few bits were missing, and while it might have been due to the new version having less than the old version (the rpm command wasn't installed, yet - I'm pretty sure - is on a default 18.04 LTS install with net access).  Is there a way after installation to trigger the installation of the rest of what ought to have been installed during installation had it had a working network connection?

---

### Post by yancek on 2018-12-07
Have you done sudp apt update && sudo apt upgrade?

I would be surprised if rpm was installed by default on any Debian/Ubuntu system as Debian/Ubuntu use apt.  rpm = Red Hat Package Manager.  rpm can be installed on Lubuntu but really should be no need to use it.

---

### Post by mikeymikec on 2018-12-07
I definitely ran the 'full upgrade' option in the Muon Package manager.  I don't recall if I ran that from the command line.

---

### Post by Impavidus on 2018-12-07
Only three things should be missing when installing without network:
- Updates. But you installed those later.
- Proprietary drivers, if available for your hardware.
- Some proprietary user software, like some codecs.
All of these are opt-in even when installing with network and you may not want them.

---

