---
title: "usb wifi causes kernel panic with Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by 1feistymedic on 2007-11-14
I have a linksys wusb54g usb wifi adapter that worked fine under Feisty.  I did a fresh install on another desktop with Gutsy and followed the same directions that I used for Feisty and got it to work perfectly.  Once I rebooted the system the following occurred:

I get a flashing keyboard and the system wont finish booting.

I did a hard shutdown and on the next restart did the following:

Hit escape and boot into Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode).

If wifi dongle plugged in at boot, boot stops and gives this error message:

[ 82.325884] Kernel panic – not syncing: Creation of kmalloc slab kmalloc_dma-2 size=2 failed.

[ 82.325886]


If plugged in after full "recovery" boot, automatically get this message

root@ubuntuserver1:~# [ 75.112448] rt73: Firmware not load

either way, I get the two lights on the keyboard next to the num lock light flashing and the system locks up.

If I allow the system to do a normal boot it boots fine.  As soon as I plug in the dongle, the keyboard flashes and the system locks up.

this is a wusb54gc that can surf when plugged up until system rebooted

I used the directions found at the following link:

[http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4](http://ubuntuforums.org/showthread.php?t=512647&highlight=1feistymedic&page=4)

Any suggestions?  Wired ethernet does not cause this problem

---

### Post by K.Mandla on 2007-11-14
If it was working under Feisty and you're getting error messages under Gutsy, you should scan Launchpad for a bug report, and file one if you don't find anything similar. I used to have a similar problem with PCMCIA cards, where inserting them caused a kernel panic. There was already a bug filed, and when I confirmed it, it got fixed within a week or two.

That might not help you in the short term, but it does help out if the devs can get as much information as possible. ;)

---

### Post by 1feistymedic on 2007-11-14
How do I do that? I need a nooby walkthrough.  Thanks.

---

### Post by 1feistymedic on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Never mind.  I filed a bug report.  I am just waiting for it to be looked at.  Thanks.  The link is:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162653)

---

### Post by 1feistymedic on 2007-11-14
Post Moved To 

Networking And Wireless

---

