---
title: "Feisty Installation Problem - Grub error"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Rashedul on 2007-04-21
I searched everywhere for it but can't figure out a solution yet. My problem is similar to this one 
[http://ubuntuforums.org/showthread.php?t=371483](http://ubuntuforums.org/showthread.php?t=371483)

I basically cleaned out one partition and tried installing Ubuntu Feisty in it. It goes well until grub installation when it produces the Fatal Error (hd0). I'm trying to install Feisty on IDE0, Partition 3 (HDA3). 

I was waiting for something like feisty to start switching to Ubuntu. Popped in the live cd and loved how easily it was able to connect to the wireless network, which was one of the only thing holding me back from using Ubuntu. Ubuntu in Live environment worked amazing. Love it, now want to install it. Help?

Edit: I'm trying to install the AMD64 version, did a slow burn 4x.

---

### Post by bulldog on 2007-04-21
Can you give us the output of```
sudo fdisk -l
``` you can perform this in a terminal in a live cd session.
It's a lowercase L not a one.

---

### Post by Rashedul on 2007-04-21
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   12  Compaq diagnostics
/dev/hda2   *         638        7583    55793745    7  HPFS/NTFS
/dev/hda3            7584       14496    55528672+   7  HPFS/NTFS
/dev/hda4           14497       14593      779152+  82  Linux swap / Solaris

I'm trying to put Ubuntu on hda3. During installation i select it and check the format option. I also created the Swap partition. Hope I can figure this out. Thanks for your help.

---

### Post by bulldog on 2007-04-21
You don't have a linux partition [ext3] just a swap file.

You have to 'mount' your hda3  as  /  [which is root]  during partitioning and set it to format ext3.
You can set the boot flag too,just read all the options carefully.
Your swap is mounted as 'swap' and format it as swap.

---

### Post by Rashedul on 2007-04-21
Yeah I understood that. HD3 was set to / mount and as ext3. Everytime I try to install it during partition manager I always set it to / and ext3 and it goes through the formatting. It all works until installation reaches 94% and Grub installation starts. Thats when it fails. GParted actually shows HDA3 as ext3. Any clue whats going on?

---

### Post by bulldog on 2007-04-21
Well it's surely not formatted because it's listed as a  NTFS fyle system!
So the formatting isn't done.

I would recommend the GParted live cd,which is only a 50MB download,burn it to a disk and boot from this cd.
You'll get a graphical partitioner like Partition Magic.
Create your partitions with this tool and format them.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Rashedul on 2007-04-21
Hey, first of all thank you for all the help. I realized that it wasn't being formatted properly so I tried few other things. With GParted I tried formating it after unmounting but it kept on giving an error that can't format to ext3 because its mounted. I unmounted but it kept on mounting automatically when GParted was refreshing. So basically decided to unmount and format before it had a chance to refresh ... if any of that made sense lol.... Everything worked fine. Installation is done. Gonna restart and start exploring now. Thanks again.

---

