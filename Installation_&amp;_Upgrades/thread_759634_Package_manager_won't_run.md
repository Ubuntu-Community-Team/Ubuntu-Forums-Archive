---
title: "Package manager won't run"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Eric Weir on 2008-04-19
I just did a fresh install of Kubuntu 7.10 on a Pentium IV machine with 512 MB of RAM. After downloading all the upgrades, adept notified me that one  application had not been upgraded because it "was broken or would break" the application.

Subsequently, when I went to install Firefox and Thunderbird, adept notified me that there was a conflict with another application, "probably some part of adept itisielf, or apt or apt-get," and asked if I wanted to try to resolve the conflict. When I said, yes, after a few seconds adept crashed. This continues to happen even after rebooting.

The only way I know to solve the problem -- not exactly being a techie -- is to do another reinstall. I imagine there are other things well short of this, but being a nontechie I don't have a clue what they are.

Any help would be appreciated.

Sincerely,

---

### Post by Pumalite on 2008-04-19
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by Eric Weir on 2008-04-19
> **Pumalite said:**
> sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

It worked. Thanks.

Sincerely,

---

### Post by Pumalite on 2008-04-19
You are welcome. Good luck.

---

