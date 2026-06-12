---
title: "i want to install dualboot, but i already have 4 primary partitions"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by doron387 on 2011-01-16
hi,
after a long time with wubi on my laptop i have decided to install it in dualboot with win7.
i have already deleted the wubi install.
i am running right now from a live usb ubuntu 10.10.
when i open gparted i get that i have already 4 primary partitions.
as i understand, for installing ubuntu i must have a primary partition for it.
the problem is that 2 of my partitions (sda1 = c: = NTFS (win7) & sda2 = d: = NTFS (data) ), are already full of data and i don't want to erase them.
except for these 2, i have 2 more partitions, which are primary ones, and i don't know what they are.

can somebody help me figure out what are these 2 last partitions ?
should i delete one of them ?
what does an extended partition mean ?
is there a solution ?

attached a screenshot of gparted, might help you figure out what's goin' on

thanks
doron387

EDIT : in the last post i summarized every step that i did.

---

### Post by Quackers on 2011-01-16
It's possible that sda3 is some kind of backup image - maybe.
sda4 is as it says, unknown. It's only 15MB in size - not very big! What does Windows say is in it?
Linux doesn't need a primary partition. A logical partition will be fine. However, you still need to delete a partition before you can create an extended partition containing logical partitions.

---

### Post by ptrinder64 on 2011-01-16
Is your laptop by chance an HP? I was trying to set up a tri-boot in the following thread and resolved it - maybe some of the advice in this thread may be of use:

[http://ubuntuforums.org/showthread.php?t=1535160](http://ubuntuforums.org/showthread.php?t=1535160)

---

### Post by malspa on 2011-01-16
Can you mount that FAT32 partition and see what's in there?

Anyway, this shot of my sda drive using GParted might help.  If you don't need what's currently on sda3 and sda4, or if you can back it up and replace it later, you can repartition and make your third or fourth partition an extended partition.  Then you can add logical partitions to that extended partition, as space permits.

---

### Post by doron387 on 2011-01-16
thanks Quackers,

win7 shows in "computer" just the 2 big partitions (C:,D:)
i do not know what are the two others (the 10 Gb and the 15 Mb), if someone knows it will be helpfull.
as i am using a netbook, i didn't get a win7 installation cd, so i would'nt like to erase essential info that i mgith need one day.

**so what are my options now ?**

let's say that i delete the d: partition (after backing up the data to an external hd), i will have 3 primary partitions.

**what should i do now ?** (I will need a data partition available from win7 as well as from ubuntu)  

thanks
doron387

---

### Post by doron387 on 2011-01-16
nope, it's an Asus 1201N.
a nice friend for the long days out of home (i am a tour guide....)

---

### Post by Quackers on 2011-01-16
If you backup what's in D: you can delete it. You will then have approx 195GB unallocated space. In this space you can create an extended partition containing as many logical partitions as you want (including a new data partition!). I would delete it using Windows, but I would create new partitions with gparted.
You still need to find out what's in the other partitions though, really.

Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ggarron on 2011-01-16
+1 to Quackers suggestion.

That way you will recover those 21 Gigs wasted (unallocated).

Create there then a logical partition NTFS for your Data, and another ext3 or ext4 for Linux.

Be sure you backup everything on D before doing that.
Also, take care Windows does not need anything from there to boot.

Good luck!

---

### Post by doron387 on 2011-01-16
well Quackers, 
thanks a lot for the detailed answer.
i am currently copying the content of the D: drive (sda2, NTFS) to an external hd. (150 Gb to go.....)
i understand from your post that in an extended partition the number of logical partitions is unlimited, am i right ?)

if it is indeed unlimied, so i would like your opinion about the following logical partitions :

extended partition :
ubuntu
**/root** 10 gb ext4 (is it the correct file system ?)  
**/swap** 3 gb swap (is it really needed when i have 2 gb ram ?)
**/home** 10 gb ext3 (is it ..... ?)
**data** 150 gb (**which file system** will be read from both os's ? and where to mount it ?)

and the last question : 
when i will be in win7, will i see just C:, or also a D: (**i wish to have a D: for the data**)

thanks
doron387

---

### Post by Quackers on 2011-01-16
/root is good
/home is ext4 by default nowadays
If you aren't going to use hibernate you can probably do without a swap, but i any case 2.1GB is enough
Data partition is I believe advised to be FAT32, but check that! Maybe somebody could confirm that please?
You should see D: in Windows

Please see my edit to post #7 and post the details of the boot script

---

### Post by doron387 on 2011-01-16
well Quackers, 
thanks a lot for the detailed answer.
i am currently copying the content of the D: drive (sda2, NTFS) to an external hd. (150 Gb to go.....)
i understand from your post that in an extended partition the number of logical partitions is unlimited, am i right ?)

if it is indeed unlimied, so i would like your opinion about the following logical partitions :

extended partition :
ubuntu
**/root** 10 gb ext4 (is it the correct file system ?)  
**/swap** 3 gb swap (is it really needed when i have 2 gb ram ?)
**/home** 10 gb ext3 (is it ..... ?)
**data** 150 gb (**which file system** will be read from both os's ? and where to mount it ?)

and the last question : 
when i will be in win7, will i see just C:, or also a D: (**i wish to have a D: for the data**)

thanks
doron387

---

### Post by doron387 on 2011-01-16
wow, you are fast replier, again thanks.

does hibernate work in ubuntu these days ? i have seen a lot of posts about problems with it....
if it works, then, i do want to have the option, so i need 2XRAM ?

about the Data partition, won't NTFS be the best ? (for 4+ Gb files like iso's)

what will i see in D: ? (just the data ?)

about the  [COLOR="RoyalBlue"]sudo bash ~/Desktop/boot_info_script*.sh[/COLOR], i could do it just after finishing the backup (it is being done in the win7 os, 101 Gb to go...)

thanks
doron387

---

### Post by Quackers on 2011-01-16
Not sure about NTFS or FAT32 as I don't have a shared data partition. Hopefully someone can help us out there.
Hibernate works in one of my installations, but not in the other 2, properly. 
2.1 or 2.2GB of swap should be enough.

Ok on the boot script. It may help us identify what's in sda3 and sda4 - maybe.

Which version of Ubuntu are you installing?

---

### Post by doron387 on 2011-01-16
my machine is an asus 1201n netbook,
as i understood from asus 1201n forum a few minutes ago, the 10 gb partition is a recovery for win7 and the other one is still unknown.

i will create a 2.2 gb swap, to try hibernation.
i have been using 10.10 for a while in wubi and it worked great so i am making the move for a real install.
hopefully tonight...

thanks for the great support.

doron387

---

### Post by Quackers on 2011-01-16
With the 10.10 installer you should definitely use the "specify manually" option in the partitioning stage of the process. The "install alongside" has been known to eat existing OSes.

---

### Post by doron387 on 2011-01-16
got it.
i'll use the manually "specify manually" option.
(41 gb to go.... with the data backup)
i'll post when it's done and after partitioning.
thanks
doron387

---

### Post by Quackers on 2011-01-16
Hokey cokey :wink:

---

### Post by doron387 on 2011-01-16
well, 
i did delete one ntfs partition (after backing up all the data)
then, i created with gparted an extended partition with ext4 for root, ext4 for home, swap for swap and ntfs for data.
i installed ubuntu 10.10 using manually partitioning.
in win7 i used the method mentioned in :
[http://www.blogsdna.com/6654/4-steps-to-hide-any-drive.htm](http://www.blogsdna.com/6654/4-steps-to-hide-any-drive.htm)
for changing the name of the data partition back to D:
and for now, everything woks fine.

consider it as SOLVED

---

### Post by Quackers on 2011-01-16
Excellent! :-) Well done!
Please mark the thread as solved using the Thread Tools near the top of the [age, thanks.

---

### Post by ggarron on 2011-01-17
> **doron387 said:**
> well, 
i did delete one ntfs partition (after backing up all the data)
then, i created with gparted an extended partition with ext4 for root, ext4 for home, swap for swap and ntfs for data.
i installed ubuntu 10.10 using manually partitioning.
in win7 i used the method mentioned in :
[http://www.blogsdna.com/6654/4-steps-to-hide-any-drive.htm](http://www.blogsdna.com/6654/4-steps-to-hide-any-drive.htm)
for changing the name of the data partition back to D:
and for now, everything woks fine.

consider it as SOLVED

Great!, happy to hear that!.

---

