---
title: "Allocate Drive Space  Question On New 11.4 Install"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2011-04-30
I tried to install 11.4 and backed off at the _Allocate drive space_ prompt.  My goal is dual boot with Win7 but I'm doing this on a netbook (Asus 1015PEM) without a CD/DVD drive for recovery.    In it's factory condition recovery (such as it is) is done by hitting a function key (F9) during boot and /dev/sda2 is used to rebuild /dev/sda1 (Windows C disk).  You might say that it is dual boot right out of the box and adding narwhal 11.4 would make it triple boot.  (If anyone thinks I mis-understand recovery here please speak up.  I am not as confident as I'd like to be that I understand it.)  

I wish to use /dev/sda3 (currently the Windows D disk) for narwhal.  I don't know how to reply to the  _Allocate drive space_ prompt.  For the four partitions there are check boxs for _Format_.  I presume that I check that only for /dev/sda3 since it needs to be ext3 or ext4 etc.  There are five buttons of which the first two are grayed out.  The five are _New partition table_, _Add_, _Change_, _Delete_, and _Revert_.  I suppose that I highlight dev/sda3 and hit the _Change_ button??  Below that there is a box for _Device for boot loader installation:_.  The choices are 1) /dev/sda ATA 250GB, 2) /dev/sda1 Windows 7 (loader), 3) /dev/sda2 Windows Recovery Environment (loader), 4) dev/sda3, and 5) dev/sda4.  Sorry but I didn't write down any comments for the last two if they were there.  I guess that dev/sda3 would be the choice here.  

Again, my goal is to retain Win7 and it's recovery and add 11.4  I'd appreciate any help.  BTW 11.4 runs well from a flash drive.  I was also skeptical about Unity but I like the way it preserves vertical real estate on the constrained display.

---

### Post by Quackers on 2011-04-30
You appear to have 4 primary partitions, (which is the maximum allowed on a mbr partitioned disc) though I have no idea what's in sda4 - neither does gparted!
You will need to delete one of those partitions before Ubuntu will install - otherwise serious problems will occur!
If you are sure that sda3 is your D: drive (in Windows parlance) and there is nothing in that partition that you need, you can delete it.
You can then install Ubuntu into that free space (probably in an extended partition).
You should also check what's in sda4 as well.

---

### Post by n4lbl on 2011-04-30
What I was thinking was re-using dev/sda3 as (as you indicated an extended partition to include swap).  So, if I follow you correctly, delete dev/sda3 and the install will provide a follow-up with an add option.  I presume that making it an extended partition will somehow become obvious.

I don't know how to proceed concerning dev/sda4.  In the absence of knowledge I was going to merely ignore it.

My guess is that I have two options.  Your suggestion of deleting dev/sda3 and re-allocating it or formatting it (with the _Change_ button).  

The question of the selection for _Device for boot loader installation:_ remains.  I need to know what to expect for the three boot possibilities: Win7, Win7 recovery, and Ubuntu 11.4.

Thanks,,,

---

### Post by Quackers on 2011-04-30
Unless you delete sda3 first I don't think the Ubuntu installer will offer anywhere to install Ubuntu (other than to use the whole disc - which you DON'T want!).
The device for boot loader installation is the drive where you are installing Ubuntu to - normally /dev/sda - NOTE, NOT a partition, like /dev/sda1 or /dev/sda2

---

### Post by n4lbl on 2011-04-30
Thanks for those answers.  After the install what I hope to be able to see is:  1) The Asus flash screen comes up.  At this point I could 2) hit F2 for the BIOS (or whatever it's new name is), 3) hit F9 to recover Win7, or 4) do nothing and Grub (Grub2??) will give me the choice of Ubuntu 11.4 or Win7.  Am I visualizing this correctly??

I'll probably wait until tonight to proceed when I'll have extended time available.

---

### Post by Quackers on 2011-04-30
After installation you will get either Ubuntu booting directly, or, hopefully, a grub menu with a choice of which operating system to boot from.
Please note, if, after installation, you choose to recover Windows it will over-write grub and Ubuntu as well!
And why do you want to get into the bios? You can do that now surely?

---

### Post by n4lbl on 2011-04-30
I was merely trying to visualize all the possibilities to test if I was thinking clearly.  I don't know if this is generally true, but on this machine a freshly inserted USB flash drive will be second in the boot order and I must change the BIOS entries to make it first.

Speaking of visualizing all the possibilities, many thanks for pointing out the consequences of a Win7 recovery!!

---

### Post by Quackers on 2011-04-30
No problem.
It is very possible that a Win 7 recovery would wipe out everything on the drive.

---

### Post by n4lbl on 2011-04-30
HELP!!  I added an ext4 partition (no extended option visible) and when I hit _Install Now_ I get a message "No root file system is defined.  Please correct...".  Going back to _Create a new partition_ I specified 1) logical (pre-filled), 2) size (pre-filled), 3) location beginning (pre-filled), 4) use as: ext4 jfs (pre-filled), and mount point "/" (pre-filled as blank last time and this time).  Is that "/" mount point correct??

---

### Post by Quackers on 2011-04-30
Did you delete sda3 first?
Yes the mount point for the root partition is "/"

---

### Post by n4lbl on 2011-04-30
Yes I deleted it.  Just changed the mount point to "/".  Now a message "You have not selected any partitions for swap space...."  It wants me to go back to the partitioning menu where I have a choice of _swap area_ instead of _ext4_ (and other choices) but no combination.

---

### Post by n4lbl on 2011-04-30
I just changed logical to primary but am afraid to proceed.  Does that make sense?

---

### Post by Quackers on 2011-04-30
Did you select "primary" or "logical" as partition type for "/"?
It needs to be logical, or you will be trying to exceed the maximum of 4 primary partitions.

---

### Post by n4lbl on 2011-04-30
The absence of a swap came about with logical.  I don't know what to do to include a swap.  Perhaps I missed something??  I am back to logical now.

---

### Post by Quackers on 2011-04-30
If you have 2GB of ram or more and don't intend to use "hibernate" you don't need a swap space.

---

### Post by n4lbl on 2011-04-30
I do have 2GB but the 10.10 machine I am on now has 3GB and uses some swap space occasionally.  I didn't use the _New Partition Table_ button.  Is that of interest??

---

### Post by Quackers on 2011-04-30
No, just double click the unallocated space, or highlight it and click on the Edit button

---

### Post by n4lbl on 2011-04-30
The choices are _New Partition Table_, _Add_, _Change_, _Delete_, and _Revert_.  

I deleted it again and with add the choices are:
[INDENT]type: primary or logical[/INDENT]
[INDENT]new partition size: ~126GB which makes sense[/INDENT]
[INDENT]location: beginning or end[/INDENT]
[INDENT]use as: ext4 jfs and other choices[/INDENT]
[INDENT]mount point: "/" (primed with blank).[/INDENT]

---

### Post by Quackers on 2011-04-30
Just double click on the unallocated (or free) space and a window will open. If you want a swap partition, make one, but change the size option first. Then OK that change.
Then double-click on the free space again and make your ext4 partition as logical with a mount point "/" using the remaining space - or any other amount you want.

---

### Post by n4lbl on 2011-04-30
Sorry if I sound up-tight, but I am.  If I double click on the free space it comes up exactly the same as in add.  There is no extended option to carve it into ext4 and swap.  I'm concerned that I missed something.

---

### Post by n4lbl on 2011-04-30
Is it possible that ext3 jfs would work??

---

### Post by Quackers on 2011-04-30
No changes are actually made until you move on from that screen - after clicking on "install" if I remember correctly.
You can experiment a little bit.
Make a swap space with type logical, then OK it.
Then double-click (or click on Add) on the free space again and try to make a ext4 partiton for root with type logical. Does it allow it? Are both new partitions displayed in the original Allocate space" window?

---

### Post by n4lbl on 2011-04-30
I deleted it, made it a swap file, double clicked to change it and selected ext4, and ended up in the same place.  

The message says that the installation can go through without a swap.  Could that be corrected later??  On this 10.10 machine (not the one we are working on) when I installed 8.04 I think (??) the installer set up the swap by itself.

---

### Post by Quackers on 2011-04-30
On the 10.10 installation you must have selected the "install alongside" option.
Did you try the above? Did you try to create a swap first with smaller size than the total amount of free space? Or did you make a swap file using up all of the free space?

---

### Post by n4lbl on 2011-04-30
The 10.10 machine is also dual boot with Vista.  It has two ntfs partitions and one extended partition with ext3 and swap.

---

### Post by n4lbl on 2011-04-30
Quackers, thank you very much for your effort and time.  I have to leave in about an hour so I'm backing out and will try again tonight or tomorrow.  If you happen to think of how I can make this partition extended to include both ext4 and swap please reply when you can.  Also, it would be of interest if the absence of a swap could be remedied after-the-fact.

Again,,, many thanks.

---

### Post by Quackers on 2011-04-30
Exit the installer and use gparted from the live cd to create an extended partition in the space where sda3 was.
You're welcome.

---

### Post by n4lbl on 2011-04-30
I did "experiment" with gparted while I was waiting (with the installation in-progress) without committing anything.  The way to do it wasn't immediately apparent.  

I'll read the gparted doc' tonight.

Again,,, many thanks.

---

### Post by n4lbl on 2011-04-30
Just to be ornery, the 11.4 running from the flash drive wouldn't shut down!!

Again, thanks,,,

---

### Post by n4lbl on 2011-04-30
Well, with gparted (not install) I took my dev/sda3 (Windows D) and made an extended partition which somehow came out ext4 and ~2GB swap which seems fine.  I started install and seem to have stalled in _Keyboard Layout_.  The file copying progress bar is at ~80%.  It says "Ready when you are" but the _forward_ or _backward_ buttons don't work.  Used space in the target is at 3.91 GB.  I have no idea of how to proceed.

---

### Post by Dutch70 on 2011-04-30
Take the capital letters out of your user name. :)

use lower case letters only.

---

### Post by n4lbl on 2011-04-30
I don't understand.

---

### Post by n4lbl on 2011-05-01
Using GParted prior to install to make an extended partition worked.  Many thanks.  Now to figure out how to mark this solved!!

---

### Post by Quackers on 2011-05-01
Thread Tools near the top of the page.
Glad you got things sorted out :-)
Have fun!

---

### Post by Dutch70 on 2011-05-01
> **n4lbl said:**
> I don't understand.

I apologize.

Using capital letters in your user name when installing will cause a similar issue, 
and it's become so common lately that I assumed that was your problem as well.

Glad you got it worked out!

---

### Post by n4lbl on 2011-05-01
Thanks for trying and no need to apologize.  

Now I'm on to the next treat.  Audio that worked running from the flash drive doesn't work with the "real" install.  Note:  this isn't a request for assistance.  Yet  ;=))

---

