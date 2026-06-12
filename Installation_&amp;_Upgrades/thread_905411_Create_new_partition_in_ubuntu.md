---
title: "Create new partition in ubuntu"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2008-08-30
I want to create new drives in ubuntu.....for the purpose of systematically keeping data...

I just have one drive named Filesystem which is 68 GB big....
I want to divide it into more no. of smaller drives...

I have also installed GParted but don't know how to use it for this purpose....

---

### Post by herteljt on 2008-08-30
> **nuke_fluke said:**
> I want to create new drives in ubuntu.....for the purpose of systematically keeping data...

I just have one drive named Filesystem which is 68 GB big....
I want to divide it into more no. of smaller drives...

I have also installed GParted but don't know how to use it for this purpose....

I do not think you're able to change the size of the drive if you are logged onto the Ubuntu system.  Two options I would suggest 
1) Boot from an Ubuntu live-cd and then install and run gparted 

or 

2) download and burn the Gparted live-cd  

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Amazona aestiva on 2008-08-30
I've used the live CD of Hardy to format a HDD.
I think gparted is installed by default on every Ubuntu live cd

---

### Post by GepettoBR on 2008-08-30
Yes, GParted is installed by default on the Ubuntu LiveCDs. You can't format the Filesystem (/) partition from Ubuntu because you'd have to unmount it first, and you can't unmount the root partition. Using GParted from the LiveCD is the way to go, but remember to backup all your data first, since there is no 100% guarantee that nothing will go wrong and if something does go wrong you lose all your data.

GParted is pretty easy to use. Once booted into the LiveCD, go to System>Administration>Partition Editor. When it's done scanning your drive, right-click the partition and choose Resize. Resize to whatever size you want (note that nothing will actually be done until you click the Apply button, so don't worry if you selected a wrong value). Then click the new empty space and select New Partition. If you intend on creating more than three partitions (not counting the one you already have) you'll have to create an Extended partition (not Primary) and create the other partitions inside the extended one. This is called logical partitioning and is a way to circumvent the existing limit of four physical (primary OR extended) partitions on disc.

Creating the new partitions is just like resizing the original one. Select a size, location on disc and filesystem (If you only have Linux installed, ext3 is the best; if not go with FAT32) and when you're done, click Apply. GParted will begin the operations, and it can take anywhere from a few seconds to over an hour depending on how much data you have. Then, just exit the LiveCD and organize your files from the regular installed Ubuntu.

---

### Post by nuke_fluke on 2008-08-30
Thanks a lot....I managed to partition ubuntu into 3 drives....

But why does each drive contain a folder named "lost+found" with a crossmark ?? and I am not permitted to look into them!!!!

When I right-click and go to Properties of this folder in each drive, I get the free space of the drive...

---

### Post by nuke_fluke on 2008-08-30
So now it seems the whole memory of the drive lies in that particular folder...as I couldn't copy any file to inside the drive (it says not enough space is available)

---

### Post by GepettoBR on 2008-08-30
> **nuke_fluke said:**
> Thanks a lot....I managed to partition ubuntu into 3 drives....

But why does each drive contain a folder named "lost+found" with a crossmark ?? and I am not permitted to look into them!!!!

When I right-click and go to Properties of this folder in each drive, I get the free space of the drive...

The lost+found folder is used to store journaling information for the filesystem, so if the disk crashes your data has a greater chance of being restored. This is the simplified explanation, but I don't know the full one :)

As for not enough space being available, that's weird but it shouldn't have anything to do with lost+found. Ubuntu doesn't pre-allocate space in your drives by default, and I can't think of anything that would make it behave that way. When you open one of the new partitions in Nautilus, does the status bar (the lower border of the window) say how much free space you have?

---

### Post by nuke_fluke on 2008-08-31
> **GepettoBR said:**
> 
 When you open one of the new partitions in Nautilus, does the status bar (the lower border of the window) say how much free space you have?

Yes ....it does
It shows 16.4 GB of free space in the drive...
But all the free space is in that particular folder...

When I tried to copy a 2 GB folder into it, it gives the following error message:
```

Error while copying
The folder "MUSIC" cannot be copied because you do not have permissions to create it in the destination.
```

EDIT:
Now my problem is solved....
I had used ext3 filesystem for the partition...
Now when I used fat32 filesystem, its working normally

---

### Post by GepettoBR on 2008-08-31
The ideal solution still is to use ext3 partitions, since they have several benefits compared to fat32, both security-wise and practically - for one, they don't fragment, which is a huge bonus. Now that I know it's a permission issue, I can offer you a simple solution (if you're willing to reformat the already-working fat32 partitions into ext3 all over again, that is). The problem appears to be that only the root user has permission to use the partition. This has noting to do with the lost+found folder, I assure you.

If you're running GNOME (Ubuntu), run this in a Terminal: ```
gksudo nautilus
``` If you're on XFCE (Xubuntu), replace "nautilus" with "thunar" and if you're on KDE (Kubuntu) use ```
kdesu konqueror
``` or ```
 kdesu dolphin
``` instead. You will be prompted for your password, type it and confirm.

Navigate to the folder where you mounted the partitions (if you don't know where you mounted them, then they're probably in /media/partition-name or /mnt/partition-name by default), right-click the root folder of the partition and select properties. Under the Permissions tab, make sure that the Owner is your username and that you have full read and write permissions to that folder. Then, exit. From now on you can normally use the new partitions and have the benefits of a journaling filesystem.

---

