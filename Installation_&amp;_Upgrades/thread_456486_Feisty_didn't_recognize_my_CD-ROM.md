---
title: "Feisty didn't recognize my CD-ROM"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-05-27
It says 'special device /dev/scd0 does not exist'.What to do?. It's a brand new Pioneer with the latest firmware. Thanks in advance.

---

### Post by Pumalite on 2007-05-27
I just got a bunch of interesting links from a previous post:

[http://ubuntuforums.org/showthread.php?t=449357](http://ubuntuforums.org/showthread.php?t=449357)
[http://lkml.org/lkml/2007/3/23/227](http://lkml.org/lkml/2007/3/23/227)
[http://lists.opensuse.org/opensuse-bugs/2007-05/msg00025.html](http://lists.opensuse.org/opensuse-bugs/2007-05/msg00025.html)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706)

Looks like we are all waiting for an answer and that this is a know bug of 7.04 that the developers have not bothered to fix. I don't think that installing Lilo is the answer. There should be a proper fix from the developers. It seems that this is an out loud secret.

---

### Post by Robin T Cox on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try this:

Add the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

---

### Post by Pumalite on 2007-05-28
> **Robin T Cox said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96826) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try this:

Add the word 'irqpoll' (without quotes) to the kernel line in /boot/grub/menu.lst thus:

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash irqpoll

Thanks a lot. I did it. I'll keep my fingers crossed. What do you think of the 16 update? It screwed me up. I'm back in 15.

---

### Post by Robin T Cox on 2007-05-28
The 16 update seems to have rectified my problem about K3b recognising the CD burner, so I'm OK with it. At the same time, my KDE update from 3.5.6 to 3.5.7 seems to have borked the recognition of my 3 HDDs ( I have 3 HDDs in this box), so it seems I can't win! Anyway, my work-around has been to go over to Xfce - and I am delighted with the result: lots more speed, so that I can now use Beryl plus the Screenlets via the widgets plugin.

It's an ill wind that blows in a soap factory ... :)

---

### Post by Pumalite on 2007-05-28
> **Pumalite said:**
> Thanks a lot. I did it. I'll keep my fingers crossed. What do you think of the 16 update? It screwed me up. I'm back in 15.

It didn't work for me. Bad luck. But then, in the meantime my kernel had updated to 16. I had to go on Recovery Mode and reinstall my NVIDIA Driver. No problem. So, I went in and I changed the line in menu.lst corresponding to kernel 16. Rebooted, but didn't work either. Anybody else with other ideas?

---

