---
title: "Installing XP after Ubuntu"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Horsman on 2006-07-25
Heres the deal. I installed Ubuntu about 3 weeks ago after I forked my harddrive, and left 8 gigs for an XP install after I got my disk back. Well after installing XP to that empty partition, I have no grub and I cant boot ubuntu. How can I fixer this, (I have no floppy drive)

---

### Post by Swab on 2006-07-25
Hmm... do you know which partitions you installed ubuntu and windows on?  

What I'm going to suggest depends on your hard drive being hda , and im making assumptions about your partition scheme.

Boot with the ubuntu live cd.  Then open a terminal and type

```

sudo su
mkdir /chroot
mount /dev/hda1 /chroot (assuming this is ubuntu root partition)
chroot /chroot

```

Now we are into your installed ubuntu, we need to edit your boot list.

```

nano /boot/grub/menu.lst

```

Add this at the end of the file

```

title           Windows XP
root            (hd0,2)   again assuming this is your windows partition
makeactive
chainloader     +1

```

save the file then type:

```

grub-install hd0

```

Reboot and hopefully everthing is good.

---

