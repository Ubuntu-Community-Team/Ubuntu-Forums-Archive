---
title: "Ubuntu netbook won't update"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Rotting Corpse on 2011-03-21
I installed ubuntu netbook, but whenever I try to go to the update manager I get an error half way through the download that says "Failed to download package files; check your internet connection"  This happens even when I plug it directly into my router.  This also happens sometimes with other software I try to get through the software center.  Any help would be appretiated.

---

### Post by gordintoronto on 2011-03-21
If you run Accessories/Terminal and enter this command:
sudo apt-get update
an error will appear. Open Administration/Software Sources and un-click the repository which caused the error. In some cases, you can get rid of the error by getting a missing "key," such as:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

Run Administration/Synaptic Package Manager, and click on "reload."

---

