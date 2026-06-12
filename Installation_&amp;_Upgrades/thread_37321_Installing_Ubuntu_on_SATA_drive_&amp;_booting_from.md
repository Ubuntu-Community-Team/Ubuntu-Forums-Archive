---
title: "Installing Ubuntu on SATA drive &amp; booting from cd"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by jacaru on 2005-05-26
Hi all,

I am new to Ubuntu but not to Linux, I have used debian many times.

My computer is an AMD 64 with nForce3 chipset. I have two drives, one SATA with windows XP & Ubuntu (5.04) installed; and one ATA with one FAT32 partition and more unpartitioned space.

This is my problematic:

I dont want to touch the MBR windows installation wrote. I would not like to risk the ability to boot into windows (as a side note, is grub aware of a windows xp installation and would it let me boot windows xp???). Usually in the past i used a floppy with lilo to boot. But this computer has no floppy.

So i want to do with a cd what i did with the floppy. Ideally i would like a cd that boots a kernel stored on my root ubuntu partition (/dev/sda3) in a way that upgrading the kernel would not mean updating the boot cd. If not i can use a cd-rw and update the boot cd when needed.

In any case, this was a solution i didnt expect to achieve right away. Until that time a pretended to boot my ubuntu installation in rescue mode with the installation cd. But I cant. Somehow on a standard installation some modules are loaded that make my sata drive visible. But if I boot from the installation cd with this command:

linux root=/dev/sda3

i get a panic complaining that theres no /dev/sda3. 

Can anyone help me with these two issues?

Thanks.

---

### Post by jacaru on 2005-05-27
I have solved my problems.

I downloaded the Ultimate Boot CD iso that comes with GRUB boot loader. I loaded Ubuntu through the GRUB command line. Reading GRUB documentation I saw too how I could make a GRUB boot CD. Now I would like GRUB could load the menu and booting configuration from the hard disk so I could use the boot cd independantly of how I arrange the partitions on the system. Maybe GRUB2 will do this. Or maybe chainloading two GRUBs? Who knows...

About Ubuntu, at first look, great presentation. It seems very well put together, with the useful stuff and not bloated. I wanted to use the system for developing but i might use it too for some desktop use.

Later.

---

