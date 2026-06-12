---
title: "Installing Windows now that I\ve installed Ubuntu"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Rycus on 2008-03-08
So, if you have read another post by me, you'll know that I accidentally reformatted my whole computer :((changed the format to fat32) and so I simply installed Ubuntu afterwards. Now, when I installed Ubuntu, I made it only use 50% of the drive. So, when I tried to install windows after that, when it asks me to pick a partition, it tells me to use the up/down keys. At this point, whatever I do makes it go to BSoD and I've gotten nowhere. At the moment,  I changed the format of that drive to ext3 (how do I mount after unmount btw) and I am gonna try to install windows. Am I doing anything wrong, is there another way (better way?) Please help...!

---

### Post by Herman on 2008-03-08
Some versions of Windows will refuse to install if they detect a Linux swap area (Windows 98SE, I know for sure, was like that), others will wipe everything off your hard drive and take over the whole hard disk. Some will install in a civilized manner. It depends which Windows version and what kind of Windows CD you have.
You might have to delete Ubuntu to install Windows, then re-install Ubuntu.

---

### Post by Rycus on 2008-03-08
Thanks...I'm using XP and whenever I go to install windows, it gives me a list of 4 drives that say something like "unknown" (all the same) and if I do anything it crashes. I'll try your idea. The problem was that I reformatted my computer when trying to dual boot. How can I do this properly (partitioning?)?
Thanks a TON!

---

### Post by jken146 on 2008-03-08
The best way is this:

0.  Back up anything you want to keep.

1.  Install Windows XP.  Use the XP installer to delete all your partitions.  Create one partition for XP, at least 15 GB in size.  Tell the installer to format it to NTFS.  Finish the XP installation.

2.  Install Ubuntu.  You can use the guided partitioning option (use largest continuous free space) if you like, or if you feel up to it, use the manual option and have the following partitions:
a 10 GB ext3 partition for /
a swap partition of size RAM x 1.5 (but not bigger than 1 GB) at the end of the drive
an ext3 partition for /home taking up all the space in the middle.

3.  Boot into Ubuntu and mount the XP partition somechere so that you can access it easily:  [www.psychocats.net/ubuntu/mountwindows](www.psychocats.net/ubuntu/mountwindows)

4.  Boot into Windows and install the ext2 driver so that you can access the /home partition:  [http://fs-driver.org](http://fs-driver.org)

---

### Post by Herman on 2008-03-08
First, make sure any data you have on the hard disk is backed up on some other media and double check to make sure, then triple check.

The easiest (and best) thing to do would be to just fire up your Ubuntu Gutsy Gibbon 'Desktop' Live CD and go 'System'-->'Administration'-->'Partition Editor' and open GParted.

You'll see a graphical view of whatever partitions you have in your hard disk. Probably you need to right-click on each one and click 'delete', and confirm that. 
If you want. try just deleting the linux swap area and reboot and try the Windows installation again. That works for me with my Windows 98SE disk.
If you really have to, delete your Ubuntu partitions and try again.

Some Windows installers can make or at least deal with partitions and some can't. With Windows 98, you need a floppy disk to prepare the partitions first, and Windows 98 could deal with a partitioned disk failry well.
Many kinds of Windows XP disks, 'Installation' disks, or various kinds of 'Recovery' disks are not so freindly.

Actually, if you don't actually need Windows, why bother with it? ...but I know what you're going to say, there's some program you need that you only know the Windows version of, that's okay. Dual booting's cool. (Once you get it set up). :)

Regards, Herman

---

### Post by Rycus on 2008-03-08
Thanks for the help. I believe I\m set, but the problem doesn't seem to go. I empties all my partitions (I\m gonna try to delete Linux Swap but I dont think that will work), and whenever I put the windows XP install disk in, I get 4 "can't read drive| drives. What should I do? This is probably one of the reasons I want to dual boot because the installation isn\t hard and there arent as many stupid problems. And you're right, I need windows for programs and because my wireless receiver needs something installed to work =(
Anyone recognize this problem. Is it the HD itself (it's only one month old). At the moment, I have a 50% ntfs partition as my first one, and another 50% partition, this one is ext3. I know I may not be making sense or I might seem a bit whiny, but I just lost basically everything...Help!

---

