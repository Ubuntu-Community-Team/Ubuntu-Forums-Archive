---
title: "Wanting to install a third OS &lt;--- Need Help!"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by sammya on 2011-06-18
So at the moment I have Ubuntu 11.04 installed alongside Chromium OS Flow by Hexxeh.I followed his guide here which basically allows you to install Chrome OS next to Ubuntu and to appear in the GRUB (or GRUB 2) menu at boot.

Now I was wondering if it was possible to install a copy of XP, basically giving me a triple boot option onto my system. HDD space isn't a problem.

I was also wondering what would be the best steps to make this possible, if there are any existing guides and if it is possible to put the option of choosing to boot from XP in the GRUB menu?

Thanks a heap

---

### Post by mikewhatever on 2011-06-18
Step1: Make some unallocated space (Gparted, Live CD).

Step2: Install Windows.

Step3: Restore GRUB (Live CD).

If you need guides for any of the steps, search the forum or google.

---

### Post by sammya on 2011-06-18
how many partitions should i do? only reason i ask is because when i installed ubuntu over windows 7 i had to make 2 partitions.. same for installing chrome?

and following your brief instructions will i be able to boot windows through grub?

cheers

*edit*
only have a netbook so no cd-drive.

---

### Post by mikewhatever on 2011-06-18
Do as many partitions (whatever that means) as your installation of Windows require. Note, I didn't say you had to create partitions for Windows, just unallocated space, and then let Windows create partitions for itself.

Grub has no problem with Windows. In case Windows is not detected after Grub restoration, run **sudo update-grub** from a terminal window.

Since there is no cdrom, you'll have to use a USB stick, but then, you've probably installed Ubuntu using one, so that shouldn't be an obstacle.

---

### Post by sammya on 2011-06-18
> **mikewhatever said:**
> Do as many partitions (whatever that means) as your installation of Windows require. Note, I didn't say you had to create partitions for Windows, just unallocated space, and then let Windows create partitions for itself.

Grub has no problem with Windows. In case Windows is not detected after Grub restoration, run **sudo update-grub** from a terminal window.

Since there is no cdrom, you'll have to use a USB stick, but then, you've probably installed Ubuntu using one, so that shouldn't be an obstacle.

okay no prob thanks for your help

---

