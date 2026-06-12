---
title: "MemTest Runs Forever"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by lazikid on 2009-12-21
Hello all,

I have a Toshiba laptop running Win XP. I used UNetbootin to install Ubuntu 9.10 as a second OS in that machine.

Now when I start the machine, I see the screen saying 'check system and then press F1'. I press F1, it takes me to BIOS settings. Once I exited BIOS, the screen prints out 'GRUB LOADING' and I see memtest86 running. This thing finishes after more than one hour and finds no errors. Once I restarted as it asks me to do, the same cycle repeats again.

What can I do now? The memtest loads right after the message 'GRUB LOADING' and me pressing anything does not make a difference. I do not have a reliable CD drive in the laptop (that is why I went for UNetbootin) to try any live cd. 

Any suggestion would greatly be appreciated.

Thank you

---

### Post by raymondh on 2009-12-21
Seems like your GRUB is set to default to the memtest entry.

Try this .... taken from dave's GRUB2 tutorial:

[B][I]GRUB_DEFAULT - Sets the default menu entry. Entries may be numeric or "saved"
GRUB_DEFAULT=0 - Sets the default menu entry by menu position. As Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.
GRUB_DEFAULT=saved - Sets the default menu entry with whatever was selected last. If the menu is displayed during boot, the last entry selected will be highlighted. If no action is taken, this selection will be booted at the end of the timeout or if the menu is hidden.
grub-set-default is enabled when this value is set to saved. You can quickly change the default OS/kernel with this command.
The format is "sudo grub-set-default X, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.31-14-generic"
To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run "grep menuentry /boot/grub/grub.cfg"
GRUB_DEFAULT="xxxx" - An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"
For an example of how to enable the "saved" option with a custom menu, see the "Custom User Entries" section.[/I][/B]

The complete (link) is in my signature below.

---

