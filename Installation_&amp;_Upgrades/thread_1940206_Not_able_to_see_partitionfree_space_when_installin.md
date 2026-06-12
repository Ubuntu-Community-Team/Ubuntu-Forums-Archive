---
title: "Not able to see partition/free space when installing"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by cyanide911 on 2012-03-13
This is my current setup:

[IMG]http://i.imgur.com/IqV6q.png[/IMG]


But this is what GParted shows and Ubuntu 11.10 live CD shows the same:

[IMG]http://i.imgur.com/wdPMk.jpg[/IMG]


So my Windows 7 C: drive is shown in both GParted and Windows 7, but ALL the remaining space is clubbed into one big mass in Gparted and Ubuntu. It doesn't show any of it's partitions or the free space I've created.

Also, the free space of that 550gb mass is clearly reported wrongly, as you can see.

What do I do to solve this? I really want to get Ubuntu running quick, I've never had this problem before when I've installed Ubuntu. 


Thanks!

---

### Post by Bucky Ball on 2012-03-13
In Gparted, click where it says '/dev/sda' in the top right and choose which physical drive you want to look at. It's not setup the same as the Windows one. ;)

(sda = Disk 0 incidentally; sdb will be Disk 1, etc.)

---

### Post by cyanide911 on 2012-03-13
I have only one HDD, the other dev/sda available to select is my 2GB Pen drive.

---

### Post by Bucky Ball on 2012-03-13
Okay. Think I have it. You already have 4 primary partitions; that is the limit. You have a problem. You are going to need to delete one of them and create an extended partition and install Ubuntu into that (Ubuntu doesn't mind but Win must be on a primary partition, preferably first partition, first drive). 

It's a bit of a time consuming drag, but you could make the recovery disks for your machine (HP has a facility in Windows to do this), kill the recovery partition (giving you three primary partitions), do whatever shrinking, expanding and shifting of partitions you need to and then create an extended partition with the free space in it. That is where you would install Ubuntu. You can only have four primarys BUT you can have as many virtual disks (partitions) as your machine can handle *inside* an extended partition (the extended partition counting in this case as your fourth primary). Hope you can follow all that. Just ask for clarification. ;)

This could be your issue (although I've never seen this outcome before). One thing's for certain: You can only have four primary partitions on one physical drive.

---

### Post by darkod on 2012-03-13
Your disk is Dynamic. Look in Disk Management to the left where it says Disk 0, Dynamic.

That is a MS format, if you try to create more than 4 primary partitions it will usually convert it to dynamic.

Ubuntu will not install on dynamic, it doesn't understand it correctly, hence the difference in the disk layout.

If you want to, you might be able to revert the disk to Basic without data loss, I think people have used something like Partition Wizard or similar. Investigate first on google how you can do that and what works. It's best to have a backup just in case.

---

### Post by oldfred on 2012-03-13
lI am not sure you can convert back. Most users are still within the 4 partition limit with partitions that have data so it is straight forward to convert back. But you have data in more partitions. Not sure if these tools move data or what. I was suggesting mini-tool but it turns out only the paid version works for dynamic conversion. It does look like the free version of EASEUS does work.

Backups become even more important if you want to convert. The only other choice is to use another drive for Ubuntu and not be able to read any of the Windows data in the dynamic partitions.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by cyanide911 on 2012-03-19
I can't get rid or any other partitions, so I guess my only other way is to delete the recovery partition.

I have the recovery media with me. But just in case, I'm thinking of making a drive image of the recovery drive. 

So in case I need the recovery partition again, I'll just delete the Ubuntu parition, and restore that recovery partition.

Any flaw in this plan?


I'll get back with results...

---

### Post by Mark Phelps on 2012-03-20
If you want to be able to restore Windows and remove the Recovery partition, then I would suggest the following:
1) Download and install the FREE version of Macrium Reflect (MR) in MS Windows
2) Launch MR and image off the Windows install to an external drive
3) Use the MR feature to create and burn a Linux Boot CD

With this, you have the means to restore your Windows install.  You no longer need your Recovery partition.

---

### Post by darkod on 2012-03-20
1. If you want to have the option to restore to factory state in the future, create the restore DVDs (there should be an option in the software) and that's it. But they will be worthless anyway for anything else but factory restore.

2. If you want to have an up to date backup only, use the built in Backup software or what ever you prefer, and create the rescue CD + current full backup pair. With the rescue CD you can boot and restore your full backup from a usb hdd or similar. That would restore your current setup including your software and data, not just a factory state.

On another note, did you notice you actually have 6 partitions on that disk? So if having a maximum of 4 is the limit to convert back to Basic disk, you need to delete 2 not 1.

Not to mention that after converting it to Basic you will have the maximum of 4 used up so you need to delete one more to be able to create logical partitions (extended partition).

---

### Post by cyanide911 on 2012-05-01
Sorry for bringing this up after a long long time, but here's the deal now.

I factory resetted my whole laptop. Now this is how my hard disk looks:

[IMG]http://i.imgur.com/GS7Ht.png[/IMG]

I want to make a total of 4 partitions out of the C: drive. 

1. 80GB for the C: Windows Partition
2: 200GB for data
3: 200GB for data
4. 100GB for Ubuntu.

But reading the above replies, there doesn't seem to be a way to achieve this! 
Is there no way? Since I have 4 partitions already (without making the above mentioned further partitions), I simply can't install Ubuntu without deleting one of these?

---

### Post by darkod on 2012-05-01
Correct, you can't install without deleting at least one partition.

From earlier cases, you should be OK if you delete the HP_TOOLS partition. If you want to, you can also create a set of recovery DVDs with the software in windows, and after that you can also delete the recovery partition. You will have the DVDs to use if you need them.

After that, in windows Disk Management you will have to shrink the C: partition to 80GB. That will leave the rest of the space as unallocated (unpartitioned).

Install ubuntu using the manual method with 100GB root partition and a swap partition (sized as you want). Create them as logical partitions, NOT primary.

After ubuntu is running too, simply create the two 200GB ntfs data partitions, also as logical. That's it.

---

### Post by jadtech on 2012-05-01
first of all you can safly remove hp=tools this is totally not needed and if you ever find a need in the furture you can get and down load it from there  site ..

this will give you only 3 primary partitions  then you can shrink the window partition as you want for your ubuntu and you 2 data partitions you want ..

do not partition this free space at all  with the windows partition tool once you do the removal of hp tools partition and shrink the windows down  the way you want reboot let windows run chkdsk as it will  then use the ubuntu live cd go to gparted and make one large extendended partion of the free unused space ..

then you can make 1 ext4 partition of 100 gb for you unbuntu install one linux swap of at least 1 or 2 gigs then take the remander and make  the other 2 data parttitions you want .. 


you should do a defrag and cckdsk  before you start after recovery and reinstall your hard drive will be like 60% fragmented 

it all many add up to a little less or more  then you plan but  you can have as many logical partitions as you  want ..

gparted will see set up will be sda1 - sda7 as veiwed in gparted 

i have neveer done this before  but I am getting ready I have an HP same issue have to get rid of one primary partition and hp tools is least if at all  needed ..

---

### Post by gordintoronto on 2012-05-01
Issue 41 of Full Circle Magazine, page 36, has instructions on how to install Ubuntu in this exact situation.

---

### Post by cyanide911 on 2012-05-02
> **darkod said:**
> Correct, you can't install without deleting at least one partition.

From earlier cases, you should be OK if you delete the HP_TOOLS partition. If you want to, you can also create a set of recovery DVDs with the software in windows, and after that you can also delete the recovery partition. You will have the DVDs to use if you need them.

After that, in windows Disk Management you will have to shrink the C: partition to 80GB. That will leave the rest of the space as unallocated (unpartitioned).

Install ubuntu using the manual method with 100GB root partition and a swap partition (sized as you want). Create them as logical partitions, NOT primary.

After ubuntu is running too, simply create the two 200GB ntfs data partitions, also as logical. That's it.

I shrunk C: to 80 Gigs, Installed Ubuntu in a logical partition of 100 Gigs. Now I have 400GB of unallocated space.

If I try to partition in Windows, it says “You cannot create a new volume in this unallocated space because the disk already contains maximum number of partitions”.

Would I be able to get past this error if I try to create logical partitions via GParted? I can't even get Ubuntu to install GParted because of yet another issue ([http://ubuntuforums.org/showthread.php?p=11898457#post11898457](http://ubuntuforums.org/showthread.php?p=11898457#post11898457))

I can't run GParted's live CD because of ANOTHER issue for which I have no patience to explain right now. 


Is there *any* other way to create a SINGLE partition out of those 400 GBs. I really need those.

---

### Post by darkod on 2012-05-02
Boot ubuntu and in terminal post the result of:
sudo parted /dev/sda unit s print

---

### Post by oldfred on 2012-05-02
If you are behind a firewall that restricts access you need to talk to the sysadmin of your network to see if they will let you access the Ubuntu sites.

You have gparted on your install liveCD/USB. And you normally have to run gparted from the liveCD as you have to unmount all partitions to edi them. Even then liveCDs use the swap partition to speed things up, so you may have to click on the swap partition and right click swap off.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by cyanide911 on 2012-05-02
> **darkod said:**
> Boot ubuntu and in terminal post the result of:
sudo parted /dev/sda unit s print

Here:

```
Number  Start        End          Size        Type      File system     Flags
 1      2048s        409599s      407552s     primary   ntfs            boot
 2      409600s      164511162s   164101563s  primary   ntfs
 4      164511742s   340486143s   175974402s  extended
 5      164511744s   324665343s   160153600s  logical   ext4
 6      324667392s   340486143s   15818752s   logical   linux-swap(v1)
 3      1221277696s  1250050047s  28772352s   primary   ntfs

```


[IMG]http://i.imgur.com/rSM9w.png[/IMG]


I'm willing to reformat the Ubuntu and swap partitions if that's what it takes to do this right...

---

### Post by darkod on 2012-05-02
I was under the impression you could do it like this, but obviously not. The problem is that the unallocated space is OUTSIDE the extended partition, /dev/sda4.

Right-click /dev/sda4 and select to resize it. Drag it's right border to include the 420GB. Once that space is INSIDE /dev/sda4, you can create logical partitions.

Or, you can try with parted in the command line, it might be easier or more difficult, depending what you are used to (GUI or command line).

With parted you can try creating a logical partition starting from the next sector after partition #6, with a size of as many sectors as you want (1 sector is 512B).

---

### Post by Bucky Ball on 2012-05-02
You have the maximum four partitions: 3 primarys and an extended. That is your limit.

Your problem is that the free space is not inside the extended partition so if you try to partition that it *will* be the fifth partition. Expand the extended partition to include the 400Gb free space so it is inside the extended partition then fire away; you will have no problems ... ;)

---

