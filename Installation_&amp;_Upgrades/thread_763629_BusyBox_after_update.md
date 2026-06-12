---
title: "BusyBox after update"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Swagman on 2008-04-23
I finally persuaded my mate to put Ubuntu on his laptop. It's an Asus A4Book, Athlon 64, 3200 with 512mb ram.

Installed a treat. Lovely stuff.

But.....
Whenever it updates, after reboot I am dumped at BusyBox..

Initramfs _

It initially did this on the beta ISO I had handy so I d/l'd the latest ISO and it sorted it. I'm due to give him this back tonight so I fired it up and let it install latest updates.

Guess what?

Yup.. BusyBox.... The mind boggles !!

Just dropped into recovery mode... error message =

mount: Mounting /dev/disk/by-uuid/CCA0-6A24 on /root failed: No such device
mount: Mounting /root on /host failed: Invalid argument
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox

Well... gee... Thanks !!

System is installed within windows using wubi

Can anyone help me suss this out please ? I suspect I'm going to have remove this *Again* and re-install.

---

### Post by Phil Rigotti on 2008-04-23
Hi Swagman,
Now this might not seem too helpful, but just wanted to say that I had the same problem this week. Installed Ubuntu 8.04 Beta with Wubi and was really happy with the results. I spent some time installing modems and setting up e-mail accounts, etc. etc...then I accepted an update which took ages. Once it had updated I was left in the same position as you...no root disk and BusyBox. 
My plan is to wait until thursday 23rd when 8.04 stable version is out and try again...hopefully then shouldn't need so many updates.
What does everyone think?

---

### Post by Swagman on 2008-04-23
I've deleted it and whilst rummaging around I noticed the filesystem on this laptop is FAT32 ? running XP home ?

Weird.. There is a NTFS file converter on the desktop so I ran that. rebooted  etc and reinstalled 8:04.

Now it hangs on the black text screen for ages whilst it activates the swap ?
It's running though after the initial update although I got a requester saying something had failed.

Now it's the long winded process of installing restricted extras... Ktorrent, art manager .. etc etc.

---

### Post by tadcan on 2008-04-23
This might help

[http://ubuntuforums.org/showthread.php?t=602957&page=3](http://ubuntuforums.org/showthread.php?t=602957&page=3)

---

