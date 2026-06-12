---
title: "Partial Upgrade"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by ranger1021994 on 2012-09-13
Is there a way to manually launch a partial upgrade rather than wait for update manager to decide when package is broken ??

Is there a command to directly launch a partial upgrade ?

---

### Post by JRV on 2012-09-13
Partial upgrades can be dangerous, it is usually best not to do them.

Read Here:

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by ranger1021994 on 2012-09-13
I wanted to do it because update manager showed me updates for vlc-data but i could not select it and it wasnt even greyed out but after partial upgrade that package was installed.
In such cases calling partial upgrade manually would make much sense rather than wait for system to decide.

Is there any command to directly launch a partial upgrade ?

---

### Post by QIII on 2012-09-13
Again:  I think you will find that most of us recommend AGAINST partial upgrades.  Because package dependencies may not yet be resolved and everything necessary put into the repos (and pushed out to mirrors), partial upgrades may cause problems with some applications.  It takes time to get all the bits and pieces into the mix and it is possible that not everything is available instantly.  Worse, your system may become unstable or inoperable.

If you simply must check manually before the Update Manager alerts you, you may use the terminal
```
sudo apt-get update
sudo apt-get upgrade
```

Replacing the second command with

```
sudo apt-get dist-upgrade
```

will attempt to "intelligently" rectify dependency issues and install new packages as necessary.  However, you should still review what is being suggested and know exactly what you are doing.  You may not want to do what has "intelligently" been determined, especially if you have third party packages installed outside of the repos.

It is best, when offered a partial upgrade, to simply wait a few hours.

My very strong recommendation:  don't do partial upgrades at all.

---

