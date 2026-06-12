---
title: "Dual Boot Xp n Ubuntu"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by gnarula on 2006-06-30
Hello!

I have a 80 GB Hard disk which is partitioned.. i have windows xp.. i also had windows 98 which i got rid of just now.. now the problem is i want to install ubuntu on the artition in which win 98 was installed but i dont know how to..

I had win 98 on C: drive n i have win XP in E: drive.. i have a floopy disk drive a dvd writer 256mb of ram.. Intel D845GLVA Motherboard.. pls tell me how to dual boot xp n ubuntu..

P.S. i m a complete newbie to Linux.. pls guide me..:cry:

**I would also like to point out that i have installed xp in a fat 32 partition**

---

### Post by chicken-man on 2006-06-30
Delete the Windows 98 partition and run the installer, when you get to partitioning make a EXT3 partition and a SWAP partition in the free space.
(500mb - 2gb for swap is good depending on how much ram you have)

The next step is to set where they will be mounted, make sure you set the EXT3 partition to be mounted on '/'.

After that just carry on with the install. Have fun :)

---

### Post by OffHand on 2006-06-30
make a seperate /home partition for easy reinstall and upgrading.
also install windows first (otherwise you have to mess with installing the grub on the mbr again, because Ubuntu recognizes XP but of course XP refuses to see Ubuntu.)

---

### Post by nickpaton on 2006-06-30
Removed since double posted for some reason!!

It wasn't that good!

---

### Post by nickpaton on 2006-06-30
Hi - Welcome to the World of Ubuntu!

The problem you have is that XP needs to be seen first on the Master Boot Record (MBR), with Linux following.  In your case you have the 98 partition as the first one. 

1. Backup your important documents and files on XP.

2. Defragment XP.  I suggest the evaluation version of Perfect Disc from Rasco: 

[http://www.raxco.com/]("http://www.raxco.com/")
 
This does a far better job than the built in Microsoft version. 

3. Combine the 98 and XP partitions into one using, say, Acronis Disc Director, again available as a trial at:

[http://www.acronis.com/homecomputing/download/]("http://www.acronis.com/homecomputing/download/")

4. Now you need to repartition your HD for Ubuntu.

To save space writing out a long script, the one I've always used is "Matthew J. Miller's HOWTO: Dual Boot Linux and Windows XP on a Toshiba laptop", which is easily adapted for whatever box you have & can be found at:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/")

The important thing that this article emphasises is the creation of an additional FAT32 partition which allows you to copy files between XP and Ubuntu, as well as a separate storage area for your Ubuntu documents.  When I first started I reinstalled Ubuntu many times, and found the FAT32 partition invaluable for things like saving my Firefox browser bookmarks I'd gathered.

The one other thing I have done is to simply install Grub in the MBR, and not to create a dual boot screen as he suggests (though I have done this as well - it's not difficult!).  

If you have gone down the MBR route, if you need to reinstall Ubuntu I would suggest cleaning up the MBR before reinstallation since you will end up with numerous Ubuntu entries!   

To do this simply insert your XP installation disc, let it boot and wait a few minutes whilst it loads the programs it needs to install.  

When it comes to the choice to install or repair, press 'r'.

At the Admin login press enter key & ignore any error messages.

Finally type 'fixmbr' (no ''s!), read (note, inwardly digest, and carry on!) the warning messages and type 'y' for yes to continue.  Done!
   
I'll stop at this point to see how you get on.  

Would others also please assist and correct me as necessary.  I too am a noob:smile:

(amended for spelling corrections!)

---

