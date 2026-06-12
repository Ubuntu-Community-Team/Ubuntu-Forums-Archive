---
title: "Help! Cycle of Continuous Rebooting!"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by Rick on 2005-04-08
Help!  Yesterday, I resized my NTFS partition to make room for Hoary.  I intend on dual-booting.  I was successful with that and got Hoary installed and everything.  Everything seemed to work fine.

Today, I tried to reboot into Hoary and now, GRUB will say "loading stage", then, my PC will reboot.  It's not just a nasty cycle of reboot, GRUB message, reboot, GRUB message, etc.

Anyone have any ideas?

---

### Post by ubuntu_demon on 2005-04-08
[QUOTE=Rick]Help!  Yesterday, I resized my NTFS partition to make room for Hoary.  I intend on dual-booting.  I was successful with that and got Hoary installed and everything.  Everything seemed to work fine.

Today, I tried to reboot into Hoary and now, GRUB will say "loading stage", then, my PC will reboot.  It's not just a nasty cycle of reboot, GRUB message, reboot, GRUB message, etc.

Anyone have any ideas?[/QUOTE]

But from a linux livecd like ubuntu livecd or knoppix. Get your local filesystem mounted.

You should first check if your /etc/grub/menu.lst is okay. If it is okay this article might help you. It's for fedora core 2 but ubuntu has this problem also sometimes.

[http://lwn.net/Articles/86835](http://lwn.net/Articles/86835)

Also you might try to put your master boot record back using a diskette with fdisk.

---

### Post by Rick on 2005-04-08
[QUOTE=demon666_nl]But from a linux livecd like ubuntu livecd or knoppix. Get your local filesystem mounted.

You should first check if your /etc/grub/menu.lst is okay. If it is okay this article might help you. It's for fedora core 2 but ubuntu has this problem also sometimes.

[http://lwn.net/Articles/86835](http://lwn.net/Articles/86835)

Also you might try to put your master boot record back using a diskette with fdisk.[/QUOTE]
 I think my problem is more with grub though.  My partitions seem to work fine.  I can reboot once just fine.  However, subsequent reboots cause my system to go into an infinite loop of reboots.

Here is exactly what happens (I've been able to reproduce this twice now):

1. Install Ubuntu
2. Use Ubuntu just fine
3. Edit /boot/grub/menu.lst to make Windows my default boot option
4. Reboot
5. Grub comes up with Windows as the default
6. Log into Windows and use it just fine
7. Reboot to log into Ubuntu again
8. BIOS comes up
9. "GRUB Loading stage 1.5" appears
10. PC automatically reboots itself

It's at this point that steps 8-10 go into an infinite loop that I can't break out of other than running my live CD.  That's what I'm using now.

It's almost as if GRUB is screwed up somehow...

---

### Post by Rick on 2005-04-09
Anyone have any ideas?

---

### Post by aresgodofwar30 on 2008-02-05
I have this same problem. 

Here is the output of my fdisk -l. Can somebody assist me? I think this may have to do with the small partition on my primary hard drive before the Windows Partition. 
If it makes any difference, I have Windows Vista Ultimate on my primary hard drive and Ubuntu 7.1 on my secondary hard drive.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f5c0f5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1        9730    78148608   42  SFS
/dev/sda3            9730        9730          88   42  SFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000597e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29645   238123431   83  Linux
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris

```

---

