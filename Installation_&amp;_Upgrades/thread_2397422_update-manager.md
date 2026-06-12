---
title: "update-manager"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by xubu2 on 2018-07-29
For more then 2 months the packages **python3-update-manager**, **update-manager** and **update-manager-core **are ready for upgrading according to synaptic.
But according to software-updater theres nothing to update.
How come it takes this long?
Is this a bug or are the develepors still working on these 3 packages?
I'm using Xubuntu 16.04.5
Regards.

---

### Post by deadflowr on 2018-07-29
Run
```
sudo apt update
apt list --upgradable
```
to confirm which is right, synaptic or update manager.

---

### Post by xubu2 on 2018-07-29
```
apt list --upgradable
Listing... Done
python3-update-manager/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]
update-manager/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]
update-manager-core/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]

```
Same thing as synaptic.
Guess they have to be tested.

---

### Post by #&amp;thj^% on 2018-07-29
> **xubu2 said:**
> ```
apt list --upgradable
Listing... Done
python3-update-manager/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]
update-manager/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]
update-manager-core/xenial-updates,xenial-updates 1:16.04.13 all [upgradable from: 1:16.04.12]

```
Same thing as synaptic.
Guess they have to be tested.
That means they are ready now:
```
sudo apt-get upgrade
```

---

### Post by xubu2 on 2018-07-29
Ok, thanks for the quick answer.
I'm gonna wait until software-updater passes them.
Greets.

---

### Post by #&amp;thj^% on 2018-07-29
Just suppose for a moment that the software-updater is not working right and there are security fixes just waiting to be installed but the software-updater is not showing you that....software-updater is just a front end for package management.
"sudo apt-get update && sudo apt-get upgrade"
I am just not a fan of gui-package-handlers>>>Just a happy terminal user here.
But as you wish. ;)

---

### Post by xubu2 on 2018-07-29
Ok got it.
I always use software-updater.
It works cause i still get other updates from it.
Software-updater is the reason why i use ubuntu.
Greets.

---

