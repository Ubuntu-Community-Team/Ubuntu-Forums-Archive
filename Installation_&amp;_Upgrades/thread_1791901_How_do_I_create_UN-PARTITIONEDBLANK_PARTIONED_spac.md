---
title: "How do I create UN-PARTITIONED/BLANK PARTIONED space?"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Shvesley on 2011-06-27
I need to install Windows Xp Pro 64 Bit, but during the installation process it asks that I partition Win Xp to Un-Partitioned space.

 The only partitions I have on my computer are /dev/sda 1 (142.96 GiB Ubuntu) and /dev/sda 2 (6.09 GiB Extended/linux-swap)

I need to create a new blank partition on which I can install my new OS. Any help?

---

### Post by sanderd17 on 2011-06-27
Boot up a live cd, open gParted, shrink a partition (by right clicking -> resize) and what is left is unallocated space.

Don't forget to click the green V to apply.

---

### Post by jerrrys on 2011-06-27
with gparted

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-resize-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-resize-partition)

---

### Post by Leslie D on 2011-06-27
You would have to find a program which can shrink one of your existing partitions by (I would guess) 40Gb or more. I can think of a Windows program which can do that, but that isn't much use to you.

You might also want to install a boot manager, because XP tends not to be particularly user friendly when it comes to installing anything other than other versions of Windows on its boot menu.

---

### Post by Shvesley on 2011-06-27
How can I boot up a CD and then open Gparted? When you boot up the Win CD doesnt it just take you to the installation process? How can I do that? I am relatively new to this.

---

### Post by Shvesley on 2011-06-27
Is this the right kind off boot manager? 

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by sanderd17 on 2011-06-27
The live CD is a linux live CD. You used one to install Ubuntu the first time didn't you?

And the boot up manager has nothing to do with your problem.

---

### Post by jerrrys on 2011-06-27
boot manager is built into ubuntu.  

as for gparted.  just boot the live ubuntu cd and go to "try without installing".  then system>admin>gparted

---

### Post by Shvesley on 2011-06-27
I also having trouble with unmounting sda 1. It says I can't unmount it from [this] mount point.

---

### Post by jerrrys on 2011-06-27
are you on the live cd?

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition)

---

### Post by sanderd17 on 2011-06-27
> **Shvesley said:**
> I also having trouble with unmounting sda 1. It says I can't unmount it from [this] mount point.

Are you running it from a live CD? You can't edit a partition that is in use (e.g. running your OS).

---

### Post by oldfred on 2011-06-27
Gparted is on the Ubuntu liveCD or you can download a separate (smaller) gparted or parted magic (which has gparted) liveCD.

Be sure to have good backups as any partitioning  is major changes to your hard drive.

Most times you just need to create a primary NTFS partition with the boot flag in gparted. Then windows will install to that. When you use the liveCD it usually mounts the swap partition to speed things up. Since your swap is not in the extended you may not have to swap off. But if you have issues you can. Windows does not see the Linux partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://partedmagic.com/](http://partedmagic.com/)

You will need the Ubuntu liveCD for the current version you have installed as windows will install its bootloader to the MBR and you will have to reinstall grub or grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Shvesley on 2011-06-27
Wait, I have a Ubuntu 10.10 Live CD. Should I boot up with that open Gparted, resize my main 11.04 partition which would make un partitioned free space, then take out the 10.10 cd, put in the win xp cd, and then install the os on that free space

right?

---

### Post by jerrrys on 2011-06-27
i much prefer one step at a time and yes, your 10.10 cd has gparted

---

### Post by Shvesley on 2011-06-27
haha sry, I was typing everything fast before I over analyzed :P

Ok, right now I am in the 10.10 LIve CD, I resized my primary partition and there is now 100 GiB of free space. 

1. Confirm new partition size

2. take out live cd

3. put in win xp cd

4. install win xp on free partition 

5. use win xp

If the Win Xp installation is a flop or I don't like Win Xp any more. I can always open Gparted on the 10.10 Live CD and just delete the Win Xp partition and resize Ubuntu 11.04 to fill in the space right?

---

