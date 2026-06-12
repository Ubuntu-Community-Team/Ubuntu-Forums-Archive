---
title: "Synaptic and &quot;sudo&quot; stops working after update xubuntu 8.04"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by cosmx on 2008-06-01
Synaptic and "sudo" command stops working after updating Xubuntu 8.04 with latest updates.  

Synaptic will not start, and also, when "sudo apt-get" is typed in terminal the reply is:
"sudoers is owned by gid 1003, should be 0"

Please help!!!

---

### Post by tamoneya on 2008-06-01
thats pretty odd.  I have no clue why it went messing with sudoers but take a look at this post:
[http://ubuntuforums.org/showthread.php?t=14366](http://ubuntuforums.org/showthread.php?t=14366)
Shows how to fix sudoers.  You are just going to have to change the permissions/group ownership around.

Note: instead of editting the grub boot parameters you can just select the recovery option in grub.

---

### Post by cosmx on 2008-06-01
> **tamoneya said:**
> thats pretty odd.  I have no clue why it went messing with sudoers but take a look at this post:
[http://ubuntuforums.org/showthread.php?t=14366](http://ubuntuforums.org/showthread.php?t=14366)
Shows how to fix sudoers.  You are just going to have to change the permissions/group ownership around.


Note: instead of editting the grub boot parameters you can just select the recovery option in grub.

Editing as suggested does not seem to work - how do I find the recovery option in grub? 
(sorry about what may seem a silly question to the wizards that be!)

---

### Post by PmDematagoda on 2008-06-01
> **cosmx said:**
> Editing as suggested does not seem to work - how do I find the recovery option in grub? 
(sorry about what may seem a silly question to the wizards that be!)

When you just start the PC up, there must be a place asking you to press Esc to view the GRUB menu, press Esc and then select the Recovery Mode entry.

---

