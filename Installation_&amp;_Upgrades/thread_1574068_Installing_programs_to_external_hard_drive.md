---
title: "Installing programs to external hard drive"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by cazanon on 2010-09-13
Well heres the deal, I Installed Ubuntu to my little flash drive, not the live disk version but the full version, but my problem is now that i installed a few packages\programs i'm out of space on the card, can I install programs to the hard drive built in that i have windows 7 installed on? Pardon if i'm forgetting something a little knew to this idea.

---

### Post by Fafler on 2010-09-13
It's possible, but theres not really a easy way to do it. Look to free up some space instead. Or get a larger drive. Or install on your windows partition using wubi.

---

### Post by coffeecat on 2010-09-13
> **cazanon said:**
> Well heres the deal, I Installed Ubuntu to my little flash drive, not the live disk version but the full version, but my problem is now that i installed a few packages\programs i'm out of space on the card, can I install programs to the hard drive built in that i have windows 7 installed on?

Sort of - in theory - but it ain't straightforward.

App files are not installed in their own neat little folder in C:\Programs as in Windows. The executables and libraries go into /usr and the config files into /etc. At least, that's when the execs don't go into /opt.

What could be done in a situation like yours is to have /usr (which is the biggest directory in size) on its own partition. You would have to create a partition with a Linux filesystem on the internal drive - the Windows partition won't do. Then you would have to copy everything from /usr to the new partition, and then create a mountpoint and edit /etc/fstab. But you couldn't do these last three booted into Ubuntu on the flash drive. You'd have to use a live CD session with the USB drive plugged in or plug the USB drive into another Ubuntu installation and do the edits and copying from there.

And there are probably one or two things I've forgotten about to trip you up on the way. Fafler's suggestions are probably the best. :)

---

