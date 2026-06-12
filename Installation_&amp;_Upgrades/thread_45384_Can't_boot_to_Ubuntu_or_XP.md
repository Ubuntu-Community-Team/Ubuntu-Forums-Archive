---
title: "Can't boot to Ubuntu or XP"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by kook44 on 2005-06-29
I just installed a new HD as primary slave to install ubunto on. (XP is already installed on primary master)  After succesfull install, I chose to place the bootloader on (hd1).  I changed the bios to boot to primary slave, followed by master.  GRUB succesfully loaded, then when I choose ubuntu:
```
root(hd1, 0)
filesystem type unknown, partition type 0x7
kernel /vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro quiet splash

Error 17: Cannot mount selected partition

```

If I select Windows XP, I get:
```

root(hd0, 0)
Filesystem type is ext2fs, partition type 0x83
savedefault
chainloader +1

Error 13: Invalid or unsupported executable format

```However, If I go back into the BIOS, and set primary master to be the first IDE drive in the sequence, XP loads fine.

---

### Post by The Na Kun on 2005-06-29
Wait, windows xp is on ext2?!? I think grub mixed up the filesystems... So you should switch it in menu.lst?

---

### Post by kook44 on 2005-06-29
> Wait, windows xp is on ext2?!?
That's what I thought.  Weird, right?

Heres my menu.lst:
```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

```
I'm viewing this by mounting the drive from the ubuntu live CD.  How can I edit it?  It's read-only...

---

### Post by kook44 on 2005-06-30
Ok, so I flip-flopped the disk numbers: Ubuntu (hd0, 0) -  XP(hd1,0).

Now ubuntu boots fine(which I can't understand - it's clearly the second drive), but still can't boot XP - same error.
I've tried editing the lines right in grub by hitting "e". no combination seems to work.  if I change the partition # to anything else, i get "partition doesn't exist".  Likewise if I change the disk number.

Any ideas?

---

### Post by MappyH on 2005-06-30
Sorry if I'm way off topic, I installed Suse9.1/XP dual boot a while back. Suse booted fine but when booting XP it failed. I added LBA in the bios for the HardDrive that XP was installed on, this solved the error ! (looks like the same error you are getting)

You can only try  :smile:

---

### Post by SQFreak on 2005-06-30
[QUOTE=kook44]Ok, so I flip-flopped the disk numbers: Ubuntu (hd0, 0) -  XP(hd1,0).

Now ubuntu boots fine(which I can't understand - it's clearly the second drive), but still can't boot XP - same error.
I've tried editing the lines right in grub by hitting "e". no combination seems to work.  if I change the partition # to anything else, i get "partition doesn't exist".  Likewise if I change the disk number.

Any ideas?[/QUOTE]
 Try making your WinXP entry look like this:

```
title           Microsoft Windows XP Home Edition
rootnoverify            (hd0,0)
makeactive
chainloader     +1
savedefault

```

---

### Post by mingus on 2005-06-30
[QUOTE=kook44]Ok, so I flip-flopped the disk numbers: Ubuntu (hd0, 0) -  XP(hd1,0).

Now ubuntu boots fine(which I can't understand - it's clearly the second drive), but still can't boot XP - same error.
I've tried editing the lines right in grub by hitting "e". no combination seems to work.  if I change the partition # to anything else, i get "partition doesn't exist".  Likewise if I change the disk number.

Any ideas?[/QUOTE]

You are close.  Boot loaders cannot read the BIOS, so grub *assumes* that the numbering sequence you've given it syncs with the BIOS.  In other words, hd0 is hda when the master is set to boot first in the BIOS, but if the slave is, then hd0 is hdb.  So, you made the right change to menu.lst.  The problem with XP is that it chokes if it doesn't think it is the first disk.  You need to remap the disks virtually, like this:

title		        Microsoft Windows XP Home Edition
root		      (hd1,0)
map                  (hd1) (hd0)
map                  (hd0) (hd1)
chainloader	+1

Take the savedefault out.  If you get a "can't mount" error you can change the "root (hd1,0)" to "rootnoverify (hd1,0), but I expect the above will work.

You can test this interactively.  When you get to the grub menu, do "c" to break into the shell.  Enter the commands above, adding "boot" to the end.

---

### Post by kook44 on 2005-06-30
yep-
that took care of it.

many thanks!

---

### Post by mingus on 2005-07-01
[QUOTE=kook44]
many thanks![/QUOTE]

Happy to oblige . . .

---

### Post by MrCheese on 2005-07-01
Hey, great thread!!  :) 
I'm having the exact same problem, caused by having a big hdd hanging off a SIL ide "Raid" card which the mobo chooses to see as the first hdd.

I know how to do the bios switcher stuff in lilo but didn't realise the same applied to grub. It would be **really** good if the nice Ubuntu chaps gave us the option of putting in extra lines to the menu.list or lilo.conf before it was committed & the system ends up in a no boot situation. Fortunately I always install the bootloader to the mbr of the 2nd (linux) hdd thus leaving XP still bootable for my wife.

I used to use Mandrake - the boot installer on that is superb, recognises the disk layout & does the bios switching stuff itself in lilo.cong - can't speak for grub as I never used it in MDK.

---

### Post by mingus on 2005-07-01
[QUOTE=MrCheese]It would be **really** good if the nice Ubuntu chaps gave us the option of putting in extra lines to the menu.list or lilo.conf before it was committed & the system ends up in a no boot situation.

I used to use Mandrake - the boot installer on that is superb, recognises the disk layout & does the bios switching stuff itself in lilo.cong - can't speak for grub as I never used it in MDK.[/QUOTE]

Grub is preferred by most distros because it has more features, coexists better with other OS's and handles a lot of filesystems.  And with its control file being external, it doesn't have to be reinstalled when the kernel changes, etc. like LILO.  But that flexibility requires exact precision to install it.  I have a standing gripe with the Debian install method, which assumes either a simple configuration.  I *always* create a boot floppy during install and *never* at that time install to the MBR; this enables me to reconfigure and reinstall the loader at a later step, and prevents problems until I do so.  SuSE has an even much stronger installer than Mandrake's, although with a complicated hw config it still needs guidance.

---

### Post by kook44 on 2005-07-01
For serach results on this thread, those that don't want to STFW-

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

### Post by ekravche on 2005-09-03
[QUOTE=mingus]You are close.  Boot loaders cannot read the BIOS, so grub *assumes* that the numbering sequence you've given it syncs with the BIOS.  In other words, hd0 is hda when the master is set to boot first in the BIOS, but if the slave is, then hd0 is hdb.  So, you made the right change to menu.lst.  The problem with XP is that it chokes if it doesn't think it is the first disk.  You need to remap the disks virtually, like this:

title		        Microsoft Windows XP Home Edition
root		      (hd1,0)
map                  (hd1) (hd0)
map                  (hd0) (hd1)
chainloader	+1

Take the savedefault out.  If you get a "can't mount" error you can change the "root (hd1,0)" to "rootnoverify (hd1,0), but I expect the above will work.

You can test this interactively.  When you get to the grub menu, do "c" to break into the shell.  Enter the commands above, adding "boot" to the end.[/QUOTE]


It feels like I've tried everything. I hope this works for me. Thanx for the reply

---

