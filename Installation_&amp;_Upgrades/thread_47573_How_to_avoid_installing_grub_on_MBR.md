---
title: "How to avoid installing grub on MBR"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by Steve1961 on 2005-07-09
I've wanted to install linux for some time now and after a lot of research I've decided to give Ubuntu a try.  My problem is that I still need windows XP for some specialised software that I run, so I need to dual boot.  This seems to be a potential nightmare, so I've bought a copy of Acronis Disk Director, which will let me do all the partitioning in windows, and it also has it's own boot manager.  So I have two questions: firstly, if I create a 20gb ext3 partition do I also need a swap partition, and if so how large should this be?  Secondly, and this is the part that really worries me, what should I do when it gets to the part where I install grub?  I'm going to use the acronis boot manager for everything if I can, so I don't need, or want, to put GRUB in the mbr.  Do I need to even install it at all?

Any help or advice appreciated as the more I read in this forum the more confused I'm starting to get.  As someone who's only used windows previously, the command line is also a complete mystery to me, so please keep any advice idiot proof.  Thanks in advance.

---

### Post by Xian on 2005-07-09
[QUOTE=Steve1961]So I have two questions: firstly, if I create a 20gb ext3 partition do I also need a swap partition, and if so how large should this be?  Secondly, and this is the part that really worries me, what should I do when it gets to the part where I install grub?  I'm going to use the acronis boot manager for everything if I can, so I don't need, or want, to put GRUB in the mbr.  Do I need to even install it at all?[/QUOTE]
1. The swap partition should be approx. 2x the size of your amount of RAM up to 1GB.

2. The InstallCD does not have an option to "skip" the bootloader step, but it will present you with options of where you would like it to be placed. You need only direct it to your root partition (or /boot if it has been created separately).

---

### Post by mingus on 2005-07-09
I would check the Acronis boot prerequisites (I have no exp with this particular product).  Boot managers work differently from one another.  Some are not actually loaders themselves; rather, they essentially just point the bootstrap to whichever partition you want to boot from and pass control to the loader installed there.  Others can load certain OS's but must chain-load others.  Therefore depending on how Acronis works, there may be a need to install the boot loader (grub) to the boot sector (as Xian described).  If you aren't sure, there probably is no harm in installing it there because if Acronis isn't looking for it, it will simply do nothing.  If you really don't want to install grub at all, install Ubuntu in expert mode; there will be a menu choice to skip the boot loader installation altogether.

---

### Post by al7kz on 2005-07-09
If you have a floppy drive you can also install GRUB on a floppy, then to boot Linux just insert the floppy and start the computer. When installing GRUB, install to fd0.

---

### Post by mingus on 2005-07-09
[QUOTE=al7kz]If you have a floppy drive you can also install GRUB on a floppy, then to boot Linux just insert the floppy and start the computer. When installing GRUB, install to fd0.[/QUOTE]

With this method you would not need Acronis at all; it would be bypassed.  And, this boot floppy would easily boot Windows as well.

---

### Post by jrev on 2005-07-09
I never had any nightmare with the dual boot and Grub in the MBR 

what is the fault ? :)

If you don't know how to use the ubuntu partitioner you can use the first CD of another distribution :
I was using the first CD of the Mandriva 9.1 that I knew very well and stopped the install after partitioning 
then i started anew with the ubuntu install 

that was the trick ...

---

### Post by Steve1961 on 2005-09-03
OK, sorry about taking time to reply.  I've only just discovered how to view all my posts and I couldn't find this one again.  Anyway, my previous problems with dual booting were with suse and mandrake on an old K6 machine.  Probably something I did wrong at installation, but neither picked up the windows installation after the install.

In contrast, Ubuntu installed seamlessly, but I went with the acronis boot manager and just installed grub to the root partition.  The manager picks this up automatically and everything seems to be working fine.  That said, I'm sure everything would have been fine anyway, but as a complete newbie I lacked confidence.  However, since using Ubuntu for the last couple of months I hardly use windows at all now - apart from when I have to run packages such as Genstat or SPSS.  What a great distro.  WHY DID I WAIT??

---

