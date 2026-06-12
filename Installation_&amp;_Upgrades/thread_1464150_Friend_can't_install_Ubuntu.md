---
title: "Friend can't install Ubuntu"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by Jessi on 2010-04-27
I have been an Ubuntu user for a little over a month and have had no problems with it. I have recently gotten a friend interested and he wants to install it too. But when he tries, he gets this error...

> sed: warning: failed to get security context of /etc/default/console-setup: operation not supported

=C

I think he's install it from an external drive on to a windows xp laptop...

Any help?

---

### Post by gadolinio on 2010-04-27
Can he boot with a liveCD or liveUSB? When does that message appear?

---

### Post by Jessi on 2010-04-28
> [02:32:50] Brandawg says:
I don't know what liveCD or liveUSB is
[02:33:06] Brandawg says:
during start up, before I pick an OS
[02:33:11] Brandawg says:
I can choose Ubuntu on XP
[02:33:14] Brandawg says:
I choose Ubuntu
[02:33:19] Brandawg says:
it goes through stuff for awhile
[02:33:22] Brandawg says:
then that message shows up
[02:33:25] Brandawg says:
and nothing happens

In his words... like I said I think he said earlier he was installing the ISO from an external hard drive or a flash drive.

---

### Post by gadolinio on 2010-04-28
Tell him to boot from the liveCD or liveUSB, the media in which he has ubuntu. He must have a CD or thumb drive from which he first installed the operative system (OS). The liveCD is the CD, the liveUSB is the thumb drive in which he has the OS.
It seems to me that he's installed ubuntu with wubi; that is, he initially turned the computer on with windows normally, then inserted the CD or USB with ubuntu, and chose to install ubuntu inside windows, using Wubi.
Well, I would try to boot directly with the usb thumb or CD. Insert it first, then turn the computer on, and a menu appears; choose "try ubuntu without making changes to the system". If it works, the media should be ok.

If the computer goes directly to windows, it might be due to the BIOS being set to boot from the hard disk drive first, instead of CD and/or USB before the hard disk drive. To fix this, he has to turn the computer on, and as soon as it's booting press a key which can change according to the computer: It can be DEL, F2, F8, etc. The screen usually shows a message like "Press DEL to enter BIOS setup" or something like that while starting up. By pressing that key and maybe holding it pressed, a blue screen appears. Surf the menus there and look where to set the booting order; CD and USB should be before hard disk.
Hope you find this useful...

---

