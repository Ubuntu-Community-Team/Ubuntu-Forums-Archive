---
title: "p965: feisty and gutsy won't boot"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by stijngysemans on 2007-08-27
EDIT: read my last post: problem persists when using Gutsy gibbon RC

system: 
*core 2 duo
*msi p965 motherboard with Jmicron chipset
*vista dual boot
*one sata harddrive connected to (according to my bios) the second of in total three connection.

1. tried to install feisty fawn; result: failed to boot after the installation
```

ata4: failed to recover some device, retrying in 5 seconds

```

2. i tried to change the menu.lst (by adding the -noapic line) but i can't find this file during my live cd. If I run the command
```

sudo fdisk -l

```
the result is an empty list! No harddrives are recognized apparently?

3. tried to install gutsy, maybe that could fix the problem (having a newer kernel is always better for new hardware). The problem persists: It can't boot after the install, only this time i do have a small commandline that I can use with limited commands.

I know a lot of people are having problem with this Jmicron chipset, but that shouldn't be the problem. It has been fixed in feisty fawn final. Before the final, I even couldn't boot the live-cd on this machine!

I don't want to get stuck here with vista only on this machine... i'm getting a litle bit desperate.

---

### Post by Pumalite on 2007-08-27
You have lots to read:

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87617](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87617)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

[http://www.mail-archive.com/opensuse-factory@opensuse.org/msg04757.html](http://www.mail-archive.com/opensuse-factory@opensuse.org/msg04757.html)

[http://www.hardforum.com/showthread.php?p=1031354605](http://www.hardforum.com/showthread.php?p=1031354605)

[http://lists4.opensuse.org/opensuse-factory/2006-10/msg00202.html](http://lists4.opensuse.org/opensuse-factory/2006-10/msg00202.html)

[http://ubuntuforums.org/showthread.php?t=375853&page=2](http://ubuntuforums.org/showthread.php?t=375853&page=2)

---

### Post by stijngysemans on 2007-08-28
> **Pumalite said:**
> You have lots to read:

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

-the a motherboard is a neo-f, so the problem doesn't apply to me. Also referred kernel is older.

> 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87617](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87617)

-this is during the livecd boot. This pc just boots fine during the live cd.

> 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

the fix is released in the 2.6.20 kernel. This problem should have been resolved. (I'm referring to this problem in my start post.
> 
It has been fixed in feisty fawn final. Before the final, I even couldn't boot the live-cd on this machine!


> 
[http://www.mail-archive.com/opensuse-factory@opensuse.org/msg04757.html](http://www.mail-archive.com/opensuse-factory@opensuse.org/msg04757.html)

Now the system can access the IDE bus, but it apparently can't access the SATA drive.
> 
[http://www.hardforum.com/showthread.php?p=1031354605](http://www.hardforum.com/showthread.php?p=1031354605)

-I don't know about this one.
> 
[http://lists4.opensuse.org/opensuse-factory/2006-10/msg00202.html](http://lists4.opensuse.org/opensuse-factory/2006-10/msg00202.html)

-same problem as referred on the mail-archive of opensuse
[http://ubuntuforums.org/showthread.php?t=375853&page=2](http://ubuntuforums.org/showthread.php?t=375853&page=2)[/QUOTE]

In general, those problems have some to do with booting from the live cd, those have been fixed for me. The machine 'just' doesn't boot after the install. Thanks

---

### Post by stijngysemans on 2007-10-13
Again. it still isn't possible to install a version of ubuntu on this particular machine!

I've tried gutsy gibbon RC. It installs without a problem but after the reboot i still got those "ata4: failed to recover some devices" messages. I plug out both dvd-rom drives and the pc boots fine! hey I tought: yes we have finally solved the problem: we just need to buy new dvd drives!

BUT. After setting up Ubuntu (installing some games and stuff), we reboot the machine and again the problem arises: ata4: failed to recover some devices (in recovery mode, in normal mode, the bar just hangs their). Sadly. i'm a little bit frustrated right now.

How can I solve this problem so that my cousin can enjoy his Ubuntu pc?
Thx!

---

### Post by stijngysemans on 2007-10-13
problem solved (i think) by adding irqpoll to /boot/grub/menu.lst

---

### Post by stijngysemans on 2007-10-16
tip for others:
when problem persists after a kernel upgrade, recheck your menu.lst!

---

