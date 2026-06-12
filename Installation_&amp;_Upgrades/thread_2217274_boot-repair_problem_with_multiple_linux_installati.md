---
title: "boot-repair problem with multiple linux installations"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by 7o7YlUcb on 2014-04-16
Hi, after re-installing windows, the grub boot menu disappeared. So I tried to get it back using boot-repair.

I have a PC with Windows 7 plus Ubuntu 12.04 plus some old experimental Linux distros installed.

When I run boot-repair (from an Ubuntu Live CD), and reboot the PC, it just presents an option to boot into Suze (one of the old distros that I dont use anymore). I want it to give me options to boot into Windows and Ubuntu (at least). I.e. sda2 and sda7.

Here is my log...
[http://paste.ubuntu.com/7261898/](http://paste.ubuntu.com/7261898/)

To run boot-repair, I followed the instructions here...
[http://www.upubuntu.com/2012/11/how-to-reinstallrepair-grub-2-boot.html?m=0](http://www.upubuntu.com/2012/11/how-to-reinstallrepair-grub-2-boot.html?m=0)

By the way, since the above report was generated I have had to get back into windows by running: `bootrec /fixmbr` from a windows recovery CD.

---

### Post by oldfred on 2014-04-16
You show two boot flags in BootInfo report. You can only have one per hard drive. If you fixed it that Windows boots I assume you removed the boot flag from sda4. Windows uses boot flag, grub does not. But a few BIOS also have to see a boot flag to let any system boot.

Your Ubuntu install shows no grub.cfg, and looks like grub is not installed at all?

You can use Boot-Repair's Advanced mode to totally uninstall & reinstall grub. You do not need the uninstall, but the reinstall will do a total reinstall. You need working Internet as it downloads grub from repository.

---

### Post by 7o7YlUcb on 2014-04-16
Thanks oldfred, 
That worked. I  ran boot-repair in advanced mode as you suggested, leaving defaults except  choosing sda7 for grub.
(Still seem to have 2 boot flags though)...
[http://paste.ubuntu.com/7262623/](http://paste.ubuntu.com/7262623/)

---

### Post by oldfred on 2014-04-16
If booting WIndows from grub, boot flags are ignored. 

But I did not think you could directly boot Windows with two boot flags, as that is what Windows uses to know which partition is its bootable partition. Also used for knowing which partition to repair and which to install into.

Best to use gparted or other tools to remove boot flag from sda4. In Windows it is the set active command to add a boot flag, but I do not know the remove command.
 set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
parted /dev/sda set 2 boot on

Some bios refuse to boot a hard drive without a boot flag. Although grub does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.
Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (not gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug;

---

