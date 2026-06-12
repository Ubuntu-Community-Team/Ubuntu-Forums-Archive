---
title: "Dual booting problems"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by bprevost on 2007-05-18
Hello, if someone can help me, it would be nice... got someproblem with my XP-Ubuntu dual boot. Here's the story :

For a while, i've been using Ubuntu and Windows with a dual boot system. I decided to format my harddrive in order to created a bigger partition for Linux (and a small one to play games on Windows). I boot with the live CD, delete my HDD partitions and create three new partitions :

   - 10 go for the main Ubuntu repertory ''/'' (ext3)
   - Around 350 go for my files and some programs to be used with Linux ''/home'' (ext3)
   - 100go for Windows (NTSF)

I installed Ubuntu without any problems and it worked just fine. Then, I booted with my Windows Home Edition CD. I've installed it on my 100go partition and everything is perfect. There is just one problem. When I boot my computer, I can't chose the OS I want to use, Windows boot directly and don't even recognize Ubuntu.  My partitions still ok and windows is on my 100go (no, I didn't format all my HDD when I installed Windows) [I don't know how if I can access my ext3 partition under windows, but I know they still there]. If someone can help me, I'll appreciate, I'm kinda new to Linux and dual booting :(. Thanx !

---

### Post by Yitram on 2007-05-18
I think its because you installed windows second.  It replaces GRUB with its own bootloader.  As to how to fix that....other than reversing the order, I'm not sure.  I can't get my dualboot working yet. :confused:  But everything I've read says to install windows first.

---

### Post by bprevost on 2007-05-18
Ohhh, thank for the answer ! I'll try to re-installed Ubuntu if no one knows how to solve my problem

---

### Post by n8bounds on 2007-05-18
you can just reinstall grub from the live cd


1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by noctiphile on 2007-05-19
I'm currently reconfiguring a multiboot system myself.  Do what n8bounds said and just reinstall grub, which is the ubuntu bootloader.  It takes only a minute.

If you get any errors using grub, especially the root () command, try running "sudo grub" when starting.    The root command attempts to mount the partition you specify, to find the grub configuration files.  I'm not sure it's necessary with the Live CD though since with it, users aren't set up in the normal way in the first place.

The disk numbers in grub start with 0, so (hd0,1) is the first hard drive, second partition.

Hope you get it fixed!

---

### Post by Ub1476 on 2007-05-19
This website contains all the information you need for dual-booting.

[Linky]("http://www.apcstart.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp")

Doesn't matter what you installed first:)

---

