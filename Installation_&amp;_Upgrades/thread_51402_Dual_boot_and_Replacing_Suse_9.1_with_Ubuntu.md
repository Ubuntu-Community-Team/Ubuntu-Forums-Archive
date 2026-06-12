---
title: "Dual boot and Replacing Suse 9.1 with Ubuntu"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by mike99 on 2005-07-23
Currently moderately happy/unhappy with Suse 9.1 on a dual boot WinXP/linux box.  

I can't afford to update to 9.3 from Novell... and can't figure out how to create a 9.3 bootable DVD, so......

I'm considering Ubunto, and have questions.

(1) If I get an Ubuntu CD, can I install it so that it will operate in dual boot mode with existing Windows XP?  Grub is currently my OS selector.   

(2)  Will Ubuntu install NEXT to the SUSE installation, or OVER it (replacing it) or does it not know how to install on a dual boot set up?

(3) Can I request from Ubuntu both a LiveCD and an installation disk?

(4)  How automagic is the Ubuntu install anyway?

thanks

---

### Post by Xian on 2005-07-23
[QUOTE=mike99]I can't afford to update to 9.3 from Novell... and can't figure out how to create a 9.3 bootable DVD, so......[/quote]
Download the iso. Open k3b.
Tools > CD > Burn CD Image

[QUOTE=mike99]If I get an Ubuntu CD, can I install it so that it will operate in dual boot mode with existing Windows XP?  Grub is currently my OS selector.[/quote]
Yes, no problem. Ubuntu uses grub by default.  

[QUOTE=mike99]Will Ubuntu install NEXT to the SUSE installation, or OVER it (replacing it) or does it not know how to install on a dual boot set up?[/quote]
Depends. If you select auto-partition it might format something you'd prefer to be left untouched. This is no different from SuSE. However, just like SuSE you can do the partitioning manually, so you'd only need to choose your mountpoints and format only the desired partitions.

[QUOTE=mike99]Can I request from Ubuntu both a LiveCD and an installation disk?[/quote]
AFAIK the LiveCD is download only.

[QUOTE=mike99]How automagic is the Ubuntu install anyway?[/quote]
[LOOK](http://mrbass.org/linux/ubuntu/install/) for yourself.

---

### Post by mike99 on 2005-07-23
Thanks.

To clarify... then if I wanted for some reason to leave my current SUSE install and also install Ubuntu, I'd have to add some partitions for Ubuntu?   

When I installed Windows XP followed by Suse, the suse installer automatically ersized the NTFS partitions and created linux file system partitions (can't remember what the linux file system is called).

That's the sort of scary operation I'm happy to have an installer handle.. not ready to do myself.

So in the process of Ubuntu install... am I going to have to figure out the repartitioning... or just designate 2 new mount points?

If I select autopartition I would assume that it would write over the SUSE install... although it would be a happy accident if it somehow left me with a functioning SUSE install also.

(By the way, did try downloading the 9.3 suse iso and burning it to DVD... but the DVD never functioned as a bootable DVD in my machine, so I was never able to install it over suse 9.1..... unlike the original from Suse 9.1 professional DVD which just got read and installed the whole shebang.  Never figured out why not.)

---

### Post by Xian on 2005-07-23
[QUOTE=mike99]So in the process of Ubuntu install... am I going to have to figure out the repartitioning... or just designate 2 new mount points?[/QUOTE]
All that "figure out" entails is: 

1. Create a new partition 
2. Choose the file system
3. Set the mount point

I trust the InstallCD auto-partitioner (both SuSE and Ubuntu) up to a point, but this does not include on a drive that contains existing Linux systems. I just feel more comfortable doing this myself. Further, if you want to continue using the SuSE bootloader you can tell Ubuntu to place the grub install into its own root directory.

---

