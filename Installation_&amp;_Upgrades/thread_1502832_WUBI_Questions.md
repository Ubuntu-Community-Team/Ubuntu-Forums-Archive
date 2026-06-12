---
title: "WUBI Questions"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by iFuzo on 2010-06-06
Is there anyway for me to increase the ubuntu partition size after installing?

E.g WUBI only allows you to have a 30GB Partition but I make it 80GB instead?

---

### Post by bcbc on 2010-06-07
See [https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?")

However, I don't recommend this, since your wubi install is contained in a virtual disk, and I would imagine, the chance of corruption is greater is a file that big (and probably performance).

Finally, be aware that LVPM hasn't been updated or tested on recent versions of ubuntu. I recommend backing up your root.disk (that contains your ubuntu file system) file before attempting this.

With that amount of free space, why don't you consider a traditional dual boot with a dedicated partition?

---

### Post by sanderd17 on 2010-06-07
I think the day has come for a real installation. I've used wubi to but when I had not enough space, I switched to a dual boot. Now I only have ubuntu and no windows anymore.

If you want to keep your settings, just store your home directory somewhere safe en copy paste the parts of your settings you need to your real installation. 

all settings are in the folder with the name ".app_name" under your home directory. That way, you wont lose Firefox add-ons, e-mail profiles ...

---

### Post by iFuzo on 2010-06-09
> **bcbc said:**
> See [https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")

However, I don't recommend this, since your wubi install is contained in a virtual disk, and I would imagine, the chance of corruption is greater is a file that big (and probably performance).

Finally, be aware that LVPM hasn't been updated or tested on recent versions of ubuntu. I recommend backing up your root.disk (that contains your ubuntu file system) file before attempting this.

With that amount of free space, why don't you consider a traditional dual boot with a dedicated partition?

And how would I go about this instead?

---

### Post by bcbc on 2010-06-09
> **iFuzo said:**
> And how would I go about this instead?

First thing you do is back up your important data. To back  up your ubuntu install look for the c:\ubuntu\disks\root.disk file and back it up (it'll be 30GB in your case, the drive letter may be different depending on where you installed wubi). Note, you can use the backup to copy over the /home directory or just data and settings later. ([This chapter]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") in the wubi guide shows how to loop mount your root.disk to get at it later.)

After backups, you need to find a partition or create one big enough for ubuntu. If you are running windows vista/7 as your primary OS, you can shrink the drive within the disk management utility. If you have XP you can use gparted or another utility to create a partition. 

Then you just install to that partition. Here's a link that'll get you started: [https://help.ubuntu.com/10.04/installation-guide/index.html](https://help.ubuntu.com/10.04/installation-guide/index.html)

---

