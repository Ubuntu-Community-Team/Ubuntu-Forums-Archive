---
title: "help with grub??"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by cornelis on 2006-04-04
Hi, 

Is GRUB is capable of supporting USB?
if can, what are the settings?

basically, I am trying to run linux live cd(whether knoppix or ubuntu). i have an external usb cd writer. But my laptop BIOS cannot support USB startup (very old laptop). so another alternative is to use boot floppy disk to point the boot process to usb.

I did some research, and i think GRUB is a possible solution. 
i manage to create the GRUB floppy.
but it only can point to the internal hard disk.

The way i create the GRUB floppy is :
1. Format the floppy
2. give FAT file system to the floppy
3. copy stage1 and stage2 from the lib/grub/i386-pc to the boot/grub directory
4. restart the computer.

once i restart, i go to the grub prompt. 
The thing is, i only can do root (hd0,0)
then continue on.

I try to do (sda,0) doesnt work
I try to do (sdb,0) doesn t work.

any one know what i should try next?

thank you

---

### Post by waster on 2006-04-04
I think you need to have an initrd to be booted on the floppy which contains the drivers to see the CD. doesn't the standard installer have a "write a boot floppy" option?

Can you update your BIOS firmware?

---

