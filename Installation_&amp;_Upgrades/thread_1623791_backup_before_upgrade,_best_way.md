---
title: "backup before upgrade, best way"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by railz68 on 2010-11-17
I am currently on Hardy 8.04. I want the latest ubuntu version, but had a bad experience with the last update, hence the version I am on (upgrade fear). Just stuck with, everything works. I kinda need to update now.

Whatever went wrong last time, I did backup /home and had to do fresh install. However, after copying everything back to /home, I had a nightmare of permission issues with nearly all files/folders.

I plan to backup /home again, but is there a "proper" way of doing it so that I can be backup and running as easily as possible ?.

Nothing on the hardware end will change, I will try to update, and if it fails (like last time), I will install fresh. I will setup user name and password the same.

anyhow, if anyone can tell me best, or proper way of backing up /home with restore in mind, thank you.

---

### Post by cybergnome on 2010-11-18
Take a look at Partimage.

---

### Post by Mark Phelps on 2010-11-18
Partimage, while it will work with 8.04, will not work with the newer Ext4-filesystem-based distros.  So, if you use this, you use a product that can't be used to backup/restore your new install.

Clonezilla, on the other hand, works with old and new filesystem formats.  Look into using that instead.

---

