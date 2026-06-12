---
title: "Hung during upgrade to Edgy"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by flostre on 2007-03-08
Hi

I was running Dapper Drake on my office PC until today I decided to upgrade to Edgy. In the phase "Fetching and Installing the upgrades", step "configuring nfs-kernel-sever", a debconf window popped up, saying "Configuration file modified: /etc/exports". From the drop-down-menu, instead of the default option "use installed version", I chose "display differences" and clicked next. That caused the pop-up to hang. After five minutes, the diff appeared in the main upgrade window in the terminal. But the pop-up is still hanging. It has been like this for half an hour now.

What am I to do?

Thanks, flostre

---

### Post by flostre on 2007-03-08
I just discoverd that there are running no less than eight processes by the name of "nfsd" plus one called "nfsd4". Can I savely kill them all?

---

### Post by watson540 on 2007-03-08
yes you can kill them. the pkg's are already safe on your hard drive, apt and dpkg will pick up where it left off

---

### Post by flostre on 2007-03-08
Okay, for people experiencing the same problem:

1. Kill the upgrade windows (press alt+F2, enter "xkill", click on one window, repeat)
2. run sudo dpkg --configure -a
3. if reboot doesn't work: press alt+ctrl+F1, login, enter "sudo reboot", re-enter password
4. Edgy Power!


For the devs: Maybe it would be a good idea to keep configuring in the background when there is a user interaction required. This would speed up unsupervised install. (Yes, there are ways to do unsupervised control. I am talking about the naive "Oh, this seems to take a while. I'm gonna go for lunch/shopping/mow the lawn/invade Iran" kind of unsupervised install.)

flostre

---

