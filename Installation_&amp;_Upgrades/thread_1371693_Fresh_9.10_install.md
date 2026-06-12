---
title: "Fresh 9.10 install"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by DemonParasite on 2010-01-03
I currently have Ubuntu 9.10 installed, as an upgrade from 9.04. I want to do a fresh install of 9.10, for a few reasons such as upgrading to ext4. I don't have an extra hard disk, so how would I go about backing up and restoring my home folder and synaptic markings?

---

### Post by zvacet on 2010-01-04
Maybe [this]("http://www.psychocats.net/ubuntu/backup") will be helpful.

---

### Post by DemonParasite on 2010-01-04
> **zvacet said:**
> Maybe [this]("http://www.psychocats.net/ubuntu/backup") will be helpful.

Well, I was thinking more along the lines of using my current media partition to store my synaptic markings file, which is the easier part. But how would I go about backing up my home folder? Assuming that I keep the username the same on both installs, could I simply copy and paste the home folder onto the new install, to keep all my program settings?

---

### Post by drs305 on 2010-01-04
In the same link provided earlier (pyschocat's site) there is a section on moving /home. By having /home on a separate partition during the install you will guarantee that the settings that need updating or creating are accomplished. Many of your settings won't change, but some will. Even with the same username, merely copying the contents back into a new install isn't the way to do it.

I usually do make a backup copy of my entire home folder (and /etc) and put it somewhere so that I can go in and retrieve selected files/folders, but I only paste them back into a new installation in very specific instances.

---

### Post by tachuela on 2010-01-04
Try Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

