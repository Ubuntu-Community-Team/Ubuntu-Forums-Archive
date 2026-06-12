---
title: "If I delete Ubuntu partition..."
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by s1mple_M4N on 2006-11-15
Hi all.

My current set up is Windoze XP/Ubuntu (Dapper) dual-boot on 40GB HD (50/50 partitioned).

I can't/won't yet totally get rid of Winblowz (wife, kids demand it), and Ubuntu is quite space hungry at the moment.

I have just purchased a second-hand 40GB HD and would like to install Dapper on this disk.

If I use windows Admin Tools to delete the current Ubuntu partition, will the PC boot OK? I'm OK with many admin tasks but the MBR I'm not too sure about.

If I reinstall Window$ on master, run the live-CD - will Ubuntu setup allow me to use slave HD as main Ubuntu installation drive?

Appreciate any help, these forums have already been an excellent source of vital info.

Thanks

Roy J

---

### Post by confused57 on 2006-11-15
Here's how to uninstall Ubuntu:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you just deleted the Ubuntu partition, you wouldn't be able to boot your pc, because grub is installed to the mbr.  The above link shows you how to restore your Windows mbr, using the Windows install cd or a Win98 bootdisk...once you have repaired the mbr & can boot Windows without grub, then you can delete the Ubuntu partition.

Here's how I have my 2 hard drive system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by SoggyCornflake on 2006-11-15
> **s1mple_M4N said:**
> I can't/won't yet totally get rid of Winblowz (wife, kids demand it), and Ubuntu is quite space hungry at the moment.
I had that same problem until my wife got fed up with the constant spam bots on our Windows XP machine.  Finally she begged me to load Ubuntu onto it. :) 

> **s1mple_M4N said:**
> If I use windows Admin Tools to delete the current Ubuntu partition, will the PC boot OK? I'm OK with many admin tasks but the MBR I'm not too sure about.
I think this depends upon what your  computer normally boots into.  If it boots into Windows by default, then you might be pretty safe.

> **s1mple_M4N said:**
> If I reinstall Window$ on master, run the live-CD - will Ubuntu setup allow me to use slave HD as main Ubuntu installation drive?
What I would do would If Reinstall is the way to go, is to install Windows without the second hard drive installed (No sense confusing the Windows installer.)  Then I would install the second hard drive and install Ubuntu on that.

I have to admit I have no first hand info on installing Ubuntu on a Windows/Dual Boot machine.  I have done this with Slackware, and it is user friendly enough to handle doing a multiboot install to a slave HD.  I'm sure Ubuntu can handle it.



> **s1mple_M4N said:**
> Appreciate any help, these forums have already been an excellent source of vital info.

Thanks

Roy J

Hope you still think that way after my post.:-D

---

### Post by s1mple_M4N on 2006-11-15
Thanks guys, I will definitely give this a go.

Everybody on these forums is so helpful!

Roy J

---

