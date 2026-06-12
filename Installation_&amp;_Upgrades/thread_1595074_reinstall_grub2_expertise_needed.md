---
title: "reinstall grub2 expertise needed"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by philetus on 2010-10-12
SOLVED.
THIS did the trick:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)



Here's what I get for:
sudo grub-install --root-directory=/media/daa35788-a8f4-42bd-a265-85cc91b9b04f /dev/sda1


ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/daa35788-a8f4-42bd-a265-85cc91b9b04f /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

---

### Post by tommcd on 2010-10-12
> **philetus said:**
> Here's what I get for:
sudo grub-install --root-directory=/media/daa35788-a8f4-42bd-a265-85cc91b9b04f /dev/sda1

From the Ubuntu live CD, try it the way it says in this tutorial:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
I think the problem is that you are trying to reinstall grub2 to **/dev/sda1** instead of **dev/sda**. You want to install grub2 to the MBR of your hard drive.

---

