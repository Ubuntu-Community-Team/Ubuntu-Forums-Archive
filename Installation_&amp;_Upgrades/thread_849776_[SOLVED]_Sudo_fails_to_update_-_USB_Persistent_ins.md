---
title: "[SOLVED] Sudo fails to update - USB Persistent install"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Separ on 2008-07-04
Sudo fails to upgrade in the update manager, HALP! :(

---

### Post by upchucky on 2008-07-04
hmm typing sudo by itself will not start an upgrade, perhaps a bit more info on the method and possible failure messages would help?

---

### Post by Separ on 2008-07-04
I mean the actual package called "Sudo" will not update.

It gives no error messages in the terminal bit of update-manager, it just hangs.

---

### Post by upchucky on 2008-07-04
need to make sure the repositories are set right, i hadda change mine to us server from main to get all updates after a ubuntu upgrade

---

### Post by Separ on 2008-07-04
Does it matter if I copied over the sources file from my desktop?

---

### Post by Separ on 2008-07-04
I had backed up the old sources file so I have now restored it. Now how do I delete the packages that it downloaded under the other sources file?

---

### Post by upchucky on 2008-07-04
just uncheck them in package manager to remove or check then to install and uninstall again

---

### Post by Separ on 2008-07-04
They aren't installed, I mean the .deb files.

EDIT: Found them in /var/cache/apt/archives but I don't know which ones to delete

Wonder what would happen if I just deleted all the .deb files in there, they are only needed for install, right? lol

Seemed to do it no harm. Sudo package is apparently still there though o_O

---

