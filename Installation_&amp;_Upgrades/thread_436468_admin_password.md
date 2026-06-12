---
title: "admin password"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by chunke on 2007-05-07
Greetings to all... I need some help here.  Okay, here&#347; my problem. whenever I try to do this ...

1. Systems - Administrations - Update Manager; the Update Manager see the update, however, the  it then prompts me for a admin password... i Enter the root password and it does not work.  

2. I then went to the terminal and logged in as su root and eveything is fine. How can I log into the log in screen?

:(

---

### Post by taurus on 2007-05-07
You should use the same password that you log in with, not the root's password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Buffalo Soldier on 2007-05-07
The initial user that you create during installation is the admin for Ubuntu. Assuming that you're currently logged in as this user, whenver the system ask for the admin password, just enter the password for that user.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chunke on 2007-05-07
just did that and it did not work... it&#347; prompting me for a admin password not a user password.

---

### Post by aysiu on 2007-05-07
The *admin* password **is** your user password, unless you've done something weird to your Ubuntu installation... or aren't in the *admin* group.

If so, [this](http://www.psychocats.net/ubuntu/sudo) should help set things back to normal.

---

