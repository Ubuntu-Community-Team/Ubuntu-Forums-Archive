---
title: "Dual-Booting Vista and Ubuntu"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by cbrian on 2008-05-05
I would like to dual boot vista and ubuntu. I have the LiveCD burned and everything, but looking through the documentation it looks like the partitioner on the disc will erase everything on my hard drive. how can i install ubuntu without doing that?

---

### Post by Pumalite on 2008-05-05
Partition with the Vista partitioner first. Provide at least 20 GB for Ubuntu od 'unallocated space' Intall Ubuntu and use that free space:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
(you have to go 'Manual' to do this)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by fmartinez on 2008-05-05
> **cbrian said:**
> I would like to dual boot vista and ubuntu. I have the LiveCD burned and everything, but looking through the documentation it looks like the partitioner on the disc will erase everything on my hard drive. how can i install ubuntu without doing that?

I've found the easiest way to do this is to: 
- Boot into Vista. 
- Use the Vista Partitioner to resize your disk to create "Unallocated Space" How much is your choice.
- Once this is done reboot into the Live CD and run the installer.
- When prompted where to install Ubuntu choose the option: "Use largest continous free space" option. 
- This will install Ubuntu on the free space and not touch you Vista partition. 
- The Ubuntu installer will take care of the rest. 
REMEMBER TO ALWAYS BACK UP YOUR DATA! JUST IN CASE.

---

### Post by cbrian on 2008-05-17
is it possible to do this without using the vista partitioner? i don't have admin so i can't use it

---

### Post by Pumalite on 2008-05-18
You have to use the Vista partitioner.

---

