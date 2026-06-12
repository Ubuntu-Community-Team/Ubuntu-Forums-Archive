---
title: "Upgrade from Precise LTS to Trusty LTS"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by hamstermoon on 2014-04-22
Hi Everyone,

I know my LTS version of Xubuntu will eventually get round telling me to upgrade to the newest and best, but I'd like to know if there is a way do this anyway without having to wait or having to totally reinstall. Is there something I can type in the terminal and can someone talk me through it?

---

### Post by slickymaster on 2014-04-22
First make sure that you are fully up-to-date, either by opening the Update Manager application or by running```
sudo apt-get update && sudo apt-get upgrade
```in a terminal window.

When that’s done just run the following command in a terminal:```
update-manager -d
```Hit the return/enter key and, when prompted, enter your user password.

The Update Manager application will open after a few seconds with a prompt to upgrade. Click this button to begin the process.

---

### Post by mörgæs on 2014-04-22
14.04 is still very young. If 12.04 is working I recommend that you wait.

---

