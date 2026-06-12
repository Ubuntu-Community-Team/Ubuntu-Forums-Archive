---
title: "Move Ubunto to another FILE SYSTEM (not cloning partition!)"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by spamhog on 2012-10-16
Hello everyone!  I really hope this isn't a dumb question.

I want to to
- CLONE a system 
- to a PREEXISTING FILE SYSTEM,
- without copying a whole partition IMAGE.

Before grub2 it was rather easy to roll up all the content of "/" like a carpet, unroll it onto another filesystem, fix a couple of things, install grub ON IT abd boot it:
[http://lists.debian.org/debian-user/2005/10/msg01869.html](http://lists.debian.org/debian-user/2005/10/msg01869.html)

Now I see tons of instructions on how to move entire partitions and reinstall grub2 as bootloader, but not to do so between file systems.

HOWEVER
- I often have multiboot systems with different partition sizes which should be wise not to muck with
- it's much quicker to backup the content of a filesystem than a whole partition
- also much easier to modify such backup (to some extent, even if compressed) prior to deployment than mounting a partition image and changing files inside it (not impossible if I recall correctly, but surely messier).

ARE THERE SUCH INSTRUCTIONS WHICH I MISSED?

IF NOT, WHAT'S THE REAL TECHNICAL PROBLEM???

I can't but see it as a regression when grub2 is compared to grub.

"Any Wisdom Welcome" ™ ® © :-)

---

### Post by The Cog on 2012-10-16
remastersys might possibly be what you are looking for.
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
It's limited to making a 4G image though, so you may have to backup the bulk of your data separately and just image the system with remastersys.

---

### Post by darkod on 2012-10-16
I really don't see your issue with grub2. Yes, you CAN simply copy all the files from / to another partition, adjust /etc/fstab (it will have the old UUIDs inside) and reinstall grub2. That's it.

As for copying, you can try fsarchiver which does a copy, not clone. And it copies only the data, not the empty sectors (like clonezilla for example).
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

So far i never needed to move the / but I think after you copy the only things you need to do is adjust the /etc/fstab with the new UUIDs, and reinstall grub2.
It's probably a better idea to enter the copied installation with chroot, completely purge grub2 and its config files, and reinstall it. That process is very easy also, and makes grub2 create the new config files with the correct existing partitions, without the possibility of having "left overs" from the old partitions.

---

