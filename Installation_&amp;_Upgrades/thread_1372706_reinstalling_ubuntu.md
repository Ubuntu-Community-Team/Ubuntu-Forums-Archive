---
title: "reinstalling ubuntu??"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by allmightymoo on 2010-01-04
ok so i have a question...if i already have ubuntu 9.1 on my computer and run the install again using the cd can i overwrite or delete the ubuntu os already on it? if not how can i uninstall ubuntu w/o effecting my win7 os?

---

### Post by adam814 on 2010-01-04
Sure you can.  Your / will have to be formatted to re-install, but if you have other partitions you can choose which to format and which not to format.  I have a separate /home I haven't formatted since Hardy and I'm now on Karmic.  As long as you don't set your Windows partition to be formatted it shouldn't be affected.

---

### Post by allmightymoo on 2010-01-04
sweet ok. So i can format it when i run the disk at startup? like it gives me that option to just format the ubuntu partition only? if not i dont know how to format just the ubuntu partition haha...

p.s. Thanks!

---

### Post by adam814 on 2010-01-04
If you run the installer it'll ask about it under the "partitioning" section.  You'll just select the ubuntu partitions you already used.  I'm assuming you're not using wubi, that would change things.

---

### Post by ubudog on 2010-01-04
Yeah, all you need to do is start with the cd, then when the partitioning part comes up, select the "Guided - Use entire disk".  But this will all change if you are using wubi.  This would get rid of your windows install. (not that thats a bad thing) :)

---

### Post by allmightymoo on 2010-01-04
Ok thanks! no not using wubi

---

### Post by ubudog on 2010-01-04
> **allmightymoo said:**
> Ok thanks! no not using wubi

OK.  Good luck.  But if you want to keep your windows install that you have now, select the "Install Ubuntu next to the other OS'es"  (not the actual option, but similar)  Good luck!

---

### Post by allmightymoo on 2010-01-04
ok i'm at that partitioning part but if i can only install it next to the other OSes i'll have 2 ubuntus which i dont want cuz one of them is unuseable this is why i want to reinstall it...so is there a way to overwrite the current ubuntu OS while still keeping windows? (to be clear i want to get rid of the ubuntu 9.1 i currently have then install it again using the disk but i want to keep win7)

---

### Post by raymondh on 2010-01-04
> **allmightymoo said:**
> ok i'm at that partitioning part but if i can only install it next to the other OSes i'll have 2 ubuntus which i dont want cuz one of them is unuseable this is why i want to reinstall it...so is there a way to overwrite the current ubuntu OS while still keeping windows? (to be clear i want to get rid of the ubuntu 9.1 i currently have then install it again using the disk but i want to keep win7)

If you can post a screenshot of that gparted step (step 4 or 5) in the installer ... or post back results (from terminal) of 

```
sudo fdisk -l
```

Then the forum will have a clearer picture of your HD set-up and will be able to tell you exactly which partition to re-format and mountpoint root.  Tip:  Ubuntu will have a 'ext' format (Ext3 or Ext4) and root will be defined by a / (slash)

Neverthless, DO NOT CLICK TO HIGHLIGHT any NTFS or FAT  formatted partition.  Chances are that is your win7 and, possibly, your recovery partition/s.

---

### Post by allmightymoo on 2010-01-04
ok well i was thinking i would use disk manager in windows to delete the ubuntu partitions to create free space and then use win7 repair disk (that i'm getting from here >> [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)) to fix windows start up...would that work? i would then reinstall ubuntu of course ;)

---

### Post by adam814 on 2010-01-04
I don't know for sure if this disk manager will do what you need. I do know gparted will and it's on almost every Linux LiveCD. Why not just start the LiveCD "without making changes to your computer" and go to System > Administration > Partition Editor and delete your ext4 and swap partitions there and install again into the free space?

---

### Post by raymondh on 2010-01-04
> **allmightymoo said:**
> ok well i was thinking i would use disk manager in windows to delete the ubuntu partitions to create free space and then use win7 repair disk (that i'm getting from here >> [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)) to fix windows start up...would that work? i would then reinstall ubuntu of course ;)

If you decide to do this ...

1.  Fix the MBR first and make sure you can boot into windows
2.  Use the disk management utility to delete the ubuntu partition (root, swap and any EXTENDED partition that houses either root and/or swap)

If you delete the ubuntu partition/s before fixing the MBR, you risk a booting error.

Regards,

---

### Post by allmightymoo on 2010-01-04
Oh...so boot the repair disk first and repair start up (is that what u mean by fix the mbr? cuz the grub loader works i just cant boot ubuntu in case that was unlcear) 

Ok so i boot the repair disk, repair start up (which will get rid of the grub loader thing), then in window delete the ubuntu partition. Right? sorry if i'm repeatingmyself just dont wanna mess anything important up haha..

---

### Post by allmightymoo on 2010-01-05
> **adam814 said:**
> I don't know for sure if this disk manager will do what you need. I do know gparted will and it's on almost every Linux LiveCD. Why not just start the LiveCD "without making changes to your computer" and go to System > Administration > Partition Editor and delete your ext4 and swap partitions there and install again into the free space?

Ok so in gparted i delete ext4 but what do u mean by 'swap partitions'? After i delete ext4 i just install ubuntu again? what about linux-swap? do i delete that to or is that what u mean by swap? haha i'm kinda confused...surprise. ;)

---

### Post by raymondh on 2010-01-05
> **allmightymoo said:**
> Oh...so boot the repair disk first and repair start up (is that what u mean by fix the mbr? cuz the grub loader works i just cant boot ubuntu in case that was unlcear) 

Ok so i boot the repair disk, repair start up (which will get rid of the grub loader thing), then in window delete the ubuntu partition. Right? sorry if i'm repeatingmyself just dont wanna mess anything important up haha..

You've got to decide what route to take.

a) Either you install 'over' your existing ubuntu or;
b) You use win7 to delete and then re-install or;
c) you use gparted to delete and then re-install.

If (a) ... that will entail a MANUAL install.  Kindly type and ppost back the results of 

```
sudo fdisk -l
```

and the forum can visualize your HD and assist you in identifying the proper partition (which was your query in the first place).

If (b) ....  see this [link]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1") to help you understand what you are about to do.  

If (c) ... make sure you have the disc downloaded first.

No matter what you decide, there are no guarantees when working with partitions so ....... have a working/tested back-up of your files.

---

### Post by presence1960 on 2010-01-05
> **allmightymoo said:**
> ok well i was thinking i would use disk manager in windows to delete the ubuntu partitions to create free space and then use win7 repair disk (that i'm getting from here >> [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)) to fix windows start up...would that work? i would then reinstall ubuntu of course ;)

If you are reinstalling Ubuntu why bother using that disk to put windows on MBR? The only reason to do that is if your windows would not boot from GRUB.

You would be better served if you partition from gparted on the Ubuntu Live CD or make a [gparted Live CD]("http://gparted.sourceforge.net/livecd.php")

Not being smart but since you are using Linux, why not learn how to do things in Linux rather than windows?

---

### Post by allmightymoo on 2010-01-05
[SIZE=1] ```
sudo fdisk -l
```

This is what i get...

[B]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf608e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23767   190908396    7  HPFS/NTFS
/dev/sda2           28985       30401    11380736    7  HPFS/NTFS
/dev/sda3           23768       28984    41905552+   5  Extended
/dev/sda5           23768       28764    40138371   83  Linux
/dev/sda6           28765       28984     1767118+  82  Linux swap / Solaris

Partition table entries are not in disk order[/B][/SIZE] 
Now what? :) i want to install over my existing ubuntu b/c i cannot boot into it.

---

### Post by adam814 on 2010-01-05
If you're using gparted and doing it from the LiveCD you'd delete these partitions in this order:
```
/dev/sda5
/dev/sda6
/dev/sda3
```
Then install Ubuntu into the free space.

---

### Post by allmightymoo on 2010-01-05
ok so i am using the live cd so i got to system>>admin>>gparted then delete those in that order? Right? I dont do anything with the terminal at this point right? just gparted?

---

### Post by adam814 on 2010-01-05
Yeah, that should work.  The order isn't set in stone, but you can't delete the extended partition (/dev/sda3) until you delete the two logical partitions in it (/dev/sda5 and /dev/sda6).  You wouldn't need to do anything else in the terminal at this point.

From there you could start the installer and simply install into the un-partitioned free space.

---

### Post by allmightymoo on 2010-01-05
In gparted program on ubuntu live cd i have the option of deleting dev/sda5 but i can only 'swap off' and 'manage flags' on dev/sda6 and i can only manage flags on dev/sda3...once i delete dev/sda6 will i be able to delete the others? what do i do?

---

### Post by adam814 on 2010-01-05
Ah, hadn't thought of it.  You need to "swapoff" /dev/sda6 before you can delete it.  Once you delete it (and /dev/sda5) you'll be able to delete /dev/sda3

---

### Post by allmightymoo on 2010-01-05
Ok thanks! So i deleted the partitions but it says its pending...but its been pending for a while and theres no progress bar so i cant tell if anything is actually happening...a screenshot is attached...

---

### Post by raymondh on 2010-01-05
> **allmightymoo said:**
> Ok thanks! So i deleted the partitions but it says its pending...but its been pending for a while and theres no progress bar so i cant tell if anything is actually happening...a screenshot is attached...

Did you click APPLY (check) in the tools above?

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

Raymond

---

### Post by allmightymoo on 2010-01-05
IT WORKED!!! i have successfully reinstalled ubuntu!!! Thanks to everyone who helped!!!! :D

---

### Post by ubudog on 2010-01-05
Any time.

---

