---
title: "Upgrading Nautilus to 3.2.1 in Oneiric"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by nogoodnamesleft on 2011-10-17
Oneiric has Nautilus 3.2.0 which has a bug with the type-ahead find (it only works properly in the user's home folder).

It is fixed in 3.2.1 which I have downloaded from Gnome's website in source format. 

Will I break anything in Oneiric by just building it as normal with the usual configure, make, make install etc?

Is there a better way to do this?

---

### Post by mjuhasz on 2011-10-18
I would wait a little bit. Nautilus 3.2.1 is already in the upload queue. It will be in the proposed repository once it gets approved.

You can check the queue here: [https://launchpad.net/ubuntu/oneiric/+queue?queue_state=1](https://launchpad.net/ubuntu/oneiric/+queue?queue_state=1)

The list of proposed packages is here: [http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

If nautilus makes it to proposed you can enable that repository and update it.
For extra points you can help testing the proposed package ;): [https://wiki.ubuntu.com/QATeam/PerformingSRUVerification](https://wiki.ubuntu.com/QATeam/PerformingSRUVerification)

---

### Post by nogoodnamesleft on 2011-10-18
Thanks for info - very helpful - will certainly test patch.

---

### Post by nogoodnamesleft on 2011-10-18
I can only seem to install from the proposed list, Nautilus 3.2.1 has not made it there yet.

However I trying the new nvidia-settings from oneiric-proposed. Hasn't died yet ... :P

Is it correct that I can't (easily) do anything until it makes it to proposed?

---

