---
title: "Move Or Reinstall?"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by jsimmons on 2005-06-24
I currently have a mobile rack so that I can have Ubuntu on one drive, and Windows on another. When I need to change OS's, I turn off the system, swap drives, and turn it back on again. I've decided this is too much of a hassle (and not necessarily easy on the electronics).

I am going to install another SATA drive and I want to move my current Ubuntu install over to that drive (without having to reinstall Ubuntu), and then setup GRUB on my Windows drive so I can dual boot.

Will I experience any problems doing this? The reason I ask is because I'll be moving Ubuntu from /dev/hda to /dev/sdb, and I'm wondering if any OS-specific stuff cares about that kind of thing.


Should I just throw in the towel and reinstall Ubuntu from scratch on the new drive, or is what I want to do doable?

---

### Post by nictuku on 2005-06-24
You don't have to reinstall.

That procedure is simple for an intermediate user.

Follow the instructions in this post:

[http://ubuntuforums.org/member.php?find=lastposter&t=44086](http://ubuntuforums.org/member.php?find=lastposter&t=44086)

In your case, you will also need to edit /etc/fstab *AND* /boot/grub/menu.lst to reflect the change from /dev/hda to /dev/sdb.

That will be all, though.

Good luck!

---

