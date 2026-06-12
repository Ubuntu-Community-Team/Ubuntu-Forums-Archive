---
title: "Help installing to USB hard drive"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by monkeyfacebag on 2006-12-21
I'm trying to install ubuntu 6.10 to a 100gig USB drive attached to my work laptop.  As this is a work laptop, I obviously cannot touch the internal hard drive (which is encrypted anyway).  I successfully got 6.06 running a while ago with the same equipment, tried to put Gentoo over it, failed miserably and came running back to Ubuntu.  However, with 6.10, the installer has changed a bit and I can't get it to boot after completion.  I suspect the issue lies with one of the final steps, selecting a place to install the GRUB bootloader.  Because I cannot touch the internal drive, I changed the install location from the default HD0 to HD1.  When I reboot after installation, GRUB loads but tells me I cannot mount the partition (which I'm assuming refers to the / partition).  Any ideas?

---

### Post by bernied on 2006-12-21
Can you post your /boot/grub/menu.lst file?

How do you boot the drive - have you changed the bios boot order?

One thing you can try, when grub boots up you have access to the grub console, which is quite powerful as grub is a mini operating system in itself. Some things to play with:
- type 'root (', then hit the TAB key, you will get a list of hard-drives, type '0', then hit TAB again, you'll get a list of partitions, type one to finish the cammand and hit ENTER
- when you have selected a partition, say 'root (hd0,0)', then type 'cat /', then hit the TAB key, you'll get a list of files. If boot is one of them, then you're in the money...
- 'cat /boot/grub/menu.lst' should display your grub config file, once you've found the right partition
- if you hit TAB at the raw prompt, then you get a list of commands, if you type a command without any parameters it will tell you what parameters it needs
- once you've found which partition you should be booting to, type 'reboot' and ENTER, then next time the menu comes up, select the entry for ubuntu, and hit 'e' (for edit), then change the line for root - this only changes it temporarily, you will still need to edit the menu.lst file

I'm guessing you've just got to change a couple of '1's to '0's in the menu.lst file, because with your bios set to boot the external hard drive first, it will become hd0, not hd1.

---

