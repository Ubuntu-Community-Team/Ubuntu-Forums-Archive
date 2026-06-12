---
title: "Fresh install fails on boot"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by jon.mithe on 2010-09-13
Hi,

Recently freshly reinstalled ubuntu 10.04 on a new / blank hard drive and it now crashes on startup.

Quick version:  I have a nvidia Quadro NVS 295, it gets to the point just after the bios with the flashing dash, seemingly tries to init xserver / gdm then crashes.  Keyboard lights go off but the pc stays on, and just sits there with the monitor in power saving mode.  Tried in recovery mode, the blue / grey ascii terminal thing pops up for less then a second then the display crashes in the same way.

Swapping with an ATI card borrowed from elsewhere, the new install will boot quite happily.

Anyone know how I can get 10.04 to boot with a nvidia quadro NVS 295?  Its a bog standard card and my version of 10.04 I upgraded to on my old hard drive works fine.

Its a reasonably new dell XPS 64bit pc.

Longer version:
I run 3 monitors using a PCI-e x16 NVS 295 and a PCI NVS 295.  This worked great under 9.10 and 10.04.  Boss gave me a solid state HD so trying to install 10.04 on that.

However on my first install attempt the live CD failed to load (same problem as above, gets to init'ing the display and crashes with no output).  I removed the second PCI card to run with just the 1 PCI-e x16 nvidia card, this time the live CD worked fine and I could install, but I am stuck on the boot problem.

Am now quite stuck.  Booted into the system using the ATI card and did an update just incase something may have changes / been fixed but the issue persists -- stuck!

Thanks for any help,
Jon

---

### Post by jon.mithe on 2010-09-13
ha, sods law you look around for help cant find any so post on a forum, then look around some more and find the answer,

Found this link:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

In case that goes down, need to get to the grub bootloader (e on grub (hold shift if not appearing after bios)) and need to replace "quite splash" with "nomodeset" for nvidia cards.  Apparently this may happen with other cards and theres similar fixes.  Then install the proprietary nvidia drivers.  Not 100% sure if this will work on the next kernal up
grade, but its a simple fix next time, I think using the nvidia drivers  will fix this though buy the sounds of it.

Awesomes,
Jon

---

### Post by sikander3786 on 2010-09-13
> **jon.mithe said:**
> ha, sods law you look around for help cant find any so post on a forum, then look around some more and find the answer,

Found this link:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

In case that goes down, need to get to the grub bootloader (e on grub (hold shift if not appearing after bios)) and need to replace "quite splash" with "nomodeset" for nvidia cards.  Apparently this may happen with other cards and theres similar fixes.  Then install the proprietary nvidia drivers.  Not 100% sure if this will work on the next kernal up
grade, but its a simple fix next time, I think using the nvidia drivers  will fix this though buy the sounds of it.

Awesomes,
Jon
Glad you got it working. It is always a good idea to search the forums before posting a thread. In most cases, Google is also a handy choice. Hope you are having a good time with Ubuntu.

Regards.

---

