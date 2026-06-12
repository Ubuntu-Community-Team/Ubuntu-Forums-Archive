---
title: "Fresh Intrepid install with Grub Error 15"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Captain Rotundo on 2008-11-07
I freshly installed Intrepid one a machine with 3 sata drives and 1 ata drive, on a partion on SATA drive 1.

I have no other OS on this machine, it is not dual booting. I get grub error 15, I found some advice on the web that said boot the livecd and reinstall grub via:

> root (hd0,0)
> setup (hd0)

(I confirmed with the find command in grub that the stage1 file is on hd0,0)

I still get grub error 15.

---

### Post by dabl on 2008-11-07
Grub and the installer and your BIOS don't always agree on how to count the hard drives.  :lolflag:

When the boot menu comes up and your Ubuntu boot item is highlighted, press "e" to edit. Then cursor down a line to the one that has the hd(0,0) in it, and change the first 0 to a 1, and then press Enter and "b" to boot.  This doesn't make any permanent change -- you're just experimenting to find out which hard drive Grub thinks Ubuntu is on.

If "1" doesn't work, try "2" and "3" as necessary.

Once you know which one is booting, then you can edit (in Super User aka root mode) the file /boot/grub/menu.lst and change the number in the applicable lines where it shows the boot menu.  :)

---

### Post by Captain Rotundo on 2008-11-07
I dont get a boot menu, I get a grub error

---

### Post by dabl on 2008-11-07
Ahhhhh -- so Ubuntu is the only installed OS?

OK, then press the Escape key after your BIOS splash disappears and before the Grub error appears.  Then do the editing thing.

---

### Post by Captain Rotundo on 2008-11-07
I dont think you understand
this is a fresh install
grub doesn't have a menu, it loads nothing
it says 

GRUB loading, please wait...
Error 15


that is all.

---

### Post by dabl on 2008-11-07
I do understand.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/194730](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/194730)

There _is_ a boot menu -- you can see it at the bottom of the file /boot/grub/menu.lst (but of course you'd have to use a Live CD to get to it, since you can't boot the system).

But, with only a single OS installed, it does not put the boot menu up on your display, since you have no choices to make at that point.  Instead, it proceeds directly to attempt to boot the Ubuntu kernel.  Only problem is, as I said before, your BIOS, Grub, and the Ubuntu installer count hard drives differently, sometimes, especially when there is a mix of IDE and SATA drives.

So, you need to try again to hold down Esc while it is booting -- push it when you see your BIOS splash, and it should bring up your boot menu.

---

### Post by Captain Rotundo on 2008-11-07
Grub does not get to the menu, it wont load the menu.

I am going to try to re-install, I am familiar with grub I have been using it since debian stopped using lilo.

---

### Post by dabl on 2008-11-07
OK.

I have one IDE and four SATA drives.  After installation, I always have to manually edit the /boot/grub/menu.lst file, because Grub always sees my drives differently than the Kubuntu installer.  If I'm remembering correctly, the installer always sees the IDE drive as hd(0) regardless of the BIOS sequence, but Grub will accept my BIOS boot sequence which shows a SATA drive first in the boot sequence.  So I have to edit /boot/grub/menu.lst and change hd(0,0) to hd(1,0) and then it's all happy.  I think you have the same problem.

You could boot the Live CD, mount the hard drive that has Ubuntu on it, and edit the menu.lst file that way, if you wanted to avoid the entire re-installation.  Prolly re-installing will not change the result anyway, if the problem is the same as mine.

---

### Post by Captain Rotundo on 2008-11-07
This seems to be what happened, I made room on the IDE and pot / there.  seems to work fine now
thanks

---

