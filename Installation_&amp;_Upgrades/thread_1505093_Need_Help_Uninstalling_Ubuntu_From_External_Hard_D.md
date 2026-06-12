---
title: "Need Help Uninstalling Ubuntu From External Hard Drive"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Athanar on 2010-06-08
Hi, I've been using Ubuntu for a few weeks now, and I like it a lot, but when I used the automatic partitioning tool on my portable hard drive (where I was installing it, it was my first time) I accidentally allotted half of the 640 GB to Ubuntu. Much more than it needs, it's unable to be accessed by Windows now. (I wanted around 40 GB for Ubuntu. Still more than it needs, but not too cluttered.)

However, I can't figure out how to erase the partition from the drive. I tried going in with the Windows Vista Drive Manager (or whatever it's called, the one that lets you manage partitions) and couldn't erase the partition. (I don't think I'd have any problems converting the partition back and combining the pieces again after doing so to work from scratch.)

Does anybody have any idea how to do this so I can reinstall Ubuntu properly?

Oh, and GRUB is on the portable as well, so I won't have trouble with Windows booting up afterward, it's the main booter. (When the portable HD isn't plugged in, my laptop just boots Windows without asking about Ubuntu.)

---

### Post by darkod on 2010-06-08
The windows Disk Management should give you option to delete the partition. It can't recognize it as linux partition but it should be able to delete it.

Another option is to have the usb hdd connected but boot from the ubuntu cd in live mode. Open Gparted in System-Administration, select the correct hdd and delete the partition(s) you want. If the swap partition is mounted in Gparted (with a key symbol next to it), just do right-click, Swapoff.

To apply the changes in Gparted you need to click the green button. Nothing is applied until you do.

---

### Post by Athanar on 2010-06-08
Thank you. I managed to delete the partition using the Disk Management system (it wouldn't let me before for some reason, but I tried again and it did). Now I just have to wait to let the space format. (For some reason, it won't let simple unallocated space get added, I think they both need to be formatted the same way so that the space can be used the same way.)

---

### Post by garvinrick4 on 2010-06-08
gparted program does have a resize option that works fine if you wish to make a partition larger or smaller without erasing your install.

---

### Post by Athanar on 2010-06-09
Oh. Well, that's good to know for the future. Too late now, though, at least for me. (I try to post updates in topics like this when I can, including on other sites, to help document what's happening for others that encounter the issue, so they can do what I've done to fix their problems, hence the continuous updates.) Anyway, I want to create several partitions and try a couple of other Linux builds as well, so I think this method is best in my case.

Edit: Okay, so formatting it was useless. Found I had simply overlooked a detail. (When you choose to extend a volume, make sure the amount the system fills in doesn't exceed the available amount by anything. Especially 1 MB. Hurts when you wait for hours only to find that out.)

---

