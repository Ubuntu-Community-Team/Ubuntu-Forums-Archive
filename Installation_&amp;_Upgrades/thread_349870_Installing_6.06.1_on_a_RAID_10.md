---
title: "Installing 6.06.1 on a RAID 10"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by CrazyToad on 2007-01-30
I'm trying to get Ubuntu 6.06.1 onto a software RAID 10. Is there a HOWTO or anybody have any advice for how to accomplish this? Thank you very much!

PS - I know /boot has to be on a RAID 1, that's no problem. I just want "/" to be on the RAID 10.

---

### Post by unisol on 2007-01-30
i dont know if it will help. try this:If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer

---

### Post by CrazyToad on 2007-01-30
> **unisol said:**
> i dont know if it will help. try this:If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer
Thanks for the response, unisol. I should have been more clear; I'm trying to install from the server cd and there's currently no OS installed on the harddrives.

---

### Post by nivis on 2007-06-05
Has anyone figured this out because I am having the same question, except for my problem is that it hangs on the partitioning creation.

---

