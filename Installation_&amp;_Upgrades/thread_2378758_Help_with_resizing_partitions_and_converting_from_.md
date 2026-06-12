---
title: "Help with resizing partitions and converting from MBR to GPT"
date: 2017-11-26
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2017-11-26
Hi guys 

Ill try to keep this simple
I using the 16.04 Ubuntu server edition -- the headless version that installed from a command line and not a GUI.  I've additionally installed this within byhve (which is a type of vm) and not bare metal.  I originally installed using MBR partition table and would like to convert to GPT -- eventually I want to change to using UEFI.  Anyway I first need to resize the main partition.  I would usually use gparted to do this --- however gparted is GUI based and I need a command line base.  I can run the Ubuntu server install disk, and it detects the current partition table, but I need to drop to a command prompt in order to resize the main partition -- this functionality doesn't seem to be in the install disk.  Do you have a live install disk or any other method I can use to drop to a command prompt to do this?

---

### Post by yancek on 2017-11-26
You could use parted which is what is behind the GParted GUI.  I would think it would be available on the server version of Ubuntu.  The link below gives some info and examples on using it including resizing.

 [https://www.tecmint.com/parted-command-to-create-resize-rescue-linux-disk-partitions/](https://www.tecmint.com/parted-command-to-create-resize-rescue-linux-disk-partitions/)

---

### Post by oldfred on 2017-11-26
I do not think gdisk requires a gui.

[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

If you convert, you need a bios_grub (ef02 in gdisk) for BIOS boot, and/or an ESP - efi system partition (FAT32 with boot flag or code ef00 in gdisk) and re-install of grub for either BIOS or UEFI.

Can you use a live Desktop installer that has the gui?

What ever you do, be sure to have good backups.

---

