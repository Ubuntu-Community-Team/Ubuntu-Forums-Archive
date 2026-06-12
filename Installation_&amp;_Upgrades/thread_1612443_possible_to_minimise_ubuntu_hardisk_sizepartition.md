---
title: "possible to minimise ubuntu hardisk size/partition ?"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Hexy86 on 2010-11-03
I've currently got ubuntu 10.4 installed, but unfortunately have to some work on windows again stuff that emulators and wine  wouldn't be up to.
[B]
So my question is can i resize the Existing installation allowing me to create another partition for which i could install XP on and how would i go about this ??[/B]

( I will repeat i've got Ubuntu already installed for ages) all the advice i see about is about adding lunux to windows or starting for the start with nothing installed

---

### Post by Elfy on 2010-11-03
You'll need to boot a livecd as you can only do so when ubuntu is unmounted.

There is a partition editor on the ubuntu livecd or you could get gparted and burn it as an iso.

Once you have resized ubuntu - install XP.

Once you have installed XP you will need to reinstall grub - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Backup your data and do not assume that gparted has hung if it takes a while - depending on the partition sizes it could be a long(ish) job

---

### Post by Hexy86 on 2010-11-03
cool beans thanks for the info

---

