---
title: "New user installation."
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by Edward46 on 2011-04-03
After doing some research for the past 2 days and of course finding out that v10.10 has some installation issues, I decided to download v10.4 lts.  I already burned it to disk and ran it without installing it and so far I am impressed.

Now for the installation part.  On my system I have 2 drives (sda and sdb).  I am planning on a dual boot set up and of course sda is to remain untouched.  Not even the boot manager is permitted to touch this drive.  The second drive contains 2 partitions, the first is for data storage only and the second is a 43gig partition which I plan on using for linux.

Question:  Is it possible to direct the installation to use this existing partition?  I understand that this partition must be prepped for linux.  I would think it would be possible to install to an existing partition.
If not, I can easily remove this partition and convert this to unallocated space.

At this point can I assume that the grub can be directed to this particular partition?

If someone could help with the basic steps here, it would be greatly appreciated.  I have researched installation procedures, but the end result is more questions than answers. 

Thanks

Edward K.

---

### Post by Hedgehog1 on 2011-04-03
You were doing great until: ***Not even the boot loaded is allowed to touch /dev/sda***

See - the computer needs a single boot point.  The Ubuntu installed grub (**GR**and **U**nified **B**oot loader) would typically add itself to the MBR of /dev/sda.

The rest of grub (setups and menu text) and all of Ubuntu can live on /dev/sdb, no problem at all.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-03
The 'rule of thumb' for partitions is: Use Windows tools for NTFS partitions, and Linux tools for Linux partitions.

Also, be aware that Windows support MBR style partition maps only allow 4 primary partitions.  They are names sda1-sda4, sdb1-sdb4 and so on.

We need more partitions for that, so when we share a system with windows we create an 'extended' partition and fill it with as many 'logical' partitions as we need (logical partitons start at sda5 and go up from there).

In you case, a layout like this is suggested:

/dev/sdb1 NTFS
/dev/sdb2 extended partition
__/dev/sdb5 ext4 '/' (said 'root') partiton 25 gigs.
__/dev/sdb6 Linux Swap (the size of your RAM + 10%)
__/dev/sdb7 ext4 '/home' Where all you Linux data lives (all the space no used by sdb5 & sdb6)


These sdb2 & sdb5-sdb7 partitons are built using gparted from the LiveCD/LiveUSB.

[SIZE="3"]My pictures are of drive sda (only ones I have); please swap the sda for sdb when doing this.[/SIZE]

In gparted, create 3 partitions:

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

Remeber, you need to translate the sda5=sdb5, sda6=sdb6 & sda7=sdb7. Now you will 'map' the three partitions on /dev/sdb.

First, make /dev/sdb1 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-03
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

:KS

---

### Post by dieselglock on 2011-04-03
If you follow Hedgehogs advice you'll be golden. That exactly how my dual boot is set up.

---

### Post by Edward46 on 2011-04-03
Past topics that I have researched indicated that the bootloader can actually be on the same drive.  In fact, I have read that the installation can be done with the first drive disconnected.  After this, grub can be updated to include the first drive or I can switch boot drives via bios.  Is the above actually true??  To make things even easier at this point, I can move the data elsewhere and dedicate the second drive totally to linux. 

I realize that this may not be leading to a true dual boot situation, but my first option is to actually keep my XP installation seperate from linux.  

Or is it possible that I am worrying too much about having the mbr on my first drive modified.  I do keep backups and I was planning on creating a new image before installing.

Edit:  Thanks for the information.  Following the above steps, the directories are created before the installation process.  Is the default layout that bad? 

Edward.

---

### Post by jocko on 2011-04-04
> **Edward46 said:**
> I realize that this may not be leading to a true dual boot situation, but my first option is to actually keep my XP installation seperate from linux.
If you can pick which hard drive to boot from in the bios, just set the one you want ubuntu on first in the boot order before you start installing. During install you'll get to select where to put the boot loader. Just make sure you put it in the boot sector of the drive (NOT partition) where you installed ubuntu. Grub should pick up your windows install and add an entry for it in the boot loader.

If you are not totally sure you can even unplug the windows drive before you install, and after install plug it in again and make sure the bios is still set to boot from the other hard drive. Then boot ubuntu, open up a terminal and run the command "sudo update-grub" to let grub detect windows and add it to the boot loader.

If windows does not boot after this you need to figure out how to make grub re-map the drives to let the windows drive be the first drive only when windows boots. Or you can switch the boot order in bios...

---

### Post by jocko on 2011-04-04
> **Edward46 said:**
> Or is it possible that I am worrying too much about having the mbr on my first drive modified.  I do keep backups and I was planning on creating a new image before installing.
The only drawback with letting grub take over the mbr of the first hard drive is that windows will become unbootable if you remove your second hard drive (where the rest of grub will be). But it's not very difficult to fix the mbr to restore the windows boot. There are several ways, requiring either a windows cd or any linux live cd...

---

