---
title: "Can't access tty: job control turned off"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by paullus on 2007-08-08
Dear All,

I am trying to install Xubuntu 7.04 (Feisty Fawn) with Desktop CD, but I am getting the following problem:

"/bin/sh: can't access tty: job control turned off

(initramfs)"

and a deadlock follows. Any ideas?

Thanks in advance,

Paul

---

### Post by logos34 on 2007-08-08
look through this thread:
[http://ubuntuforums.org/showthread.php?t=415009&highlight=tty+job+control+initramfs](http://ubuntuforums.org/showthread.php?t=415009&highlight=tty+job+control+initramfs)

I got the same message yesterday (for the first time ever) trying to boot a ubuntu feisty livecd (factory cd)...Finally resolved it on third boot after ejecting the floppy diskette I had left in the drive, even though it was set to boot first from cdrom and floppy seek was disabled in bios.

---

### Post by Bluebyte001 on 2007-08-08
Hope this works by others with this problem.
I did had the same problem with ubuntu and kubuntu.
When i put the cd in the tray and boot it, i place boot disk 98 (MS),
And press install after i put it in the drive.
It works very nice an installd it without a problem.
No tty errors anymore.

So i must add this to my message it didn't work with Kubuntu at here.
But maybe it will work with your pc.

Ik know its a little stupid the idee using a ms boot disk for installing Linux.
But it workt for me hope others may have use at this.

Ore even better maybe someone find an other way to solve this problem by using this information.
If you looking for a boodisk you can find it [here]("http://www.bootdisk.com") there are different os bootdisks to download. (maybe you can try a linux bootdisk first i didn't try it out yet)

---

### Post by nilfisk1 on 2007-08-08
Hello Paullus,

I had this problem just yesterday ( it was my first linux install so yeah, it scared me off ). The trick for me was to put a floppy into your floppy drive once the linux live cd is booted, and keep it in for the rest of the install. Do not ask me why, but it fixed it.

I hope this also works for you.

Nils

---

