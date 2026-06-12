---
title: "About to upgrade to Feisty - What files to back up?"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Ebiggs on 2007-05-18
I'm planning on upgrading to Feisty in a few days on this PC, but there are a few things I'd like to keep as they are, settings-wise.  I had some troubles getting my monitors working the way I wanted, so backing up the xorg.conf file will work fine for upgrading, right?  I also want to keep my customized toolbars and probably my Beryl settings.  I'd guess I would keep the data in my home folder "./beryl" for the latter, but I don't know where the toolbar data would be kept at.

I'd appreciate any advice. :)

Edit:  This is currently running Edgy Eft Ubuntu.

---

### Post by lw5 on 2007-05-19
I'd backup my entire /etc and /home/$user directories. Feisty should use your original settings but if something should go wrong you've got everything backed up.

---

### Post by Ebiggs on 2007-05-19
Okay, thanks.  I'll give it a shot now.

Edit:  So how do I archive /etc ?

---

### Post by pbw on 2007-05-19
If it's a one time local backup, just tar /etc into your home directory.

eg. 

tar czvf ~/etcbackup.tar.gz /etc

-- pbw

---

### Post by mlind on 2007-05-19
> **pbw said:**
> If it's a one time local backup, just tar /etc into your home directory.

eg. 

tar czvf ~/etcbackup.tar.gz /etc

-- pbw

You may need to do this as root user to get access for all files. put sudo before tar call or switch to root before doing the archive.

---

