---
title: "mount via etc/fstab doesn't work"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by nafihsus on 2010-06-19
I have following entries in /etc/fstab trying to mount 4 directories of my nas. The first two work fine, the 'pictures' and 'cenk' directories fail.

eldenas:/music		/mnt/nas-music		nfs
eldenas:/video		/mnt/nas-video		nfs
eldenas:/pictures 	/mnt/nas-pictures	nfs
eldenas:/cenk		/mnt/nas-cenk	cifs user,uid=1000,rw,suid,credentials=/etc/credentials 0 0

I use Ubuntu 9.1.
Any help is highly appreciated.

Knowing that this might be the wrong forum to ask a related question:
I do get access from my win7/winxp clients to the directories under 'music' but I can't see any music files. No issue from ubuntu clients.

---

### Post by dino99 on 2010-06-19
dont get headache with fstab, install and use mountmanager to deal with partitions and devices rights ( system admin mountmanager)

---

