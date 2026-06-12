---
title: "Multi distro installation questions:"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by Jujimufu on 2005-09-06
I've used the search function both here and google.  I want to create a multi distro machine, and I think I have a good idea on how to do it from reading this comment in another thread:

[QUOTE=buster]
1. Install Windows.
2. Install Distro A and write grub to the mbr.
3. Check that these both work.
4. Install Distro B and write grub to a FLOPPY. Test booting with the floppy. Make a backup copy of the floppy.
5. Install Distro C and write grub to a floppy etc, etc etc.
6.Repeat steps 4 and 5.
7. AT YOUR LEISURE play with the grub menu list in Distro A.
[/QUOTE]

Well, I have windows and ubuntu on a dual setup now with grub on the mbr. I set my fdisk up like this:

> [color=gray]
Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   HPFS/NTFS **(WINDOWS)**
/dev/hdc2   83   Linux **(BOOT)**
/dev/hdc3   82   Linux **(Swap / Solaris**[/color])
--
/dev/hdc4    Extended
/dev/hdc5    83  Linux **(UBUNTU)**
/dev/hdc6    83  Linux **(BLANK)**
/dev/hdc7    83  Linux **(BLANK)**
/dev/hdc8    83  Linux **(/home)**
/dev/hdc9    83  Linux **(/usr/local)**


Now I want to install slackware and maybe suse or something on the two blank paritions: *dev/hdc6* and *dev/hdc7*.  As far as I'm aware, Slackware only uses lilo...?  And this is where I'm confused.  Would I just install lilo into the partition where slackware would be (not the mbr).  If so, how would I get grub to find slackware/lilo thing?

Other than this, how sound do you think the advice is from the quote at the beginning of the thread?  I would just edit Ubuntu's /boot/grub/menu.lst and add the other distros in right?  Not letting them install their grubs or lilos into the mbr but rather on junk floppy discs.  But anyway...  

Thanks to he or she that helps me understand this.

 :razz:  :razz: :razz: :razz: :razz:

---

### Post by wvslkr on 2005-09-06
The setup you propose will work fine.  Grub will boot slackware just the same as any other distro.  Lilo will also boot all distros plus windows. Just different implementations.

All you have to do normally is edit menu.lst to add the appropriate entries for the new system.

As a note, if you are planning to share the home directory some problems may arise
because of differences in distros.  Will be a matter of experimentation with what plays well together.

Hope that helps and Have Fun :)

---

### Post by Jujimufu on 2005-09-06
[QUOTE=wvslkr]
All you have to do normally is edit menu.lst to add the appropriate entries for the new system.
[/QUOTE]

Well, just one question then.  If the entry data to boot slackware is in lilo format, how could I use slackware's bootup entry data in grub if it's written for lilo? 

Thanks for the okay for other grub using distros, but slack is lilo so it throws it all off for me - and I really want to try it too hahaha! 

 :-o

---

### Post by wvslkr on 2005-09-06
If you look at your menu.lst you will see that for the linux entries all they are just pointers to the kernel to boot and the initrd file to use.   Slack has these just the same as any other linux.  Lilo is older and some still prefer it, but basically grub and lilo can be interchanged for each other.  That being said you may occasionally run across hardware where one will work and the other won't.

In the end you can use grub with slack or install lilo to the root partition and I think you can still chainload like you do a windows partition.  To me it would be simpler to just use grub with slack since you have it installed.

---

### Post by Jujimufu on 2005-09-06
[QUOTE=wvslkr]If you look at your menu.lst you will see that for the linux entries all they are just pointers to the kernel to boot and the initrd file to use.   Slack has these just the same as any other linux.  Lilo is older and some still prefer it, but basically grub and lilo can be interchanged for each other.  That being said you may occasionally run across hardware where one will work and the other won't.

In the end you can use grub with slack or install lilo to the root partition and I think you can still chainload like you do a windows partition.  To me it would be simpler to just use grub with slack since you have it installed.[/QUOTE]
 Alright bud, I'll give it a shot and tell you how it goes. (If you care, haha).  Thanks!

---

### Post by wvslkr on 2005-09-06
If you have problems post back. if I can't help someone else will jump in  GL.

---

