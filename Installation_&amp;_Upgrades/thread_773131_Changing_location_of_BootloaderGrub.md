---
title: "Changing location of Bootloader/Grub"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by traveller18 on 2008-04-28
I want to change grub/bootloader to my other hard drive, and you can do this on the last step of installing a system in the advanced window. My question is changing the location do anything to that harddrive like erase data on it or anything like that.

Thanks

---

### Post by Pumalite on 2008-04-28
Post:
sudo fdisk -l

---

### Post by traveller18 on 2008-04-28
... yeah that doesn't answer my question at all

---

### Post by Pumalite on 2008-04-28
I'm trying to figure out if it is convinient for you to do it. But, if you want a dry answer; it's no. Grub install to the first 512 bytes unless you install it to sdb1.

---

### Post by xzero1 on 2008-04-28
As far as I know, the bootloader cannot be moved. You can change grub to boot another os or partition if you like though.

---

### Post by traveller18 on 2008-04-28
Ok, well i really do want to move it. yeah well ok

---

### Post by xzero1 on 2008-04-28
Just curious why would you want to move it?

---

### Post by lemming465 on 2008-04-28
short answer: you can put a bootloader nearly anywhere, and it usually won't touch the data in partitions you apply it to.  So go wild ;)

longer answer:
The BIOS loads 446 bytes of MBR off the first block of the first disk.
The MBR code loads the first block of some partition, somewhere.
The secondary boot block loads up to 8K more stage 1 loader from that partition.  This is stored in the reserved sectors at the start of the partition.  All logical partitions and any primary partitions created by most tools will have 63 reserved sectors before the dat starts to acomodate this.
The secondary boot loader loads a boot menu selector ("stage 1.5"); the user picks a boot menu item, and some OS specific code ("stage 2") loads the chosen OS.  Grub can load Linux and BSD and Hurd directly; windows NT-2003 eventually ends up using "ntldr", or windows vista "winload".

Someone has to own the MBR on the disk the BIOS is booting.  That has to point at another partition somewhere, usually a primary one.  It can be on any BIOS accessible disk.  Once you are in the boot menu, you can either chain to another boot loader on yet another partition, or boot an OS directly.

If you have the grub documentation installed, try *info grub* for all the gory details.

Generally grub-install will target the partition with /boot on it for the secondary loader stuff.  If you just want to move grub to a compatible primary partition with a populated /boot, do
```
sudo grub-install --root-directory=/path/to/new/boot /dev/YourBootDisk
```
If you make the destination disk be a specific partition, you can put entries formatted like
```
title my nested boot
root (hdN,Y)
chainloader +1
```
and make arbitrarily complicated nests of boot menus.

I usually let the Linux version I run most own the MBR, and then let every other variant I install put its own grub on its own partition.

---

### Post by Pumalite on 2008-04-28
> **xzero1 said:**
> As far as I know, the bootloader cannot be moved. You can change grub to boot another os or partition if you like though.
The reason is probably that he wants to boot off the other drive or use the BIOS to choose drive or boot Ubuntu with Super Grub, etc, etc. The reasons can be many.

---

### Post by xzero1 on 2008-04-29
I guess I'm getting bootloader and bootrecord confused but just to be clear; you can't move that tiny part of grub that is installed in the first disk right?

---

### Post by gtdaqua on 2008-04-29
> **xzero1 said:**
> I guess I'm getting bootloader and bootrecord confused but just to be clear; you can't move that tiny part of grub that is installed in the first disk right?

that's where the MBR resides which dictates what is to be booted. If you are moving (this part is tricky), then your BIOS must know which drive shud be booted first (this part is easy).

Although, I do not know wat are you trying to achieve by moving. Can't it be achieved anyway else? Because even if you did move the loader, the new loader should come into action first and kick off the boot and locate the OS files (obviously on a diff location) to continue booting.

---

### Post by lemming465 on 2008-04-29
> you can't move that tiny part of grub that is installed in the first disk right?

Not if you want to have Grub control the Master Boot Record and be the first thing running after the BIOS POST, no.  However, you can put Grub somewhere else (sda2, sdb1, sdc3, ...) and let some other OS's boot loader go first.  Windows tends to grab back the MBR any time you install it or apply a service pack, for example.

In general, Linux boot loaders such as Grub are more flexible and easier to configure than most other OS's, so on my dual-triple-quad-quintuple boot systems I prefer to let Linux squat on the MBR.

To restore windows boot loader code, for XP boot the recovery console and run```
fixmbr
```For Vista's recovery environment try the *startup repair* option, or get to a command prompt and run ```
bootrec /FixMbr
```See the Microsoft [troubleshoot and repair Vista startup]("http://support.microsoft.com/kb/927392") KB article for further gory details.

---

