---
title: "Dual boot with windows vista"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by omeron on 2008-11-14
Hi, 
I'm trying to install Ubuntu with Vista. Vista is installed and I have a 60GB partition ready for Ubuntu. the thing is that the installer tries to resize the vista partition or install on the entire disk. I want it to install to /dev/sda3 (attached is a screenshot). any ideas?

---

### Post by kgavriil on 2008-11-14
Click on the manual option of the partitioner and make a swap partition and assign the "/" root partition to /dev/sdax where x stands for 3 in your position.

---

### Post by blackened on 2008-11-14
I've always found the guided partitioner to be kinda flaky. I would suggest manually paritioning if you know what you're doing.

---

### Post by alwez_loner on 2008-11-14
Have you done the initial partition?

You need to partition the hard drive with partition magic then you can direct the installation in that partition.

Hope this helps.

---

