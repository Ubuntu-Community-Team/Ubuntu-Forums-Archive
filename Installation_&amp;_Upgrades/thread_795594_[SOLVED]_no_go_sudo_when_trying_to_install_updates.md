---
title: "[SOLVED] no go sudo when trying to install updates"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by davehkent on 2008-05-15
I, along with quite a few others it would appear, am having trouble installing updates onto my Hardy Heron 8.04 system. There are currently 36 to install, but when I click on the 'Install Updates' button, nothing happens.

 So, I've been reading the other posts on this forum with the same problem and trying to follow the suggestions posted there, but this is where my problem is. Any suggestion to enter a command at the Terminal using sudo is failing. For instance, if I enter 'sudo apt-get update' I get the following reply: 'sudo: /etc/sudoers is mode 0777, should be 0440'. I can't change the file permissions using 'sudo chmod' either, so I'm going round in circles here!

I've obviously done something wrong here in trying to fix the update problem, and any help with both problems would be appreciated.

Thanks
davehkent

---

### Post by mahuyar on 2008-05-16
Have you tried with the "recovery mode" at the GRUB menu?  That would grant you root access automagically, but you'll manually have to mount the root partition.  Then, you'll be able to change the permissions on /etc/sudoers.

This is at least a way what I can think of atm.  Post back if things don't go smooth.  GL!

---

### Post by davehkent on 2008-05-18
Thanks, that appears to have solved the problem, updates now installed!

---

