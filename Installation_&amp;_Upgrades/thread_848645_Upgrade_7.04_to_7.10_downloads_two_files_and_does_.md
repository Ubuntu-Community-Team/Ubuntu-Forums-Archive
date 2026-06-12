---
title: "Upgrade 7.04 to 7.10 downloads two files and does nothing"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by PaperPilot on 2008-07-03
I have a DELL 1420n running 7.04.  When the Update Manager says I can upgrade to 7.10, it downloads two files and does nothing else.

---

### Post by SkonesMickLoud on 2008-07-03
Run:

```
sudo aptitude update
```

and try again.

---

### Post by PaperPilot on 2008-07-03
Tried the sudo aptitude update and got this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

Tried running apt-get update and got:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

What can I do now?

---

### Post by Pumalite on 2008-07-03
You seem to have another instannce of apt-get running; Synaptic maybe. Close it. As for the upgrade: remove all third parties from your sources.list, including the Medibuntu folder (delete it). Make sure your present OS is fully updated, then try again.

---

### Post by PaperPilot on 2008-07-03
I removed all third-party repositories from the Synaptic Package Manager.  The aptitude update worked all right, but I still can't get the version to upgrade.

---

### Post by Pumalite on 2008-07-03
This is the official way of doing it. You will find out that you can use an Alternate CD too.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

