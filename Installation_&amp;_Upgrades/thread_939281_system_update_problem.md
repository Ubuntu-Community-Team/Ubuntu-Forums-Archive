---
title: "system update problem"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by jackgu1988 on 2008-10-05
hi! i have a problem when i try to update my system... from the update manager when i press on check it begins checking and when checking almost comes to an end this message appears (after long time waiting for the last package to be downloaded):

> W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

and when i try from the terminal > sudo apt-get update when it reaches > 95% [Connecting to ubuntu.beryl-project.org (80.77.247.17)] just stops... :(

is there anything i can do?

thank you!

---

### Post by Pumalite on 2008-10-05
Edit /etc/apt/sources.list and comment out the offending line.
First backup:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list
Add a # in front of the Beryl line.
Save, exit
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by jackgu1988 on 2008-10-05
thank you! it worked!:)

---

### Post by Pumalite on 2008-10-05
You are welcome. Good luck!

---

