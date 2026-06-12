---
title: "XP Dual Boot - Uninstall Questions"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by okcomputer on 2006-10-27
I've searched and read lots of threads here and elsewhere, but I've yet to find a solid answer from someone who's performed the same operation I'm wanting to attempt.

I've used Partition Magic to create a partition on my main Windows XP drive. I installed Ubuntu. Things work well, but I need the space back, and I don't use Ubuntu as much now that I also have a Mac.

So, I'm wanting to remove Ubuntu and reclaim that hard drive space for Windows to use.


I've read that I can:

a) Reboot with the XP CD and run the Recovery Console
b) Run fixmbr
c) Run fixboot
d) Reboot and then Windows should load fine
e) Reclaim the space with Partition Magic

... I think.


When I run fixmbr, however I get this message:

"This computer seems to have a non - standard or invalid master boot record.

FIXMBR may damage your partition tables if you proceed."


Will running fixmbr and then fixboot remove GRUB and allow me to boot Windows normally? Is that the order I should run them? Is there a risk I'll lose all my data? Are the above steps the best way to do this?

Thanks so much!

---

### Post by waynep on 2006-10-27
I just did what you did except I had Fedora Core 5 as the other boot option. I did it wrong but recovered fine. It looks like you have the right order. Yes definatly run fixmbr before wiping out your /boot partition as Grub reads the conf file from there.

I got the same error message you state. I went ahead and proceded with fixmbr with the intended results. Grub gone and Win XP booting normally.

The way I did it was the following:

1 - Gparted to remove partitions.
2 - Found I could not boot since Grub could not read config from /boot partition. It was gone after step one.
3 - Boot from XP disk to recovery console
4 - run fixmbr seeing same message you stated but proceeded
5 - ended up with normal booting Win XP system and recovered disk space. 

When you finish, Windows will run a chkdsk. It's normal after you alter the Win partition size.

-wayne

---

