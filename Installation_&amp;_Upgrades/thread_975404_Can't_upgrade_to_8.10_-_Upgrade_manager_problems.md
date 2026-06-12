---
title: "Can't upgrade to 8.10 - Upgrade manager problems"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by harryeddy on 2008-11-08
Okay, so I'm trying to upgrade to 8.10. I went to the sources and selected show all dist upgrades. I started the upgrade and then had to cancel for other reasons. Now, when I run update manager, it does not show the dist upgrade. I followed instructions from another thread and ran ```
update-manager -c
```and got the following error: ```
current dist not found in meta-release file

```

Scary. What's up?

---

### Post by Pumalite on 2008-11-08
Run in the Terminal:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

Then upgrade after removing all third parties from your sources.list; including the Medibuntu folder if you have one.

---

### Post by harryeddy on 2008-11-08
Okay - I tried the commands, deselected all third-party sources, and got the same error. Help!:confused:

---

### Post by Pumalite on 2008-11-08
From what to 8.10 are you trying to update?

---

### Post by harryeddy on 2008-11-08
sorry for the long reply - I am running 8.04

---

### Post by Pumalite on 2008-11-08
This is the official method of upgrading:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by harryeddy on 2008-11-08
Yes, this was the method I tried...unfortunately, I still get the same error...:eek:

---

### Post by Pumalite on 2008-11-08
Maybe you should take a look at the 'Before You Start' notes and this:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

