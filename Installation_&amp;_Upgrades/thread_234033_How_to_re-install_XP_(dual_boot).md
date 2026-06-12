---
title: "How to re-install XP (dual boot)"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Ric95 on 2006-08-10
A virus ate Xp. Fine, I have Ubuntu as well. But for some things I would like to have Xp back too...:-& 

hda0 = RP ( Compaq recovery parition)
hda1 = XP , now formated in fat32.
hda2 = Ubuntu
hda3 = Linux swap
 If I use the Recovery Partition it allegedly wipe hda2 and 3, restoring to factory condition.
I also have an older XP pro install disk, but it only acknowleges the hard drive, and wants to erase everything :(
Has anyone here fixed their dual boot? How? Can I copy the whole disk to hda1 and install from there?

---

### Post by JerMe on 2006-08-10
It's hard to say since everything that I've read so far says the WinXP installation won't kill your other partitions (it'll recognize them as unknown but won't touch them).  I'll take your word for it though.

I'm from Gentoo originally, so here's a guide that might be of some use to you:
[http://gentoo-wiki.com/HOWTO_Install_Windows_after_Gentoo](http://gentoo-wiki.com/HOWTO_Install_Windows_after_Gentoo)

Basically you'd have to install XP to /dev/hda1, then boot the LiveCD, chroot into Ubuntu and run grub-install.  Sorry I'm not much help.  Try the WinXP cd again?

---

### Post by Ric95 on 2006-08-11
You're right, reinstalling XP didn't kill Linux ( at least not when using the restore partition that HP/Compaq provides.)
I'm glad the HP techs were wrong 8)

---

### Post by JerMe on 2006-08-12
Glad to have helped. :)  I'm sure you can google how to get GRUB back with the grub-install command.  Have fun~

---

