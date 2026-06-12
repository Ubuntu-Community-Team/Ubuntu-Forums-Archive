---
title: "2 copies of Grub!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by GlennB on 2007-10-27
Hi All,

I'm hoping for some help with removing an excess copy of 'Grub' that I acquired while giving Suse 10.2 a try.

I triple-boot my laptop: XP, Ubuntu 7.10, and recently I added a Suse 10.2 install. I messed up during installation of Suse, and allowed it to install its own copy of Grub. Now I want to remove Suse from its partition, but that partition hosts the active version of Grub. Question is, how do I remove it safely?

Here's the setup:

hda2 (hd0,1) - mounts as the root of the Ubuntu install. The Ubuntu grub is in boot/grub relative to the root of this partition.
hda6 (hd0,5) - is where Suse lives. The active version of Grub is in boot/grub on this partition.

XP is on hda1.

I want to remove Suse and keep Ubuntu and XP. The question is, how can I reconfigure the system to use the Ubuntu grub (i.e. revert to the dual boot config I had before Suse went on).

I've done some reading about grub, and I think I may be able to do something like:

```
# grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
# reboot
```

However, I'm a grub newbie, and I'd be grateful for some pointers!

Many thanks,

Glenn.

---

### Post by confused57 on 2007-10-27
The instructions you have should work:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Ehtetur on 2007-10-27
> **GlennB said:**
> I want to remove Suse and keep Ubuntu and XP. The question is, how can I reconfigure the system to use the Ubuntu grub (i.e. revert to the dual boot config I had before Suse went on).

If SuSE installed on hda6, you probably have an hda3 and an hda5 (swap) partitions as well.
Anyway, if you're looking to dual boot  *buntu and win32, and to free up the space SuSE was using, why not delete all the linux partitions, keeping hda1, and do a fresh install of *buntu.
That way, it'll reinstall grub and it will be configured to dual boot.

---

### Post by meierfra on 2007-10-27
> # grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
# reboot

you need to start with "sudo grub" not  just "grub". Otherwise, it is correct.

---

### Post by louieb on 2007-10-27
Actually when it comes to kernel update time having separate Grubs for each distro is advantageous. Keeps them from stepping on the other distro kernel and menu.list entry.    And keeps you from  manually having to fix it. 

What you do is have one grub pointed to by the MBR. Then you use the configfile option or chainloader option to bring up the other distros grub. 
For more info search this page for **configfile** [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")
Good Luck.

---

### Post by GlennB on 2007-10-28
Thanks to everyone for the replies.

It worked perfectly - I now have one version of Grub on the Ubuntu partition, and the Suse partition's grub is no longer being used, so I can reclaim the disk space.

Thanks again,

Glenn.

---

