---
title: "Can I install Xubuntu on a computer that already has ubuntu?"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by snowboard975 on 2007-02-21
I want to try Xubuntu 6.10, but my computer already has Windows XP and Ubuntu 6.10. Can I install Xubuntu on the same partition with Ubuntu? Or Do I have to make another partition for Xubuntu?
I have no idea how to configure my partitions.
Will I be able to triple boot among Windows XP, Ubuntu, and Xubuntu?
Sorry for too many questions. 
Thank you!

---

### Post by dcstar on 2007-02-21
> **snowboard975 said:**
> I want to try Xubuntu 6.10, but my computer already has Windows XP and Ubuntu 6.10. Can I install Xubuntu on the same partition with Ubuntu? Or Do I have to make another partition for Xubuntu?
I have no idea how to configure my partitions.
Will I be able to triple boot among Windows XP, Ubuntu, and Xubuntu?
Sorry for too many questions. 
Thank you!

I believe that you can just install the Xfce components on you existing system, and then select either Gnome or Xfce when the Ubuntu GUI boots (I don't know how, do a search if you want the details).

If you want a totally separate system, then you just need sufficient available disk space to do a Xubuntu install, the installation process should take care of all the Grub boot entries for the various systems.

---

### Post by rsambuca on 2007-02-21
Yeah, just enter the following commands and you will be able to select either one at login in the "sessions" selection
```
sudo aptitude update
```
```
sudo aptitude install xubuntu-desktop
```
You can also install the kubuntu destkop with```
sudo aptitude install kubuntu-desktop
```

This will save you from repartitioning and installing from scratch.

---

### Post by snowboard975 on 2007-02-21
Thanks a lot, guys!
Xubuntu is quite neat! I think I'll like it.

---

