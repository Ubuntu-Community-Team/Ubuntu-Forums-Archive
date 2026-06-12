---
title: "BusyBox and kernel panic trying to fix GUI Feisty upgrade"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by TygerFish on 2007-05-15
I did a GUI upgrade from Edgy to Feisty and rebooted, apparently without problem.  Upon reboot, I had a GRUB error 17.  From previous experience with kernel upgrades, I surmised that it had messed with the GRUB list file.  Sure enough, I found this the default Ubuntu boot listing:
```
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=72F89F63F89F247F ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
My Windows partition is the first and my Ubuntu partition is the second, so I changed the first line to...
```
root (hd0,1)
```
...and booted.  This seemed to fix the problem for a few seconds; the computer moves to the new Feisty splash screen and the progress bar gets about a pixel or two across its journey when the screen blanks out and dumps this on the screen:
```
BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh:can't access tty; job control turned off
(initramfs) _
```
I went back and took a closer look at the BASH list file.  The last time I'd gotten a BusyBox error, it was because I'd forgotten to update the "root=" entry in the kernel line. Sure enough... but wait - what is this "UUID" business?  I've never seen that before.  I changed the boot settings to the following:
```
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=hda2
initrd /boot/initrd.img-2.6.20-15-generic
```
The boot process froze a few seconds into it with the last few lines as follows:
```
Begin: Mounting root file system...
/init: /init: 148: Syntax error: 0xhda2
[431.103247] kernel panic - not syncing: Attempted to kill init!
[431.103317] _
```
The cursor flashes along with the caps lock and scroll lock buttons on the keyboard; the computer does not respond to input and requires a hard power-down.

The box I'm using is a mostly-Dell-built 1.8 P4 with 768MB RAM.  I've seen some people encountering these kinds of errors with SATA drives, but this is a 5 year-old box; it's all IDE.  The Windows partition boots without a hitch - I'm using it right now, in fact - so I know there aren't any problems with the hardware.  I have no idea where to go from here, so any help tracking down solutions would be greatly appreciated.

---

### Post by daveg2 on 2007-05-20
I'm sorry to see no response to this thread.  My system and my problem looks to be identical, at least on the first look.  Mine is a Dell Dimension 8200, but with a bit more RAM, ~1.25 GB.  No too sure what to add that might help?  

TygerFish, have you submitted a bug report? Or did you find a solution?

---

