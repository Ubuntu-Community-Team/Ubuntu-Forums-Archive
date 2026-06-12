---
title: "Recover single partition without losing others"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by thecoldheartofspac on 2013-11-17
I dual booted with linux mint 13 a while ago on my grandma's computer that had vista. I decided that since vista crashes so much and is nearly unusable, I'd install xp. I got everything ready with gparted, but when I installed xp, it corrupted the linux partition. I had some important data on there and found testdisk which I started, but I don't get how to recover only that single partition. If anyone could help, I'd be very great full! Thanks!

---

### Post by oldfred on 2013-11-18
Did Windows do like usual and make a partition in the extended partition disappear. Or worse did you overwrite the Linux partition.
Windows does not correctly see Linux partitions and during install it rewrites partition table often forgetting to include the linux partition.

Testdisk will show many or all old versions of partition table. Best if you know where on drive and approxite size. Actual best is fdisk output or Boot-Info report from before to know exact sectors.
If you have empty space in an extended partition that probably was your Linux partition. Testdisk should let you just recover that, but do not change status of other partitions.

Best to backup current partition table and post details here as another backup.
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Also post the contents of PTsda.txt in code tags. You can use # icon in advanced editor to add code tags around highlighted text.
Also post this:
 sudo parted /dev/sda unit s print

---

### Post by thecoldheartofspac on 2013-11-18
Thanks for the quick reply! Ya. the main sections of the enxtended partition is "unallocated" but the rest is fine. With the first command #sudo sfdisk -d /dev/sda > PTsda.txt# I got #Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently# on the second
 #Number  Start       End         Size        Type      File system     Flags
 1      63s         112454s     112392s     primary   fat16           diag
 2      112640s     66555903s   66443264s   primary   ntfs            boot
 3      66555904s   185708543s  119152640s  primary   ntfs
 4      185708544s  488280063s  302571520s  extended
 5      185710592s  202147839s  16437248s   logical   ext4
 6      486207488s  488280063s  2072576s    logical   linux-swap(v1)"
  
in testdisk I got
#Disk /dev/sda - 250 GB / 232 GiB - CHS 30395 255 63#

Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1     6 254 63     112392 [DellUtility]
 2 P FAT32 LBA                7   0  1  4184 254 63   67119570 [NO NAME]
 3 P Linux                11559 242 12 12583  30 55   16437248 [otherinstall]
 4 E extended LBA         12583  31  1 30394 254 63  286147827
 5 L Linux                12583  63 25 30264 226 42  284055552 [mint13]    <---- the one I want to recover
 6 L Linux Swap           30265   4 12 30394   6 60    2072560#

I don't get entirely how to use testdisk, so any help that can be given there would be greatly appreciated as opposed to me experimenting and destroying it all. Thanks!

---

### Post by nerdtron on 2013-11-18
I don't think you messed up your partitions. Windows XP just blew GRUB away. You can still access you data once you boot from a LIVE CD.
Or a better solution would be to restore GRUB.

---

### Post by thecoldheartofspac on 2013-11-18
I've checked it with gparted and every partition is fine. Xp and vista both boot fine through grub. I would show you a screenshot, but I don't know how to save it to the disk to upload. I'm typing this and all other messages from a smartphone so I can't really show you anything but text. 
      I'm only 15, and I usually learn about linux one or two topics at a time in different sections as my computer and others I fix have problems or break. This is the fist time I have had a single partition with important info corrupted without being overwritten and other thing I need to keep intact, so it's my first time learning about this program. Thanks for the guess though :)

---

### Post by oldfred on 2013-11-18
Ignore cylinder boundry error. That was for old IDE drives years ago. 

I am having a bit of an issue with the differnece between the fdisk and testdisk output. Testdisk does use the old CHS - cylinders, heads, sectors which are not really used any more. 
Fdisk shows your extended sda4 with a current sda5 as a Linux ext4, then a gap (missing partition?) and then sda6 your swap.
But testdisk is not showing that. It has an extended, with just one ext4 labeled as Mint13 and swap inside the extended. Normally a deleted partition had a D and you have to change to L or P for logical or primary. All logical partitions must be in one extended partition.
Did you have two Linux partitions in your extended or one large one and the current small one is not correct?
Have you tried deeper search in testdisk?

        Guide to Forum features ** INCLUDES: Beans, titles, searching, and more 
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
How to attach file, screenshots
[http://ubuntuforums.org/showpost.php?p=12229098&postcount=4](http://ubuntuforums.org/showpost.php?p=12229098&postcount=4)
[http://i.stack.imgur.com/0E6qS.png](http://i.stack.imgur.com/0E6qS.png)

---

### Post by thecoldheartofspac on 2013-11-19
The one that says "otherinstall" is the other linux partition. It's just where I plan to put any OS I want to experiment with. I haven't tried deeper search, but I have found everything I need to. Here's the picture of gparted and testdisk. Hopefully it clears up what I've been trying to say.  The unpartitioned part is where my main linux should be. everything else should stay intact. Thanks for the link showing how to upload photos ;) For some reason I couldn't see it on my computer untill I used firefox.

---

### Post by oldfred on 2013-11-19
Your testdisk does not show any NTFS partitions and has otherinstall as primary. But your current gparted shows otherinstall as logical and the space that is you mint as unallocated. Usually testdist shows all the old combinations of partitions and you have to pick & choose a set that is correct and does not overlap.

Since it is only one partition I might just try gparted's recovery or parted's rescue. I think gparted is doing the same thing as parted (gparted is really the gui for parted).
 
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted


[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by thecoldheartofspac on 2013-11-19
Okay. I just tried to use parted, but when the first part didn't work, I tried doing ```
check 4
``` and I got ```
Error: Partition /dev/sda4 is being used. You must unmount it before you modify it with Parted
``` I checked and the hdd isn't mounted. If gparted is based on parted, I'd guess that's why it didn't do anything either the first time I tried.

---

### Post by oldfred on 2013-11-19
If swap is in extended partition the live system mounts swap to speed up processing and that in effect mounts the entire extended partition.
You need to swap off on swap. Click on swap and right click.

---

### Post by thecoldheartofspac on 2013-11-19
okay, I did that with parted, but then instead, it started trying to use the cd instead of the hdd. Also, I got testdisk mostly working and mostly figured out, but now, it won't let me bring back all my wanted partitions. That's the picture on the attachments. I see that "D" means delete, and the rest are various options, but it will only let me select a few at a time. I think that it's not counting the extended partition as extended, because it only allows for 4 to come back. Is there a way to make this detect that the linux partitions are in extended?

---

### Post by oldfred on 2013-11-19
You do not explicitly set the extended. Put both linux and the swap as logical as it will make a correct extended.
All logical have to be next to each other so they all can be in one extended partition.
You can only have 4 primary and the extended counts as one of the primary. 
So you should specify 3 primary and the rest as logical. 
None of the choices can overlap as you show 3 starting about at 7 and going to 4142, so only one of those three can be selected. Choose the correct one probably OS but I do not know for sure.

---

