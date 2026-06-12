---
title: "How do I dual boot vista and ubuntu safely?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by MSdefecter on 2008-05-23
Hi,
I have just sold out and bought Vista, and, just for the record I do feel quite dirty about it. I am currentlly running Ubuntu 8.04 and would like to now install Vista along side it on a seperate physical hard disk. However I have heard all sorts of horror stories regarding dual boots between Vista and Ubuntu where one locks the other out and so on. I was wondering if anyone knows of the most effective way of installing these two, it does not matter to me if this involves reinstalling Ubuntu.

---

### Post by iaculallad on 2008-05-23
> **MSdefecter said:**
> Hi,
I have just sold out and bought Vista, and, just for the record I do feel quite dirty about it. I am currentlly running Ubuntu 8.04 and would like to now install Vista along side it on a seperate physical hard disk. However I have heard all sorts of horror stories regarding dual boots between Vista and Ubuntu where one locks the other out and so on. I was wondering if anyone knows of the most effective way of installing these two, it does not matter to me if this involves reinstalling Ubuntu.

Try referring to this [howto]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty") first before doing it. Same process though with Feisty and Heron.

---

### Post by Sef on 2008-05-23
With Vista, shrink the partition using its partitioner.  

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by Sidewinder1 on 2008-05-23
I believe that installing vista *after* ubuntu will hose grub and you will no longer be able to boot into ubuntu. If as you say, you've no problem reinstalling 8.04, just back up anything that you do not wish to loose then install vista; then reinstall ubuntu. Perhaps someone more adept could suggest an easier way.

---

### Post by logos34 on 2008-05-23
> **MSdefecter said:**
> I am currentlly running Ubuntu 8.04 and would like to now install Vista along side it on a **seperate** physical hard disk. 

If you want to install vista on a second hard disk:

-add a windows entry to grub [like this (with mapping).]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

gksudo gedit /boot/grub/menu.lst

Reboot and enter the Bios:

-in the Bios set the vista target drive as first in the **hard disk** boot order.  Set the cdrom as first in the **device** boot order 

-install vista 

-reboot, re-enter the bios and set the linux drive back to first in boot order.

-try to boot vista from grub menu.  If it refuses go back into bios and set the windows drive back to first place and boot directly into vista using it's own bootloader.  Try using [EasyBCD to dualboot]("http://neosmart.net/wiki/display/EBCD/Linux").

So basically you want to try using grub first, then EasyBCD.  If neither works, you can always just toggle the boot order in the bios to getinto either OS.

---

