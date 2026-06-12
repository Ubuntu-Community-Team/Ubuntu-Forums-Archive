---
title: "Ubuntu Installation Could be Better"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by sdebo on 2006-08-16
I wish to share my experience with installing Ubuntu Dapper hoping that some of the issues I point out are addressed (or better still, I am corrected and shown a better way to do this)

I installed Ubuntu on a PII 233 machine with 256Mb RAM along side windows 98.  I use the text based installer all along.  I prefer it to the GUI since the text based one provides more feedback and does not treat me like a complete noob (even though I am)

First time round installation completed ok, but upon rebooting I got a GRUB error 17.  Tried messing around with grub menu.lst but had no luck. GRUB error 15.

I reinstalled. The installer warned me that an older installation existed and I decided to move ahead.  The installer stopped when trying to install the software components.  It did not tell me what was the problem or if maybe the CD was damaged.  Some more feedback from the installer would be useful here.  C**an anyone explain what could have been the problem please?** I was a bit frustrated in that it stopped me from ejecting the disc.  What if I wanted to switch it with a newer one which is not damaged?

I repartitioned the drive and now I got a GRUB error 18.  It would be nifty to list of references to what these errors mean built into the installer.  I was lucky to have an XP machine running, with which to look up the meaning of these errors.

I downloaded the LDP books and will be going through most of that.  I am not complaining about LINUX (IT IS GREAT!) but the installation process is still not user friendly enough.  It expects users to be knowledgeable and does not mention the possible problems.

---

### Post by bernied on 2006-08-16
Check section 14 of the GRUB manual for a list of errors:
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

It's possible that, due to the age of your machine, the bootloader was unable to access the partition where you installed Ubuntu. Maybe.

---

### Post by bernied on 2006-08-16
oops sorry, I see you already found a list of grub errors. So this was just a general rant? In that case, I feel your pain.

Trying to install on top of an existing installation will always cause trouble. Can I suggest that you fix issues as they arise? Barging ahead when something is clearly wrong can only lead to more head-banging.

---

### Post by orb9220 on 2006-08-16
Well more info about the hd and partitions you setup would help.

Like is win98 the first partition? Then you created a / partition of >5Gb  for root and a linux-swap partition of 512mb? This would map out to 

hda1 ---> win98 fat32
hda2 ---> /     ext3
hda3 ---> linux-swap

Did you install the grub to hd1 mbr? It has to be there to allow you to dual boot.

Above are examples and hope they helped.

---

### Post by sdebo on 2006-08-16
I found the meaning of the errors and know how to sort out the booting problem.  bernied is probably right in that I installed Linux to a 40Gb drive (partition 1) and BIOS is unable to access the drive.  Will repartition, reinstall and confirm. 

Why will installing on top of an existing installation always cause trouble?  Aren't the directories and files overwritten?

Mine was just a general rant for the devs to take up an possibly include more feedback in the text based install.

**My difficulties are:**

[LIST]
[*]How do I create a GRUB boot floppy?
[*]When using the live CD how do I boot to a terminal screen without waiting for Xorg to come up just to run terminal or switch to a terminal screen?
[*]How do I repartition the drives from term?
[/LIST][LIST=1]
[/LIST]

Thanks repartitioned and it worked.  Would still appreciate an answer to my questions above please.

---

### Post by bernied on 2006-08-17
>     * How do I create a GRUB boot floppy?
Try:
grub-install /dev/fd0
More info on this with
man grub-install
And also at the grub manual (linked in previous post). If this doesn't work, using the grub console will. Just say if you want help with that.
>     * When using the live CD how do I boot to a terminal screen without waiting for Xorg to come up just to run terminal or switch to a terminal screen?
Depends on the live-cd. Try Ctrl-Alt-F1 or any Fx from 1 to 6, this is pretty standard for most distros, even live cds (I think). Usually Ctrl-Alt-F7 will return you to your X session (if you are running multiple X sessions, try the next Fx up). 
>     * How do I repartition the drives from term?
For basic creation and deletion of partitions, you can't beat fdisk, but it's a bit clunky.
Try:
fdisk /dev/hda1
(as the root user)
BUT BE VERY CAREFUL
You may also have access to cfdisk, which is a bit easier to use, but I think is still based on the same back-end.

parted is a terminal-based partition resizing tool. I haven't used it much so can't help with its operation.

One thing to be careful of though, some live-cds mount all your hard-drives at startup, and you don't want to be repartitioning mounted drives.
Try:
mount
without any parameters, to get a list of mounted filesystems. Unmount any that are on the drive that you're going to work on.
Try:
umount /dev/hda*
to unmount the first hard-drive or even
umount /dev/hd*
to unmount all drives

All of this info is easy enough to find - once you know what words to use in your web search. It's just about knowing those words. Lurking around forums helps with that.

---

### Post by sdebo on 2006-08-18
Thanks a lot for your detailed help.

---

