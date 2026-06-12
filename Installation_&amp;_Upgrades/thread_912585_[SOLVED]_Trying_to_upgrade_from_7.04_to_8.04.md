---
title: "[SOLVED] Trying to upgrade from 7.04 to 8.04"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by tahirih on 2008-09-06
I'm a newbie... I just discovered Ubuntu 7.04 (Feisty Fawn) and barely got to explore it when I had lost my internet. I finally have it again but I need to upgrade to 8.04. When I went to the Update Manager, I checked for Updates and it gave me this message:


W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263



So what do I do???

---

### Post by Partyboi2 on 2008-09-06
before upgrading make sure you disable all 3rd party repo's in Software Sources (System>Admin>Software Sources)

---

### Post by tahirih on 2008-09-06
I did that and the "checking for updates" box keeps repeatedly popping up. And it doesnt show any updates...

---

### Post by Pumalite on 2008-09-06
Run:
sudo apt-get update
sudo apt-get dist-upgrade
(before you attempt to upgrade)

---

### Post by kshane on 2008-09-07
> **Pumalite said:**
> Run:
sudo apt-get update
sudo apt-get dist-upgrade
(before you attempt to upgrade)

Yeah...  You should have your current system up to date before attempting to upgrade your distro...

---

### Post by lukjad on 2008-09-07
From personal experience, the best choice is to copy your /home/yourusername folder to an external media and wipe and reinstall with the new 8.04 CD. I tried to upgrade to 8.04 from 7.04 and ended up with a horrid mess.

---

### Post by tahirih on 2008-09-07
thanx for all the advice, guys. I think I'm just gonna do what lukjad007 suggested because I have 21,357 updates. Like I said, It's been a while since I've been online :lolflag: Thanks guys!

---

### Post by lukjad on 2008-09-07
Hope all goes well!

---

